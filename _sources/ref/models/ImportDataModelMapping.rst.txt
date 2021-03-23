
=========================================
ImportDataModelMapping
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **FromConnectionName** |br|
         string
      -
      -  The name of the source connector
      -
   *  -  **FromSchemaName** |br|
         string
      -
      -  The source schema name
      -
   *  -  **ToConnectionName** |br|
         string
      -
      -  The name of the destination connector
      -
   *  -  **ToSchemaName** |br|
         string
      -
      -  The destination schema name
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "FromConnectionName": "Northwind",
         "FromSchemaName": "dbo",
         "ToConnectionName": "Northwind",
         "ToSchemaName": "dbo"
      }