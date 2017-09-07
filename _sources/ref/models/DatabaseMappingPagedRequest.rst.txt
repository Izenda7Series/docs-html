

=========================================
DatabaseMappingPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **loadFromDatabase** |br|
         boolean
      -
      -  Whether to load from database
      -
   *  -  **serverTypeName** |br|
         string
      -
      -  The database server type
      -
   *  -  **databaseServer** |br|
         string
      -
      -  The database server
      -
   *  -  **databaseName** |br|
         string
      -
      -  The database name
      -
   *  -  **type** |br|
         integer
      -
      -  *  1 = Schema
         *  2 = Database

      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **DatabaseMappingPagedRequest Sample**:

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
