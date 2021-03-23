

=========================================
ReportDefinition
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **inaccessible** |br|
         boolean
      -
      -  True if report is inaccessible for user
      -
   *  -  **category** |br|
         object
      -
      -  A :doc:`Category` object
      -
   *  -  **subCategory** |br|
         object
      -
      -  A :doc:`Category` object
      -
   *  -  **reportRelationship** |br|
         array of objects
      -
      -  An array of :doc:`Relationship` objects
      -
   *  -  **reportPart** |br|
         array of objects
      -
      -  An array of :doc:`ReportPartDefinition` objects
      -
   *  -  **reportFilter** |br|
         object
      -
      -  A :doc:`ReportFilterSetting` object
      -
   *  -  **calculatedFields** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceField` objects
      -
   *  -  **accesses** |br|
         array of objects
      -
      -  An array of :doc:`UserPermission` objects
      -
   *  -  **schedules** |br|
         array of objects
      -
      -  An array of :doc:`Subscription` objects
      -
   *  -  **reportParams** |br|
         array of objects
      -
      -  An array of :doc:`ReportConnectionParam` objects
      -
   *  -  **dynamicQuerySourceFields** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceField` objects
      -




Inherited fields:

.. include:: Report.rst


.. container:: toggle

   .. container:: header

      **ReportDefintion Sample**:

   .. code-block:: json

      {
            "inaccessible": false,
            "category": null,
            "subCategory": null,
            "reportRelationship": [
                  {
                  "joinConnectionId": "5963219c-5243-4b6f-9042-b27ca9cbc5ec",
                  "foreignConnectionId": "5963219c-5243-4b6f-9042-b27ca9cbc5ec",
                  "joinQuerySourceAlias": null,
                  "foreignQuerySourceAlias": null,
                  "joinFieldAlias": null,
                  "specifictJoinFieldAlias": null,
                  "foreignFieldAlias": null,
                  "specifictForeignFieldAlias": null,
                  "alias": "Employees 2",
                  "systemRelationship": true,
                  "joinType": "Inner",
                  "parentRelationshipId": null,
                  "position": null,
                  "relationshipPosition": 0,
                  "relationshipKeyJoins": [],
                  "reportId": null,
                  "foreignAlias": "",
                  "joinQuerySourceUniqueName": "[con;#0].[cat;#0].[Employees]",
                  "joinFieldUniqueName": "[con;#0].[cat;#0].[Employees].[EmployeeID]",
                  "forgeinQuerySourceUniqueName": "[con;#0].[cat;#0].[Employees]",
                  "forgeinFieldUniqueName": "[con;#0].[cat;#0].[Employees].[ReportsTo]",
                  "tempId": "10273410-348a-4892-b33a-0fae8ea148d9",
                  "aliasTempId": "alias_164",
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isForeignDataObjectAlias": false,
                  "selectedForeignAlias": "894cfc27-099f-4b81-8d78-5263218f5b79_Employees",
                  "joinQuerySourceName": "Employees",
                  "joinQuerySourceId": "894cfc27-099f-4b81-8d78-5263218f5b79",
                  "joinFieldId": "bccc3651-6f50-486b-a6d2-4d0d98994c73",
                  "joinFieldType": null,
                  "foreignQuerySourceName": "Employees",
                  "foreignQuerySourceId": "894cfc27-099f-4b81-8d78-5263218f5b79",
                  "foreignFieldId": "ab815bd2-54a9-43f0-b347-45ed693d7c9b",
                  "foreignFieldType": null,
                  "joinFieldName": "EmployeeID",
                  "foreignFieldName": "ReportsTo",
                  "joinDataSourceCategoryId": "00000000-0000-0000-0000-000000000000",
                  "joinDataSourceCategoryName": "",
                  "foreignDataSourceCategoryId": "00000000-0000-0000-0000-000000000000",
                  "foreignDataSourceCategoryName": null,
                  "comparisonOperator": "= (Field)",
                  "id": "10273410-348a-4892-b33a-0fae8ea148d9",
                  "state": 2,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System Admin",
                  "modified": null,
                  "modifiedBy": null
                  }
            ],
            "reportPart": [
                  {
                  "reportPartContent": {
                        "columns": {
                              "text": null,
                              "properties": {},
                              "settings": {},
                              "elements": [
                              {
                                    "name": "EmployeeID",
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
                                                "format": {},
                                                "previewResult": ""
                                          },
                                          "grandTotal": {
                                                "label": "",
                                                "function": "",
                                                "expression": "",
                                                "dataType": "",
                                                "format": {},
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
                                          "otherProps": {}
                                    },
                                    "settings": {},
                                    "chartType": null,
                                    "showTotal": false,
                                    "position": 1,
                                    "field": {
                                          "fieldId": "bccc3651-6f50-486b-a6d2-4d0d98994c73",
                                          "fieldUniqueName": "[con;#0].[cat;#0].[Employees].[EmployeeID]",
                                          "originalName": null,
                                          "fieldName": "EmployeeID",
                                          "fieldNameAlias": "EmployeeID",
                                          "dataFieldType": "Numeric",
                                          "querySourceId": "894cfc27-099f-4b81-8d78-5263218f5b79",
                                          "querySourceUniqueName": "[con;#0].[cat;#0].[Employees]",
                                          "querySourceType": "Table",
                                          "sourceAlias": "Employees",
                                          "querySourceAlias": null,
                                          "runningDeep": -1,
                                          "isRunningField": false,
                                          "builtRunningField": false,
                                          "relationshipId": "00000000-0000-0000-0000-000000000000",
                                          "visible": true,
                                          "filterable": false,
                                          "reportId": null,
                                          "fieldFunctionExpression": "",
                                          "expression": null,
                                          "grandTotalExpression": "",
                                          "grandTotalFormat": null,
                                          "subTotalExpression": "",
                                          "subtotalFormat": null,
                                          "sort": "Unsorted",
                                          "autoSort": false,
                                          "function": "",
                                          "formating": {
                                          "format": null,
                                          "createNewHiddenPercenOfGroupField": false
                                          },
                                          "functionDataType": "",
                                          "isCalculated": false,
                                          "hasAggregatedFunction": false,
                                          "invalidField": 0,
                                          "isCrossFilter": false
                                    }
                              },
                              {
                                    "name": "Address",
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
                                                "format": {},
                                                "previewResult": "",
                                                "fieldDataType": "Text",
                                                "previewRecord": 10
                                          },
                                          "grandTotal": {
                                                "label": "",
                                                "function": "",
                                                "expression": "",
                                                "dataType": "",
                                                "format": {},
                                                "previewResult": "",
                                                "fieldDataType": "Text",
                                                "previewRecord": 10
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
                                          "otherProps": {}
                                    },
                                    "settings": {},
                                    "chartType": null,
                                    "showTotal": false,
                                    "position": 2,
                                    "field": {
                                          "fieldId": "1e14ca64-3b9b-4691-948c-fc92460e1cd2",
                                          "fieldUniqueName": "[con;#0].[cat;#0].[Employees].[Address]",
                                          "originalName": null,
                                          "fieldName": "Address",
                                          "fieldNameAlias": "Address",
                                          "dataFieldType": "Text",
                                          "querySourceId": "894cfc27-099f-4b81-8d78-5263218f5b79",
                                          "querySourceUniqueName": "[con;#0].[cat;#0].[Employees]",
                                          "querySourceType": "Table",
                                          "sourceAlias": "Employees",
                                          "querySourceAlias": null,
                                          "runningDeep": -1,
                                          "isRunningField": false,
                                          "builtRunningField": false,
                                          "relationshipId": "00000000-0000-0000-0000-000000000000",
                                          "visible": true,
                                          "filterable": false,
                                          "reportId": null,
                                          "fieldFunctionExpression": "",
                                          "expression": null,
                                          "grandTotalExpression": "",
                                          "grandTotalFormat": null,
                                          "subTotalExpression": "",
                                          "subtotalFormat": null,
                                          "sort": "Unsorted",
                                          "autoSort": false,
                                          "function": "",
                                          "formating": {
                                          "format": null,
                                          "createNewHiddenPercenOfGroupField": false
                                          },
                                          "functionDataType": "",
                                          "isCalculated": false,
                                          "hasAggregatedFunction": false,
                                          "invalidField": 0,
                                          "isCrossFilter": false
                                    }
                              }
                              ]
                        },
                        "rows": {
                              "text": null,
                              "properties": {},
                              "settings": {},
                              "elements": []
                        },
                        "values": {
                              "text": null,
                              "properties": {},
                              "settings": {},
                              "elements": []
                        },
                        "separators": {
                              "text": null,
                              "properties": {},
                              "settings": {},
                              "elements": []
                        },
                        "paginable": true,
                        "type": "3",
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
                        "settings": {},
                        "title": {
                              "text": "",
                              "properties": {},
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
                              "properties": {},
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
                        },
                        "expandedLevel": -1,
                        "isCrossFiltering": false,
                        "isFormatted": false
                  },
                  "title": "Grid",
                  "positionX": 0,
                  "positionY": 0,
                  "width": 0,
                  "height": 0,
                  "reportId": "1e547675-361b-494a-a286-8f42ddd4d2d1",
                  "numberOfRecord": null,
                  "sourceId": null,
                  "id": "c0ae9b2a-aad3-488f-b31e-7ddb22dbb6da",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-10-23T14:19:08.52",
                  "createdBy": "System Admin",
                  "modified": "2017-10-23T14:19:08.52",
                  "modifiedBy": "System Admin"
                  }
            ],
            "reportFilter": {
                  "filterFields": [],
                  "baseFilterLogic": null,
                  "logic": "",
                  "visible": false,
                  "reportId": "1e547675-361b-494a-a286-8f42ddd4d2d1",
                  "id": "49b39bfc-a99f-409d-bb8a-3949f87741d7",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-10-23T14:19:08.517",
                  "createdBy": "System Admin",
                  "modified": "2017-10-23T14:19:08.517",
                  "modifiedBy": "System Admin"
            },
            "calculatedFields": [],
            "accesses": [],
            "schedules": [],
            "reportParams": [
                  {
                  "categories": [
                        {
                              "querySourceNames": [
                              "Employees"
                              ],
                              "id": "860cab58-d90a-4d6d-9251-ec45c067f6b9",
                              "name": "dbo"
                        }
                  ],
                  "id": "5963219c-5243-4b6f-9042-b27ca9cbc5ec",
                  "name": "Retail"
                  }
            ],
            "dynamicQuerySourceFields": [],
            "name": "Copy Console Report",
            "reportDataSource": [
                  {
                  "reportId": "1e547675-361b-494a-a286-8f42ddd4d2d1",
                  "querySourceId": null,
                  "querySourceUniqueName": "[con;#0].[cat;#0].[Employees]",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": false,
                  "id": "61f7ab7c-1d49-4ffd-b03d-af6fb4d922a7",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-10-23T14:19:08.51",
                  "createdBy": "System Admin",
                  "modified": "2017-10-23T14:19:08.51",
                  "modifiedBy": "System Admin"
                  }
            ],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": null,
            "categoryName": null,
            "subCategoryId": null,
            "subCategoryName": null,
            "tenantId": "e41e53a4-5d75-4bb9-97d8-6199f6c9d3c9",
            "tenantName": "CopyConsoleTenant",
            "description": "",
            "title": "",
            "lastViewed": null,
            "owner": "System Admin",
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "excludedRelationships": "10273410-348a-4892-b33a-0fae8ea148d9",
            "numberOfView": 0,
            "renderingTime": 0,
            "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "snapToGrid": false,
            "usingFields": null,
            "hasDeletedObjects": false,
            "header": {
                  "visible": false,
                  "items": [
                  {
                        "isDirty": false,
                        "type": "image",
                        "label": "Image",
                        "id": "formatDetails_183",
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
                        "id": "formatDetails_184",
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
                        "id": "formatDetails_185",
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
                        "id": "formatDetails_186",
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
                        "id": "formatDetails_187",
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
                        "id": "formatDetails_188",
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
                        "id": "formatDetails_189",
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
                        "id": "formatDetails_190",
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
                        "id": "formatDetails_191",
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
                        "id": "formatDetails_192",
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
                  }
                  ]
            },
            "footer": {
                  "visible": false,
                  "items": [
                  {
                        "isDirty": false,
                        "type": "horizontalRule",
                        "label": "Horizontal Rule",
                        "id": "formatDetails_193",
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
                        "id": "formatDetails_194",
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
                        "id": "formatDetails_195",
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
                        "id": "formatDetails_196",
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
                  }
                  ]
            },
            "titleDescription": {
                  "visible": false,
                  "items": [
                  {
                        "isDirty": false,
                        "type": "title",
                        "label": "Title",
                        "id": "formatDetails_197",
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
                        "id": "formatDetails_198",
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
                  }
                  ]
            },
            "sourceId": null,
            "checked": false,
            "copyDashboard": false,
            "exportFormatSetting": {
                  "orientation": 0,
                  "margins": 0,
                  "centerOnPage": {
                  "horizontally": false,
                  "vertically": false
                  },
                  "pageBreakAfterReportPart": false,
                  "marginSettings": [
                  {
                        "type": 3,
                        "topValue": 0.75,
                        "bottomValue": 0.75,
                        "leftValue": 0.7,
                        "rightValue": 0.7,
                        "headerValue": 0.3,
                        "footerValue": 0.3
                  },
                  {
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
                  }
                  ]
            },
            "deletable": false,
            "editable": false,
            "movable": false,
            "copyable": false,
            "accessPriority": 0,
            "active": false,
            "fullPath": null,
            "computeNameSettings": null,
            "isGlobal": false,
            "isCheck": false,
            "id": "1e547675-361b-494a-a286-8f42ddd4d2d1",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-10-23T14:19:08.413",
            "createdBy": "System Admin",
            "modified": "2017-10-23T14:19:08.413",
            "modifiedBy": "System Admin"
      }
