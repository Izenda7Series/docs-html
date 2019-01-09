

===================================
Data Model/Relationships and Schema
===================================

The **Data Model/Relationships** and **Data Model/Schema** pages allows
user to
 
-  manage relationships for tables, views and stored procedures
-  view database schema

List relationships
------------------

#. In browser, log in to Izenda
   as a user with Data Model permission.
#. Click Settings, then Data Setup then Data Model in the left menu.
#. Select the Setting Level: either System or a specific tenant.
#. Select Relationships in the Middle Panel. (:numref:`Data_Model_Relationships_Location`)

   .. _Data_Model_Relationships_Location:

   .. figure:: /_static/images/Data_Model_Relationships_Location.png
      :width: 429px

      Data Model - Relationships |br|

#. Relationships of all visible data sources from all connections will
   be displayed.
#. By default, only the first page with 10 items are displayed. To see
   more, either use the next page icon

   .. figure:: /_static/images/Data_Model_Next_Page_Icon.png
      :width: 92px

      Data Model - Next Page |br|

   or select a larger number in Items per page box.

   .. figure:: /_static/images/Data_Model_Items_per_page.png
      :width: 172px

      Data Model - Items per page |br|


Search for relationships
------------------------

The Search box at the top allows user to search for specific
relationships.

#. .. _Data_Model_Relationships_Search_by_Elements:

   .. figure:: /_static/images/Data_Model_Relationships_Search_by_Elements.png
      :align: right
      :width: 300px

      Data Model - Search Relationships by element

   Select a specific element to search for in the dropdown on the left
   of the Search box. Default is All. |br|
#. Type a partial name and click the search icon (🔍).
#. Only the matching relationships will be displayed.

Add relationship
----------------

#. .. _Data_Model_Relationships_Add_New_button:

   .. figure:: /_static/images/Data_Model_Relationships_Add_New_button.png
      :align: right
      :width: 225px

      Data Model - Add New Relationship

   Click the Add Relationship button at the top. (:numref:`Data_Model_Relationships_Add_New_button`) |br|
#. A new empty row will appear at the first line.
#. Select the elements of the relationship from dropdown boxes.

       User must select Connection Name, then Data Source, then Data
       Source Field in that order for the dropdown boxes to populate
       conveniently.

       User should input the positionID to define the priority of each relationship when querying data. (This option is available from version 2.16.0).

#. Continue to add more relationships.
#. Click the Save button at the top.1w`

       Relationships that already exists or have errors will be
       highlighted and not saved. (:numref:`Data_Model_Relationships_Existed_Error` and :numref:`Data_Model_Relationships_Data_Type_Error`)

       .. _Data_Model_Relationships_Existed_Error:

       .. figure:: /_static/images/Data_Model_Relationships_Existed_Error.png
          :width: 300px

          Data Model - Relationship Already Exists |br|

       .. _Data_Model_Relationships_Data_Type_Error:

       .. figure:: /_static/images/Data_Model_Relationships_Data_Type_Error.png
          :width: 382px

          Data Model - Data Type Error |br|

.. note::

   Only single-column relationships are supported in Data Model. Multiple-column relationships are supported in :ref:`Report Designer <Add_Key_Join_Relationship>`.

Copy relationship
-----------------

The copy feature help users to save efforts in adding and editing
relationships.

#. Click the Copy icon (that looks a bit like this ❐) of each
   relationship to copy its details to a new line beneath.
#. Edit the new line to make a new relationship.
#. Continue for more relationships.
#. Click the Save button at the top.

Edit relationship
-----------------

User can freely edit any relationship in a page and save them.

Delete relationship
-------------------

User can only delete relationships newly created in Data Model.
Relationships originally created from physical database cannot be
deleted, their delete icon will be disabled.

#. Click the Delete icon (x) of each relationship.
#. Click OK in the confirmation pop-up.
#. The relationship is deleted.

.. warning::

   The Cancel button at the top will have no effect in this case.

View the schema
---------------

To be updated.
