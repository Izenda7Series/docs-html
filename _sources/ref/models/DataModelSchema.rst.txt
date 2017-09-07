

=========================================
DataModelSchema
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySources** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceSchema` objects
      -
   *  -  **relationships** |br|
         array of objects
      -
      -  An array of :doc:`RelationshipSchema` objects
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "querySources": [{
            "id": "8aa52ba9-8324-4b8e-bf42-619a3f050aa5",
            "name": "dbo.Customers",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-04-19T03:08:56.091528",
            "fields": [{
                 "name": "ContactName",
                 "properties": ""
            }, {
                 "name": "CustomerID",
                 "properties": "{\"PrimaryKey\":true}"
            }]
         }, {
            "id": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "name": "dbo.Orders",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-12-19T03:08:56.091528",
            "fields": [{
                 "name": "CustomerID",
                 "properties": ""
            }, {
                 "name": "OrderDate",
                 "properties": ""
            }, {
                 "name": "OrderID",
                 "properties": "{\"PrimaryKey\":true}"
            }]
         }, {
            "id": "26efbdf4-c724-4824-bd9c-6ae1e2dc7435",
            "name": "dbo.Order Details",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-12-19T03:08:56.091528",
            "fields": [{
                 "name": "OrderID",
                 "properties": "{\"PrimaryKey\":true}"
            }, {
                 "name": "ProductID",
                 "properties": "{\"PrimaryKey\":true}"
            }, {
                 "name": "Quantity",
                 "properties": ""
            }, {
                 "name": "UnitPrice",
                 "properties": ""
            }]
         }],
         "relationships": [{
            "joinQuerySourceId": "8aa52ba9-8324-4b8e-bf42-619a3f050aa5",
            "foreignQuerySourceId": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "twoWays": false
         }, {
            "joinQuerySourceId": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "foreignQuerySourceId": "26efbdf4-c724-4824-bd9c-6ae1e2dc7435",
            "twoWays": true
         }]
      }
