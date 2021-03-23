
=========================================
ExportDataModel
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **SourceTenant** |br|
         string
      -
      -  The name of the source tenant (or blank if it is System level).
      -
   *  -  **SelectedConnections** |br|
         array of objects
      -
      -  An array of :doc:`Connection` objects.

         .. note::
            It is enough to specify only the names of the Сonnector, Schema, and DataSource, as in the example below.
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "SourceTenant": "YourSourceTenantName",
         "SelectedConnections": [
            {
               "Name": "Northwind",
               "DBSource": {
                  "QuerySources": [
                     {
                        "Name": "dbo",
                        "QuerySources": [
                           {
                              "Name": "Orders"
                           },
                           {
                              "Name": "Order Details"
                           }
                        ]
                     }
                  ]
               }
            }
         ]
      }
