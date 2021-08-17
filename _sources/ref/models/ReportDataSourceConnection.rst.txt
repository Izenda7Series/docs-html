=========================================
ReportDataSourceConnection
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
      -  Y
      -  The id of the object
      -
   *  -  **name** |br|
         string
      -
      -  The name of the connection
      -
   *  -  **querySource** |br|
         array of objects
      -
      -  An array of :doc:`ReportQuerySource` objects
      -
   *  -  **serverTypeId** |br|
         string
      -
      -  The id of the server type
      -
   *  -  **serverTypeName** |br|
         string
      -
      -  The type of the server
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "id": "83554d8c-3383-42b6-be73-0bb31cdb40db",
         "name": "Northwind-MSSQL",
         "querySource": [{
            "connectionId": "83554d8c-3383-42b6-be73-0bb31cdb40db",
            "connectionName": "Northwind-MSSQL",
            "dataSourceCategoryId": "518033c3-9db5-4ac1-9cb0-c4581d052b76",
            "dataSourceCategoryName": "MSSQL",
            "fields": [{
               "alias": "",
               "allowDistinct": true,
               "allowToSave": false,
               "approval": 0,
               "calculatedTree": null,
               "categoryName": null,
               "checked": false,
               "created": null,
               "createdBy": "System Admin",
               "dataBaseType": 0,
               "dataType": "int",
               "deleted": false,
               "existed": false,
               "expression": null,
               "expressionFields": [],
               "extendedProperties": null,
               "filterLookupStatus": 0,
               "filterLookupType": 0,
               "filterable": true,
               "filteredValue": "{}",
               "fullName": null,
               "fullPath": null,
               "functionName": null,
               "groupPosition": 0,
               "hasAggregatedFunction": false,
               "hasSupportDefaultTotal": true,
               "id": "7de99693-eb74-4209-80b4-12b530837211",
               "inaccessible": false,
               "inputFeatures": null,
               "inserted": true,
               "isAlias": false,
               "isCalculated": false,
               "isCheck": false,
               "isCompositeField": false,
               "isParameter": false,
               "isPredicated": false,
               "isRunningField": false,
               "izendaDataType": "Numeric",
               "matchedTenant": false,
               "modelName": null,
               "modified": "0001-01-01T00:00:00",
               "modifiedBy": null,
               "name": "OrderID",
               "originalAlias": null,
               "originalId": "00000000-0000-0000-0000-000000000000",
               "originalName": "OrderID",
               "parentId": null,
               "physicalChange": 0,
               "position": 0,
               "querySource": null,
               "querySourceId": "ec16146f-5873-4146-9a89-3c7b36f2d1bf",
               "querySourceName": null,
               "relationColumn": null,
               "reportId": null,
               "state": 0,
               "supportDefaultTotal": null,
               "targetValue": null,
               "type": 0,
               "version": null,
               "visible": true
            }, {
               "alias": "",
               "allowDistinct": true,
               "allowToSave": false,
               "approval": 0,
               "calculatedTree": null,
               "categoryName": null,
               "checked": false,
               "created": null,
               "createdBy": "System Admin",
               "dataBaseType": 0,
               "dataType": "nchar",
               "deleted": false,
               "existed": false,
               "expression": null,
               "expressionFields": [],
               "extendedProperties": null,
               "filterLookupStatus": 0,
               "filterLookupType": 0,
               "filterable": true,
               "filteredValue": "{}",
               "fullName": null,
               "fullPath": null,
               "functionName": null,
               "groupPosition": 0,
               "hasAggregatedFunction": false,
               "hasSupportDefaultTotal": true,
               "id": "bb2f13f3-eba8-45bc-90ea-cac543691c04",
               "inaccessible": false,
               "inputFeatures": null,
               "inserted": true,
               "isAlias": false,
               "isCalculated": false,
               "isCheck": false,
               "isCompositeField": false,
               "isParameter": false,
               "isPredicated": false,
               "isRunningField": false,
               "izendaDataType": "Text",
               "matchedTenant": false,
               "modelName": null,
               "modified": "0001-01-01T00:00:00",
               "modifiedBy": null,
               "name": "CustomerID",
               "originalAlias": null,
               "originalId": "00000000-0000-0000-0000-000000000000",
               "originalName": "CustomerID",
               "parentId": null,
               "physicalChange": 0,
               "position": 0,
               "querySource": null,
               "querySourceId": "ec16146f-5873-4146-9a89-3c7b36f2d1bf",
               "querySourceName": null,
               "relationColumn": null,
               "reportId": null,
               "state": 0,
               "supportDefaultTotal": null,
               "targetValue": null,
               "type": 0,
               "version": null,
               "visible": true
            }],
            "id": "ec16146f-5873-4146-9a89-3c7b36f2d1bf",
            "isAlias": false,
            "isCheck": false,
            "isDynamic": false,
            "name": "Orders",
            "numOfCheckedChilds": 0,
            "numOfChilds": 2,
            "originalName": "Orders",
            "querySourceCategoryName": "dbo",
            "selected": false,
            "visible": true,
            "type": "Table"
         }],
         "serverTypeId": "572bd576-8c92-4901-ab2a-b16e38144813",
         "serverTypeName": "MSSQL",
      }
