

=================
Advanced Settings
=================

The **Advanced Settings** page allows user to

* manage the list of data source categories
* update system settings in related groups

.. _Add_data_source_categories:

Add data source categories
--------------------------

A category should be added before showing up for assignment to a data
source.

#. In browser, log in to Izenda as a user with Advanced Settings
   permission.
#. Click Settings, then Data Setup then Advanced Settings in the left
   menu.
#. Select the Setting Level: either System or a specific tenant.
#. .. _Menu_Advanced_Settings_Category:

   .. figure:: /_static/images/Menu_Advanced_Settings_Category.jpg
      :align: right
      :width: 391px

      Category Menu

   Click Category in the Middle Panel. (:numref:`Menu_Advanced_Settings_Category`) |br|
#. Click Add New + button and type the name into the new text box. (:numref:`Settings_Category_Add_New`)

   .. _Settings_Category_Add_New:

   .. figure:: /_static/images/Settings_Category_Add_New.jpg
      :width: 622px

      Add New button |br|
#. Continue to click Add New + button to enter more categories.
#. Click Save button at the top to save the whole list.

.. note::

   User will not be able to save the list unless there is no duplication.

Delete data source categories
-----------------------------

#. In the category list, click the delete icon (x) on the right of each category to delete it. (:numref:`Settings_Category_Delete`)

   .. _Settings_Category_Delete:

   .. figure:: /_static/images/Settings_Category_Delete.jpg
      :width: 621px

      Delete icon |br|
#. Click OK in the pop-up confirmation. (:numref:`Category_Deletion_Confirmation`)

   .. _Category_Deletion_Confirmation:

   .. figure:: /_static/images/Category_Deletion_Confirmation.jpg
      :width: 456px

      Delete confirmation |br|
#. The category is deleted immediately.

       The Save and Cancel buttons at the top does not have any effect in this action.

.. note::

   The category will be deleted even if it has been assigned to data sources. After that these data sources will have no category.

.. note::

   To change the name of a category, the `Rename data source categories`_ feature should be used instead.

Rename data source categories
-----------------------------

Renaming a category will only change the name and keep the assignments
to data sources intact.

#. In the category list, click the text box of any category and change the name. (:numref:`Settings_Category_Rename`)

   .. _Settings_Category_Rename:

   .. figure:: /_static/images/Settings_Category_Rename.jpg
      :align: right
      :width: 617px

      Rename categories |br|
#. Continue to change more category names
#. Click Save button at the top to save the whole list.

.. _Update_settings_in_Performance_Security_Additive_Fields_and_Others_group:

Update settings in Performance, Security/Additive Fields and Others group
-------------------------------------------------------------------------

#. In browser, log in to Izenda as a user with Advanced Settings
   permission.
#. Click Settings, then Data Setup then Advanced Settings in the left
   menu.
#. Select the Setting Level: either System or a specific tenant.
#. .. _Menu_Advanced_Settings_Performance_Security_and_Others:

   .. figure:: /_static/images/Menu_Advanced_Settings_Performance_Security_Others.jpg
      :align: right
      :width: 389px

      Performance, Security and Others

   Click Performance, Security or Others. (:numref:`Menu_Advanced_Settings_Performance_Security_and_Others`) |br|
#. The settings are listed together with their current values.
#. Update the values.

      User can revert any setting back to its system default value by clicking the back arrow icon (↺). (:numref:`Advanced_Settings_Back_to_Default_Value`)

      .. _Advanced_Settings_Back_to_Default_Value:

      .. figure:: /_static/images/Advanced_Settings_Back_to_default_value.jpg
         :width: 618px

         Revert back to default value |br|

#. Click Save button at the top to save the whole setting group.

   .. note::

      The input boxes only accept a limited range of values and will not allow invalid entries.

   .. note::

      For a detailed description of any setting, point over that setting to see the information icon (i), then point over that icon to see the description tooltip. (:numref:`Advanced_Settings_Detailed_Description_Tooltip`)

      .. _Advanced_Settings_Detailed_Description_Tooltip:

      .. figure:: /_static/images/Advanced_Settings_Detailed_description_tooltip.jpg
         :width: 617px

         Detailed description tooltip |br|

.. note::

   The Use No Lock setting instructs the database engine to return the current version of data immediately, instead of waiting for all pending transactions to complete. Check the possible consequences `here <https://www.izenda.com/blog/high-performance-sql-views-using-withnolock/>`__ before using this option.

Update settings in Security/Tenant group
----------------------------------------

For security in multi-tenant systems, it is a best practice to have an
automatic filter condition to always restrict data retrieval to only
that of the current tenant. To enable this feature:

#. Untick Show Tenant Field check-box.
#. Enter the name of tenant id fields into the Tenant Field box. The Tenant Field must be enclosed in brackets [fieldname] and multiple fields should be separated by a semi-colon.
#. Click Save button at the top.
#. Then:

   -  These tenant id fields will be hidden from Report Designer.
   -  The reports will automatically have a filter condition to restrict
      data retrieval to only that of the current tenant.

Cancel the changes
------------------

.. _Settings_Cancel_Confirmation:

.. figure:: /_static/images/Cancel_Confirmation.jpg
   :align: right
   :width: 465px

   Cancel confirmation pop-up

To cancel any changes without saving:

#. Click the Cancel button at the top.
#. Click OK in the confirmation pop-up. (:numref:`Settings_Cancel_Confirmation`) |br|

See also
--------

-  :ref:`Data Model - Assign a category to a table, view or stored procedure <Assign_a_category_to_a_table_view_or_stored_procedure>`
