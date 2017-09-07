

=========================================
QuerySourceCategoryPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **ConnectionId** |br|
         string (GUID)
      -
      -  The id of the connection containing the query source category.
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **QuerySourceCategoryPagedRequest Sample**:

   .. code-block:: json

      {
        "connectionId" : "ed13d1d0-cc0c-49bc-8925-3a11da65ef65",
        "tenantId" : null,
        "criteria" : [{
              "key" : "All",
              "value" : "demo",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : null
      }
