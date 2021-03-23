

=========================================
QuerySourceFieldPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySource** |br|
         object
      -
      -  The parent :doc:`QuerySource` object
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **QuerySourceFieldPagedRequest Sample**:

   .. code-block:: json

      {
        "querySource" : {
           "id" : "9fa90af2-5329-44ac-a753-50c27f9d6fd5",
           "type" : "Table"
        },
        "criteria" : [],
        "tenantId" : null,
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "Alias",
              "descending" : true
           }
        ]
      }
