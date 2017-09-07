

=======================
WorkspaceDetailConsole
=======================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportDefinition** |br|
         object
      -
      -  A :doc:`ReportDefinition` object
      -
   *  -  **destinationTenants** |br|
         array of objects
      -
      -  An array of :doc:`DestinationTenant` objects
      -
   *  -  **mappingType** |br|
         integer
      -
      -  Whether Database mapping or Schema mapping
      -
   *  -  **dataSourceConnections** |br|
         object
      -
      -  A :doc:`DataSourceConnections` object
      -
   *  -  **sourceTenantConnections** |br|
         array of objects
      -
      -  An array of :doc:`Connection` objects
      -
   *  -  **sourceRoles** |br|
         array of objects
      -
      -  An array of :doc:`Role` objects
      -
   *  -  **categoryType** |br|
         integer
      -
      -  
         * 0 = Report
         * 1 = Template
         * 2 = Dashboard
      -
   *  -  **sourceUserPermissions** |br|
         dynamic object
      -
      -  A dynamic object with field names equal to id of reports and dashboards, and field values populated by an array of :doc:`UserPermission` objects
      -
   *  -  **dashBoardDefinition** |br|
         object
      -
      -  A :doc:`DashboardDefinition` object
      -
   *  -  **sourceReports** |br|
         array of objects
      -
      -  An array of :doc:`Report` objects
      -
   *  -  **reportDefinitions** |br|
         array of objects
      -
      -  An array of :doc:`ReportDefinition` objects
      -


Inherited fields:

.. include:: WorkspaceDetail.rst
