

=========================================
DashboardFilterFieldPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dashboard** |br|
         object
      -
      -  A :doc:`DashboardDefinition` object
      -
   *  -  **commonFilterName** |br|
         string
      -
      -  The common filter name
      -
   *  -  **includeAll** |br|
         boolean
      -
      -  Whether paged result should include [ALL]
      -
   *  -  **includeBlank** |br|
         boolean
      -
      -  Whether paged result should include [BLANK]
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **DashboardFilterFieldPagedRequest Sample**:

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
