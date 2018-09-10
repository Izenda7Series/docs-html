

==========================
Copy Management
==========================

.. tip::

   Copy Dashboard is available from release v0.22.14.

The **Copy Management** page allows user to:

-  define rules to copy data among system and tenants, including:

   .. hlist::
      :columns: 2

      -  logical data model
      -  advanced data settings
      -  dashboards
      -  reports
      -  tenant permissions
      -  role names
      -  roles and their permissions

-  validate data model consistency between two locations
-  save mapping rules into workspaces

View Workspace List
-------------------

#. .. _Workspace_List:

   .. figure:: /_static/images/Workspace_List.png
      :align: right
      :width: 367px

      Workspace List

   In browser, log in to Izenda as a user with Copy Management permission.
#. Click Settings, then Data Setup then Copy Management in the left menu.
#. Select the Setting Level: either System or a specific tenant.
#. The list of workspaces are displayed under Middle Panel.
#. Tick the Show only my workspace check-box to filter the list by workspaces owned by current user.
#. Type a partial name into the Search box to further filter the list by similar name.

   -  Click on a workspace to open it.
   -  Click the x icon to delete the workspace. |br|

Edit a Workspace
----------------

Clicking on a workspace in Middle Panel will open it. Each workspace
contains 5 sections:

-  Workspace Name and created date

       allows user to view workspace name and created date, and to
       rename the workspace.

-  Items to Copy Options

       allows user to quickly specify groups of settings then run copy.

-  Source Data Model Copy List

       allows user to pick specific data model items to copy instead of
       all visible items.

-  Destination Tenant List

       contains the tenants to copy to.

-  Mappings List

       contains mapping from Source to Destination physical location.

Rename a Workspace
~~~~~~~~~~~~~~~~~~

#. .. _Workspace_Rename_Duplication:

   .. figure:: /_static/images/Workspace_Rename_Duplication.png
      :align: right
      :width: 211px

      Rename a Workspace

   Click the pencil icon to rename the workspace.
#. Enter a new name for the workspace.
#. Click the check icon to confirm the new name.
#. The name will be checked for duplication. |br|

Items to Copy Options
~~~~~~~~~~~~~~~~~~~~~

This section lists selectable items to copy:

-  Data Model
-  Advanced Data Settings
-  Tenant Permissions
-  Roles
-  Role Permissions

Configure Source Data Model Copy List
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Source panel on the left shows visible database connections, schemas
together with visible inner data model items.

   Tick the checkbox next to each item to include it in the Data Model copy operation.

Destination panel on the right is the list of selected tenants to copy
to, together with validation and authentication status.

Configure Destination Tenant List
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Click the down arrow in Destination box to see the list of tenants.
#. Click each tenant to add it to the box.
#. Click the down arrow again to close the list.

.. note::

   To copy to all tenants, simply select "All Tenants" option. It will replace all currently selected tenants when selected.

Edit mappings
~~~~~~~~~~~~~

A mapping specifies the physical destination for each database
connection or schema of tenant (in case the database connection or
schema name in destination is different from logical data model).

#. Select a database connection in Source.
#. Choose the mapping type: Database or Schema.
#. -  Select a schema from the Object list if using Schema mapping.
   -  For Database mapping, the Object list is already populated with
      the database name.
#. Select the target database connection.
#. -  Enter the schema name (expression) into Object list if using
      Schema mapping.
   -  For Database mapping, the Object list is already populated with
      the database name.
#. Select the tenants to apply this mapping to.
#. Continue to add mappings to cover all selected database connections,
   schemas and tenants.

Rules:

-  Roles, Role Permissons, and Tenant Permissions can only be copied between tenants. They cannot be copied from system to tenant. This is due to the nature of system level permissions.
-  Tenants without a Database mapping will be copied to the same
   database connection.
-  Each schema without mapping will be copied to a schema with the same
   name (in the database connection specified in mapping).

For example, user needs to copy data model for schema Sales to Tenant01, Tenant02 and Tenant03.

    The schemas are named Sales0x with x = 1, 2 or 3 for each tenant
    respectively.

    Tenant02 and Tenant03 share the same physical database TenantDB
    while Tenant03 uses ACMEDB database on a separate server.

Following is how to configure the workspace:

#. Tick Data Model check-box in Items to Copy section.
#. .. _Copy_Management_Sample_Sales_schema:

   .. figure:: /_static/images/Copy_Management_Sample_Sales_schema.png
      :align: right
      :width: 664px

      Copy Sales schema

   Tick the Sales schema to include it in the copy. |br|
#. Select Tenant01, Tenant02 and Tenant03 as Destinations.
#. Add Connection to TenantDB for Tenant02 and Tenant03, and add connection to ACMEDB for Tenant03.
#. Add the mappings.

   .. _Copy_Management_Sample_Mapping:

   .. figure:: /_static/images/Copy_Management_Sample_Mapping.png
      :width: 900px

      Map database connections and schemas |br|

Validate Consistency between Source and Destinations
----------------------------------------------------

#. Click the Validate button at the top to validate for tenants with
   status "Need validated":

       Each tenant will be checked for a valid mapping for each schema.

#. Click the gear icon (⚙) next to
   each tenant to open Advanced Settings page for that tenant.
#. Click Validate button at the top to validate consistency in data
   model between source and the selected tenant.

       Selected objects in source will be checked for existence in data
       model for selected tenant by name.

#. Click OK to close the page.

   .. _Copy_Management_Data_Model_Comparison:

   .. figure:: /_static/images/Copy_Management_Data_Model_Comparison.png
      :width: 637px

      Data Model Comparison |br|

Run Copy
--------

#. Click Run Copy button to perform the copy of selected items for
   tenants with status "Ready To Copy".
#. .. _Copy_Management_Overwritten_Confirmation:

   .. figure:: /_static/images/Copy_Management_Overwritten_Confirmation.png
      :align: right
      :width: 452px

      Confirm to Overwrite existing Data Model

   Click OK to confirm to overwrite existing Data Model if needed. |br|
