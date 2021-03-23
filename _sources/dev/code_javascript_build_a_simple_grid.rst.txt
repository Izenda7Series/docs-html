=========================================================
Build a simple Grid
=========================================================

Steps:

#. Follow :doc:`code_javascript_build_a_generic_report` until the step to add report parts.
#. Prepare an empty :doc:`/ref/models/ReportPartGrid` object with default properties.
#. For each selected data source fields, populate a :doc:`/ref/models/ReportPartElement` object with default properties.
#. Add the :doc:`/ref/models/ReportPartElement` objects into ``columns.elements`` in :doc:`/ref/models/ReportPartGrid` object.
#. Update the properties of the grid in ``properties`` field per user selection (See :doc:`/ref/models/ReportPartGridProperties`).
#. Back to the steps in :doc:`code_javascript_build_a_generic_report`.

Prepare an empty ReportPartGrid object
----------------------------------------

.. container:: toggle

   .. container:: header

      Empty ReportPartGrid object

   |br|

   *  The highlighted ``columns.elements`` is where the selected data source fields will be added
   *  The highlighted ``properties`` contains the default properties

   .. code-block:: json
      :linenos:
      :emphasize-lines: 4,19

      {
         "type": 3,
         "columns": {
            "elements": [],
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
            "generalInfo": {
               "gridStyle": "Vertical",
               "separatorStyle": "Comma"
            },
            "table": {
               "border": {
                  "top": {},
                  "right": {},
                  "bottom": {},
                  "midVer": {},
                  "left": {},
                  "midHor": {}
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
                  "backgroundColor": "#E4E4E4"
               },
               "alignment": "left",
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
               "pivotColumnsPerExportedPage": "",
               "pageSize": 10
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
         }
      }

.. _Grid_Populate_selected_data_sources_fields:

Populate selected data sources fields
---------------------------------------

#. Get the list of available data sources fields from :ref:`POST_report/availableQuerySourceFields` with this payload:

   .. code-block:: json

      {
         "reportKey": {
            "key": "<the id of the report>"
         }
      }

   The response is an array containing exactly one :doc:`/ref/models/ReportDataSourceCategory` object, with ``querySource`` field containing an array of selected data sources (:doc:`/ref/models/ReportQuerySource` objects), with ``fields`` field containing an array of available data source fields. For example:

   .. code-block:: json

      [
         {
            "id": null,
            "name": "Selected Data Source",
            "querySource": [
               {
                  "id": "af773c7b-878e-461b-9345-27ee6592db1a",
                  "name": "Orders",
                  "originalName": "Orders",
                  "type": "Table",
                  "selected": true,
                  "visible": true,
                  "querySourceCategoryName": "dbo",
                  "connectionName": "test",
                  "isAlias": false,
                  "isDynamic": false,
                  "fields": [
                     {
                        "name": "CustomerID",
                        "remaining items": "have been omitted"
                     },
                     {
                        "name": "OrderID",
                        "remaining items": "have been omitted"
                     }
                  ]
               }
            ]
         }
      ]

#. For each selected data source field (:doc:`/ref/models/QuerySourceField` object), build a corresponding :doc:`/ref/models/ReportPartElement` object

   .. code-block:: json

      {
         "name": "<User-defined Field Name Alias of the selected QuerySourceField>",
         "position": "<position in the list of selected fields>",
         "field": {
            "fieldId": "<id of the selected QuerySourceField>",
            "fieldName": "<name of the selected QuerySourceField>",
            "fieldNameAlias": "User-defined Field Name Alias of the selected QuerySourceField",
            "dataFieldType": "<Izenda data type of the selected QuerySourceField>",
            "querySourceId": "<id of the parent QuerySource>",
            "querySourceType": "<Table, View or Stored Procedure>",
            "sourceAlias": "",
            "relationshipId": null,
            "visible": true,
            "calculatedTree": null,
            "schemaName": "<name of the schema>",
            "querySourceName": "<name of the parent QuerySource>",
            "databaseName": "<name of the connection>",
            "isCalculated": false,
            "hasAggregatedFunction": false
         },
         "properties": {}
      }

   .. list-table::
      :header-rows: 1

      * - :download:`Sample QuerySourceField <included_samples/QuerySourceField_OrderID.json>`
        - :download:`Sample ReportPartElement  <included_samples/ReportPartElement_OrderID.json>`
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 1-2
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 1-2
      * -
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 3
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 37
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 5
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 2
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 6
      * - User entered "OID"
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 7
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 5
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 8
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 9
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 9
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 13
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 10
      * - Alias of the parent QuerySource
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 11
      * - Name of the schema
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 12
      * - Name of the parent QuerySource
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 13
      * - Name of the database
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 14
      * - .. literalinclude:: included_samples/QuerySourceField_OrderID.json
             :lines: 7
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 15
      * -
        - .. literalinclude:: included_samples/ReportPartElement_OrderID.json
              :lines: 16-20

   See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for more samples.

#. Populate a default :doc:`/ref/models/ReportPartElementProperties` for ``properties`` field in each :doc:`/ref/models/ReportPartElement` object

   .. container:: toggle

      .. container:: header

         Default ReportPartElementProperties object

      .. code-block:: json

         {
            "fieldItemVisible": true,
            "dataFormattings": {
               "function": "",
               "functionInfo": {},
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
         }

#. Add the :doc:`/ref/models/ReportPartElement` objects into ``columns.elements`` in :doc:`/ref/models/ReportPartGrid` object.

   .. _Sample_full_ReportPartGrid_object:

   .. container:: toggle

      .. container:: header

         Sample full ReportPartGrid object

      .. code-block:: json

         {
            "type": 3,
            "columns": {
               "elements": [
                  {
                     "name": "OrderID",
                     "position": 1,
                     "field": {
                        "fieldId": "b648344c-526e-4984-bfc3-7be462b800fe",
                        "fieldName": "OrderID",
                        "fieldNameAlias": "OID",
                        "dataFieldType": "Numeric",
                        "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                        "querySourceType": "Table",
                        "sourceAlias": "Orders",
                        "schemaName": "dbo",
                        "querySourceName": "Orders",
                        "databaseName": "test",
                        "visible": true,
                        "relationshipId": null,
                        "calculatedTree": null,
                        "isCalculated": false,
                        "hasAggregatedFunction": false
                     },
                     "properties": {
                        "fieldItemVisible": true,
                        "dataFormattings": {
                           "function": "",
                           "functionInfo": {},
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
                     "isDeleted": false,
                     "isSelected": false,
                     "offset": {}
                  }
               ],
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
               "generalInfo": {
                  "gridStyle": "Vertical",
                  "separatorStyle": "Comma"
               },
               "table": {
                  "border": {
                     "top": {},
                     "right": {},
                     "bottom": {},
                     "midVer": {},
                     "left": {},
                     "midHor": {}
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
                     "backgroundColor": "#E4E4E4"
                  },
                  "alignment": "left",
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
                  "pivotColumnsPerExportedPage": "",
                  "pageSize": 10
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
            }
         }

Update the properties of each field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartElementProperties` for the purpose of each field.

See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for more samples.

Update the properties of the grid in "properties" field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartGridProperties` for the purpose of each field.

Back to the step in :ref:`Build a Generic Report <Populate_the_report_parts>`
------------------------------------------------------------------------------
