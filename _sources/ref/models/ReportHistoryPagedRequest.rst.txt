

=========================================
ReportHistoryPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report if available
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

      **ReportHistoryPagedRequest Sample**:

   .. code-block:: json

      {
        "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "tenantId" : null,
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "version",
              "descending" : true
           }
        ]
      }
