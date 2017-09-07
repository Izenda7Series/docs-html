

==========================
Connection String
==========================

The **Connection String** page allows user to

-  manage the list of connections
-  select individual items from these connections to be visible in Data
   Model and Reports

Add connection and select visible data sources
----------------------------------------------

In this step user adds a connection and selects data sources to be
visible in reports.

#. .. _Menu_Connection_String:

   .. figure:: /_static/images/Menu_Connection_String.jpg
      :align: right
      :width: 195px

      Connection String Menu

   In browser, log in to Izenda as a user with Connection String permission.
#. Click Settings, then Data Setup then Connection String in the left menu.
#. Select the Setting Level: either System or a specific tenant. (:numref:`Menu_Connection_String`) |br|
#. Click on Add Connection. (:numref:`Connection_Add_Connection`)

   .. _Connection_Add_Connection:

   .. figure:: /_static/images/Connection_Add_Connection.jpg
      :width: 181px

      Add Connection |br|

#. .. _Connection_Select_Database_Server_Type:

   .. figure:: /_static/images/Connection_Select_Database_Server_Type.jpg
      :align: right
      :width: 310px

      Select Database Server Type

   Select the database server type from the drop-down box. (:numref:`Connection_Select_Database_Server_Type`) |br|
#. .. _Connection_Connection_Builder:

   .. figure:: /_static/images/Connection_Builder.jpg
      :align: right
      :width: 458px

      Connection Builder tool

   Click the Connection Builder icon (⚡) to help build the connection string easily. (:numref:`Connection_Connection_Builder`) |br|

      This step can be bypassed when user already knows the connection string. In this case, it can be copied and pasted straight into the Connection String box.
#. Click the Test button to verify the connection string.

   .. note::

      Unless the Connection String has been verified successfully, user will not be able to move next.

#. .. _Connection_Connection_String_Test:

   .. figure:: /_static/images/Connection_Connection_String_Test.jpg
      :align: right
      :width: 619px

      Test the Connection and give it a name

   The connection name will be automatically populated from the database name. User can edit to give it a more suitable name. (:numref:`Connection_Connection_String_Test`) |br|

#. .. _Connection_Connect:

   .. figure:: /_static/images/Connection_Connect.jpg
      :align: right
      :width: 624px

      Connect to the Connection

   Click the Connect button to show the list of available data sources. (:numref:`Connection_Connect`) |br|

#. .. _Connection_Expand_Available_Data_Sources:

   .. figure:: /_static/images/Connection_Expand_Available_Data_Sources.jpg
      :align: right
      :width: 322px

      Expand to see the data sources

   Expand the listed user schemas and object types to see the data sources. (:numref:`Connection_Expand_Available_Data_Sources`) |br|

      .. _Connection_Available_Data_Sources_Filter:

      .. figure:: /_static/images/Connection_Available_Data_Sources_Filter.jpg
         :align: right
         :width: 297px

         Filter the data sources

      The data sources can be quickly filtered by typing a partial name in the Search box. (:numref:`Connection_Available_Data_Sources_Filter`) |br|
#. .. _Connection_Move_Data_Source_to_Visible_List:

   .. figure:: /_static/images/Connection_Move_Data_Source_to_Visible_List.jpg
      :align: right
      :width: 611px

      Move data sources between the two lists

   Click on the data sources to move them between the two lists. (:numref:`Connection_Move_Data_Source_to_Visible_List`) |br|

   .. _Connection_Move_a_Group_of_Data_Sources:

   .. figure:: /_static/images/Connection_Move_a_Group_of_Data_Sources.jpg
      :align: right
      :width: 614px

      Move a group of data sources

   User can quickly move all data sources in a group (Table, View, Stored Procedure or Function) by clicking on that group name. (:numref:`Connection_Move_a_Group_of_Data_Sources`) |br|

#. Click Save button at the top to save the connection and the visible data sources.

.. _Connection_Permissions:

Connection Permissions
------------------------------

Izenda needs permissions to view the database schema and read from selected tables and views.

If using stored procedures as data source, Izenda needs execute permission on these stored procedures as well as create table and delete table permissions.

