
=========================================
ImportDataModel
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **DataModelFileId** |br|
         string
      -
      -  The id of \*.bidm file uploaded to the server using the external API (:doc:`../../swagger/import-export`)
      -
   *  -  **DestinationTenants** |br|
         array of objects
      -
      -  An array of :doc:`ImportDataModelTenant` objects
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "DataModelFileId": "4ba9b973-629b-458b-94fc-f901dba49852_DatamodelofSystemtenant",
         "DestinationTenants": [
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
         ]
      }
