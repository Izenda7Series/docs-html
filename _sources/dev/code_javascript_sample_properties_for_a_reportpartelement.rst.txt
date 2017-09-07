=========================================================
Sample Properties for a ReportPartElement
=========================================================

.. note::

   See :doc:`/ref/models/ReportPartElementProperties` for the purpose of each field.

.. container:: toggle

   .. container:: header

      Sample for ``GROUP(OrderDate)``

   |br|

   *  "7f942ac7-08d8-41fa-9e89-bad96f07f102" is the id for GROUP function
   *  Get the list of functions from :ref:`POST_report/function/{function_mode}/{data_type}/(tenant_id)`
   *  "76875180-32c1-4180-b92f-03bdb14c4f6a" is the id for Year format
   *  Get the list of formats from :ref:`GET_report/field/dataFormat/{dataType}`

   .. code-block:: json
      :linenos:
      :emphasize-lines: 9,21

      {
         "name": "OrderDate",
         "other fields": "are not included in this sample",
         "properties": {
            "fieldItemVisible": true,
            "dataFormattings": {
               "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
               "functionInfo": {
                  "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                  "name": "Group",
                  "expression": null,
                  "dataType": "Datetime",
                  "formatDataType": "Datetime",
                  "syntax": null,
                  "expressionSyntax": null,
                  "isOperator": false,
                  "userDefined": false,
                  "extendedProperties": {}
               },
               "format": {
                  "formatId": "76875180-32c1-4180-b92f-03bdb14c4f6a",
                  "format": "Year",
                  "groupBy": "year",
                  "formatDataType": null,
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
               "sort": "ASC",
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
         }
      }

.. container:: toggle

   .. container:: header

      Sample for ``SUM(Freight)``

   |br|

   *  "902a9168-fc01-4a35-92fb-ea67942d099d" is the id for SUM function
   *  Get the list of functions from :ref:`POST_report/function/{function_mode}/{data_type}/(tenant_id)`

   .. code-block:: json
      :linenos:
      :emphasize-lines: 9

      {
         "name": "Sum (Freight)",
         "other fields": "are not included in this sample",
         "properties": {
            "fieldItemVisible": true,
            "dataFormattings": {
               "function": "902a9168-fc01-4a35-92fb-ea67942d099d",
               "functionInfo": {
                  "id": "902a9168-fc01-4a35-92fb-ea67942d099d",
                  "name": "Sum",
                  "expression": null,
                  "dataType": "Money",
                  "formatDataType": "Money",
                  "syntax": null,
                  "expressionSyntax": null,
                  "isOperator": false,
                  "userDefined": false,
                  "extendedProperties": {}
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
               "sort": "ASC",
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
         }
      }

.. container:: toggle

   .. container:: header

      Sample for ``SUM(Freight)`` with Gauge Static Threshold setting

   |br|

   *  "902a9168-fc01-4a35-92fb-ea67942d099d" is the id for SUM function
   *  Get the list of functions from :ref:`POST_report/function/{function_mode}/{data_type}/(tenant_id)`
   *  The Gauge metric settings are also highlighted:

      -  Scale from 4000 to 8000
      -  Unit label shows "USD"
      -  Static threshold levels: less than 5000, between 5000 and 7000, greater than 7000

   .. code-block:: json
      :linenos:
      :emphasize-lines: 8,107-109,111,118,120,127-129,136,137

      {
         "name": "Sum (Freight)",
         "properties": {
            "fieldItemVisible": true,
            "dataFormattings": {
               "function": "902a9168-fc01-4a35-92fb-ea67942d099d",
               "functionInfo": {
                  "id": "902a9168-fc01-4a35-92fb-ea67942d099d",
                  "name": "Sum",
                  "expression": null,
                  "dataType": "Money",
                  "formatDataType": "Money",
                  "syntax": null,
                  "expressionSyntax": null,
                  "isOperator": false,
                  "userDefined": false,
                  "extendedProperties": {}
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
               "sort": "ASC",
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
            "otherProps": {},
            "metric": {
               "scale": {
                  "from": 4000,
                  "to": 8000
               },
               "unitLabel": "USD",
               "thresholds": {
                  "setting": "static",
                  "levels": [
                     {
                        "name": "low",
                        "color": "#55BF3B",
                        "operator": "less than",
                        "value": null,
                        "valueUpper": 5000,
                        "element": null,
                        "elementUpper": null
                     },
                     {
                        "name": "target",
                        "color": "#DDDF0D",
                        "operator": "between",
                        "value": 5000,
                        "valueUpper": 7000,
                        "element": null,
                        "elementUpper": null
                     },
                     {
                        "name": "high",
                        "color": "#DF5353",
                        "operator": "greater than",
                        "value": 7000,
                        "valueUpper": null,
                        "element": null,
                        "elementUpper": null
                     }
                  ]
               },
               "supplementaryKPI": {
                  "valueType": "",
                  "unitLabel": "",
                  "value": null,
                  "element": null
               }
            }
         },
         "position": 1,
         "field": {
            "fieldId": "61b3c4ad-cbd4-49b0-9385-540568397e05",
            "fieldName": "Freight",
            "fieldNameAlias": "Sum (Freight)",
            "dataFieldType": "Money",
            "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
            "querySourceType": "Table",
            "sourceAlias": "Orders",
            "relationshipId": "00000000-0000-0000-0000-000000000000",
            "visible": true,
            "calculatedTree": null,
            "isCalculated": false,
            "hasAggregatedFunction": false
         }
      }

.. container:: toggle

   .. container:: header

      Sample for ``SUM(UnitsInStock)`` with Gauge Dynamic Threshold setting

   |br|

   *  "902a9168-fc01-4a35-92fb-ea67942d099d" is the id for SUM function
   *  Get the list of functions from :ref:`POST_report/function/{function_mode}/{data_type}/(tenant_id)`
   *  The Gauge Dynamic Threshold setting: ``low: SUM(UnitsInStock) less than SUM(UnitsOnOrder)``

   .. code-block:: json
      :linenos:
      :emphasize-lines: 173,179,281,282,287,291-292,298

      {
         "type": 2,
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
         "activeSerie": null,
         "labels": {
            "elements": [
               {
                  "name": "SupplierID",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                        "functionInfo": {
                           "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                           "name": "Group",
                           "expression": null,
                           "dataType": "Numeric",
                           "formatDataType": "Numeric",
                           "syntax": null,
                           "expressionSyntax": null,
                           "isOperator": false,
                           "userDefined": false,
                           "extendedProperties": {}
                        },
                        "format": {},
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
                        "sort": "ASC",
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
                  "position": 1,
                  "field": {
                     "fieldId": "a79ccaa4-d294-4b02-aed8-70f7ea1ee303",
                     "fieldName": "SupplierID",
                     "fieldNameAlias": "SupplierID",
                     "dataFieldType": "Numeric",
                     "querySourceId": "59c2e0a9-138a-4d29-b12d-bf98f99f6cc3",
                     "querySourceType": "Table",
                     "sourceAlias": "Products",
                     "relationshipId": null,
                     "visible": true,
                     "calculatedTree": null,
                     "schemaName": "dbo",
                     "querySourceName": "Products",
                     "databaseName": "Northwind",
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  }
               }
            ],
            "name": "labels"
         },
         "values": {
            "elements": [
               {
                  "name": "Sum (UnitsInStock)",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "902a9168-fc01-4a35-92fb-ea67942d099d",
                        "functionInfo": {
                           "id": "902a9168-fc01-4a35-92fb-ea67942d099d",
                           "name": "Sum",
                           "expression": null,
                           "dataType": "Numeric",
                           "formatDataType": "Numeric",
                           "syntax": null,
                           "expressionSyntax": null,
                           "isOperator": false,
                           "userDefined": false,
                           "extendedProperties": {}
                        },
                        "format": {},
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
                        "sort": "ASC",
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
                     "otherProps": {},
                     "metric": {
                        "scale": {
                           "from": null,
                           "to": null
                        },
                        "unitLabel": "",
                        "thresholds": {
                           "setting": "dynamic",
                           "levels": [
                              {
                                 "name": "low",
                                 "color": "#ff0000",
                                 "operator": "less than",
                                 "value": null,
                                 "valueUpper": null,
                                 "element": null,
                                 "elementUpper": {
                                    "name": "Sum (UnitsOnOrder)",
                                    "properties": {
                                       "fieldItemVisible": true,
                                       "dataFormattings": {
                                          "function": "902a9168-fc01-4a35-92fb-ea67942d099d",
                                          "functionInfo": {
                                             "id": "902a9168-fc01-4a35-92fb-ea67942d099d",
                                             "name": "Sum",
                                             "expression": null,
                                             "dataType": "Numeric",
                                             "formatDataType": "Numeric",
                                             "syntax": null,
                                             "expressionSyntax": null,
                                             "isOperator": false,
                                             "userDefined": false,
                                             "extendedProperties": {}
                                          },
                                          "format": {},
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
                                          "sort": "ASC",
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
                                    "position": 1,
                                    "field": {
                                       "fieldId": "9baea98a-8cf8-46d9-8bcc-89a3374da404",
                                       "fieldName": "UnitsOnOrder",
                                       "fieldNameAlias": "Sum (UnitsOnOrder)",
                                       "dataFieldType": "Numeric",
                                       "querySourceId": "59c2e0a9-138a-4d29-b12d-bf98f99f6cc3",
                                       "querySourceType": "Table",
                                       "sourceAlias": "Products",
                                       "relationshipId": null,
                                       "visible": true,
                                       "calculatedTree": null,
                                       "schemaName": "dbo",
                                       "querySourceName": "Products",
                                       "databaseName": "Northwind",
                                       "isCalculated": false,
                                       "hasAggregatedFunction": false
                                    }
                                 }
                              },
                              {
                                 "name": "target",
                                 "color": "#008000",
                                 "operator": "less than",
                                 "value": null,
                                 "valueUpper": null,
                                 "element": {
                                    "name": "Sum (UnitsOnOrder)",
                                    "properties": {
                                       "fieldItemVisible": true,
                                       "dataFormattings": {
                                          "function": "902a9168-fc01-4a35-92fb-ea67942d099d",
                                          "functionInfo": {
                                             "id": "902a9168-fc01-4a35-92fb-ea67942d099d",
                                             "name": "Sum",
                                             "expression": null,
                                             "dataType": "Numeric",
                                             "formatDataType": "Numeric",
                                             "syntax": null,
                                             "expressionSyntax": null,
                                             "isOperator": false,
                                             "userDefined": false,
                                             "extendedProperties": {}
                                          },
                                          "format": {},
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
                                          "sort": "ASC",
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
                                    "position": 1,
                                    "field": {
                                       "fieldId": "9baea98a-8cf8-46d9-8bcc-89a3374da404",
                                       "fieldName": "UnitsOnOrder",
                                       "fieldNameAlias": "Sum (UnitsOnOrder)",
                                       "dataFieldType": "Numeric",
                                       "querySourceId": "59c2e0a9-138a-4d29-b12d-bf98f99f6cc3",
                                       "querySourceType": "Table",
                                       "sourceAlias": "Products",
                                       "relationshipId": null,
                                       "visible": true,
                                       "calculatedTree": null,
                                       "schemaName": "dbo",
                                       "querySourceName": "Products",
                                       "databaseName": "Northwind",
                                       "isCalculated": false,
                                       "hasAggregatedFunction": false
                                    },
                                    "isDeleted": false,
                                    "isSelected": false
                                 },
                                 "elementUpper": null
                              },
                              {
                                 "name": "high",
                                 "color": "#000000",
                                 "operator": "greater than",
                                 "value": null,
                                 "valueUpper": null,
                                 "element": null,
                                 "elementUpper": null
                              }
                           ]
                        },
                        "supplementaryKPI": {
                           "valueType": "",
                           "unitLabel": "",
                           "value": null,
                           "element": null
                        }
                     }
                  },
                  "position": 1,
                  "field": {
                     "fieldId": "bbd3b5a1-4be2-40c3-be9f-89e19a9487df",
                     "fieldName": "UnitsInStock",
                     "fieldNameAlias": "Sum (UnitsInStock)",
                     "dataFieldType": "Numeric",
                     "querySourceId": "59c2e0a9-138a-4d29-b12d-bf98f99f6cc3",
                     "querySourceType": "Table",
                     "sourceAlias": "Products",
                     "relationshipId": null,
                     "visible": true,
                     "calculatedTree": null,
                     "schemaName": "dbo",
                     "querySourceName": "Products",
                     "databaseName": "Northwind",
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  }
               }
            ],
            "name": "values"
         },
         "separators": {
            "elements": [],
            "name": "separators"
         },
         "properties": {
            "staticProperties": {},
            "chartType": "SolidGauge",
            "optionByType": {
               "izUseSeparator": true,
               "izUsePagination": true,
               "izItemPerRow": 2
            },
            "view": {
               "showLabels": false,
               "dataRefreshInterval": {
                  "enable": false,
                  "updateInterval": 0,
                  "isAll": true,
                  "latestRecord": 0
               }
            },
            "printing": {
               "izPageBreakAfterSeparator": false
            }
         }
      }
