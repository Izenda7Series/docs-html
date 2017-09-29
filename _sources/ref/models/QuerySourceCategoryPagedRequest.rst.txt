

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
         string
      -
      -  The id of the :doc:`Connection`

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **QuerySourceCategoryPagedRequest Sample**:

   .. code-block:: json

      {
        "ConnectionId" : "2046c03b-3830-4385-9ac0-bdc95e92ea49",
        "criteria" : [],
        "tenantId" : null,
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "value",
              "descending" : false
           }
        ]
      }
