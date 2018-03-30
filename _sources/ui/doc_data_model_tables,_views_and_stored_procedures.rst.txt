

===============================================
Data Model/Tables, Views and  Stored Procedures
===============================================

The **Data Model/Tables**, **Data Model/Views** and **Data Model/Stored Procedures** pages allow user to

-  manage tables, views, their columns and relationships
-  add and remove calculated fields
-  manage stored procedures, their parameters, output columns and
   relationships
-  assign filter values for stored procedure parameters
-  mark stored procedures as dynamic

**Note:** |br|
   Stored Procedures are not supported in AWS Redshift databases.

List tables, views or stored procedures
---------------------------------------

#. In browser, log in to Izenda as a user with Data Model permission.
#. Click Settings, then Data Setup then Data Model in the left menu.
#. Select the Setting Level: either System or a specific tenant.
#. Click Tables, Views or Stored Procedures in the Middle Panel. (:numref:`Data_Model_Tables_Views_Stored_Procedures_Location`)

   .. _Data_Model_Tables_Views_Stored_Procedures_Location:

   .. figure:: /_static/images/Data_Model_Tables_Views_Stored_Procedures_Location.png
      :width: 476px

      Data Model - Tables, Views and Stored Procedures |br|

#. Visible tables, views, or stored procedures from all connections will
   be displayed in the upper data source grid, and columns of the
   currently selected one will be displayed in the lower Column Grid. (:numref:`Data_Model_Tables_and_Views_Column_Grid`)

   .. _Data_Model_Tables_and_Views_Column_Grid:

   .. figure:: /_static/images/Data_Model_Tables_and_Views_Column_Grid.png
      :width: 476px

      Data Model - Data Source Grid and Column Grid |br|

#. By default, only the first page with 10 items are displayed. To see
   more, either use the next page icon

   .. figure:: /_static/images/Data_Model_Next_Page_Icon.png
      :width: 92px

      Data Model - Next Page |br|

   or select a larger number in Items per page box.

   .. figure:: /_static/images/Data_Model_Items_per_page.png
      :width: 172px

      Data Model - Items per page |br|

Search for tables, views or stored procedures
---------------------------------------------

The Search box at the top allows user to search for specific tables,
views or stored procedures.

#. .. _Data_Model_Tables_and_Views_Search_by_Elements:

   .. figure:: /_static/images/Data_Model_Tables_and_Views_Search_by_Elements.png
      :align: right
      :width: 289px

      Data Model - Search Tables or Views by element

   Select a specific element to search for in the dropdown on the left
   of the Search box. Default is All. (:numref:`Data_Model_Tables_and_Views_Search_by_Elements`)
#. Type a partial name and click the search icon (🔍).
#. Only the matching tables, views or stored procedures will be
   displayed. |br|

.. _Assign_a_category_to_a_table_view_or_stored_procedure:

Assign a category to a table, view or stored procedure
------------------------------------------------------

#. Select a name in the Category dropdown to assign it to the table,
   view or stored procedure.
#. If the category name is not yet in the list, user can add it by typing the name in and press Enter. (:numref:`Data_Model_New_Category`)

   .. _Data_Model_New_Category:

   .. figure:: /_static/images/Data_Model_New_Category.png
      :width: 600px

      Data Model - Functions |br|

#. Continue to assign category to more tables, views or stored
   procedures in the same page.
#. Click Save button at the top, then click OK in the confirmation
   pop-up.

       .. note::

          User must save the assignments before moving to another page or another group in the Middle Panel.

.. seealso::

   :ref:`Advanced Settings/Add data source categories <Add_data_source_categories>`.

Assign an alias to a table, view or stored procedure
----------------------------------------------------

#. Enter an alias into the Database Source Alias box to assign it to the
   table, view or stored procedure.
#. Continue to assign alias to more tables, views or stored procedures
   in the same page.

       The alias can contain any characters except for "[" and "]".

#. Click Save button at the top, then click OK in the confirmation
   pop-up.

       .. note::

          User must save the assignments before moving to another page or another group in the Middle Panel.

.. note::

   Within a category, the aliases cannot be duplicated. In :numref:`Data_Model_Duplicated_Category_and_Alias`, Alias\_1 is duplicated because the data sources are in the same Category2, and Alias\_2 is valid because the data sources are in different categories.

   .. _Data_Model_Duplicated_Category_and_Alias:

   .. figure:: /_static/images/Data_Model_Duplicated_Category_and_Alias.png
      :width: 966px

      Data Model - Duplicated Aliases in Category |br|

Manage relationships for a table, view or stored procedure
----------------------------------------------------------

