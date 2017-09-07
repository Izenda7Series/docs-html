

=========================================
ReportSelectedPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySources** |br|
         array of objects
      -
      -  An array of :doc:`ReportSelectedQuerySource` objects
      -
   *  -  **categoryId** |br|
         string (GUID)
      -  Y
      -  The id of the category if available
      -  Inherited from :doc:`ReportPagedRequest`
   *  -  **subCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the sub-category if available
      -  Inherited from :doc:`ReportPagedRequest`
   *  -  **timestampOffset** |br|
         real number
      -
      -  The timestamp offset. See :doc:`/ui/doc_user_setup`.
      -  Inherited from :doc:`ReportPagedRequest`

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **ReportSelectedPagedRequest Sample**:

   .. code-block:: json

       {
         "querySources" : [{
             "querySourceId": "39e2a9b9-3be3-4b8b-ae86-0823ecb3c533",
             "selected": true
          }],
         "tenantId" : null,
         "criteria" : null,
         "pageIndex" : 1,
         "pageSize" : 10,
         "sortOrders" : null
       }
