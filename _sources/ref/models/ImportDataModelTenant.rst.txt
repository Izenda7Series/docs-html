
=========================================
ImportDataModelTenant
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **Name** |br|
         string
      -
      -  The name of the destination tenant
      -
   *  -  **Mappings** |br|
         array of objects
      -
      -  An array of :doc:`ImportDataModelMapping` objects
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "Name": "YourDestinationTenantName",
         "Mappings": [
            {
               "FromConnectionName": "Northwind",
               "FromSchemaName": "dbo",
               "ToConnectionName": "Northwind",
               "ToSchemaName": "dbo"
            }
         ]
      }
