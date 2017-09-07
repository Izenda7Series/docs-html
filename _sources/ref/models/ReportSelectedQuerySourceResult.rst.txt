

=========================================
ReportSelectedQuerySourceResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **result** |br|
         array of objects
      -
      -  An array of :doc:`ReportSelectedQuerySourceDetail` objects
      -
   *  -  **relatedQuerySources** |br|
         array of objects
      -
      -  An array of :doc:`ReportSelectedQuerySource` objects
      -
   *  -  **pageIndex** |br|
         integer
      -
      -  The index of the page
      -  Inherited from :doc:`PagedResult`
   *  -  **pageSize** |br|
         integer
      -
      -  The size of the page
      -  Inherited from :doc:`PagedResult`
   *  -  **total** |br|
         integer
      -
      -  The total number of rows
      -  Inherited from :doc:`PagedResult`

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "relatedQuerySources": [{
            "querySourceId": "39e2a9b9-3be3-4b8b-ae86-0823ecb3c533",
            "isNew": false,
            "physicalChange": 0,
            "selected": false
         }, {
            "querySourceId": "c25dc1d3-8066-4fe2-9adb-179060780088",
            "isNew": false,
            "physicalChange": 0,
            "selected": false
         }, {
            "querySourceId": "2c26efb2-9ff8-43ea-bcc7-6f1063e1f635",
            "isNew": false,
            "physicalChange": 0,
            "selected": false
         }],
         "result": [{
            "id": "39e2a9b9-3be3-4b8b-ae86-0823ecb3c533",
            "category": null,
            "databaseName": "Northwind",
            "schemaName": "dbo",
            "dataObject": "CustomerCustomerDemo",
            "dataObjectType": "Table"
         }],
         "total": 1,
         "pageIndex": 1,
         "pageSize": 10
      }