.. note::

   The create table permission will be used to create temporary tables to store the output of stored procedures, for joining to other data sources. And the delete table permission will be used to clean up these temporary tables afterwards.

Delete connection
-----------------

#. .. _Connection_Delete:

   .. figure:: /_static/images/Connection_Delete.jpg
      :align: right
      :width: 185px

      Delete Connection

   Click the delete icon (x) on the right of a connection to delete it. (:numref:`Connection_Delete`) |br|
#. .. _Connection_Delete_Confirmation:

   .. figure:: /_static/images/Connection_Delete_Confirmation.jpg
      :align: right
      :width: 457px

      Confirmation pop-up

   Click OK in the confirmation pop-up. (:numref:`Connection_Delete_Confirmation`) |br|

Make a connection hidden
------------------------

All data sources from a connection can be hidden quickly by making that
connection hidden.

#. .. _Connection_Make_Hidden_All:

   .. figure:: /_static/images/Connection_Make_Hidden_All.jpg
      :align: right
      :width: 194px

      Hide a connection

   Click the visibility icon on the right of that connection. (:numref:`Connection_Make_Hidden_All`) |br|
#. .. _Connection_Make_Hidden_All_Confirmation:

   .. figure:: /_static/images/Connection_Make_Hidden_All_Confirmation.jpg
      :align: right
      :width: 455px

      Confirmation pop-up

   Click OK in the confirmation pop-up. (:numref:`Connection_Make_Hidden_All_Confirmation`) |br|

      .. _Connection_Hidden:

      .. figure:: /_static/images/Connection_Hidden.jpg
         :align: right
         :width: 194px

         Hidden versus visible connections

      All data sources from this connection is hidden from Data Model and Reports. The right pane is disabled and the connection's visibility icon is changed to a hidden one. (:numref:`Connection_Hidden`) |br|

.. _Connection_Make_Visible_All_Confirmation:

.. figure:: /_static/images/Connection_Make_Visible_All_Confirmation.jpg
   :align: right
   :width: 460px

   Make a connection visible

To restore the visibility of the data sources:

#. Click the "hidden visibility" icon on the right of that connection.
#. Click OK in the confirmation pop-up. (:numref:`Connection_Make_Visible_All_Confirmation`) |br|

      The visibility of all data sources from this connection is restored back to the time before being hidden. The right pane is enabled and the connection's visibility icon is changed back to normal.

      .. warning::

         The description in the confirmation pop-up has not been updated.

.. _Refresh_the_list_of_available_data_sources:

Refresh the list of available data sources
------------------------------------------

When there is a remote change in a connection, it will not be
automatically reflected in Izenda. The Reconnect button needs to be
manually clicked on to detect that.

#. Click on the connection.
#. Click the Reconnect button.

   .. _Connection_Reconnect_button:

   .. figure:: /_static/images/Connection_Reconnect_button.jpg
      :width: 611px

      Reconnect the connection

#. The remote changes in the data sources will be marked as either New
   data source or Changed data source.

      The Data Setup, Connection String and Data Model menu items will also be marked with Changed data source icon (!). (:numref:`Connection_Changed_Data_Sources`)

      .. _Connection_Changed_Data_Sources:

      .. figure:: /_static/images/Connection_Changed_Data_Sources.jpg
         :width: 862px

         New and Changed data sources

#. Go to :doc:`Data Model <doc_data_model_tables,_views_and_stored_procedures>` page to
   resolve the changes.

Filter the connection list
--------------------------

.. _Connection_Filter_box:

.. figure:: /_static/images/Connection_Filter_box.jpg
   :align: right
   :width: 183px

   Filter the connection list

The connection list can be quickly filtered by typing a partial connection name in the Search box. (:numref:`Connection_Filter_box`) |br|

Cancel the changes
------------------

To cancel any changes without saving:

.. _Connection_Cancel_Confirmation:

.. figure::  /_static/images/Cancel_Confirmation.jpg
   :align: right
   :width: 465px

   Cancel confirmation pop-up

#. Click the Cancel button at the top.
#. Click OK in the confirmation pop-up. (:numref:`Connection_Cancel_Confirmation`) |br|
