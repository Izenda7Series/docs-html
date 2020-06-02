


Workspace
-----------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **name** |br|
         string
      -
      -  The name of the workspace
      -
   *  -  **description** |br|
         string
      -
      -  The description of the workspace
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantName** |br|
         string
      -
      -  The name of the tenant
      -
   *  -  **ownerId** |br|
         string (GUID)
      -  Y
      -  The id of the owner
      -
   *  -  **copyOnlySettings** |br|
         boolean
      -
      -  Does user select to copy only settings
      -  .. versionadded:: 3.9.3
   *  -  **copyDataConnector** |br|
         boolean
      -
      -  Does user select to copy data connectors
      -  .. versionadded:: 3.9.3
   *  -  **copySystemConfiguration** |br|
         boolean
      -
      -  Does user select to copy system configuration
      -  .. versionadded:: 3.9.3
   *  -  **copyGoogleMapConfiguration** |br|
         boolean
      -
      -  Does user select to copy Google maps configuration
      -  .. versionadded:: 3.9.3
   *  -  **copyReportConfiguration** |br|
         boolean
      -
      -  Does user select to copy report configuration
      -  .. versionadded:: 3.9.3
   *  -  **copyEmailConfiguration** |br|
         boolean
      -
      -  Does user select to copy email configuration
      -  .. versionadded:: 3.9.3
   *  -  **copyRoles** |br|
         boolean
      -
      -  Does user select to copy roles
      -
   *  -  **copyRolePermission** |br|
         boolean
      -
      -  Does user select to copy role permissions
      -
   *  -  **copyAdvancedSettings** |br|
         boolean
      -
      -  Does user select to copy advanced settings
      -
   *  -  **copyDataModel** |br|
         boolean
      -
      -  Does user select to copy data model
      -
   *  -  **copyReport** |br|
         boolean
      -
      -  Does user select to copy reports
      -
   *  -  **copyDashboard** |br|
         boolean
      -
      -  Does user select to copy dashboards
      -
   *  -  **copyTenantPermissions** |br|
         boolean
      -
      -  Does user select to copy tenant permissions
      -
   *  -  **sourceId** |br|
         string (GUID)
      -  Y
      -  The id of the source
      -
   *  -  **selectAllTenants** |br|
         boolean
      -
      -  Does user select all tenants as destination
      -
   *  -  **sourceHashCode** |br|
         string
      -
      -  Hashcode for source
      -
   *  -  **copyPositionID** |br|
         boolean
      -
      -  Whether system admin select to copy positionID or not
      -  .. versionadded:: 2.16.0


Inherited fields:

.. include:: Entity.rst
