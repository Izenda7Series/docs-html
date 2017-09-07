

=========================================
ReloadQuerySourceRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySourceId** |br|
         string (GUID)
      -
      -  The query source id
      -
   *  -  **postedParameters** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceField` objects
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **ReloadQuerySourceRequest Sample**:

   .. code-block:: json

      {
        "querySourceId" : "0cd0f186-48f1-47a9-9975-1f2bded3a5cc",
        "postedParameters" : [{
              "id" : "8ccfac80-c883-446b-948d-18568dc4d173",
              "name" : "@OrderID",
              "filteredValue" : {
                 "type":"1",
                 "databaseName":"Northwind",
                 "databaseId":"f7d00fd9-bfb4-40ae-b25a-61007781b196",
                 "querySourceName":"dbo.Order Details",
                 "querySourceId":"000e6c8a-89fd-4b38-8d6a-1b891c180daa",
                 "lookupKeyQuerySourceFieldName":"OrderID",
                 "lookupKeyQuerySourceFieldId":"a0acf5b0-4e47-49d6-af73-c953408df3ef",
                 "displayQuerySourceFieldName":"OrderID",
                 "displayQuerySourceFieldId":"a0acf5b0-4e47-49d6-af73-c953408df3ef",
                 "userDefinedValues": []
              }
           }
        ],
        "sortOrders" : [{
              "key" : "ColumnName",
              "descending" : true
           }
        ]
      }
