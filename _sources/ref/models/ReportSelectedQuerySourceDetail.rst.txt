

=========================================
ReportSelectedQuerySourceDetail
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The query source id
      -
   *  -  **category** |br|
         string
      -
      -  The category name
      -
   *  -  **databaseName** |br|
         string
      -
      -  The database name
      -
   *  -  **schemaName** |br|
         string
      -
      -  The schema name
      -
   *  -  **dataObject** |br|
         string
      -
      -  The data object name
      -
   *  -  **dataObjectType** |br|
         string
      -
      -  The data object type
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "id": "39e2a9b9-3be3-4b8b-ae86-0823ecb3c533",
         "category": null,
         "databaseName": "Northwind",
         "schemaName": "dbo",
         "dataObject": "CustomerCustomerDemo",
         "dataObjectType": "Table"
      }
