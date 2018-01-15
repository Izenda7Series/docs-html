

=============================================
Report Designer Data and Expressions APIs
=============================================

The **Report Designer** page allows user to

-  create a report
-  select report data sources
-  create report filters
-  design report layout
-  set up report schedule

This page documents the APIs related to data and expressions.

Summary 
------------

.. list-table::
   :class: apitable
   :widths: 25 45 30
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `POST fusion/validateExpression`_
     - Validates calculated field expression syntax and returns a suggested data type (can handle multiple data sources). |br| |br|
       See also: `POST fusion/validateDataModelExpression`_
     - Report Designer > Fields > Add Calculated Field > Expression
   * - `POST fusion/validateGrandTotalExpression`_
     - Validates grand total expression syntax and returns a suggested data type.
     - In Report Designer > Field Properties > Grand Total > Choose [Expression] in Grand Total Funtion dropdown list > Input an expression
   * - `POST fusion/validateSubTotalExpression`_
     - Validates sub total expression syntax and returns a suggested data type. |br| |br|
       Same request and response as `POST fusion/validateGrandTotalExpression`_
     - In Report Designer > Field Properties > Sub Total > Choose [Expression] in Sub Total Funtion dropdown list > Input an expression
   * - `POST fusion/loadData`_
     - Loads data for report.
     - Report Viewer
   * - `POST fusion/reportPartPreview`_
     - Loads preview data for report part.
     - In Report Designer:
       \- Add any field to the container |br|
       \- OR Copy a report part
   * - `POST fusion/previewGrandTotal`_
     - Loads preview data for grand total.
     - In Report Designer > Field Properties > Grand Total > Input all required fields in Grand Total Settings popup > Click on "Preview" button
   * - `GET fusion/{report_id}/{report_part_id}/(pageIndex)/(pageSize)`_
     - Loads report part data with paging and optional overridden filter values and operators.
     -
   * - `POST fusion/validateDataModelExpression`_
     - Validates a calculated field expression in Data Model and returns a suggested data type (in a single data source). |br| |br|
       See also: `POST fusion/validateExpression`_
     - Settings > Data Setup > Data Model > Tables > Add Calculated Field > Expression
   * - `POST fusion/previewCalculatedField`_
     - Loads preview data for a calculated field.
     - Report Designer - Field > Addd Calculated Field > Preview
   * - `POST fusion/previewSubTotal`_
     - Loads preview data for sub total.
     - In Report Designer > Field Properties > Sub Total > Input all required fields in Sub Total Settings popup > Click on "Preview" button
   * - `POST fusion/calculatedFieldValue`_
     - Returns a single calculated field value for preview section.
     -
   * - `POST fusion/retrieveRandomExpandedLevelData`_
     - Returns random expanded level data.
     -
   * - `POST fusion/printQuery`_
     - Returns the sql query for a data request.
     - 
   * - `POST fusion/reportPartPreview`_
     - Returns data for a report part preview request.
     - In Report Designer: |br|
        \- Click on "Update Result" button |br|
        \- OR Add any field to containers |br|
        \- OR Remove any fiels from containers |br|
        \- OR Make any field in containers changed
   * - `GET fusion/printQuery/{reportId}/{reportPartId}/(pageIndex)/(pageSize)`_
     - Returns the sql query for a report part load with paging and optional overridden filter values and operators.
     -

POST fusion/validateExpression
--------------------------------------------------------------

Validates filter expression syntax and returns a suggested data type (can handle multiple data sources). |br| |br|
See also: `POST fusion/validateDataModelExpression`_

**Request**

    Payload: a :doc:`models/ReportExpressionParameter` object

**Response**

    A :doc:`models/ValidationOperationResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/validateExpression HTTP/1.1

   Request payload::

      {
            "reportKey": {
                  "key": "c0091e01-22f9-44a5-99e3-eb656a1fcebd"
            },
            "expression": "RUNNINGCOUNT([SQL-Northwind].[dbo].[Order Details].[OrderID])",
            "izendaDataType": "Numeric",
            "querySourceFieldId": null,
            "previewRecord": 10
      }

   Response::

      {
         "result": {
            "izendaDataType": "Numeric",
            "isRunningField": false,
            "isCompositeField": false
         },
         "success": true,
         "messages": [],
         "data": null
      }


POST fusion/validateGrandTotalExpression
--------------------------------------------------------------

Validates grand total expression syntax and returns a suggested data type.

**Request**

    Payload: a :doc:`models/ReportPartValidateExpressionParameter` object

**Response**

    An :doc:`models/ValidationOperationResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/validateGrandTotalExpression HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "reportKey" : {
              "key" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1"
           },
           "report" : {
              "name" : "",
              "type" : "Templates",
              "previewRecord" : 10,
              "advancedMode" : true,
              "allowNulls" : false,
              "isDistinct" : false,
              "category" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "subCategory" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "reportDataSource" : [{
                    "aliasId" : "1641cb37-b60c-42bc-b986-c51667e8037d_Suppliers",
                    "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                    "querySourceName" : "Suppliers",
                    "selected" : true,
                    "categoryId" : "00000000-0000-0000-0000-000000000000",
                    "primaryFields" : [{
                          "name" : "SupplierID",
                          "alias" : "",
                          "dataType" : "int",
                          "izendaDataType" : "Numeric",
                          "allowDistinct" : false,
                          "visible" : true,
                          "filterable" : true,
                          "deleted" : false,
                          "querySourceId" : "00000000-0000-0000-0000-000000000000",
                          "parentId" : null,
                          "expressionFields" : [],
                          "filteredValue" : "",
                          "type" : 0,
                          "groupPosition" : 0,
                          "position" : 0,
                          "extendedProperties" : "{\"PrimaryKey\":true}",
                          "physicalChange" : 0,
                          "approval" : 0,
                          "existed" : false,
                          "matchedTenant" : false,
                          "functionName" : null,
                          "expression" : null,
                          "fullName" : null,
                          "calculatedTree" : null,
                          "reportId" : null,
                          "originalName" : "SupplierID",
                          "isParameter" : false,
                          "isCalculated" : false,
                          "querySource" : null,
                          "id" : "47954424-fff3-4157-9296-ad08b751e71d",
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : "0001-01-01T00:00:00.0000000-08:00",
                          "modifiedBy" : null
                       }
                    ]
                 }
              ],
              "reportRelationship" : [],
              "reportFilter" : {
                 "logic" : "",
                 "visible" : false,
                 "filterFields" : [],
                 "id" : "4a75d01f-1fb3-4eca-ae13-8f17d41289ea",
                 "reportId" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1"
              },
              "reportPart" : [{
                    "isDirty" : true,
                    "reportPartContent" : {
                       "isDirty" : false,
                       "type" : 3,
                       "columns" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [{
                                "reportPartContent" : null,
                                "isDirty" : false,
                                "name" : "Country",
                                "properties" : {
                                   "isDirty" : false,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "",
                                      "functionInfo" : {},
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Text"
                                      },
                                      "grandTotal" : {
                                         "label" : "Total Number of Countries",
                                         "function" : "Count Distinct",
                                         "expression" : "",
                                         "dataType" : "Numeric",
                                         "previewResult" : 10,
                                         "fieldDataType" : "Text"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : 0,
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 1,
                                "field" : {
                                   "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
                                   "fieldName" : "Country",
                                   "fieldNameAlias" : "Country",
                                   "dataFieldType" : "Text",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : true
                             }, {
                                "reportPartContent" : null,
                                "isDirty" : true,
                                "name" : "Count (SupplierID)",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                      "functionInfo" : {
                                         "id" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                         "name" : "Count",
                                         "expression" : null,
                                         "dataType" : "Numeric",
                                         "formatDataType" : "Numeric",
                                         "syntax" : null,
                                         "expressionSyntax" : null,
                                         "isOperator" : false
                                      },
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      },
                                      "grandTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : {},
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 2,
                                "field" : {
                                   "fieldId" : "47954424-fff3-4157-9296-ad08b751e71d",
                                   "fieldName" : "SupplierID",
                                   "fieldNameAlias" : "Count (SupplierID)",
                                   "dataFieldType" : "Numeric",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : false
                             }
                          ],
                          "name" : "columns"
                       },
                       "rows" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "rows"
                       },
                       "values" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "values"
                       },
                       "separators" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "separators"
                       },
                       "properties" : {
                          "isDirty" : true,
                          "generalInfo" : {
                             "gridStyle" : "Vertical",
                             "separatorStyle" : "Comma"
                          },
                          "table" : {
                             "backgroundColor" : "#efefef",
                             "border" : {
                                "top" : {},
                                "right" : {},
                                "bottom" : {},
                                "midVer" : {},
                                "left" : {},
                                "midHor" : {}
         
                             }
                          },
                          "columns" : {
                             "width" : {
                                "value" : null,
                                "unit" : "Pixels"
                             },
                             "alterBackgroundColor" : false
                          },
                          "rows" : {
                             "height" : 40,
                             "alterBackgroundColor" : false
                          },
                          "headers" : {
                             "font" : {
                                "family" : "Roboto",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "backgroundColor" : "#dbf2ff"
                             },
                             "alignment" : "left",
                             "wordWrap" : true,
                             "removeHeaderForExport" : false
                          },
                          "grouping" : {
                             "useSeparator" : false
                          },
                          "view" : {
                             "dataRefreshInterval" : {
                                "enable" : false,
                                "updateInterval" : 0,
                                "isAll" : true,
                                "latestRecord" : 0
                             }
                          }
                       },
                       "settings" : {},
                       "dataSource" : {},
                       "title" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       },
                       "description" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : false,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       }
                    },
                    "reportId" : "00000000-0000-0000-0000-000000000000",
                    "positionX" : 0,
                    "positionY" : 0,
                    "width" : 12,
                    "height" : 4,
                    "state" : 3,
                    "modified" : null,
                    "numberOfRecord" : 0,
                    "isBackSide" : true,
                    "expandedLevel" : 0,
                    "points" : [{
                          "key" : "All",
                          "filter" : [{
                                "key" : "",
                                "value" : ""
                             }
                          ],
                          "expandedLevel" : 0,
                          "isViewSeparator" : false
                       }
                    ],
                    "isSelected" : true,
                    "title" : "Grid",
                    "id" : "561dba1e-f799-42be-be9d-bbfa078aee43"
                 }
              ],
              "version" : 0
           },
           "title" : "Grid",
           "expression" : "",
           "reportField" : {
              "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
              "fieldName" : "Country",
              "fieldNameAlias" : "Country",
              "dataFieldType" : "Text",
              "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
              "querySourceType" : "Table",
              "sourceAlias" : "Suppliers",
              "relationshipId" : null,
              "visible" : true,
              "calculatedTree" : null,
              "schemaName" : "dbo",
              "querySourceName" : "Suppliers",
              "databaseName" : "Northwind",
              "isCalculated" : false
           }
         }

   Response::

      {
         "result": {
            "izendaDataType": "Numeric"
         },
         "success": true,
         "messages": [],
         "data": null
      }

