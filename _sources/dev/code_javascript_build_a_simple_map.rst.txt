=========================================================
Build a simple Map
=========================================================

Steps:

#. Follow :doc:`code_javascript_build_a_generic_report` until the step to add report parts.
#. Prepare an empty :doc:`/ref/models/ReportPartMap` object with default properties.
#. For each selected data source fields, populate a :doc:`/ref/models/ReportPartElement` object with default properties.
#. Add the :doc:`/ref/models/ReportPartElement` objects into either ``pointOptions.elements``, ``shadingMetric.elements`` or ``bubbleMetrics.elements`` in :doc:`/ref/models/ReportPartMap` object.
#. Update the properties of the map in ``properties`` field per user selection (See :doc:`/ref/models/ReportPartMapProperties`).
#. Back to the steps in :doc:`code_javascript_build_a_generic_report`.

Prepare an empty ReportPartMap object
----------------------------------------

.. container:: toggle

   .. container:: header

      Empty ReportPartMap object

   |br|

   *  The highlighted ``pointOptions.elements``, ``shadingMetric.elements`` and ``bubbleMetrics.elements`` are where the selected data source fields will be added
   *  The highlighted ``properties`` contains the default properties
   *  The highlighted ``properties.reportPartState.pointOptionsList`` and ``properties.reportPartState.activePointOption`` must be updated with the selected data source fields in Point Options boxes, see :doc:`/ref/models/ReportPartMapProperties`

   .. code-block:: json
      :linenos:
      :emphasize-lines: 41,45,46,83,90,94

      {
         "type": 4,
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
         "properties": {
            "reportPartState": {
               "drilldownInfo": [],
               "activeSerie": {},
               "pointOptionsList": [],
               "activePointOption": {}
            },
            "chartType": "World",
            "continentInfo": {},
            "countryInfo": {},
            "stateInfo": {},
            "commonOptions": {
               "izHoverLabels": true,
               "izLegend.visibility": false,
               "izLegend.horizontalAlign": "izRight",
               "izLegend.verticalAlign": "izBottom",
               "izLegend.borderWidth": 0,
               "izChartStyle": {},
               "izendaHiddenAllAxis": false
            },
            "optionByType": {
               "izValueLabel": false,
               "izShowTooltip": true,
               "izMapLabel": false,
               "izMapNavigation.enabled": false,
               "legendSettings": true
            },
            "view": {
               "showLabels": false,
               "dataRefreshInterval": {
                  "enable": false,
                  "updateInterval": 0,
                  "isAll": true,
                  "latestRecord": 0
               }
            }
         },
         "shadingMetric": {
            "text": null,
            "properties": {},
            "settings": {},
            "name": "shadingMetric",
            "elements": []
         },
         "bubbleMetrics": {
            "text": null,
            "properties": {},
            "settings": {},
            "name": "bubbleMetrics",
            "elements": []
         },
         "settings": {},
         "pointOptions": {
            "elements": [],
            "name": "pointOptions"
         }
      }

Populate selected data sources fields
---------------------------------------

#. Refer to the :ref:`similar step in Building a Grid guide <Grid_Populate_selected_data_sources_fields>` to:

   #. Get the list of available data sources fields from :ref:`POST_report/availableQuerySourceFields`
   #. Build a corresponding ReportPartElement object for each selected data source field
   #. Populate a default ReportPartElementProperties for ``properties`` field in each ReportPartElement object

   See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for some samples.

#. Add the :doc:`/ref/models/ReportPartElement` objects into ``pointOptions.elements``, ``shadingMetric.elements`` and ``bubbleMetrics.elements`` in :doc:`/ref/models/ReportPartMap` object.
#. Update ``properties.reportPartState.pointOptionsList`` and ``properties.reportPartState.activePointOption`` with the selected data source fields in Point Options boxes.

.. _Sample_full_ReportPartMap_object:

