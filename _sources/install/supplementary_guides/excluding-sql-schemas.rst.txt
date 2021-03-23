======================================
Excluding SQL Schemas
======================================
|

Introduction
------------------------------------------
Izenda v2.6.21 and higher allows application administrators to explicitly exclude any specified schemas from the available data sources. This option is applied globally and will affect the system and tenant users.

.. warning::

	Please ensure that any schemas you intend to exclude are not in use. If the excluded schemas are in use, any reports or dashboards using those schemas will be broken and cannot be recovered. We recommend backing up your Izenda configuration database before making this change.
	

Configuration
----------------------------------------------------
This option is configured by the adding a key/value entry for the desired database and schemas in the API/Web.config file as shown below:

.. code-block:: xml
	:linenos:
	
	<!-- Please be sure that there are no leading or trailing spaces for each entry. -->
	<appSettings> 
		<add key="izenda.mssql.excludeSchema" value="MANAGEMENT"/> 
		<add key="izenda.oracle.excludeSchema" value="HR,ACCOUNTING"/> 
		<add key="izenda.postgresql.excludeSchema" value="SCHEMA1,SCHEMA2"/> 
	</appSettings>

	
.. note::

	Depending on your IIS configuration, changes to the Web.config file may automatically trigger the application to be reloaded.
	
	
List of Supported Keys
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+--------------------------------------------+
| **izenda.mssql.excludeSchema**             |
+--------------------------------------------+
| **izenda.oracle.excludeSchema**            |
+--------------------------------------------+
| **izenda.postgresql.excludeSchema**        |
+--------------------------------------------+


.. note::

	This option is not available for MySQL. The application will only enumerate the schema specified in the connection string for MySQL databases.
	

Restarting the web sites
###############################

After updating the Web.config file, restart the API and front-end sites.


Verifying the changes
###############################

In the example below, several schemas for Oracle are excluded via the Web.config file.

.. code-block:: xml
	:linenos:
	
	<appSettings> 
		<add key="izenda.oracle.excludeSchema" value="IZENDACONFIG2,RDSADMIN,IZENDA11,IZENDACONFIG"/>  
	</appSettings>

	
Before the changes:

.. figure:: images/exclude_schema_before.png


After restarting the API and reconnecting, the change works as expected:

.. figure:: images/exclude_schema_after.png