POST fusion/validateSubTotalExpression
--------------------------------------------------------------

Validates grand total expression syntax and returns a suggested data type.

**Request**

    Payload: a :doc:`models/ReportPartValidateExpressionParameter` object

**Response**

    An :doc:`models/ValidationOperationResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/validateSubTotalExpression HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
            "reportKey": {
               "key": "eb627589-cc33-47a6-9031-3ad1f2787638",
               "tenantId": "28788c9b-4e0d-464e-b588-ea5bee676bd3"
            },
            "report": {
               "name": "exReport",
               "type": 0,
               "previewRecord": 10,
               "advancedMode": true,
               "allowNulls": false,
               "isDistinct": false,
               "categoryId": "c279ed4d-f4d0-4abd-8d10-d396512ee77a",
               "category": {
                  "id": "c279ed4d-f4d0-4abd-8d10-d396512ee77a",
                  "name": "myCategory",
                  "type": 0,
                  "tenantId": "28788c9b-4e0d-464e-b588-ea5bee676bd3"
               },
               "subCategory": {
                  "id": null,
                  "name": "",
                  "type": 0,
                  "tenantId": "28788c9b-4e0d-464e-b588-ea5bee676bd3"
               },
               "subCategoryId": null,
               "reportDataSource": [{
                  "aliasId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03_film_actor",
                  "querySourceId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03",
                  "querySourceName": "film_actor",
                  "selected": true,
                  "categoryId": "30077a15-9fef-42af-8b24-d224ab7757ba",
                  "primaryFields": [{
                     "name": "actor_id",
                     "alias": "",
                     "dataType": "smallint",
                     "izendaDataType": "Numeric",
                     "allowDistinct": false,
                     "visible": true,
                     "filterable": true,
                     "querySourceId": "00000000-0000-0000-0000-000000000000",
                     "parentId": null,
                     "expressionFields": [],
                     "filteredValue": "",
                     "type": 0,
                     "groupPosition": 0,
                     "position": 0,
                     "extendedProperties": "{\"PrimaryKey\":true}",
                     "physicalChange": 0,
                     "approval": 0,
                     "existed": false,
                     "matchedTenant": false,
                     "functionName": null,
                     "expression": null,
                     "isRunningField": false,
                     "fullName": null,
                     "calculatedTree": null,
                     "reportId": null,
                     "originalName": "actor_id",
                     "originalId": "00000000-0000-0000-0000-000000000000",
                     "isParameter": false,
                     "isCalculated": false,
                     "hasAggregatedFunction": false,
                     "querySource": null,
                     "querySourceName": null,
                     "categoryName": null,
                     "inaccessible": false,
                     "originalAlias": null,
                     "fullPath": null,
                     "isCheck": false,
                     "id": "070926fc-0ffe-449c-aa4b-867cc09c6399",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": null,
                     "created": null,
                     "createdBy": "System5 Admin5",
                     "modified": "0001-01-01T00:00:00",
                     "modifiedBy": null
                  },
                  {
                     "name": "film_id",
                     "alias": "",
                     "dataType": "smallint",
                     "izendaDataType": "Numeric",
                     "allowDistinct": false,
                     "visible": true,
                     "filterable": true,
                     "querySourceId": "00000000-0000-0000-0000-000000000000",
                     "parentId": null,
                     "expressionFields": [],
                     "filteredValue": "",
                     "type": 0,
                     "groupPosition": 0,
                     "position": 0,
                     "extendedProperties": "{\"PrimaryKey\":true}",
                     "physicalChange": 0,
                     "approval": 0,
                     "existed": false,
                     "matchedTenant": false,
                     "functionName": null,
                     "expression": null,
                     "isRunningField": false,
                     "fullName": null,
                     "calculatedTree": null,
                     "reportId": null,
                     "originalName": "film_id",
                     "originalId": "00000000-0000-0000-0000-000000000000",
                     "isParameter": false,
                     "isCalculated": false,
                     "hasAggregatedFunction": false,
                     "querySource": null,
                     "querySourceName": null,
                     "categoryName": null,
                     "inaccessible": false,
                     "originalAlias": null,
                     "fullPath": null,
                     "isCheck": false,
                     "id": "bf92615e-e775-422e-8ef7-335affbe9fad",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": null,
                     "created": null,
                     "createdBy": "System5 Admin5",
                     "modified": "0001-01-01T00:00:00",
                     "modifiedBy": null
                  }]
               }],
               "reportRelationship": [],
               "reportFilter": {
                  "logic": "",
                  "visible": false,
                  "filterFields": [],
                  "id": "f018f1f9-e5ac-4569-869e-c3c5417dbde1",
                  "reportId": "eb627589-cc33-47a6-9031-3ad1f2787638"
               },
               "reportPart": [{
                  "isDirty": false,
                  "reportPartContent": {
                     "subReportDefinitionCollection": [],
                     "collapseStatus": 0,
                     "isDirty": false,
                     "isCrossFiltering": false,
                     "type": "3",
                     "columns": 
                     {
                        "text": null,
                        "properties": {
                           
                        },
                        "settings": {
                           
                        },
                        "elements": [
                        {
                           "reportPartContent": null,
                           "isDirty": false,
                           "name": "actor_id",
                           "properties": null,
                           "position": 1,
                           "field": {
                              "fieldId": "070926fc-0ffe-449c-aa4b-867cc09c6399",
                              "fieldName": "actor_id",
                              "fieldNameAlias": "actor_id",
                              "dataFieldType": "Numeric",
                              "querySourceId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03",
                              "querySourceType": "Table",
                              "sourceAlias": "film_actor",
                              "relationshipId": "00000000-0000-0000-0000-000000000000",
                              "visible": true,
                              "calculatedTree": null,
                              "isCalculated": false,
                              "isRunningField": false,
                              "hasAggregatedFunction": false
                           },
                           "isDeleted": false,
                           "isSelected": false,
                           "offset": null
                        },
                        {
                           "reportPartContent": null,
                           "isDirty": false,
                           "name": "film_id",
                           "properties": {
                              "isDirty": false,
                              "fieldItemVisible": true,
                              "dataFormattings": {
                                 "function": "",
                                 "functionInfo": {
                                    "id": null,
                                    "name": ""
                                 },
                                 "format": {
                                    "createNewHiddenPercenOfGroupField": false
                                 },
                                 "font": null,
                                 "width": {
                                    "value": null
                                 },
                                 "alignment": "alignLeft",
                                 "sort": "Unsort",
                                 "color": null,
                                 "alternativeText": null,
                                 "customURL": null,
                                 "embeddedJavascript": null,
                                 "subTotal": {
                                    "label": "Subtotal  film_id",
                                    "function": "[Expression]",
                                    "expression": "COUNT([film_id]) * 10",
                                    "dataType": "Numeric",
                                    "format": {
                                       
                                    },
                                    "previewResult": "",
                                    "fieldDataType": "Numeric",
                                    "previewRecord": 10
                                 },
                                 "grandTotal": null
                              },
                              "headerFormating": {
                                 "font": {
                                    "family": null,
                                    "size": null,
                                    "bold": null,
                                    "italic": null,
                                    "underline": null,
                                    "color": null,
                                    "backgroundColor": null
                                 },
                                 "alignment": null,
                                 "wordWrap": null,
                                 "columnGroup": ""
                              },
                              "drillDown": {
                                 "subReport": {
                                    "selectedReport": null,
                                    "style": null,
                                    "reportPartUsed": null,
                                    "reportFilter": true,
                                    "mappingFields": [],
                                    "selectedIconValue": {
                                       "icon": null,
                                       "value": null
                                    },
                                    "viewSettingByLink": null
                                 }
                              },
                              "otherProps": {
                                 
                              }
                           },
                           "position": 2,
                           "field": {
                              "fieldId": "bf92615e-e775-422e-8ef7-335affbe9fad",
                              "fieldName": "film_id",
                              "fieldNameAlias": "film_id",
                              "dataFieldType": "Numeric",
                              "querySourceId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03",
                              "querySourceType": "Table",
                              "sourceAlias": "film_actor",
                              "relationshipId": "00000000-0000-0000-0000-000000000000",
                              "visible": true,
                              "calculatedTree": null,
                              "isCalculated": false,
                              "isRunningField": false,
                              "hasAggregatedFunction": false
                           },
                           "isDeleted": false,
                           "isSelected": false,
                           "offset": null
                        }],
                        "name": "columns"
                     },
                     "rows": null,
                     "values": null,
                     "separators": null,
                     "properties": {
                        "isDirty": false,
                        "generalInfo": {
                           "gridStyle": "Vertical",
                           "separatorStyle": "Comma"
                        },
                        "table": null,
                        "columns": {
                           "width": {
                              "value": 150
                           },
                           "alterBackgroundColor": false
                        },
                        "rows": {
                           "alterBackgroundColor": false
                        },
                        "headers": null,
                        "grouping": {
                           "useSeparator": true
                        },
                        "view": {
                           "dataRefreshInterval": {
                              "enable": false,
                              "updateInterval": 0,
                              "isAll": true,
                              "latestRecord": 0
                           },
                           "usePagination": true,
                           "collapseDrilldownByDefault": false,
                           "pageSize": 10,
                           "pivotColumnsPerExportedPage": ""
                        },
                        "printing": {
                           "usePageBreakAfterSeparator": false
                        }
                     },
                     "settings": null,
                     "changeGridStyleStatus": true,
                     "inconsitentFunction": false,
                     "dataSource": {
                        
                     },
                     "title": null,
                     "description": null
                  },
                  "reportId": "eb627589-cc33-47a6-9031-3ad1f2787638",
                  "width": 4,
                  "height": 6,
                  "state": 0,
                  "modified": null,
                  "numberOfRecord": null,
                  "configField": {
                     "reportPartContent": null,
                     "isDirty": false,
                     "name": "film_id",
                     "properties": {
                        "isDirty": false,
                        "fieldItemVisible": true,
                        "dataFormattings": null,
                        "headerFormating": null,
                        "drillDown": {
                           "subReport": {
                              "selectedReport": null,
                              "style": null,
                              "reportPartUsed": null,
                              "reportFilter": true,
                              "mappingFields": [],
                              "selectedIconValue": {
                                 "icon": null,
                                 "value": null
                              },
                              "viewSettingByLink": null
                           }
                        },
                        "otherProps": {
                           
                        }
                     },
                     "position": 2,
                     "field": {
                        "fieldId": "bf92615e-e775-422e-8ef7-335affbe9fad",
                        "fieldName": "film_id",
                        "fieldNameAlias": "film_id",
                        "dataFieldType": "Numeric",
                        "querySourceId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03",
                        "querySourceType": "Table",
                        "sourceAlias": "film_actor",
                        "relationshipId": "00000000-0000-0000-0000-000000000000",
                        "visible": true,
                        "calculatedTree": null,
                        "isCalculated": false,
                        "isRunningField": false,
                        "hasAggregatedFunction": false
                     },
                     "isDeleted": false,
                     "isSelected": false,
                     "offset": {
                        "x": 561.15625,
                        "y": 582,
                        "width": 79.84375,
                        "height": 22,
                        "left": 561.15625,
                        "right": 641,
                        "top": 582,
                        "bottom": 604
                     }
                  },
                  "stateReview": 0,
                  "refreshDataProcess": null,
                  "refreshDataInterval": null,
                  "positionY": 0,
                  "positionX": 0,
                  "title": "Grid",
                  "id": "8a23ae27-7e6f-4236-ad74-8e42c89ddcf1"
               }],
               "header": null,
               "footer": null,
               "titleDescription": null,
               "version": 1,
               "schedules": [],
               "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
               "accesses": [],
               "exportFormatSetting": null,
               "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
               "dynamicQuerySourceFields": [],
               "snapToGrid": false,
               "excludedRelationships": "",
               "isGlobal": false
            },
            "title": "Grid",
            "expression": "COUNT([film_id]) * 10",
            "izendaDataType": "Numeric",
            "reportField": {
               "fieldId": "bf92615e-e775-422e-8ef7-335affbe9fad",
               "fieldName": "film_id",
               "fieldNameAlias": "film_id",
               "dataFieldType": "Numeric",
               "querySourceId": "7a9c6bda-ac03-4f79-9c8e-9d4c21a2bc03",
               "querySourceType": "Table",
               "sourceAlias": "film_actor",
               "relationshipId": "00000000-0000-0000-0000-000000000000",
               "visible": true,
               "calculatedTree": null,
               "isCalculated": false,
               "isRunningField": false,
               "hasAggregatedFunction": false
            },
            "querySourceFieldId": null,
            "previewRecord": 10
         }

   Sample succesful response::

      {
         "result":{"izendaDataType":"Numeric"},
         "success":true,
         "messages":[],
         "data":null
      }

POST fusion/loadData
--------------------------------------------------------------

Loads data for report.

**Request**

    Payload: a :doc:`models/FusionDataRequest` object

**Response**

    A :doc:`models/FusionResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/loadData HTTP/1.1

   Request payload::

      {
        "reportId" : "49911d8e-aed6-43f2-8df6-35d82a1c2d49",
        "reportPartId" : "a83414fa-7616-4a1b-8e2c-89289deb509c",
        "expandedLevel" : -1
      }

   Sample response::

      {
        "grandTotalMapping" : [],
        "subTotalMapping" : [],
        "sideTotalMapping" : [],
        "records" : [{
              "customerid_e0272ef4_a4b8_" : "VINET",
              "employeeid_32f2548d_87bf_" : 5
           }, {
              "customerid_e0272ef4_a4b8_" : "TOMSP",
              "employeeid_32f2548d_87bf_" : 6
           }, {
              "customerid_e0272ef4_a4b8_" : "HANAR",
              "employeeid_32f2548d_87bf_" : 4
           }, {
              "customerid_e0272ef4_a4b8_" : "VICTE",
              "employeeid_32f2548d_87bf_" : 3
           }, {
              "customerid_e0272ef4_a4b8_" : "SUPRD",
              "employeeid_32f2548d_87bf_" : 4
           }, {
              "customerid_e0272ef4_a4b8_" : "HANAR",
              "employeeid_32f2548d_87bf_" : 3
           }, {
              "customerid_e0272ef4_a4b8_" : "CHOPS",
              "employeeid_32f2548d_87bf_" : 5
           }, {
              "customerid_e0272ef4_a4b8_" : "RICSU",
              "employeeid_32f2548d_87bf_" : 9
           }, {
              "customerid_e0272ef4_a4b8_" : "WELLI",
              "employeeid_32f2548d_87bf_" : 3
           }, {
              "customerid_e0272ef4_a4b8_" : "HILAA",
              "employeeid_32f2548d_87bf_" : 4
           }
        ],
        "fieldsMapping" : [{
              "fieldId" : "e0272ef4-a4b8-4cc6-b319-3c2794688e7c",
              "fieldNameAlias" : "CustomerID",
              "columnName" : "customerid_e0272ef4_a4b8_"
           }, {
              "fieldId" : "32f2548d-87bf-468d-846c-c7cc665da203",
              "fieldNameAlias" : "EmployeeID",
              "columnName" : "employeeid_32f2548d_87bf_"
           }
        ],
        "paging" : {
           "pageIndex" : 0,
           "pageSize" : 0,
           "total" : 0
        }
      }


