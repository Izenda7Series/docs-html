=================
Load Balancing
=================
|
|

Introduction
------------------------------------------

The Izenda application can be load balanced to offer better performance and scalability.
The most common scenario would be to load balance the API among two or more servers. The diagram below assumes that SSL is terminated by the load balancer. To clarify, traffic to the load balancer is encrypted and the load balancer sends unencrypted traffic to the API server(s) in a trusted network

|

Configuration
----------------------------------------------------
|

#. Update the WebApiUrl value in the izenda_config.js file with the IP or host name of the load balancer. 

#. Update the WebApiUrl in the [IzendaSystemSetting] table with the hostname or IP of the load balancer.

.. figure:: images/load-balancing1.png

Scheduling
----------------------------------------------------
|

The Izenda Scheduler will store scheduling information in RAM of the server by default. If you are using any type of a distributed enviroment where there is more than one instance of the Izenda API (webfarms, etc.) you will need to use a database (ADO.NET job store) for storage of the scheduling information. Please follow the instructions below for setting up the scheduler to run in a distributed environment:

1. Download the creation script for your database type: |br|
Download quartz database script ~\database\tables\tables_sqlServer.sql inside Quartz.NET-3.0.7.zip. Use that script to create the database on your DB server. https://github.com/quartznet/quartznet/releases/tag/v3.0.7 |br|

2. Create the database (by default the table prefix "QRTZ_" but this can be set in the config) |br|

.. note::
	- If using the .NET Core API resources, the Quartz configuration in steps 3 and 4 will instead be in a separate *quartz.config* file which can be downloaded `here <https//izenda.com/utilities/quartz.config>`_.
	- The *quartz.config* file should be placed in the root of the Izenda API directory.

3. Add quartz config section into Web.config |br|  
<section name="quartz" type="System.Configuration.NameValueSectionHandler" /> |br|

4. Add quartz section content into Web.config (under the  </system.webServer> tag) and replace the value of config quartz.dataSource.QuartzNET_DS.connectionString by your server name (Server), user (User Id) and password (Password) to access quartzNET307 database. |br|

.. code-block:: xml
	:linenos:
	
	  <quartz>
		<add key="quartz.scheduler.instanceName" value="Izenda_Quartz" />
		<add key="quartz.scheduler.instanceId" value="Izenda_API" />
		<add key="quartz.threadPool.threadCount" value="10" />
		
		<add key="quartz.jobStore.type" value="Quartz.Impl.AdoJobStore.JobStoreTX, Quartz" />
		<add key="quartz.jobStore.driverDelegateType" value="Quartz.Impl.AdoJobStore.SqlServerDelegate, Quartz"/>
		<add key="quartz.jobStore.tablePrefix" value="QRTZ_"/>
		<add key="quartz.jobStore.lockHandler.type" value="Quartz.Impl.AdoJobStore.UpdateLockRowSemaphore, Quartz"/>
		<add key="quartz.jobStore.dataSource" value="QuartzNET_DS"/>
		<add key="quartz.dataSource.QuartzNET_DS.connectionString" value="[YOUR CONNECTION STRING HERE]"/>
		
		<!-- If you are using a database other than SQL Server, be sure to use the appropriate provider for your database 
		
			SqlServer - SQL Server driver for .NET Framework 2.0
			OracleODP - Oracle’s Oracle Driver
			OracleODPManaged - Oracle’s managed driver for Oracle 11
			MySql - MySQL Connector/.NET
			Npgsql - PostgreSQL Npgsql
			
			For more information, please consult the Quartz documentation:
			https://www.quartz-scheduler.net/documentation/quartz-3.x/tutorial/job-stores.html -->
		<add key="quartz.dataSource.QuartzNET_DS.provider" value="SqlServer"/>
		<add key="quartz.jobStore.useProperties" value="true"/>
		<add key="quartz.jobStore.misfireThreshold" value="60000"/>
		<add key="quartz.jobStore.clustered" value="true"/>
		<add key="quartz.serializer.type" value="json"/>
	  </quartz>

-  Each instance in the cluster node should use the same copy of the quartz properties above except each node in the cluster MUST have a unique instanceId (quartz.scheduler.instanceId) |br|
-  The datasource name is QuartzNET_DS, you can define whatever name you want, just note that it always come with config quartz.dataSource.QuartzNET_DS.xyz |br|
-  Above are setting for MS SQL Server, if you want to use other DBMS you have to use correct database script for that DB type and must set correct quartz properties which are related to DB connection, that are quartz.jobStore.driverDelegateType, quartz.dataSource.QuartzNET_DS.connectionString, and quartz.dataSource.QuartzNET_DS.provider. Prefer JobStores tutorial chapter here https://www.quartz-scheduler.net/documentation/quartz-3.x/tutorial/job-stores.html). |br|
-  To verify the config is correct or not on Izenda API, check the log file of all cluster nodes and make sure that there is only one node logs out the line contains "[Izenda_Quartz_Worker-###][INFO ][SubscriptionJob                     ] Start scheduling {#number} subscription jobs" |br|
  
5. After setting this configuration you will need to alter a setting in IzendaSystemSetting table as below: |br|

.. code-block:: sql
	:linenos:

	Update IzendaSystemSetting
	Set Value = 1
	Where Name = 'UseADOJobStore'
  
6. Then you will need to clear any schedules already running in memory to add them to the database using the Update statement below: |br|

.. code-block:: sql
	:linenos:
	
	UPDATE IzendaSubscription SET IsScheduled = '0'

.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.

7. After making these changes, all API instances should be restarted.  
