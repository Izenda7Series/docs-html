

=========================================
SystemVariablePagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportingType** |br|
         integer
      -
      -  The reporting type

         * 1 = Report
         * 2 = Dashboard
         * 0 = Both
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **SystemVariablePagedRequest Sample**:

   .. code-block:: json

      {
        "reportingType" : 0,
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "name",
              "descending" : true
           }
        ],
        "criteria" : []
      }
