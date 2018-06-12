=================================
Scheduling
=================================
|

Scheduled items are not being sent on time 
-----------------------------------------------------------------

This issue can occur if the API site has been shutdown or stopped via an IIS reset/recycle or a similar event. This may be evident in the API logs by large time gaps in activity.

If there is a scheduled iis reset or recycle, the application must be reinitialized for the scheduler to continue to ping and operate as expected. This can be as simple as logging in to the application, or a scheduled task that re-initializes the application. Once the  Izenda application has been initialized, it will continue to ping the server to keep iis running every 5 minutes (default interval).

The system will use the settings below (IzendaSystemSetting table) to ping our API to ensure that scheduled and subscribed items are delivered as expected. The SubscriptionJobInterval value will determine (in minutes) how often the API gets a ping to keep it up and running.

========================   ============
Name                 		    Value
========================   ============
WebAPIUrl        				     http://localhost/api/
SubscriptionJobInterval      5 (default)
========================   ============

If the WebAPIUrl is not set, you will see the error message below in the Izenda API logs:

 [DefaultQuartzScheduler_Worker-1][INFO ][SubscriptionJob] Ping system status failure: The remote server returned an error: (404) Not Found. 


You can use the script below to add the WebAPIUrl: 

.. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [IzendaSystemSetting]
	SET [Value] = '<your url here including the trailing slash>'
	WHERE [Name] = 'WebAPIUrl'


.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.


Duplicate scheduled items are being sent 
-----------------------------------------------------------------

The Izenda Scheduler will store scheduling information in RAM of the server by default. If you are using any type of a distributed enviroment where there is more than one instance of the Izenda API (webfarms, etc.) you will need to use a database (ADO.NET job store) for storage of the scheduling information. Please follow the instructions below for setting up the scheduler to run in a distributed environment:

1. Download the creation script for your database type: |br|
Download quartz database script ~\database\tables\tables\sqlServer.sql inside Quartz.NET-2.3.3.zip. Use that script to create database quartzNET233 on your DB server. https://github.com/quartznet/quartznet/releases/tag/v2.3.3 |br|

2. Create the database (by default the table prefix "QRTZ_" but this can be set in the config) |br|

3. Add quartz config section into Web.config |br|  
<section name="quartz" type="System.Configuration.NameValueSectionHandler" /> |br|

4. Add quartz section content into Web.config (under the  </system.webServer> tag) and replace the value of config quartz.dataSource.QuartzNET_DS.connectionString by your server name (Server), user (User Id) and password (Password) to access quartzNET233 database. |br|

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
		
			SqlServer-20 - SQL Server driver for .NET Framework 2.0
			OracleODP-20 - Oracle’s Oracle Driver
			OracleODPManaged-1123-40 Oracle’s managed driver for Oracle 11
			OracleODPManaged-1211-40 Oracle’s managed driver for Oracle 12
			MySql-50 - MySQL Connector/.NET v. 5.0 (.NET 2.0)
			MySql-51 - MySQL Connector/:NET v. 5.1 (.NET 2.0)
			Npgsql-20 - PostgreSQL Npgsql
			
			For more information, please consult the Quartz documentation:
			https://www.quartz-scheduler.net/documentation/quartz-2.x/tutorial/job-stores.html -->
		<add key="quartz.dataSource.QuartzNET_DS.provider" value="SqlServer-20"/>
		<add key="quartz.jobStore.useProperties" value="true"/>
		<add key="quartz.jobStore.misfireThreshold" value="60000"/>
		<add key="quartz.jobStore.clustered" value="true"/>
	  </quartz>

-  Each instance in the cluster node should use the same copy of the quartz properties above except each node in the cluster MUST have a unique instanceId (quartz.scheduler.instanceId) |br|
-  The datasource name is QuartzNET_DS, you can define whatever name you want, just note that it always come with config quartz.dataSource.QuartzNET_DS.xyz |br|
-  Above are setting for MS SQL Server, if you want to use other DBMS you have to use correct database script for that DB type and must set correct quartz properties which are related to DB connection, that are quartz.jobStore.driverDelegateType, quartz.dataSource.QuartzNET_DS.connectionString, and quartz.dataSource.QuartzNET_DS.provider. Prefer JobStores tutorial chapter here https://www.quartz-scheduler.net/documentation/quartz-2.x/tutorial/job-stores.html). |br|
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