#. Click the relationhips icon at the end of each line to open the
   Relationships dialog.
#. See :doc:`doc_data_model_relationships_and_schema` for how to manage
   relationships.

Assign an alias to a column in table, view or stored procedure
--------------------------------------------------------------

#. In the Column Grid, enter an alias into the Column Alias box to
   assign it to the column.
#. Continue to assign alias to more columns in the same page.

       The alias can contain any characters except for "[" and "]".

#. Click Save button at the top, then click OK in the confirmation
   pop-up.

       .. note::

          User must save the assignments before moving to another page or another group in the Middle Panel.

.. note::

   Within a table or view, the aliases cannot be duplicated. (:numref:`Data_Model_Duplicated_Column_Alias`)

   .. _Data_Model_Duplicated_Column_Alias:

   .. figure:: /_static/images/Data_Model_Duplicated_Column_Alias.png
      :width: 702px

      Data Model - Duplicated Column Alias |br|

Select visible or not for a column in table, view or stored procedure
---------------------------------------------------------------------

A visible column will be included in any field selection control in
report.

#. Untick the Visible check-box to exclude the column from field
   selection controls in report, or leave it checked to include.
#. Continue for more columns in the same page.
#. Click Save button at the top, then click OK in the confirmation
   pop-up.

       .. note::

          User must save the changes before moving to another page or another group in the Middle Panel.

Select filterable or not for a column in table, view or stored procedure
------------------------------------------------------------------------

A filterable (and visible) column will be included in any filter in
report.

.. note::

   A not visible column will be excluded from any filter in report no matter it is filterable or not.

#. Untick the Filterable check-box to exclude the column from filters in
   report, or leave it checked to include.
#. Continue for more columns in the same page.
#. Click Save button at the top, then click OK in the confirmation
   pop-up.

       .. note::

          User must save the changes before moving to another page or another group in the Middle Panel.

Add a calculated field to table or view
---------------------------------------

.. topic:: Calculated field

   Calculated field is a virtual field calculated from an expression that can use other fields in the same table or view. A calculated field is created to simplify the select queries by hiding the detailed formula, and the formula can be replaced without any change in existing queries. A calculated field will also avoid data redundancy since it is re-calculated in each query.

   For example, from a student test score, the grade can be calculated by this formula:

   .. code-block:: sql

      WHEN score >= 0 AND score < 7 THEN 'GOOD'
      WHEN score >= 7 AND score < 9 THEN 'EXCELLENT'
      WHEN score >= 9               THEN 'OUTSTANDING'

   If defined as a calculated field, the grade can later use another formula without changing any queries.
   
   .. note::

          Calculated fields cannot be used in relationships between tables or views.

   .. seealso::

      `Computed Columns <https://technet.microsoft.com/en-us/library/ms191250(v=sql.105).aspx>`_

|br|

#. Select the table or view in the upper data source grid.
#. Click Add Field button on top of the Column Grid to open Add
   Calculated Field pop-up.
#. Enter the field name
   into Column Name box.

       The field name must be unique in that table or view. (:numref:`Data_Model_Calculated_Field_Duplicated_Name`)

       .. _Data_Model_Calculated_Field_Duplicated_Name:

       .. figure:: /_static/images/Data_Model_Calculated_Field_Duplicated_Name.png
          :width: 456px

          Data Model - Calculated Field Name |br|

#. Enter the
   definition for the calculated field into Expression box.

       Click the bulb icon (💡) to see the list of available fields,
       functions and operators.
       Then click a field, function or operator to insert it into the
       cursor position. (:numref:`Data_Model_Calculated_Field_Bulb_Pop-up`)

       .. _Data_Model_Calculated_Field_Bulb_Pop-up:

       .. figure:: /_static/images/Data_Model_Calculated_Field_Bulb_Pop-up.png
          :width: 518px

          Data Model - Calculated Field Available List |br|

#. Depending on the
   formula, a suitable data type is suggested in Data Type drop-down.
#. Click Preview button to see a sample result of the formula.
#. Click OK to accept the formula and close the pop-up. (:numref:`Data_Model_Calculated_Field_FirstName_WhiteSpace_LastName`)
#. Click Save at the top.

   .. _Data_Model_Calculated_Field_FirstName_WhiteSpace_LastName:

   .. figure:: /_static/images/Data_Model_Calculated_Field_FirstName_WhiteSpace_LastName.png
      :width: 456px

      Data Model - FullName Calculated Field |br|

.. seealso::

   -  :doc:`Izenda Data Types </ref/spec_izenda_data_types>`
   -  :doc:`Izenda Operators </ref/spec_izenda_operators>`
   -  :doc:`Izenda Functions </ref/spec_izenda_functions>`