POST fusion/reportPartPreview
--------------------------------------------------------------

Loads preview data for report part.

**Request**

    Payload: a :doc:`models/ReportPartPreviewParameter` object

**Response**

    An object or an array of :doc:`models/FusionResult` objects

**Samples**

   .. code-block:: http

      POST /api/fusion/reportPartPreview HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "reportKey" : {
              "key" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1",
              "modified" : null
           },
           "section" : 2,
           "saveAs" : false,
           "ignoreCheckChange" : false,
           "report" : {
              "name" : "",
              "type" : "Templates",
              "previewRecord" : 10,
              "advancedMode" : true,
              "allowNulls" : false,
              "isDistinct" : false,
              "category" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "subCategory" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "reportDataSource" : [{
                    "aliasId" : "1641cb37-b60c-42bc-b986-c51667e8037d_Suppliers",
                    "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                    "querySourceName" : "Suppliers",
                    "selected" : true,
                    "categoryId" : "00000000-0000-0000-0000-000000000000",
                    "primaryFields" : [{
                          "name" : "SupplierID",
                          "alias" : "",
                          "dataType" : "int",
                          "izendaDataType" : "Numeric",
                          "allowDistinct" : false,
                          "visible" : true,
                          "filterable" : true,
                          "deleted" : false,
                          "querySourceId" : "00000000-0000-0000-0000-000000000000",
                          "parentId" : null,
                          "expressionFields" : [],
                          "filteredValue" : "",
                          "type" : 0,
                          "groupPosition" : 0,
                          "position" : 0,
                          "extendedProperties" : "{\"PrimaryKey\":true}",
                          "physicalChange" : 0,
                          "approval" : 0,
                          "existed" : false,
                          "matchedTenant" : false,
                          "functionName" : null,
                          "expression" : null,
                          "fullName" : null,
                          "calculatedTree" : null,
                          "reportId" : null,
                          "originalName" : "SupplierID",
                          "isParameter" : false,
                          "isCalculated" : false,
                          "querySource" : null,
                          "id" : "47954424-fff3-4157-9296-ad08b751e71d",
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : "0001-01-01T00:00:00.0000000-08:00",
                          "modifiedBy" : null
                       }
                    ]
                 }
              ],
              "reportRelationship" : [],
              "reportFilter" : {
                 "logic" : "",
                 "visible" : false,
                 "filterFields" : [],
                 "id" : "4a75d01f-1fb3-4eca-ae13-8f17d41289ea",
                 "reportId" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1"
              },
              "reportPart" : [{
                    "isDirty" : true,
                    "reportPartContent" : {
                       "isDirty" : false,
                       "type" : 3,
                       "columns" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [{
                                "reportPartContent" : null,
                                "isDirty" : true,
                                "name" : "Country",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "",
                                      "functionInfo" : {},
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Text"
                                      },
                                      "grandTotal" : {
                                         "label" : "Total Number of Countries",
                                         "function" : "Count Distinct",
                                         "expression" : "",
                                         "dataType" : "Numeric",
                                         "previewResult" : 10,
                                         "fieldDataType" : "Text"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : {},
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 1,
                                "field" : {
                                   "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
                                   "fieldName" : "Country",
                                   "fieldNameAlias" : "Country",
                                   "dataFieldType" : "Text",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : true
                             }, {
                                "reportPartContent" : null,
                                "isDirty" : true,
                                "name" : "Count (SupplierID)",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                      "functionInfo" : {
                                         "id" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                         "name" : "Count",
                                         "expression" : null,
                                         "dataType" : "Numeric",
                                         "formatDataType" : "Numeric",
                                         "syntax" : null,
                                         "expressionSyntax" : null,
                                         "isOperator" : false
                                      },
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      },
                                      "grandTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : {},
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 2,
                                "field" : {
                                   "fieldId" : "47954424-fff3-4157-9296-ad08b751e71d",
                                   "fieldName" : "SupplierID",
                                   "fieldNameAlias" : "Count (SupplierID)",
                                   "dataFieldType" : "Numeric",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : false
                             }
                          ],
                          "name" : "columns"
                       },
                       "rows" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "rows"
                       },
                       "values" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "values"
                       },
                       "separators" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "separators"
                       },
                       "properties" : {
                          "isDirty" : true,
                          "generalInfo" : {
                             "gridStyle" : "Vertical",
                             "separatorStyle" : "Comma"
                          },
                          "table" : {
                             "backgroundColor" : "#efefef",
                             "border" : {
                                "top" : {},
                                "right" : {},
                                "bottom" : {},
                                "midVer" : {},
                                "left" : {},
                                "midHor" : {}
         
                             }
                          },
                          "columns" : {
                             "width" : {
                                "value" : null,
                                "unit" : "Pixels"
                             },
                             "alterBackgroundColor" : false
                          },
                          "rows" : {
                             "height" : 40,
                             "alterBackgroundColor" : false
                          },
                          "headers" : {
                             "font" : {
                                "family" : "Roboto",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "backgroundColor" : "#dbf2ff"
                             },
                             "alignment" : "left",
                             "wordWrap" : true,
                             "removeHeaderForExport" : false
                          },
                          "grouping" : {
                             "useSeparator" : false
                          },
                          "view" : {
                             "dataRefreshInterval" : {
                                "enable" : false,
                                "updateInterval" : 0,
                                "isAll" : true,
                                "latestRecord" : 0
                             }
                          }
                       },
                       "settings" : {},
                       "dataSource" : {},
                       "title" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       },
                       "description" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : false,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       }
                    },
                    "reportId" : "00000000-0000-0000-0000-000000000000",
                    "positionX" : 0,
                    "positionY" : 0,
                    "width" : 12,
                    "height" : 4,
                    "state" : 3,
                    "modified" : null,
                    "numberOfRecord" : 0,
                    "isBackSide" : true,
                    "expandedLevel" : 0,
                    "points" : [{
                          "key" : "All",
                          "filter" : [{
                                "key" : "",
                                "value" : ""
                             }
                          ],
                          "expandedLevel" : 0,
                          "isViewSeparator" : false
                       }
                    ],
                    "isSelected" : true,
                    "title" : "Grid",
                    "id" : "561dba1e-f799-42be-be9d-bbfa078aee43"
                 }
              ],
              "version" : 0
           },
           "expandedLevel" : -1,
           "filters" : [],
           "title" : "Grid"
         }


   Response::

      {
        "grandTotalMapping" : [{
              "fieldNameAlias" : "Country",
              "columnName" : "grandtotal_country"
           }
        ],
        "subTotalMapping" : [],
        "sideTotalMapping" : [],
        "records" : [{
              "country_76139896_c2c3_" : "Australia",
              "countsup_supplieri_1e0310bebb" : 2,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Brazil",
              "countsup_supplieri_1e0310bebb" : 1,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Canada",
              "countsup_supplieri_1e0310bebb" : 2,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Denmark",
              "countsup_supplieri_1e0310bebb" : 1,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Finland",
              "countsup_supplieri_1e0310bebb" : 1,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "France",
              "countsup_supplieri_1e0310bebb" : 3,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Germany",
              "countsup_supplieri_1e0310bebb" : 3,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Italy",
              "countsup_supplieri_1e0310bebb" : 2,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Japan",
              "countsup_supplieri_1e0310bebb" : 2,
              "grandtotal_country" : 10
           }, {
              "country_76139896_c2c3_" : "Netherlands",
              "countsup_supplieri_1e0310bebb" : 1,
              "grandtotal_country" : 10
           }
        ],
        "fieldsMapping" : [{
              "fieldId" : "76139896-c2c3-432e-898a-2c2204bb2e35",
              "fieldNameAlias" : "Country",
              "columnName" : "country_76139896_c2c3_"
           }, {
              "fieldId" : "47954424-fff3-4157-9296-ad08b751e71d",
              "fieldNameAlias" : "Count (SupplierID)",
              "columnName" : "countsup_supplieri_1e0310bebb"
           }
        ]
      }


