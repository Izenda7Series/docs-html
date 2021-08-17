=========================================
RelatedDataSourcesWithRelationshipsResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **relatedDataSources** |br|
         array of objects
      -
      -  An array of :doc:`QuerySource` objects
      -
   *  -  **selectedRealtionships** |br|
         array of objects
      -
      -  An array of :doc:`Relationship` objects
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "relatedDataSources": [{
            "serverTypeId": "572bd576-8c92-4901-ab2a-b16e38144813",
            "serverTypeName": "MSSQL",
            "id": "83554d8c-3383-42b6-be73-0bb31cdb40db",
            "name": "Northwind-MSSQL",
            "querySource": [{
               "id": "8b26c324-6b9e-484e-8202-123e2180bd0b",
               "name": "Employees",
               "originalName": "Employees",
               "type": "Table",
               "selected": true,
               "visible": true,
               "querySourceCategoryName": "dbo",
               "dataSourceCategoryName": "MSSQL",
               "dataSourceCategoryId": "518033c3-9db5-4ac1-9cb0-c4581d052b76",
               "connectionName": "Northwind-MSSQL",
               "connectionId": "83554d8c-3383-42b6-be73-0bb31cdb40db",
               "isAlias": false,
               "isNativeAlias": false,
               "isDynamic": false,
               "fields": [{
                  "name": "EmployeeID",
                  "alias": "",
                  "dataType": "int",
                  "izendaDataType": "Numeric",
                  "allowDistinct": true,
                  "visible": true,
                  "filterable": true,
                  "querySourceId": "8b26c324-6b9e-484e-8202-123e2180bd0b",
                  "parentId": null,
                  "expressionFields": [],
                  "filteredValue": "{}",
                  "type": 0,
                  "groupPosition": 0,
                  "position": 0,
                  "extendedProperties": null,
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "checked": false,
                  "matchedTenant": false,
                  "functionName": null,
                  "expression": null,
                  "isRunningField": false,
                  "supportDefaultTotal": null,
                  "fullName": null,
                  "calculatedTree": null,
                  "reportId": null,
                  "originalName": "EmployeeID",
                  "isAlias": false,
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isParameter": false,
                  "isCalculated": false,
                  "isPredicated": false,
                  "modelName": null,
                  "targetValue": null,
                  "relationColumn": null,
                  "inputFeatures": null,
                  "hasAggregatedFunction": false,
                  "isCompositeField": false,
                  "hasSupportDefaultTotal": true,
                  "querySource": null,
                  "querySourceName": null,
                  "categoryName": null,
                  "inaccessible": false,
                  "originalAlias": null,
                  "allowToSave": false,
                  "filterLookupType": 0,
                  "filterLookupStatus": 0,
                  "dataBaseType": 0,
                  "fullPath": null,
                  "isCheck": false,
                  "id": "4fdcb7e5-0d09-4fdf-a0f2-e1b69589941f",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System Admin",
                  "modified": "0001-01-01T00:00:00",
                  "modifiedBy": null
               }],
               "numOfChilds": 1,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false
            }],
            "numOfChilds": 0,
            "numOfCheckedChilds": 0,
            "indeterminate": false,
            "fullPath": null,
            "computeNameSettings": null,
            "isCheck": false
         }],
         "selectedRealtionships": [{
            "joinConnectionId": "83554d8c-3383-42b6-be73-0bb31cdb40db",
            "foreignConnectionId": "83554d8c-3383-42b6-be73-0bb31cdb40db",
            "joinQuerySourceAlias": null,
            "foreignQuerySourceAlias": null,
            "joinFieldAlias": "",
            "specifictJoinFieldAlias": null,
            "foreignFieldAlias": "",
            "specifictForeignFieldAlias": null,
            "alias": "Employees (Self-Joined)",
            "systemRelationship": false,
            "disabled": false,
            "joinType": "Inner",
            "parentRelationshipId": "b5109c00-7c43-4e88-9216-3b22cd3768b5",
            "position": null,
            "relationshipPosition": 0,
            "hasBeenModified": false,
            "isPredictionRelation": false,
            "predictionRelationId": null,
            "predictionId": null,
            "relationshipKeyJoins": [],
            "reportId": null,
            "foreignAlias": null,
            "joinQuerySourceUniqueName": null,
            "joinFieldUniqueName": null,
            "forgeinQuerySourceUniqueName": null,
            "forgeinFieldUniqueName": null,
            "tempId": null,
            "aliasTempId": null,
            "originalId": "00000000-0000-0000-0000-000000000000",
            "isForeignDataObjectAlias": false,
            "positionId": null,
            "selectedForeignAlias": "8b26c324-6b9e-484e-8202-123e2180bd0b_Employees",
            "joinQuerySourceName": "Employees",
            "joinQuerySourceId": "8b26c324-6b9e-484e-8202-123e2180bd0b",
            "joinFieldId": "68f8968b-d5d7-4e5f-b822-abba656bea34",
            "joinFieldType": null,
            "foreignQuerySourceName": "Employees",
            "foreignQuerySourceId": "8b26c324-6b9e-484e-8202-123e2180bd0b",
            "foreignFieldId": "4fdcb7e5-0d09-4fdf-a0f2-e1b69589941f",
            "foreignFieldType": null,
            "joinFieldName": "ReportsTo",
            "foreignFieldName": "EmployeeID",
            "joinDataSourceCategoryId": "518033c3-9db5-4ac1-9cb0-c4581d052b76",
            "joinDataSourceCategoryName": "MSSQL",
            "foreignDataSourceCategoryId": "518033c3-9db5-4ac1-9cb0-c4581d052b76",
            "foreignDataSourceCategoryName": "MSSQL",
            "comparisonOperator": null,
            "id": "5c41f75b-7cc0-4459-91ab-4187da590ea8",
            "state": 1,
            "deleted": false,
            "inserted": false,
            "version": null,
            "created": null,
            "createdBy": "System Admin",
            "modified": "2021-06-17T14:42:13",
            "modifiedBy": null
         }]
      }
