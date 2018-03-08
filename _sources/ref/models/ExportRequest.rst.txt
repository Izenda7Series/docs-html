

=========================================
ExportRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard if available
      -
   *  -  **dashboardPartId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard part if available
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report if available
      -
   *  -  **draftID** |br|
         string (GUID)
      -  Y
      -  The id of the draft if available
      -
   *  -  **reportPartId** |br|
         string (GUID)
      -  Y
      -  The id of the report part if available
      -
   *  -  **filters** |br|
         array of objects
      -  Y
      -  An array of :doc:`FilterItem` objects.
      -
   *  -  **fileSession** |br|
         string
      -
      -  The key of this specific session.
      -
   *  -  **reportDefinition** |br|
         object
      -  Y
      -  The :doc:`ReportDefinition` object if available.
      -
   *  -  **dashboardDefinition** |br|
         object
      -  Y
      -  The :doc:`DashboardDefinition` object if available.
      -
   *  -  **dashboardPartIndex** |br|
         integer
      -  Y
      -  The index of the dashboard part if available.
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available.
      -
   *  -  **subReportFilters** |br|
         object
      -  Y
      -  An array of :doc:`FilterItem` objects if available.
      -
   *  -  **queryString** |br|
         string
      -  Y
      -  The query string
      -
   *  -  **token** |br|
         object
      -  Y
      -  The authentication token
      -