POST fusion/previewGrandTotal
--------------------------------------------------------------

Loads preview data for grand total.

**Request**

    Payload: a :doc:`models/ReportPartValidateExpressionParameter` object

**Response**

    A :doc:`models/FusionPreviewResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/previewGrandTotal HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "reportKey" : {
              "key" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1"
           },
           "report" : {
              "name" : "",
              "type" : "Templates",
              "previewRecord" : 10,
              "advancedMode" : true,
              "allowNulls" : false,
              "isDistinct" : false,
              "category" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "subCategory" : {
                 "id" : null,
                 "name" : "",
                 "type" : "Templates"
              },
              "reportDataSource" : [{
                    "aliasId" : "1641cb37-b60c-42bc-b986-c51667e8037d_Suppliers",
                    "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                    "querySourceName" : "Suppliers",
                    "selected" : true,
                    "categoryId" : "00000000-0000-0000-0000-000000000000",
                    "primaryFields" : [{
                          "name" : "SupplierID",
                          "alias" : "",
                          "dataType" : "int",
                          "izendaDataType" : "Numeric",
                          "allowDistinct" : false,
                          "visible" : true,
                          "filterable" : true,
                          "deleted" : false,
                          "querySourceId" : "00000000-0000-0000-0000-000000000000",
                          "parentId" : null,
                          "expressionFields" : [],
                          "filteredValue" : "",
                          "type" : 0,
                          "groupPosition" : 0,
                          "position" : 0,
                          "extendedProperties" : "{\"PrimaryKey\":true}",
                          "physicalChange" : 0,
                          "approval" : 0,
                          "existed" : false,
                          "matchedTenant" : false,
                          "functionName" : null,
                          "expression" : null,
                          "fullName" : null,
                          "calculatedTree" : null,
                          "reportId" : null,
                          "originalName" : "SupplierID",
                          "isParameter" : false,
                          "isCalculated" : false,
                          "querySource" : null,
                          "id" : "47954424-fff3-4157-9296-ad08b751e71d",
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : "0001-01-01T00:00:00.0000000-08:00",
                          "modifiedBy" : null
                       }
                    ]
                 }
              ],
              "reportRelationship" : [],
              "reportFilter" : {
                 "logic" : "",
                 "visible" : false,
                 "filterFields" : [],
                 "id" : "4a75d01f-1fb3-4eca-ae13-8f17d41289ea",
                 "reportId" : "1e1316a9-b6ce-46c8-9496-671fd5ddeee1"
              },
              "reportPart" : [{
                    "isDirty" : true,
                    "reportPartContent" : {
                       "isDirty" : false,
                       "type" : 3,
                       "columns" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [{
                                "reportPartContent" : null,
                                "isDirty" : false,
                                "name" : "Country",
                                "properties" : {
                                   "isDirty" : false,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "",
                                      "functionInfo" : {},
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Text"
                                      },
                                      "grandTotal" : {
                                         "label" : "Total Number of Countries",
                                         "function" : "Count Distinct",
                                         "expression" : "",
                                         "dataType" : "Numeric",
                                         "previewResult" : "",
                                         "fieldDataType" : "Text"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : 0,
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 1,
                                "field" : {
                                   "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
                                   "fieldName" : "Country",
                                   "fieldNameAlias" : "Country",
                                   "dataFieldType" : "Text",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : true
                             }, {
                                "reportPartContent" : null,
                                "isDirty" : true,
                                "name" : "Count (SupplierID)",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                      "functionInfo" : {
                                         "id" : "8a74f4e0-b845-4b9e-adfa-bb678a116878",
                                         "name" : "Count",
                                         "expression" : null,
                                         "dataType" : "Numeric",
                                         "formatDataType" : "Numeric",
                                         "syntax" : null,
                                         "expressionSyntax" : null,
                                         "isOperator" : false
                                      },
                                      "format" : {},
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {},
                                         "cellColor" : {}
         
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      },
                                      "grandTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      }
                                   },
                                   "headerFormating" : {
                                      "width" : {
                                         "value" : 0,
                                         "unit" : "pixels"
                                      },
                                      "height" : {},
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   },
                                   "otherProps" : {}
         
                                },
                                "position" : 2,
                                "field" : {
                                   "fieldId" : "47954424-fff3-4157-9296-ad08b751e71d",
                                   "fieldName" : "SupplierID",
                                   "fieldNameAlias" : "Count (SupplierID)",
                                   "dataFieldType" : "Numeric",
                                   "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Suppliers",
                                   "relationshipId" : null,
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "schemaName" : "dbo",
                                   "querySourceName" : "Suppliers",
                                   "databaseName" : "Northwind",
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : false
                             }
                          ],
                          "name" : "columns"
                       },
                       "rows" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "rows"
                       },
                       "values" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "values"
                       },
                       "separators" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "separators"
                       },
                       "properties" : {
                          "isDirty" : true,
                          "generalInfo" : {
                             "gridStyle" : "Vertical",
                             "separatorStyle" : "Comma"
                          },
                          "table" : {
                             "backgroundColor" : "#efefef",
                             "border" : {
                                "top" : {},
                                "right" : {},
                                "bottom" : {},
                                "midVer" : {},
                                "left" : {},
                                "midHor" : {}
         
                             }
                          },
                          "columns" : {
                             "width" : {
                                "value" : null,
                                "unit" : "Pixels"
                             },
                             "alterBackgroundColor" : false
                          },
                          "rows" : {
                             "height" : 40,
                             "alterBackgroundColor" : false
                          },
                          "headers" : {
                             "font" : {
                                "family" : "Roboto",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "backgroundColor" : "#dbf2ff"
                             },
                             "alignment" : "left",
                             "wordWrap" : true,
                             "removeHeaderForExport" : false
                          },
                          "grouping" : {
                             "useSeparator" : false
                          },
                          "view" : {
                             "dataRefreshInterval" : {
                                "enable" : false,
                                "updateInterval" : 0,
                                "isAll" : true,
                                "latestRecord" : 0
                             }
                          }
                       },
                       "settings" : {},
                       "dataSource" : {},
                       "title" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       },
                       "description" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : false,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       }
                    },
                    "reportId" : "00000000-0000-0000-0000-000000000000",
                    "positionX" : 0,
                    "positionY" : 0,
                    "width" : 12,
                    "height" : 4,
                    "state" : 3,
                    "modified" : null,
                    "numberOfRecord" : 0,
                    "isBackSide" : true,
                    "expandedLevel" : 0,
                    "points" : [{
                          "key" : "All",
                          "filter" : [{
                                "key" : "",
                                "value" : ""
                             }
                          ],
                          "expandedLevel" : 0,
                          "isViewSeparator" : false
                       }
                    ],
                    "isSelected" : true,
                    "title" : "Grid",
                    "id" : "561dba1e-f799-42be-be9d-bbfa078aee43"
                 }
              ],
              "version" : 0
           },
           "title" : "Grid",
           "expression" : "",
           "reportField" : {
              "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
              "fieldName" : "Country",
              "fieldNameAlias" : "Country",
              "dataFieldType" : "Text",
              "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
              "querySourceType" : "Table",
              "sourceAlias" : "Suppliers",
              "relationshipId" : null,
              "visible" : true,
              "calculatedTree" : null,
              "schemaName" : "dbo",
              "querySourceName" : "Suppliers",
              "databaseName" : "Northwind",
              "isCalculated" : false
           }
         }

   Response::

      {"value":10,"hasRecord":false,"dataType":"Numeric"}

GET fusion/{report_id}/{report_part_id}/(pageIndex)/(pageSize)
--------------------------------------------------------------

Loads report part data with paging and optional overridden filter values and operators.

**Request**

   No payload

   Optional overridden filter values and operators are passed as query string parameters:
   
   * value:    ``&p{filter_number}Value={filter_value}``
   * operator: ``&p{filter_number}Operator={filter_operator_id}``
    
   For example, to load data from a report part while overriding the second filter to ``equal "t-shirt"``::
      
      GET /api/fusion/81a64b45-fc04-4026-8708-244f341b4284/6493401d-c0b6-4f4a-801d-51e4b0ac3bb1?p2Value=t-shirt&p2Operator=042A04A3-DFE1-4EF9-BD27-1B657886F02E

   (``042A04A3-DFE1-4EF9-BD27-1B657886F02E`` is the id of Equals filter operator from :ref:`GET_report/filter/operators`)

**Response**

    A :doc:`models/FusionResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/9197f210-766a-45d3-a1f9-5c4f4a4aa8ba/90ff323c-38f8-4663-823f-35afd85239ee HTTP/1.1

   Sample response::

      {
         "grandTotalMapping": [],
         "subTotalMapping": [],
         "sideTotalMapping": [],
         "executionTrace": [],
         "records": [
            {
                  "orderid_2be8c595_91a3_": 10250,
                  "shipcountry_bfeceef4_e536_": "Brazil",
                  "rowNumber": 1
            },
            {
                  "orderid_2be8c595_91a3_": 10253,
                  "shipcountry_bfeceef4_e536_": "Brazil",
                  "rowNumber": 2
            },
         ],
         "fieldsMapping": [
            {
                  "fieldId": "2be8c595-91a3-4250-8828-dbbc07eaba83",
                  "fieldNameAlias": "OrderID",
                  "columnName": "orderid_2be8c595_91a3_"
            },
            {
                  "fieldId": "bfeceef4-e536-4823-8cde-adb8f71d52f5",
                  "fieldNameAlias": "ShipCountry",
                  "columnName": "shipcountry_bfeceef4_e536_"
            }
         ],
         "paging": {
            "pageIndex": 1,
            "pageSize": 100000,
            "total": 2,
            "skipItems": 0,
            "isLastPage": false
         },
         "pivotHeaderValues": [],
         "cities": [],
         "postalCodes": []
      }


POST fusion/validateDataModelExpression
--------------------------------------------------------------