.. container:: toggle

   .. container:: header

      Sample full ReportPartMap object

   *  Highlighted in ``pointOptions.elements`` are the ReportPartElement objects for ``GROUP(ShipCountry)`` and ``GROUP(ShipCity)``
   *  Highlighted in ``bubbleMetrics.elements`` is the ReportPartElement for ``SUM(Freight)``
   *  Highlighted ``properties.reportPartState.pointOptionsList`` and ``properties.reportPartState.activePointOption`` have been updated with the select data source fields in Point Options boxes
   *  Highlighted in ``properties.chartType`` is the chart type (World)

   |br|

   .. code-block:: json
      :linenos:
      :emphasize-lines: 45,177,445,482,487,614,615

      {
         "type": 4,
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
         "properties": {
            "reportPartState": {
               "drilldownInfo": [],
               "activeSerie": {},
               "activePointOption": {
                  "label": "ShipCountry",
                  "value": "ShipCountry",
                  "field": {
                     "reportPartContent": null,
                     "isDirty": false,
                     "name": "ShipCountry",
                     "properties": {
                        "isDirty": false,
                        "fieldItemVisible": true,
                        "dataFormattings": {
                           "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                           "functionInfo": {
                              "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                              "name": "Group",
                              "expression": null,
                              "dataType": "Text",
                              "formatDataType": "Text",
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
                     },
                     "position": 1,
                     "field": {
                        "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                        "fieldName": "ShipCountry",
                        "fieldNameAlias": "ShipCountry",
                        "dataFieldType": "Text",
                        "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                        "querySourceType": "Table",
                        "sourceAlias": "Orders",
                        "relationshipId": "00000000-0000-0000-0000-000000000000",
                        "visible": true,
                        "calculatedTree": null,
                        "isCalculated": false,
                        "hasAggregatedFunction": false
                     },
                     "isDeleted": false
                  },
                  "pointType": "country",
                  "pointTypeName": "country"
               },
               "pointOptionsList": [
                  {
                     "label": "ShipCountry",
                     "value": "ShipCountry",
                     "field": {
                        "reportPartContent": null,
                        "isDirty": false,
                        "name": "ShipCountry",
                        "properties": {
                           "isDirty": false,
                           "fieldItemVisible": true,
                           "dataFormattings": {
                              "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                              "functionInfo": {
                                 "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                 "name": "Group",
                                 "expression": null,
                                 "dataType": "Text",
                                 "formatDataType": "Text",
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
                        },
                        "position": 1,
                        "field": {
                           "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                           "fieldName": "ShipCountry",
                           "fieldNameAlias": "ShipCountry",
                           "dataFieldType": "Text",
                           "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                           "querySourceType": "Table",
                           "sourceAlias": "Orders",
                           "relationshipId": "00000000-0000-0000-0000-000000000000",
                           "visible": true,
                           "calculatedTree": null,
                           "isCalculated": false,
                           "hasAggregatedFunction": false
                        },
                        "isDeleted": false
                     },
                     "pointType": "country",
                     "pointTypeName": "country"
                  },
                  {
                     "label": "ShipCity",
                     "value": "ShipCity",
                     "field": {
                        "reportPartContent": null,
                        "isDirty": false,
                        "name": "ShipCity",
                        "properties": {
                           "isDirty": false,
                           "fieldItemVisible": true,
                           "dataFormattings": {
                              "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                              "functionInfo": {
                                 "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                 "name": "Group",
                                 "expression": null,
                                 "dataType": "Text",
                                 "formatDataType": "Text",
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
                           "fieldId": "b0554a37-b744-4db8-b1b0-95b029d8cae2",
                           "fieldName": "ShipCity",
                           "fieldNameAlias": "ShipCity",
                           "dataFieldType": "Text",
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
                        "isDeleted": false
                     },
                     "pointType": "city",
                     "pointTypeName": "city"
                  }
               ],
            },
            "chartType": "World",
            "continentInfo": {},
            "countryInfo": {},
            "stateInfo": {},
            "commonOptions": {
               "izHoverLabels": true,
               "izLegend.visibility": false,
               "izLegend.horizontalAlign": "izRight",
               "izLegend.verticalAlign": "izBottom",
               "izLegend.borderWidth": 0,
               "izChartStyle": {},
               "izendaHiddenAllAxis": false
            },
            "optionByType": {
               "izValueLabel": false,
               "izShowTooltip": true,
               "izMapLabel": false,
               "izMapNavigation.enabled": false,
               "legendSettings": true
            },
            "view": {
               "showLabels": false,
               "dataRefreshInterval": {
                  "enable": false,
                  "updateInterval": 0,
                  "isAll": true,
                  "latestRecord": 0
               }
            }
         },
         "shadingMetric": {
            "text": null,
            "properties": {},
            "settings": {},
            "name": "shadingMetric",
            "elements": []
         },
         "bubbleMetrics": {
            "text": null,
            "properties": {},
            "settings": {},
            "name": "bubbleMetrics",
            "elements": [
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
                     "otherProps": {}
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
                  },
                  "isDeleted": false
               }
            ]
         },
         "settings": {},
         "pointOptions": {
            "elements": [
               {
                  "name": "ShipCountry",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                        "functionInfo": {
                           "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                           "name": "Group",
                           "expression": null,
                           "dataType": "Text",
                           "formatDataType": "Text",
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
                     "pointOptionType": "country"
                  },
                  "position": 1,
                  "field": {
                     "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                     "fieldName": "ShipCountry",
                     "fieldNameAlias": "ShipCountry",
                     "dataFieldType": "Text",
                     "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                     "querySourceType": "Table",
                     "sourceAlias": "Orders",
                     "relationshipId": "00000000-0000-0000-0000-000000000000",
                     "visible": true,
                     "calculatedTree": null,
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false
               },
               {
                  "name": "ShipCity",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                        "functionInfo": {
                           "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                           "name": "Group",
                           "expression": null,
                           "dataType": "Text",
                           "formatDataType": "Text",
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
                     "pointOptionType": "city"
                  },
                  "position": 2,
                  "field": {
                     "fieldId": "b0554a37-b744-4db8-b1b0-95b029d8cae2",
                     "fieldName": "ShipCity",
                     "fieldNameAlias": "ShipCity",
                     "dataFieldType": "Text",
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
                  "isDeleted": false
               }
            ],
            "name": "pointOptions"
         }
      }

Update the properties of each field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartElementProperties` for the purpose of each field.

See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for more samples.

Update the properties of the Map in "properties" field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartMapProperties` for the purpose of each field.

Back to the Save step in :ref:`Build a Generic Report <Populate_the_report_parts>`
----------------------------------------------------------------------------------------

.. container:: toggle

   .. container:: header

      Sample full ReportSavingParameter object for Save report API

   .. code-block:: json

      {
         "reportKey": {
            "key": "17905361-f72b-4e2e-8f6d-80847174f902",
            "tenantId": null
         },
         "section": 2,
         "saveAs": false,
         "ignoreCheckChange": false,
         "report": {
            "inaccessible": false,
            "category": {
               "name": null,
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
            "subCategory": {
               "name": null,
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
                     "type": 4,
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
                     "properties": {
                        "reportPartState": {
                           "drilldownInfo": [],
                           "activeSerie": {},
                           "activePointOption": {
                              "label": "ShipCountry",
                              "value": "ShipCountry",
                              "field": {
                                 "reportPartContent": null,
                                 "isDirty": false,
                                 "name": "ShipCountry",
                                 "properties": {
                                    "isDirty": false,
                                    "fieldItemVisible": true,
                                    "dataFormattings": {
                                       "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                       "functionInfo": {
                                          "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                          "name": "Group",
                                          "expression": null,
                                          "dataType": "Text",
                                          "formatDataType": "Text",
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
                                 },
                                 "position": 1,
                                 "field": {
                                    "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                                    "fieldName": "ShipCountry",
                                    "fieldNameAlias": "ShipCountry",
                                    "dataFieldType": "Text",
                                    "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                                    "querySourceType": "Table",
                                    "sourceAlias": "Orders",
                                    "relationshipId": "00000000-0000-0000-0000-000000000000",
                                    "visible": true,
                                    "calculatedTree": null,
                                    "isCalculated": false,
                                    "hasAggregatedFunction": false
                                 },
                                 "isDeleted": false
                              },
                              "pointType": "country",
                              "pointTypeName": "country"
                           },
                           "pointOptionsList": [
                              {
                                 "label": "ShipCountry",
                                 "value": "ShipCountry",
                                 "field": {
                                    "reportPartContent": null,
                                    "isDirty": false,
                                    "name": "ShipCountry",
                                    "properties": {
                                       "isDirty": false,
                                       "fieldItemVisible": true,
                                       "dataFormattings": {
                                          "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                          "functionInfo": {
                                             "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                             "name": "Group",
                                             "expression": null,
                                             "dataType": "Text",
                                             "formatDataType": "Text",
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
                                    },
                                    "position": 1,
                                    "field": {
                                       "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                                       "fieldName": "ShipCountry",
                                       "fieldNameAlias": "ShipCountry",
                                       "dataFieldType": "Text",
                                       "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                                       "querySourceType": "Table",
                                       "sourceAlias": "Orders",
                                       "relationshipId": "00000000-0000-0000-0000-000000000000",
                                       "visible": true,
                                       "calculatedTree": null,
                                       "isCalculated": false,
                                       "hasAggregatedFunction": false
                                    },
                                    "isDeleted": false
                                 },
                                 "pointType": "country",
                                 "pointTypeName": "country"
                              },
                              {
                                 "label": "ShipCity",
                                 "value": "ShipCity",
                                 "field": {
                                    "reportPartContent": null,
                                    "isDirty": false,
                                    "name": "ShipCity",
                                    "properties": {
                                       "isDirty": false,
                                       "fieldItemVisible": true,
                                       "dataFormattings": {
                                          "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                          "functionInfo": {
                                             "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                             "name": "Group",
                                             "expression": null,
                                             "dataType": "Text",
                                             "formatDataType": "Text",
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
                                       "fieldId": "b0554a37-b744-4db8-b1b0-95b029d8cae2",
                                       "fieldName": "ShipCity",
                                       "fieldNameAlias": "ShipCity",
                                       "dataFieldType": "Text",
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
                                    "isDeleted": false
                                 },
                                 "pointType": "city",
                                 "pointTypeName": "city"
                              }
                           ],
                        },
                        "chartType": "World",
                        "continentInfo": {},
                        "countryInfo": {},
                        "stateInfo": {},
                        "commonOptions": {
                           "izHoverLabels": true,
                           "izLegend.visibility": false,
                           "izLegend.horizontalAlign": "izRight",
                           "izLegend.verticalAlign": "izBottom",
                           "izLegend.borderWidth": 0,
                           "izChartStyle": {},
                           "izendaHiddenAllAxis": false
                        },
                        "optionByType": {
                           "izValueLabel": false,
                           "izShowTooltip": true,
                           "izMapLabel": false,
                           "izMapNavigation.enabled": false,
                           "legendSettings": true
                        },
                        "view": {
                           "showLabels": false,
                           "dataRefreshInterval": {
                              "enable": false,
                              "updateInterval": 0,
                              "isAll": true,
                              "latestRecord": 0
                           }
                        }
                     },
                     "shadingMetric": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "name": "shadingMetric",
                        "elements": []
                     },
                     "bubbleMetrics": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "name": "bubbleMetrics",
                        "elements": [
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
                                 "otherProps": {}
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
                              },
                              "isDeleted": false
                           }
                        ]
                     },
                     "settings": {},
                     "pointOptions": {
                        "elements": [
                           {
                              "name": "ShipCountry",
                              "properties": {
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                    "functionInfo": {
                                       "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                       "name": "Group",
                                       "expression": null,
                                       "dataType": "Text",
                                       "formatDataType": "Text",
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
                                 "pointOptionType": "country"
                              },
                              "position": 1,
                              "field": {
                                 "fieldId": "500f4309-beb3-4af2-892b-dcec65bf8604",
                                 "fieldName": "ShipCountry",
                                 "fieldNameAlias": "ShipCountry",
                                 "dataFieldType": "Text",
                                 "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "calculatedTree": null,
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false
                           },
                           {
                              "name": "ShipCity",
                              "properties": {
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                    "functionInfo": {
                                       "id": "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                       "name": "Group",
                                       "expression": null,
                                       "dataType": "Text",
                                       "formatDataType": "Text",
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
                                 "pointOptionType": "city"
                              },
                              "position": 2,
                              "field": {
                                 "fieldId": "b0554a37-b744-4db8-b1b0-95b029d8cae2",
                                 "fieldName": "ShipCity",
                                 "fieldNameAlias": "ShipCity",
                                 "dataFieldType": "Text",
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
                              "isDeleted": false
                           }
                        ],
                        "name": "pointOptions"
                     }
                  },
                  "width": 12,
                  "height": 4,
                  "positionY": 0,
                  "positionX": 0,
                  "title": "Map"
               }
            ],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": true,
               "reportId": "17905361-f72b-4e2e-8f6d-80847174f902",
               "id": "7809bcc1-329e-40c0-ba30-632aae85f107",
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
            "name": "Example Map 8",
            "reportDataSource": [
               {
                  "reportId": "17905361-f72b-4e2e-8f6d-80847174f902",
                  "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": true,
                  "id": "31af528f-219d-453e-ba6d-59d708d345d8",
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
            "categoryId": null,
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
            "id": "17905361-f72b-4e2e-8f6d-80847174f902",
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
