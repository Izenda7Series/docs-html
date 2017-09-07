

====================
FusionDataRequest
====================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **userAction** |br|
         string
      -
      -  The user action, used for logging user behavior
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report
      -
   *  -  **reportPartId** |br|
         string (GUID)
      -  Y
      -  The id of the report part
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **dashboardPartId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard part
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **expandedLevel** |br|
         integer
      -
      -  The expanded level
      -
   *  -  **filters** |br|
         array of objects
      -
      -  An array of :doc:`FilterItem` objects
      -
   *  -  **masterReportId** |br|
         string (GUID)
      -  Y
      -  The id of the master report
      -
   *  -  **inheritMasterReportFilter** |br|
         boolean
      -
      -  Whether to inherit filters from master report
      -
   *  -  **paging** |br|
         object
      -
      -  A :doc:`PagingInfo` object
      -
   *  -  **overridingFilterValue** |br|
         object
      -
      -  A dynamic object to store filter values to override
      -
   *  -  **overridingFilterOperator** |br|
         object
      -
      -  A dynamic object to store filter operators to override
      -
   *  -  **sortOrders** |br|
         array of objects
      -
      -  An array of :doc:`SortParam` objects
      -
   *  -  **loadDraft** |br|
         boolean
      -
      -  Whether to load report from draft
      -
   *  -  **loadAll** |br|
         boolean
      -
      -  Whether to load all records for exporting or printing
      -
   *  -  **loadDefaultData** |br|
         boolean
      -
      -  Whether to load default data for dashboard part
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "dashboardPartId" : "8f64491a-3c07-46c7-a224-f5f6a58a1e29",
        "expandedLevel" : -1
      }
