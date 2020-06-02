

==========================
Data Connectors
==========================

The **Data Connectors** page allows user to

-  manage the list of connectors
-  select individual items from these connectors to be visible in Data Model and Reports

.. note:: 

   For the Reporting Databases: |br|
   \- The connection string user should have permissions to read schema; to select on all tables, views, store procedures and functions that will be used as data sources; to execute those store procedures and functions. |br|
   \- The user should also have permissions to create temp tables. |br|

Add connector and select visible data sources
----------------------------------------------

In this step user adds a connector and selects data sources to be
visible in reports.

.. warning::

         Please use caution when adding stored procedures to the visible data source list. All stored procedures are executed when added to visible (input parameters are set to NULL) to obtain the resulting fields returned. Some stored procedures are created to do things like delete tables, add data to tables, etc. If these are added to the visible data sources, they will be executed in the database.

#. In browser, log in to Izenda as a user with Data Connectors permission.
#. Click Settings, then Data Setup then Data Connectors in the left menu.

   .. _Connector_Add_Connector:

   .. figure:: /_static/images/connector/Connector_Add_Connector.png
      :width: 500px

      Add Connector

#. Select the Setting Level: either System or a specific tenant.
#. Click on Add Connector in the middle panel.

   .. _Connector_Server_Type:

   .. figure:: /_static/images/connector/Connector_Server_Type.png
      :width: 700px

      Connector Data Server Type

#. Select the data server type from the popup.
#. The Database Connection popup appears for configuring the connector.

   .. _Connector_Builder:

   .. figure:: /_static/images/connector/Connector_Builder.png
      :width: 500px

      Database Connection Builder |br|

   a. Fill in the **Server Name**, e.g. "yourdbserver.com".
   b. Fill in the **Database** name, e.g. "Northwind".
   c. Select the **Authentication** type from the drop-down box. 
   d. Fill in the **Login** and **Password** if necessary.
   e. Optional. Fill in the additional connection options specific to the selected data server.

   These steps can be bypassed when user already knows the connection string. In this case, it can be copied and pasted straight into the Connection String box.
   For examples of connection strings, please see the `Connection String Examples <https://www.izenda.com/docs/ui/doc_connection_string.html#connection-string-examples>`_ section below.
   To do this, switch to Connection String mode:

   .. _Connector_Builder_Connection_String:

   .. figure:: /_static/images/connector/Connector_Builder_Connection_String.png
      :width: 500px

      Database Connection Builder (Connection String) |br|

#. Click OK button to verify the connection and go to the next step after all required fields are filled in.

   .. note::

      - Unless the Connection String has been verified successfully, user will not be able to move next.

#. The connector name will be automatically populated from the database name. User can edit to give it a more suitable name.

   .. _Connector_Name:

   .. figure:: /_static/images/connector/Connector_Name.png
      :width: 700px

      Connector Name

#. Expand the listed user schemas and object types to see the data sources. |br|
   The data sources can be quickly filtered by typing a partial name in the Search box.
#. Click on the data sources to move them between the two lists.
   User can quickly move all data sources in a group (Table, View, Stored Procedure or Function) by clicking on that group name.

   .. _Connector_Data_Sources:

   .. figure:: /_static/images/connector/Connector_Data_Sources.png
      :width: 800px

      Data Sources

#. Click Save button at the top to save the connector and the visible data sources.

.. _Connection_Permissions:

Connector Permissions
----------------------

Izenda needs permissions to view the database schema and read from selected tables and views.

If using stored procedures as data source, Izenda needs execute permission on these stored procedures as well as create table and delete table permissions.

.. note::

   The create table permission will be used to create temporary tables to store the output of stored procedures, for joining to other data sources. And the delete table permission will be used to clean up these temporary tables afterwards.

Delete connector
-----------------

#. Click the delete icon (x) on the right of a connector to delete it.
#. Click OK in the confirmation pop-up.

Make a conector hidden
------------------------

All data sources from a connector can be hidden quickly by making that connector hidden.

#. Click the visibility icon on the right of that connector.

   .. _Connector_Visible_Invisible:

   .. figure:: /_static/images/connector/Connector_Visible_Invisible.png
      :width: 450px

      Connector Visible/Invisible

#. Click OK in the confirmation pop-up.

      All data sources from this connector is hidden from Data Model and Reports. The right pane is disabled and the connector's visibility icon is changed to a hidden one.

      .. _Connector_Visible_Confirmation:

      .. figure:: /_static/images/connector/Connector_Visible_Confirmation.png
         :width: 500px

         Confirmation pop-up

To restore the visibility of the data sources:

#. Click the "hidden visibility" icon on the right of that connector.
#. Click OK in the confirmation pop-up.

      The visibility of all data sources from this connector is restored back to the time before being hidden. The right pane is enabled and the connector's visibility icon is changed back to normal.

.. _Refresh_the_list_of_available_data_sources:

Refresh the list of available data sources
------------------------------------------

When there is a remote change in a connector, it will not be automatically reflected in Izenda. The Reconnect button needs to be manually clicked on to detect that.

#. Click on the connector.
#. Click the Reconnect button.
#. The remote changes in the data sources will be marked as either New data source or Changed data source.

      The Data Setup, Data Connectors and Data Model menu items will also be marked with Changed data source icon (!).

      .. _Connector_New_And_Changed_Data_Sources:

      .. figure:: /_static/images/connector/Connector_New_And_Changed_Data_Sources.png
         :width: 800px

         New and changed Data Sources

#. Go to :doc:`Data Model <doc_data_model_tables,_views_and_stored_procedures>` page to resolve the changes.

Filter the connector list
--------------------------

The connector list can be quickly filtered by typing a partial connector name in the Search box.

Cancel the changes
------------------

To cancel any changes without saving:

#. Click the Cancel button at the top.
#. Click OK in the confirmation pop-up.

Connection String Examples
--------------------------

- Oracle:
      - Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.45.37)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=MyOracleSID)));User Id=user;Password=password;
      - Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.45.37)(PORT=1521))(CONNECT_DATA=(SID=xe)));User Id=user;Password=password;

- Microsoft SQL Server:
      - Server=192.168.45.37,1433;Database=testdatabase;User ID=user;Password=password
      - Server=HOST-PC;Database=testdatabase;User ID=user;Password=password

- MySQL:
      - Server=MY-PC;Port=3306;Database=testdatabase;User ID=user;Password=password

- PostgreSQL:
      - Server=mydomainname;Port=5432;Database=testdatabase;User ID=user;Password=password
      - Server=mydomainname;Port=5432;Database=testdatabase;User ID=user;Password=password;SslMode=Require;Trust Server Certificate=true;

      .. note:: 
            - If using Izenda v3.0.0 or greater and a PostgreSQL connection string with "SslMode=Require", the "Trust Server Certificate=true;" parameter will also need to be added.

- `Elasticsearch <https://www.izenda.com/docs/intro/elastic.html>`_:
      - server=https://xxxxxxxx.us-east-1.aws.found.io;Port=9243;User=user;Password=password;

- `MongoDB <https://www.izenda.com/docs/intro/mongo.html>`_:
      - Server=localhost;Port=27017;Database=admin;User=user;Password=password;
      - User=user;Password=password;Server=atlas-host1;Port=27017;Database=testdatabase;AuthDatabase=admin;AuthMechanism=SCRAM-SHA-1;ReplicaSet=cluster0-shard-00-01-u49p2.mongodb.net:27017,cluster0-shard-00-02-u49p2.mongodb.net:27017;UseSSL=true;SlaveOK=true;
