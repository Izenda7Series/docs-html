=========================================================
Build a simple Gauge
=========================================================

Steps:

#. Follow :doc:`code_javascript_build_a_generic_report` until the step to add report parts.
#. Prepare an empty :doc:`/ref/models/ReportPartGauge` object with default properties.
#. For each selected data source fields, populate a :doc:`/ref/models/ReportPartElement` object with default properties.
#. Add the :doc:`/ref/models/ReportPartElement` objects into either ``labels.elements``, ``values.elements`` or ``separators.elements`` in :doc:`/ref/models/ReportPartGauge` object.
#. Update the properties of the chart in ``properties`` field per user selection (See :doc:`/ref/models/ReportPartGaugeProperties`).
#. Back to the steps in :doc:`code_javascript_build_a_generic_report`.

Prepare an empty ReportPartGauge object
----------------------------------------

.. container:: toggle

   .. container:: header

      Empty ReportPartGauge object

   |br|

   *  The highlighted ``labels.elements``, ``values.elements`` and ``separators.elements`` are where the selected data source fields will be added
   *  The highlighted ``properties`` contains the default properties

   .. code-block:: json
      :linenos:
      :emphasize-lines: 42,46,50,53

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
         "labels": {
            "elements": [],
            "name": "labels"
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

Populate selected data sources fields
---------------------------------------

#. Refer to the :ref:`similar step in Building a Grid guide <Grid_Populate_selected_data_sources_fields>` to:

   #. Get the list of available data sources fields from :ref:`POST_report/availableQuerySourceFields`
   #. Build a corresponding ReportPartElement object for each selected data source field
   #. Populate a default ReportPartElementProperties for ``properties`` field in each ReportPartElement object

   See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for some samples.

#. Add the :doc:`/ref/models/ReportPartElement` objects into ``labels.elements``, ``values.elements`` and ``separators.elements`` in :doc:`/ref/models/ReportPartChart` object.

.. _Sample_full_ReportPartGauge_object:

.. container:: toggle

   .. container:: header

      Sample full ReportPartGauge object

   *  Highlighted in ``labels.elements`` is the ReportPartElement for ``GROUP(OrderDate)``
   *  Highlighted in ``values.elements`` is the ReportPartElement for ``SUM(Freight)``

   |br|

   .. code-block:: json
      :linenos:
      :emphasize-lines: 43-184,190-343

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
         "labels": {
            "elements": [
               {
                  "reportPartContent": null,
                  "isDirty": true,
                  "name": "OrderDate",
                  "properties": {
                     "isDirty": true,
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
                           "formatId": "8e4b292a-9685-4bca-93ca-03bdeee470cc",
                           "format": "Month Name",
                           "groupBy": "month",
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
                        "alignment": null,
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
                     "fieldId": "fbf031a0-3e2d-49e7-972e-fffc98b634e5",
                     "fieldName": "OrderDate",
                     "fieldNameAlias": "OrderDate",
                     "dataFieldType": "Datetime",
                     "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                     "querySourceType": "Table",
                     "sourceAlias": "Orders",
                     "relationshipId": null,
                     "visible": true,
                     "calculatedTree": null,
                     "schemaName": "dbo",
                     "querySourceName": "Orders",
                     "databaseName": "test",
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false,
                  "isSelected": false,
                  "offset": {
                     "top": 500,
                     "right": 436.671875,
                     "bottom": 522,
                     "left": 337,
                     "width": 99.671875,
                     "height": 22
                  }
               }
            ],
            "name": "labels"
         },
         "values": {
            "elements": [
               {
                  "reportPartContent": null,
                  "isDirty": false,
                  "name": "Sum (Freight)",
                  "properties": {
                     "isDirty": false,
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
                        "isDirty": false,
                        "scale": {
                           "from": null,
                           "to": null
                        },
                        "unitLabel": "",
                        "thresholds": {
                           "setting": "",
                           "levels": []
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
                     "relationshipId": null,
                     "visible": true,
                     "calculatedTree": null,
                     "schemaName": "dbo",
                     "querySourceName": "Orders",
                     "databaseName": "test",
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false,
                  "isSelected": false,
                  "offset": {
                     "top": 643,
                     "right": 592.25,
                     "bottom": 665,
                     "left": 473.25,
                     "width": 119,
                     "height": 22
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

Update the properties of each field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartElementProperties` for the purpose of each field.

See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for more samples.

Update the properties of the Gauge in "properties" field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartGaugeProperties` for the purpose of each field.

Back to the Save step in :ref:`Build a Generic Report <Populate_the_report_parts>`
----------------------------------------------------------------------------------------

.. container:: toggle

   .. container:: header

      Sample full ReportSavingParameter object for Save report API

   .. code-block:: json

      {
         "reportKey": {
            "key": "3b50a6e7-1ae0-47c3-8c1c-70b375c86d85",
            "tenantId": null
         },
         "section": 2,
         "saveAs": false,
         "ignoreCheckChange": false,
         "report": {
            "inaccessible": false,
            "category": {
               "name": "TestCategory",
               "type": 0,
               "parentId": null,
               "tenantId": null,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": null,
               "dashboards": null,
               "id": "1bf05555-def3-43e1-ada2-f326217b72f1",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "John Doe",
               "modified": null,
               "modifiedBy": null
            },
            "subCategory": {
               "name": "",
               "type": 0,
               "parentId": null,
               "tenantId": null,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": null,
               "dashboards": null,
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "John Doe",
               "modified": null,
               "modifiedBy": null
            },
            "reportRelationship": [],
            "reportPart": [
               {
                  "reportPartContent": {
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
                     "labels": {
                        "elements": [
                           {
                              "reportPartContent": null,
                              "isDirty": true,
                              "name": "OrderDate",
                              "properties": {
                                 "isDirty": true,
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
                                       "formatId": "8e4b292a-9685-4bca-93ca-03bdeee470cc",
                                       "format": "Month Name",
                                       "groupBy": "month",
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
                                    "alignment": null,
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
                                 "fieldId": "fbf031a0-3e2d-49e7-972e-fffc98b634e5",
                                 "fieldName": "OrderDate",
                                 "fieldNameAlias": "OrderDate",
                                 "dataFieldType": "Datetime",
                                 "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": null,
                                 "visible": true,
                                 "calculatedTree": null,
                                 "schemaName": "dbo",
                                 "querySourceName": "Orders",
                                 "databaseName": "test",
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false,
                              "offset": {
                                 "top": 500,
                                 "right": 436.671875,
                                 "bottom": 522,
                                 "left": 337,
                                 "width": 99.671875,
                                 "height": 22
                              }
                           }
                        ],
                        "name": "labels"
                     },
                     "values": {
                        "elements": [
                           {
                              "reportPartContent": null,
                              "isDirty": false,
                              "name": "Sum (Freight)",
                              "properties": {
                                 "isDirty": false,
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
                                    "isDirty": false,
                                    "scale": {
                                       "from": null,
                                       "to": null
                                    },
                                    "unitLabel": "",
                                    "thresholds": {
                                       "setting": "",
                                       "levels": []
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
                                 "relationshipId": null,
                                 "visible": true,
                                 "calculatedTree": null,
                                 "schemaName": "dbo",
                                 "querySourceName": "Orders",
                                 "databaseName": "test",
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false,
                              "offset": {
                                 "top": 643,
                                 "right": 592.25,
                                 "bottom": 665,
                                 "left": 473.25,
                                 "width": 119,
                                 "height": 22
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
                  },
                  "width": 12,
                  "height": 4,
                  "positionY": 0,
                  "positionX": 0,
                  "title": "Gauge"
               }
            ],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": true,
               "reportId": "3b50a6e7-1ae0-47c3-8c1c-70b375c86d85",
               "id": "56aa84a0-5301-44fa-850f-e0e28d9c8abd",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "John Doe",
               "modified": null,
               "modifiedBy": null
            },
            "calculatedFields": [],
            "accesses": [],
            "schedules": [],
            "dynamicQuerySourceFields": [],
            "name": "Example Gauge 3",
            "reportDataSource": [
               {
                  "reportId": "3b50a6e7-1ae0-47c3-8c1c-70b375c86d85",
                  "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": true,
                  "id": "1ef0995e-43f9-4465-b26e-55c0256c84fa",
                  "state": 1,
                  "deleted": false,
                  "inserted": false,
                  "version": null,
                  "created": null,
                  "createdBy": "John Doe",
                  "modified": null,
                  "modifiedBy": null
               }
            ],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": "1bf05555-def3-43e1-ada2-f326217b72f1",
            "categoryName": null,
            "subCategoryId": null,
            "subCategoryName": null,
            "tenantId": null,
            "tenantName": null,
            "description": "",
            "title": "",
            "lastViewed": null,
            "owner": "John Doe",
            "ownerId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
            "excludedRelationships": null,
            "numberOfView": 0,
            "renderingTime": 0,
            "createdById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
            "modifiedById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
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
                     "id": "formatDetails_57",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_58",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "thinHorizontalRule",
                     "label": "Horizontal Rule",
                     "id": "formatDetails_59",
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
                     "thickness": 2
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_60",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_61",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_62",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "dateTime",
                     "label": "Date Time",
                     "id": "formatDetails_63",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_64",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_65",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "horizontalRule",
                     "label": "Horizontal Rule",
                     "id": "formatDetails_66",
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
                     "thickness": 4
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
                     "id": "formatDetails_67",
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
                     "thickness": 4
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_68",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_69",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "pageNumber",
                     "label": "Page Number",
                     "id": "formatDetails_70",
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
                     "thickness": 1
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
                     "id": "formatDetails_71",
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
                     "thickness": 1
                  },
                  {
                     "isDirty": false,
                     "type": "description",
                     "label": "Description",
                     "id": "formatDetails_72",
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
                     "thickness": 1
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
            "id": "3b50a6e7-1ae0-47c3-8c1c-70b375c86d85",
            "state": 1,
            "deleted": false,
            "inserted": false,
            "version": 0,
            "created": null,
            "createdBy": "John Doe",
            "modified": null,
            "modifiedBy": "John Doe"
         }
      }