Validates a calculated field expression in Data Model and returns a suggested data type (in a single data source). |br| |br|
See also: `POST fusion/validateExpression`_

**Request**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  NULL
          -  Description
          -  Note
       *  -  **querySourceId** |br|
             string (GUID)
          -
          -  The id of the query source
          -
       *  -  **expression** |br|
             string
          -
          -  The expression
          -
       *  -  **izendaDataType** |br|
             string
          -
          -  The output data type
          -
       *  -  **querySourceFieldId** |br|
             string (GUID)
          -
          -  The id of the query source field
          -
       *  -  **tenantId** |br|
             string (GUID)
          -
          -  The id of the tenant
          -

**Response**

    A :doc:`models/ValidationOperationResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/validateDataModelExpression HTTP/1.1

   Request payload::

      {
         "querySourceId": "e1bc9a64-c12c-41fd-b8c9-5e7bccf754e9",
         "expression": "RUNNINGSUM([FREIGHT])",
         "izendaDataType": null,
         "querySourceFieldId": null,
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e"
      }

   Sample response::

      {
         "result": {
            "izendaDataType": "Numeric",
            "isRunningField": false,
            "isCompositeField": false
         },
         "success": true,
         "messages": [],
         "data": null
      }


POST fusion/previewCalculatedField
--------------------------------------------------------------

Loads preview data for a calculated field. |br| |br|
Obsolete, use `POST fusion/validateExpression`_ instead

**Request**

    Payload: a :doc:`models/ReportExpressionParameter` object

**Response**

    A :doc:`models/FusionPreviewResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/previewCalculatedField HTTP/1.1

   Request payload::

      {
         "reportKey": {
            "key": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba"
         },
         "expression": "Sum([Northwind-BA].[dbo].[Orders].[Freight])",
         "izendaDataType": "Money",
         "querySourceFieldId": null,
         "previewRecord": 10
      }

   Sample response::

      {
         "value": 25733.12,
         "hasRecord": true,
         "dataType": "Money"
      }

POST fusion/previewSubTotal
--------------------------------------------------------------

Loads preview data for sub total.

**Request**

    Payload: a :doc:`models/ReportPartValidateExpressionParameter` object