Remove a calculated field from table or view
--------------------------------------------

#. Select the table or view in the upper data source grid.
#. Click the remove icon (X) at the end of the calculated field.

       The remove icon is only enabled for calculated fields. (:numref:`Data_Model_Calculated_Field_Remove_Icon`)

       .. _Data_Model_Calculated_Field_Remove_Icon:

       .. figure:: /_static/images/Data_Model_Calculated_Field_Remove_Icon.png
          :width: 1026px

          Data Model - Remove Calculated Field |br|

#. Click OK in the confirmation pop-up.

       If the calculated field has been used in any report, user will
       have to confirm that these reports will not be viewable anymore.

#. Click Save at the top.

Set stored procedure as dynamic
-------------------------------

For stored procedures with any input parameter, they can be set as
dynamic.

.. topic:: Dynamic stored procedure

   A stored procedure with one (or more) input parameter might have different output schemas based on the value of that input parameter. The reports have 2 options to handle this situation:

   * Dynamic: The schema is only determined at report design time by a user-supplied input value.
      The schema is empty in Data Model.
   * Non-dynamic: The schema is assumed to remain consistent regardless of the input value.
      System can try getting that schema for Data Model by executing with null input parameters. In case it cannot because any parameter requires NOT NULL, user will be prompted for a proper input value.

      The exact rule for NOT NULL input parameters:

      #. If Filter Value has been defined for a parameter, the first value in that list will be used as input value.
      #. If not, then null will be used as input value.

   Non-dynamic should be the default value since in practice, well-coded stored procedures should return a consistent schema.

|br|

#. .. _Data_Model_SP_Set_Dynamic_Confirmation:

   .. figure:: /_static/images/Data_Model_SP_Set_Dynamic_Confirmation.png
      :align: right
      :width: 456px

      Data Model - Set stored procedure as dynamic confirmation

   Tick the Dynamic check-box to set a stored procedure as dynamic.
#. Click OK in the confirmation pop-up. (:numref:`Data_Model_SP_Set_Dynamic_Confirmation`)
#. Click Save button at the top, then click OK in the confirmation
   pop-up.
#. The stored procedure will be set as dynamic and its schema will be
   removed from the lower Column Grid. The Execute button is also
   disabled. |br|

Set stored procedure as non-dynamic
-----------------------------------

#. Untick the Dynamic check-box to set a stored procedure as
   non-dynamic.
#. Click Save button at the top, then click OK in the confirmation
   pop-up.
#. The stored procedure will be set as non-dynamic. The Execute button
   is also enabled for user to get the schema.

Execute a non-dynamic stored procedure to get the schema
--------------------------------------------------------

#. Click the Execute button above the lower Column Grid.
#. System tries running the stored procedure to get the schema.
#. The schema will be populated into the lower Column Grid.
#. Click Save button at the top, then click OK in the confirmation
   pop-up.

The action will fail if one of the parameters requires not null and
Filter Value has not been defined.

In this case, please update the Filter Value section.

Update Filter Value for a stored procedure parameter
----------------------------------------------------

#. Click the icon in Filter Value box.

       Filter Value icon only appears for parameters.

#. Select either Filter Lookup Key - Value or User Defined Filter Value

   -  Example to set
      parameter @OrderID to look up from NorthwindA.dbo.Orders.OrderID,
      displaying column ShipName to end-user. (:numref:`Data_Model_SP_Filter_Lookup_Key_-_Value`)

      .. _Data_Model_SP_Filter_Lookup_Key_-_Value:

      .. figure:: /_static/images/Data_Model_SP_Filter_Lookup_Key_-_Value.png
         :width: 458px

         Data Model - Filter Lookup Key - Value |br|

   -  Example to set
      parameter @OrderID to look up from a list of 3 values: the value
      of Tenant ID and 2 fixed values NewValueA and NewValueB. (:numref:`Data_Model_SP_User_Defined_Filter_Value`)

      .. _Data_Model_SP_User_Defined_Filter_Value:

      .. figure:: /_static/images/Data_Model_SP_User_Defined_Filter_Value.png
         :width: 458px

         Data Model - User Defined Filter Value |br|

#. .. _Data_Model_SP_View_User_Defined_Filter_Value:

   .. figure:: /_static/images/Data_Model_SP_View_User_Defined_Filter_Value.png
      :align: right
      :width: 245px

      Data Model - Selected User Defined Filter Value

   The  selected filter value will appear in the Filter Value box. (:numref:`Data_Model_SP_View_User_Defined_Filter_Value`) |br|
#. Click Save button at the top, then click OK in the confirmation
   pop-up.
