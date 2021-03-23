

=========================================
CategoryPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **type** |br|
         integer
      -
      -  *  0 = ReportTemplate
         *  1 = Dashboard

      -

Inherited fields:

.. include:: PagedRequest.rst

.. note:: 

   The key for :doc:`SearchCriteria`: "Name"

.. container:: toggle

   .. container:: header

      **CategoryPagedRequest Sample**:

   .. code-block:: json

      {
        "dashboardId": "a3243533-166d-4377-90eb-add25edf6563",
        "criteria": [
          {
            "key": "All",
            "value": "",
            "operation": 1
          }
        ],
        "pageIndex": 1,
        "pageSize": 10,
        "sortOrders": [
          {
            "key": "shareWith",
            "descending": true
          }
        ]
      }