**Response**

    A :doc:`models/FusionPreviewResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/previewSubTotal HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "reportKey" : {
              "key" : "2a1bf476-d6c7-4869-b625-30f5423948b7"
           },
           "report" : {
              "name" : "Total Testing Report",
              "type" : 0,
              "previewRecord" : 10,
              "advancedMode" : true,
              "allowNulls" : false,
              "isDistinct" : false,
              "category" : {
                 "id" : null,
                 "name" : "",
                 "type" : 0
              },
              "subCategory" : {
                 "id" : null,
                 "name" : "",
                 "type" : 0
              },
              "reportDataSource" : [{
                    "aliasId" : "72bf3820-3259-4b77-8f99-c2c001388413_Order Details",
                    "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
                    "querySourceName" : "Order Details",
                    "selected" : true,
                    "categoryId" : "00000000-0000-0000-0000-000000000000",
                    "primaryFields" : [{
                          "name" : "OrderID",
                          "alias" : "",
                          "dataType" : "int",
                          "izendaDataType" : "Numeric",
                          "allowDistinct" : false,
                          "visible" : true,
                          "filterable" : true,
                          "deleted" : false,
                          "querySourceId" : "00000000-0000-0000-0000-000000000000",
                          "parentId" : null,
                          "expressionFields" : [],
                          "filteredValue" : "",
                          "type" : 0,
                          "groupPosition" : 0,
                          "position" : 0,
                          "extendedProperties" : "{\"PrimaryKey\":true}",
                          "physicalChange" : 0,
                          "approval" : 0,
                          "existed" : false,
                          "matchedTenant" : false,
                          "functionName" : null,
                          "expression" : null,
                          "fullName" : null,
                          "calculatedTree" : null,
                          "reportId" : null,
                          "originalName" : "OrderID",
                          "isParameter" : false,
                          "isCalculated" : false,
                          "hasAggregatedFunction" : false,
                          "querySource" : null,
                          "fullPath" : null,
                          "id" : "507012a6-fb37-4035-b64b-7e5d82493889",
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : "0001-01-01T00:00:00.0000000-08:00",
                          "modifiedBy" : null
                       }, {
                          "name" : "ProductID",
                          "alias" : "",
                          "dataType" : "int",
                          "izendaDataType" : "Numeric",
                          "allowDistinct" : false,
                          "visible" : true,
                          "filterable" : true,
                          "deleted" : false,
                          "querySourceId" : "00000000-0000-0000-0000-000000000000",
                          "parentId" : null,
                          "expressionFields" : [],
                          "filteredValue" : "",
                          "type" : 0,
                          "groupPosition" : 0,
                          "position" : 0,
                          "extendedProperties" : "{\"PrimaryKey\":true}",
                          "physicalChange" : 0,
                          "approval" : 0,
                          "existed" : false,
                          "matchedTenant" : false,
                          "functionName" : null,
                          "expression" : null,
                          "fullName" : null,
                          "calculatedTree" : null,
                          "reportId" : null,
                          "originalName" : "ProductID",
                          "isParameter" : false,
                          "isCalculated" : false,
                          "hasAggregatedFunction" : false,
                          "querySource" : null,
                          "fullPath" : null,
                          "id" : "8cc4ea1e-fa55-4721-9963-c65602e5757a",
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : "0001-01-01T00:00:00.0000000-08:00",
                          "modifiedBy" : null
                       }
                    ]
                 }
              ],
              "reportRelationship" : [],
              "reportFilter" : {
                 "logic" : "",
                 "visible" : true,
                 "filterFields" : [],
                 "id" : "ad432d5c-a450-4624-b741-69674f8652c1",
                 "reportId" : "2a1bf476-d6c7-4869-b625-30f5423948b7"
              },
              "reportPart" : [{
                    "isDirty" : false,
                    "reportPartContent" : {
                       "isDirty" : false,
                       "type" : 3,
                       "columns" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [{
                                "reportPartContent" : null,
                                "isDirty" : false,
                                "name" : "ProductID",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "",
                                      "functionInfo" : {},
                                      "format" : {
                                         "formatId" : "",
                                         "groupBy" : null
                                      },
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {
                                            "rangePercent" : null,
                                            "rangeValue" : null,
                                            "value" : null
                                         },
                                         "cellColor" : {
                                            "rangePercent" : null,
                                            "rangeValue" : null,
                                            "value" : null
                                         }
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "T1",
                                         "function" : "Sum",
                                         "expression" : "",
                                         "dataType" : "Numeric",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      },
                                      "grandTotal" : {
                                         "label" : "T1",
                                         "function" : "Sum",
                                         "expression" : "",
                                         "dataType" : "Numeric",
                                         "previewResult" : "",
                                         "fieldDataType" : "Numeric"
                                      }
                                   },
                                   "headerFormating" : {
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   }
                                },
                                "position" : 1,
                                "field" : {
                                   "fieldId" : "8cc4ea1e-fa55-4721-9963-c65602e5757a",
                                   "fieldName" : "ProductID",
                                   "fieldNameAlias" : "ProductID",
                                   "dataFieldType" : "Numeric",
                                   "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Order Details",
                                   "relationshipId" : "00000000-0000-0000-0000-000000000000",
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : false
                             }, {
                                "reportPartContent" : null,
                                "isDirty" : false,
                                "name" : "UnitPrice",
                                "properties" : {
                                   "isDirty" : true,
                                   "fieldItemVisible" : true,
                                   "dataFormattings" : {
                                      "function" : "",
                                      "functionInfo" : {},
                                      "format" : {
                                         "formatId" : "",
                                         "groupBy" : null
                                      },
                                      "font" : {
                                         "family" : "Roboto",
                                         "size" : 14,
                                         "bold" : false,
                                         "italic" : false,
                                         "underline" : false,
                                         "color" : "",
                                         "backgroundColor" : ""
                                      },
                                      "alignment" : "alignLeft",
                                      "sort" : "",
                                      "color" : {
                                         "textColor" : {
                                            "rangePercent" : null,
                                            "rangeValue" : null,
                                            "value" : null
                                         },
                                         "cellColor" : {
                                            "rangePercent" : null,
                                            "rangeValue" : null,
                                            "value" : null
                                         }
                                      },
                                      "alternativeText" : {
                                         "rangePercent" : null,
                                         "rangeValue" : null,
                                         "value" : null
                                      },
                                      "customURL" : {
                                         "url" : "",
                                         "option" : "Open link in New Window"
                                      },
                                      "embeddedJavascript" : {
                                         "script" : ""
                                      },
                                      "subTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : ""
                                      },
                                      "grandTotal" : {
                                         "label" : "",
                                         "function" : "",
                                         "expression" : "",
                                         "dataType" : "",
                                         "previewResult" : ""
                                      }
                                   },
                                   "headerFormating" : {
                                      "font" : {
                                         "family" : null,
                                         "size" : null,
                                         "bold" : null,
                                         "italic" : null,
                                         "underline" : null,
                                         "color" : null,
                                         "backgroundColor" : null
                                      },
                                      "alignment" : null,
                                      "wordWrap" : null,
                                      "columnGroup" : ""
                                   },
                                   "drillDown" : {
                                      "subReport" : {
                                         "selectedReport" : null,
                                         "style" : null,
                                         "reportPartUsed" : null,
                                         "reportFilter" : true,
                                         "mappingFields" : []
                                      }
                                   }
                                },
                                "position" : 2,
                                "field" : {
                                   "fieldId" : "9820a839-11a2-4b01-a5a9-a9028b34c319",
                                   "fieldName" : "UnitPrice",
                                   "fieldNameAlias" : "UnitPrice",
                                   "dataFieldType" : "Money",
                                   "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
                                   "querySourceType" : "Table",
                                   "sourceAlias" : "Order Details",
                                   "relationshipId" : "00000000-0000-0000-0000-000000000000",
                                   "visible" : true,
                                   "calculatedTree" : null,
                                   "isCalculated" : false
                                },
                                "isDeleted" : false,
                                "isSelected" : false
                             }
                          ],
                          "name" : "columns"
                       },
                       "rows" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "rows"
                       },
                       "values" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "values"
                       },
                       "separators" : {
                          "text" : null,
                          "properties" : {},
                          "settings" : {},
                          "elements" : [],
                          "name" : "separators"
                       },
                       "properties" : {
                          "isDirty" : true,
                          "generalInfo" : {
                             "gridStyle" : "Vertical",
                             "separatorStyle" : "Comma"
                          },
                          "table" : {
                             "border" : {
                                "top" : {},
                                "right" : {},
                                "bottom" : {},
                                "midVer" : {},
                                "left" : {},
                                "midHor" : {}
                             },
                             "backgroundColor" : "#efefef"
                          },
                          "columns" : {
                             "width" : {
                                "value" : null,
                                "unit" : "Pixels"
                             },
                             "alterBackgroundColor" : false
                          },
                          "rows" : {
                             "height" : 40,
                             "alterBackgroundColor" : false
                          },
                          "headers" : {
                             "font" : {
                                "family" : "Roboto",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "backgroundColor" : "#dbf2ff"
                             },
                             "alignment" : "left",
                             "wordWrap" : false,
                             "removeHeaderForExport" : false
                          },
                          "grouping" : {
                             "useSeparator" : true
                          },
                          "view" : {
                             "dataRefreshInterval" : {
                                "enable" : false,
                                "updateInterval" : 0,
                                "isAll" : true,
                                "latestRecord" : 0
                             },
                             "usePagination" : false
                          },
                          "printing" : {
                             "usePageBreakAfterSeparator" : false
                          }
                       },
                       "settings" : {},
                       "dataSource" : {},
                       "isActiveForEdit" : false,
                       "title" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : true,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       },
                       "description" : {
                          "text" : "",
                          "properties" : {},
                          "settings" : {
                             "font" : {
                                "family" : "",
                                "size" : 14,
                                "bold" : false,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "highlightColor" : ""
                             },
                             "alignment" : {
                                "alignment" : ""
                             }
                          },
                          "elements" : []
                       }
                    },
                    "reportId" : "2a1bf476-d6c7-4869-b625-30f5423948b7",
                    "positionX" : 0,
                    "positionY" : 0,
                    "width" : 12,
                    "height" : 4,
                    "state" : 3,
                    "modified" : null,
                    "numberOfRecord" : 0,
                    "isBackSide" : true,
                    "points" : [{
                          "key" : "All",
                          "filter" : [{
                                "key" : "",
                                "value" : ""
                             }
                          ],
                          "expandedLevel" : 0,
                          "isViewSeparator" : false
                       }
                    ],
                    "configField" : {
                       "reportPartContent" : null,
                       "isDirty" : false,
                       "name" : "ProductID",
                       "properties" : {
                          "isDirty" : true,
                          "fieldItemVisible" : true,
                          "dataFormattings" : {
                             "function" : "",
                             "functionInfo" : {},
                             "format" : {
                                "formatId" : "",
                                "groupBy" : null
                             },
                             "font" : {
                                "family" : "Roboto",
                                "size" : 14,
                                "bold" : false,
                                "italic" : false,
                                "underline" : false,
                                "color" : "",
                                "backgroundColor" : ""
                             },
                             "alignment" : "alignLeft",
                             "sort" : "",
                             "color" : {
                                "textColor" : {
                                   "rangePercent" : null,
                                   "rangeValue" : null,
                                   "value" : null
                                },
                                "cellColor" : {
                                   "rangePercent" : null,
                                   "rangeValue" : null,
                                   "value" : null
                                }
                             },
                             "alternativeText" : {
                                "rangePercent" : null,
                                "rangeValue" : null,
                                "value" : null
                             },
                             "customURL" : {
                                "url" : "",
                                "option" : "Open link in New Window"
                             },
                             "embeddedJavascript" : {
                                "script" : ""
                             },
                             "subTotal" : {
                                "label" : "T1",
                                "function" : "Sum",
                                "expression" : "",
                                "dataType" : "Numeric",
                                "previewResult" : "",
                                "fieldDataType" : "Numeric"
                             },
                             "grandTotal" : {
                                "label" : "T1",
                                "function" : "Sum",
                                "expression" : "",
                                "dataType" : "Numeric",
                                "previewResult" : "",
                                "fieldDataType" : "Numeric"
                             }
                          },
                          "headerFormating" : {
                             "font" : {
                                "family" : null,
                                "size" : null,
                                "bold" : null,
                                "italic" : null,
                                "underline" : null,
                                "color" : null,
                                "backgroundColor" : null
                             },
                             "alignment" : null,
                             "wordWrap" : null,
                             "columnGroup" : ""
                          },
                          "drillDown" : {
                             "subReport" : {
                                "selectedReport" : null,
                                "style" : null,
                                "reportPartUsed" : null,
                                "reportFilter" : true,
                                "mappingFields" : []
                             }
                          }
                       },
                       "position" : 1,
                       "field" : {
                          "fieldId" : "8cc4ea1e-fa55-4721-9963-c65602e5757a",
                          "fieldName" : "ProductID",
                          "fieldNameAlias" : "ProductID",
                          "dataFieldType" : "Numeric",
                          "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
                          "querySourceType" : "Table",
                          "sourceAlias" : "Order Details",
                          "relationshipId" : "00000000-0000-0000-0000-000000000000",
                          "visible" : true,
                          "calculatedTree" : null,
                          "isCalculated" : false
                       },
                       "isDeleted" : false,
                       "isSelected" : false
                    },
                    "expandedLevel" : 0,
                    "title" : "Grid",
                    "id" : "eca9c621-08da-4919-814f-2c6396ca7700"
                 }
              ],
              "header" : {
                 "visible" : false,
                 "items" : [{
                       "isDirty" : false,
                       "type" : "image",
                       "label" : "Image",
                       "id" : "formatDetails_385",
                       "positionX" : 0,
                       "positionY" : 0,
                       "width" : 6,
                       "height" : 6,
                       "name" : "Logo Image",
                       "value" : "",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "imageUrl" : "http://",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_386",
                       "positionX" : 20,
                       "positionY" : 0,
                       "width" : 12,
                       "height" : 2,
                       "name" : "Report Name",
                       "value" : "{reportName}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "thinHorizontalRule",
                       "label" : "Horizontal Rule",
                       "id" : "formatDetails_387",
                       "positionX" : 20,
                       "positionY" : 4,
                       "width" : 12,
                       "height" : 1,
                       "name" : "Upper Separator Line",
                       "value" : "{horizontalRule}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 2
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_388",
                       "positionX" : 20,
                       "positionY" : 5,
                       "width" : 6,
                       "height" : 2,
                       "name" : "Report Generated",
                       "value" : "Report Generated:",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_389",
                       "positionX" : 20,
                       "positionY" : 7,
                       "width" : 6,
                       "height" : 2,
                       "name" : "User",
                       "value" : "User:",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_390",
                       "positionX" : 20,
                       "positionY" : 9,
                       "width" : 6,
                       "height" : 2,
                       "name" : "Tenant",
                       "value" : "Tenant:",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "dateTime",
                       "label" : "Date Time",
                       "id" : "formatDetails_391",
                       "positionX" : 26,
                       "positionY" : 5,
                       "width" : 6,
                       "height" : 2,
                       "name" : "Current Date Time",
                       "value" : "{currentDateTime}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_392",
                       "positionX" : 26,
                       "positionY" : 7,
                       "width" : 6,
                       "height" : 2,
                       "name" : "Current User Name",
                       "value" : "{currentUserName}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_393",
                       "positionX" : 26,
                       "positionY" : 9,
                       "width" : 6,
                       "height" : 2,
                       "name" : "Tenant Name",
                       "value" : "{tenantName}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "horizontalRule",
                       "label" : "Horizontal Rule",
                       "id" : "formatDetails_394",
                       "positionX" : 0,
                       "positionY" : 11,
                       "width" : 32,
                       "height" : 1,
                       "name" : "Lower Separator Line",
                       "value" : "{horizontalRule}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 4
                    }
                 ]
              },
              "footer" : {
                 "visible" : false,
                 "items" : [{
                       "isDirty" : false,
                       "type" : "horizontalRule",
                       "label" : "Horizontal Rule",
                       "id" : "formatDetails_395",
                       "positionX" : 0,
                       "positionY" : 0,
                       "width" : 32,
                       "height" : 1,
                       "name" : "Separator Line",
                       "value" : "{horizontalRule}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 4
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_396",
                       "positionX" : 0,
                       "positionY" : 1,
                       "width" : 10,
                       "height" : 2,
                       "name" : "Footer Text",
                       "value" : "Footer Text",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "text",
                       "label" : "Text",
                       "id" : "formatDetails_397",
                       "positionX" : 20,
                       "positionY" : 1,
                       "width" : 4,
                       "height" : 2,
                       "name" : "Page",
                       "value" : "Page",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "pageNumber",
                       "label" : "Page Number",
                       "id" : "formatDetails_398",
                       "positionX" : 24,
                       "positionY" : 1,
                       "width" : 8,
                       "height" : 2,
                       "name" : "Page Number",
                       "value" : "{pageNumber}",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }
                 ]
              },
              "titleDescription" : {
                 "visible" : false,
                 "items" : [{
                       "isDirty" : false,
                       "type" : "title",
                       "label" : "Title",
                       "id" : "formatDetails_399",
                       "name" : "Title",
                       "value" : "",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }, {
                       "isDirty" : false,
                       "type" : "description",
                       "label" : "Description",
                       "id" : "formatDetails_400",
                       "name" : "Description",
                       "value" : "",
                       "font" : {
                          "family" : "Roboto",
                          "size" : 14,
                          "bold" : false,
                          "italic" : false,
                          "underline" : false,
                          "color" : "#000",
                          "backgroundColor" : "#fff"
                       },
                       "color" : "#000",
                       "dashStyle" : "solid",
                       "thickness" : 1
                    }
                 ]
              },
              "version" : 1,
              "schedules" : []
           },
           "title" : "Grid",
           "expression" : "",
           "izendaDataType" : "Numeric",
           "reportField" : {
              "fieldId" : "8cc4ea1e-fa55-4721-9963-c65602e5757a",
              "fieldName" : "ProductID",
              "fieldNameAlias" : "ProductID",
              "dataFieldType" : "Numeric",
              "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
              "querySourceType" : "Table",
              "sourceAlias" : "Order Details",
              "relationshipId" : "00000000-0000-0000-0000-000000000000",
              "visible" : true,
              "calculatedTree" : null,
              "isCalculated" : false
           }
         }

   Sample response::

      {"value":426.0,"dataType":"Money","hasRecord":false}


POST fusion/calculatedFieldValue
--------------------------------------------------------------

Returns a single calculated field value for preview section.

**Request**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  NULL
          -  Description
          -  Note
       *  -  **querySourceId** |br|
             string (GUID)
          -
          -  The id of the query source
          -
       *  -  **expression** |br|
             string
          -
          -  The expression
          -
       *  -  **izendaDataType** |br|
             string
          -
          -  The output data type
          -
       *  -  **tenantId** |br|
             string (GUID)
          -  Y
          -  The id of the tenant
          -

**Response**

    A :doc:`models/FusionPreviewResult` object

**Samples**

   .. code-block:: http

      POST /api/fusion/calculatedFieldValue HTTP/1.1

   Request payload::

      {
        "querySourceId" : "72bf3820-3259-4b77-8f99-c2c001388413",
        "expression" : "[Discount] * [UnitPrice]",
        "izendaDataType" : "Numeric"
      }

   Response::

      {
        "value":0.0,
        "hasRecord": true,
        "dataType":"Numeric"
      }


POST fusion/retrieveRandomExpandedLevelData
--------------------------------------------------------------

Returns random expanded level data.

**Request**

    Payload: a :doc:`models/ReportPartPreviewParameter` object

**Response**

    An object or an array of :doc:`models/FusionResult` objects

**Samples**

   .. code-block:: http

      POST /api/fusion/retrieveRandomExpandedLevelData HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload::

      .. code-block:: json

            {
               "reportKey": {
                  "key": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
                  "modified": null,
                  "tenantId": null
               },
               "section": 2,
               "saveAs": false,
               "ignoreCheckChange": false,
               "report": {
                  "name": "091217-test",
                  "type": 0,
                  "previewRecord": 10,
                  "advancedMode": true,
                  "allowNulls": false,
                  "isDistinct": false,
                  "categoryId": "dc04087a-a761-43fb-b82d-5dd56fe8d9e3",
                  "category": {
                     "id": "dc04087a-a761-43fb-b82d-5dd56fe8d9e3",
                     "name": "",
                     "type": 0,
                     "tenantId": null
                  },
                  "subCategory": {
                     "id": null,
                     "name": "",
                     "type": 0,
                     "tenantId": null
                  },
                  "subCategoryId": null,
                  "reportDataSource": [{
                     "reportId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
                     "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                     "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                     "querySourceCategoryId": null,
                     "connectionId": null,
                     "selected": false,
                     "id": "e8cd9782-98bc-4f6b-9251-e48c756c9937",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 1,
                     "created": "2017-09-12T06:30:52.84",
                     "createdBy": "System5 Admin5",
                     "modified": "2017-09-12T06:30:52.84",
                     "modifiedBy": "System5 Admin5"
                  }],
                  "reportRelationship": [],
                  "reportFilter": {
                     "logic": "",
                     "visible": false,
                     "filterFields": [],
                     "id": "e7845036-2d0c-4576-ab76-53b0e0e41ea3",
                     "reportId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba"
                  },
                  "reportPart": [{
                     "isDirty": true,
                     "reportPartContent": {
                        "subReportDefinitionCollection": [],
                        "collapseStatus": 0,
                        "isDirty": true,
                        "isCrossFiltering": false,
                        "type": 3,
                        "columns": {
                           "text": null,
                           "properties": {
                              
                           },
                           "settings": {
                              
                           },
                           "elements": [{
                              "reportPartContent": null,
                              "isDirty": false,
                              "name": "OrderID",
                              "properties": {
                                 "isDirty": false,
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                    "functionInfo": {
                                       "dataType": "Numeric",
                                       "expression": null,
                                       "expressionSyntax": null,
                                       "extendedProperties": {
                                          
                                       },
                                       "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                       "isOperator": false,
                                       "name": "Group",
                                       "syntax": null,
                                       "userDefined": false,
                                       "formatDataType": "Numeric"
                                    },
                                    "format": {
                                       "createNewHiddenPercenOfGroupField": false
                                    },
                                    "font": {
                                       "family": "Roboto",
                                       "size": 14,
                                       "bold": false,
                                       "italic": false,
                                       "underline": false,
                                       "color": "",
                                       "backgroundColor": ""
                                    },
                                    "width": {
                                       "value": null
                                    },
                                    "alignment": "alignLeft",
                                    "sort": "Unsort",
                                    "color": {
                                       "textColor": {
                                          "rangePercent": null,
                                          "rangeValue": null,
                                          "value": null
                                       },
                                       "cellColor": {
                                          "rangePercent": null,
                                          "rangeValue": null,
                                          "value": null
                                       }
                                    },
                                    "alternativeText": {
                                       "rangePercent": null,
                                       "rangeValue": null,
                                       "value": null
                                    },
                                    "customURL": {
                                       "url": "",
                                       "option": "LINK_NEW_WINDOW"
                                    },
                                    "embeddedJavascript": {
                                       "script": ""
                                    },
                                    "subTotal": {
                                       "label": "",
                                       "function": "",
                                       "expression": "",
                                       "dataType": "",
                                       "format": {
                                          
                                       },
                                       "previewResult": ""
                                    },
                                    "grandTotal": {
                                       "label": "",
                                       "function": "",
                                       "expression": "",
                                       "dataType": "",
                                       "format": {
                                          
                                       },
                                       "previewResult": ""
                                    }
                                 },
                                 "headerFormating": {
                                    "font": {
                                       "family": null,
                                       "size": null,
                                       "bold": null,
                                       "italic": null,
                                       "underline": null,
                                       "color": null,
                                       "backgroundColor": null
                                    },
                                    "alignment": null,
                                    "wordWrap": null,
                                    "columnGroup": ""
                                 },
                                 "drillDown": {
                                    "subReport": {
                                       "selectedReport": null,
                                       "style": null,
                                       "reportPartUsed": null,
                                       "reportFilter": true,
                                       "mappingFields": [],
                                       "selectedIconValue": {
                                          "icon": null,
                                          "value": null
                                       },
                                       "viewSettingByLink": null
                                    }
                                 },
                                 "otherProps": {
                                    
                                 }
                              },
                              "position": 1,
                              "field": {
                                 "fieldId": "2be8c595-91a3-4250-8828-dbbc07eaba83",
                                 "fieldName": "OrderID",
                                 "fieldNameAlias": "OrderID",
                                 "dataFieldType": "Numeric",
                                 "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "calculatedTree": null,
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false,
                              "offset": {
                                 
                              }
                           }],
                           "name": "columns"
                        },
                        "rows": {
                           "text": null,
                           "properties": {
                              
                           },
                           "settings": {
                              
                           },
                           "elements": [],
                           "name": "rows"
                        },
                        "values": {
                           "text": null,
                           "properties": {
                              
                           },
                           "settings": {
                              
                           },
                           "elements": [],
                           "name": "values"
                        },
                        "separators": {
                           "text": null,
                           "properties": {
                              
                           },
                           "settings": {
                              
                           },
                           "elements": [],
                           "name": "separators"
                        },
                        "properties": {
                           "isDirty": true,
                           "generalInfo": {
                              "gridStyle": "Vertical",
                              "separatorStyle": "Comma"
                           },
                           "table": {
                              "border": {
                                 "top": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 },
                                 "right": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 },
                                 "bottom": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 },
                                 "midVer": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 },
                                 "left": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 },
                                 "midHor": {
                                    "color": null,
                                    "dashStyle": null,
                                    "thinkness": null
                                 }
                              },
                              "backgroundColor": "#fff"
                           },
                           "columns": {
                              "width": {
                                 "value": 150
                              },
                              "alterBackgroundColor": false
                           },
                           "rows": {
                              "alterBackgroundColor": false
                           },
                           "headers": {
                              "font": {
                                 "family": "Roboto",
                                 "size": 14,
                                 "bold": true,
                                 "italic": false,
                                 "underline": false,
                                 "color": "#000000",
                                 "backgroundColor": "#E4E4E4"
                              },
                              "alignment": "center",
                              "wordWrap": false,
                              "removeHeaderForExport": false
                           },
                           "grouping": {
                              "useSeparator": true
                           },
                           "view": {
                              "dataRefreshInterval": {
                                 "enable": false,
                                 "updateInterval": 0,
                                 "isAll": true,
                                 "latestRecord": 0
                              },
                              "usePagination": true,
                              "collapseDrilldownByDefault": false,
                              "pageSize": 10,
                              "pivotColumnsPerExportedPage": ""
                           },
                           "printing": {
                              "usePageBreakAfterSeparator": false
                           }
                        },
                        "settings": {
                           
                        },
                        "changeGridStyleStatus": true,
                        "inconsitentFunction": false,
                        "dataSource": {
                           
                        },
                        "title": {
                           "text": "",
                           "properties": {
                              
                           },
                           "settings": {
                              "font": {
                                 "family": "",
                                 "size": 14,
                                 "bold": true,
                                 "italic": false,
                                 "underline": false,
                                 "color": "",
                                 "highlightColor": ""
                              },
                              "alignment": {
                                 "alignment": ""
                              }
                           },
                           "elements": []
                        },
                        "description": {
                           "text": "",
                           "properties": {
                              
                           },
                           "settings": {
                              "font": {
                                 "family": "",
                                 "size": 14,
                                 "bold": false,
                                 "italic": false,
                                 "underline": false,
                                 "color": "",
                                 "highlightColor": ""
                              },
                              "alignment": {
                                 "alignment": ""
                              }
                           },
                           "elements": []
                        }
                     },
                     "reportId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
                     "width": 5,
                     "height": 6,
                     "state": 3,
                     "modified": null,
                     "numberOfRecord": null,
                     "configField": null,
                     "stateReview": 0,
                     "refreshDataProcess": null,
                     "refreshDataInterval": null,
                     "positionY": 0,
                     "positionX": 0,
                     "title": "Grid",
                     "id": "90ff323c-38f8-4663-823f-35afd85239ee"
                  }],
                  "header": {
                     "visible": false,
                     "items": [{
                        "isDirty": false,
                        "type": "image",
                        "label": "Image",
                        "id": "formatDetails_154",
                        "positionX": 0,
                        "positionY": 0,
                        "width": 6,
                        "height": 6,
                        "name": "Logo Image",
                        "value": "",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "imageUrl": "http://",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_155",
                        "positionX": 20,
                        "positionY": 0,
                        "width": 12,
                        "height": 2,
                        "name": "Report Name",
                        "value": "{reportName}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "thinHorizontalRule",
                        "label": "Horizontal Rule",
                        "id": "formatDetails_156",
                        "positionX": 20,
                        "positionY": 4,
                        "width": 12,
                        "height": 1,
                        "name": "Upper Separator Line",
                        "value": "{horizontalRule}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 2,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_157",
                        "positionX": 20,
                        "positionY": 5,
                        "width": 6,
                        "height": 2,
                        "name": "Report Generated",
                        "value": "Report Generated:",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_158",
                        "positionX": 20,
                        "positionY": 7,
                        "width": 6,
                        "height": 2,
                        "name": "User",
                        "value": "User:",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_159",
                        "positionX": 20,
                        "positionY": 9,
                        "width": 6,
                        "height": 2,
                        "name": "Tenant",
                        "value": "Tenant:",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "dateTime",
                        "label": "Date Time",
                        "id": "formatDetails_160",
                        "positionX": 26,
                        "positionY": 5,
                        "width": 6,
                        "height": 2,
                        "name": "Current Date Time",
                        "value": "{currentDateTime}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_161",
                        "positionX": 26,
                        "positionY": 7,
                        "width": 6,
                        "height": 2,
                        "name": "Current User Name",
                        "value": "{currentUserName}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_162",
                        "positionX": 26,
                        "positionY": 9,
                        "width": 6,
                        "height": 2,
                        "name": "Tenant Name",
                        "value": "{tenantName}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "horizontalRule",
                        "label": "Horizontal Rule",
                        "id": "formatDetails_163",
                        "positionX": 0,
                        "positionY": 11,
                        "width": 32,
                        "height": 1,
                        "name": "Lower Separator Line",
                        "value": "{horizontalRule}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 4,
                        "isSelected": false
                     }]
                  },
                  "footer": {
                     "visible": false,
                     "items": [{
                        "isDirty": false,
                        "type": "horizontalRule",
                        "label": "Horizontal Rule",
                        "id": "formatDetails_164",
                        "positionX": 0,
                        "positionY": 0,
                        "width": 32,
                        "height": 1,
                        "name": "Separator Line",
                        "value": "{horizontalRule}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 4,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_165",
                        "positionX": 0,
                        "positionY": 1,
                        "width": 10,
                        "height": 2,
                        "name": "Footer Text",
                        "value": "Footer Text",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "text",
                        "label": "Text",
                        "id": "formatDetails_166",
                        "positionX": 20,
                        "positionY": 1,
                        "width": 4,
                        "height": 2,
                        "name": "Page",
                        "value": "Page",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "pageNumber",
                        "label": "Page Number",
                        "id": "formatDetails_167",
                        "positionX": 24,
                        "positionY": 1,
                        "width": 8,
                        "height": 2,
                        "name": "Page Number",
                        "value": "{pageNumber}",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     }]
                  },
                  "titleDescription": {
                     "visible": false,
                     "items": [{
                        "isDirty": false,
                        "type": "title",
                        "label": "Title",
                        "id": "formatDetails_168",
                        "name": "Title",
                        "value": "",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     },
                     {
                        "isDirty": false,
                        "type": "description",
                        "label": "Description",
                        "id": "formatDetails_169",
                        "name": "Description",
                        "value": "",
                        "font": {
                           "family": "Roboto",
                           "size": 14,
                           "bold": false,
                           "italic": false,
                           "underline": false,
                           "color": "#000",
                           "backgroundColor": "#fff"
                        },
                        "color": "#000",
                        "dashStyle": "solid",
                        "thickness": 1,
                        "isSelected": false
                     }]
                  },
                  "version": 4,
                  "schedules": [],
                  "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "accesses": [],
                  "exportFormatSetting": {
                     "orientation": 0,
                     "margins": 0,
                     "centerOnPage": {
                        "horizontally": false,
                        "vertically": false
                     },
                     "pageBreakAfterReportPart": false,
                     "marginSettings": [{
                        "type": 0,
                        "topValue": 0.75,
                        "bottomValue": 0.75,
                        "leftValue": 0.7,
                        "rightValue": 0.7,
                        "headerValue": 0.3,
                        "footerValue": 0.3
                     },
                     {
                        "type": 1,
                        "topValue": 0.75,
                        "bottomValue": 0.75,
                        "leftValue": 0.25,
                        "rightValue": 0.25,
                        "headerValue": 0.3,
                        "footerValue": 0.3
                     },
                     {
                        "type": 2,
                        "topValue": 1,
                        "bottomValue": 1,
                        "leftValue": 1,
                        "rightValue": 1,
                        "headerValue": 0.5,
                        "footerValue": 0.5
                     },
                     {
                        "type": 3,
                        "topValue": 0.75,
                        "bottomValue": 0.75,
                        "leftValue": 0.7,
                        "rightValue": 0.7,
                        "headerValue": 0.3,
                        "footerValue": 0.3
                     }]
                  },
                  "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "dynamicQuerySourceFields": [],
                  "snapToGrid": false,
                  "excludedRelationships": "",
                  "isGlobal": false
               },
               "expandedLevel": -1,
               "title": "Grid",
               "paging": {
                  "pageIndex": 1,
                  "pageSize": 10
               },
               "sortOrders": [{
                  "key": "OrderID",
                  "sortingType": "Unsort"
               }],
               "filters": []
            }

   Response::

      {
         "grandTotalMapping": [],
         "subTotalMapping": [],
         "sideTotalMapping": [],
         "executionTrace": [],
         "records": [
            {
                  "orderid_2be8c595_91a3_": 10250,
                  "rowNumber": 1
            },
            {
                  "orderid_2be8c595_91a3_": 10283,
                  "rowNumber": 10
            }
         ],
         "fieldsMapping": [
            {
                  "fieldId": "2be8c595-91a3-4250-8828-dbbc07eaba83",
                  "fieldNameAlias": "OrderID",
                  "columnName": "orderid_2be8c595_91a3_"
            }
         ],
         "paging": {
            "pageIndex": 1,
            "pageSize": 10,
            "total": 2,
            "skipItems": 0,
            "isLastPage": false
         },
         "pivotHeaderValues": [],
         "cities": [],
         "postalCodes": []
      }

POST fusion/printQuery
--------------------------------------------------------------

Returns the sql query for a data request.

**Request**

    Payload: a :doc:`models/FusionDataRequest` object

**Response**

    The query a text (.txt) file

**Samples**

   .. code-block:: HTTP

      POST /api/fusion/printQuery HTTP/1.1

   Request payload::

      {
         "loadDraft": false,
         "reportId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
         "reportPartId": "90ff323c-38f8-4663-823f-35afd85239ee",
         "tenantId": null,
         "userAction": null,
         "paging": {
            "pageIndex": 1,
            "pageSize": 10
         },
         "expandedLevel": -1,
         "sortOrders": [{
            "key": "OrderID",
            "sortingType": "Unsort"
         },
         {
            "key": "Sum(Frieght)",
            "sortingType": "Unsort"
         },
         {
            "key": "ShipCountry",
            "sortingType": "ASC"
         }],
         "filters": []
      }

POST fusion/printQuery/reportPartPreview
--------------------------------------------------------------

Returns the sql query for a report part preview request.

**Request**

    Payload: a :doc:`models/ReportPartPreviewParameter` object

**Response**

    The query a text (.txt) file

**Samples**

   .. code-block:: http

      POST /api/fusion/printQuery/reportPartPreview HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload::

      .. code-block:: json

            {
               "reportKey": {
                  "key": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
                  "modified": null,
                  "tenantId": null
               },
               "section": 2,
               "saveAs": false,
               "ignoreCheckChange": true,
               "report": {
                  "name": "091217-test",
                  "type": 0,
                  "previewRecord": 10,
                  "advancedMode": true,
                  "allowNulls": false,
                  "isDistinct": false,
                  "categoryId": "dc04087a-a761-43fb-b82d-5dd56fe8d9e3",
                  "category": {
                     "id": "dc04087a-a761-43fb-b82d-5dd56fe8d9e3",
                     "name": "",
                     "type": 0,
                     "tenantId": null
                  },
                  "subCategory": {
                     "id": null,
                     "name": "",
                     "type": 0,
                     "tenantId": null
                  },
                  "subCategoryId": null,
                  "reportDataSource": [{
                     "reportId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
                     "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                     "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                     "querySourceCategoryId": null,
                     "connectionId": null,
                     "selected": false,
                     "id": "e8cd9782-98bc-4f6b-9251-e48c756c9937",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 1,
                     "created": "2017-09-12T06:30:52.84",
                     "createdBy": "System5 Admin5",
                     "modified": "2017-09-12T06:30:52.84",
                     "modifiedBy": "System5 Admin5"
                  }],
                  "reportRelationship": [],
                  "reportFilter": null,
                  "reportPart": [{
                     "isDirty": true,
                     "reportPartContent": {
                        "subReportDefinitionCollection": [],
                        "collapseStatus": 0,
                        "isDirty": false,
                        "isCrossFiltering": false,
                        "type": 3,
                        "columns": {
                           "elements": [{
                              "reportPartContent": null,
                              "isDirty": false,
                              "name": "OrderID",
                              "properties": {
                                 "isDirty": false,
                                 "fieldItemVisible": true,
                                 "dataFormattings": null,
                                 "headerFormating": null,
                                 "drillDown": {
                                    "subReport": {
                                       "selectedReport": null,
                                       "style": null,
                                       "reportPartUsed": null,
                                       "reportFilter": true,
                                       "mappingFields": [],
                                       "selectedIconValue": {
                                          "icon": null,
                                          "value": null
                                       },
                                       "viewSettingByLink": null
                                    }
                                 },
                                 "otherProps": {
                                    
                                 }
                              },
                              "position": 1,
                              "field": {
                                 "fieldId": "2be8c595-91a3-4250-8828-dbbc07eaba83",
                                 "fieldName": "OrderID",
                                 "fieldNameAlias": "OrderID",
                                 "dataFieldType": "Numeric",
                                 "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": null,
                                 "visible": true,
                                 "calculatedTree": null,
                                 "schemaName": "dbo",
                                 "querySourceName": "Orders",
                                 "databaseName": "Northwind-BA",
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false,
                              "offset": {
                                 
                              }
                           }],
                           "name": "columns"
                        },
                        "rows": {
                           "elements": [],
                           "name": "rows"
                        },
                        "values": {
                           "elements": [],
                           "name": "values"
                        },
                        "separators": {
                           "elements": [],
                           "name": "separators"
                        },
                        "properties": {
                           "isDirty": false,
                           "generalInfo": {
                              "gridStyle": "Vertical",
                              "separatorStyle": "Comma"
                           },
                           "table": null,
                           "columns": {
                              "width": {
                                 "value": 150
                              },
                              "alterBackgroundColor": false
                           },
                           "rows": {
                              "alterBackgroundColor": false
                           },
                           "headers": null,
                           "grouping": {
                              "useSeparator": true
                           },
                           "view": {
                              "dataRefreshInterval": {
                                 "enable": false,
                                 "updateInterval": 0,
                                 "isAll": true,
                                 "latestRecord": 0
                              },
                              "usePagination": true,
                              "collapseDrilldownByDefault": false,
                              "pageSize": 10,
                              "pivotColumnsPerExportedPage": ""
                           },
                           "printing": {
                              "usePageBreakAfterSeparator": false
                           }
                        },
                        "settings": {
                           
                        },
                        "changeGridStyleStatus": true,
                        "inconsitentFunction": false,
                        "title": null,
                        "description": null
                     },
                     "width": 0,
                     "height": 0,
                     "state": 1,
                     "modified": null,
                     "configField": {
                        
                     },
                     "stateReview": 0,
                     "positionY": 0,
                     "positionX": 0,
                     "title": "Grid"
                  }],
                  "header": null,
                  "footer": null,
                  "titleDescription": null,
                  "version": 5,
                  "schedules": [],
                  "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "accesses": [],
                  "exportFormatSetting": null,
                  "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "dynamicQuerySourceFields": [],
                  "snapToGrid": false,
                  "excludedRelationships": "",
                  "isGlobal": false
               },
               "expandedLevel": -1,
               "title": "Grid",
               "paging": {
                  "pageIndex": 1,
                  "pageSize": 10
               },
               "sortOrders": [{
                  "key": "OrderID",
                  "sortingType": "Unsort"
               }],
               "filters": []
            }

GET fusion/printQuery/{reportId}/{reportPartId}/(pageIndex)/(pageSize)
-------------------------------------------------------------------------

Returns the sql query for a report part load with paging and optional overridden filter values and operators.

**Request**

    No payload

**Response**

    The query a text (.txt) file

**Samples**

   .. code-block:: http

      GET /api/fusion/printQuery/9197f210-766a-45d3-a1f9-5c4f4a4aa8ba/79bf6715-4467-4f1b-8289-ad81c9defd6b HTTP/1.1
