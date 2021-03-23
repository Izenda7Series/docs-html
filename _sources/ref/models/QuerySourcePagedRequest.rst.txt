

=========================================
QuerySourcePagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySourceType** |br|
         string
      -
      -  The query source type (Table, View, or Stored Procedure)
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **QuerySourcePagedRequest Sample**:

   .. code-block:: json

      {
        "querySourceType" : "Table",
        "tenantId" : null,
        "criteria" : [{
              "key" : "DataSourceName",
              "value" : "demo",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "Category",
              "descending" : true
           }
        ]
      }
