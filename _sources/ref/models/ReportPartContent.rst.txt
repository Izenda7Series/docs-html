

=========================================
ReportPartContent
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **type** |br|
         integer
      -
      -  The type of the report part

         -  0 = Chart
         -  1 = Form
         -  2 = Gauge
         -  3 = Grid
         -  4 = Map
      -
   *  -  **properties** |br|
         object
      -
      -  A dynamic object to keep the properties in Report Part Properties box, can be user-defined
      -
   *  -  **settings** |br|
         object
      -
      -  A dynamic object to keep the properties in Report Part Configuration, can be user-defined
      -
   *  -  **title** |br|
         object
      -
      -  A :doc:`ContentContainer` object
      -
   *  -  **description** |br|
         object
      -
      -  A :doc:`ContentContainer` object
      -
   *  -  **expandedLevel** |br|
         integer
      -
      -  The expand level of the report part
      -
   *  -  **isCrossFiltering** |br|
         boolean
      -
      -  Whether this is selected to apply :term:`cross filtering`
      -
   *  -  **isFormatted** |br|
         boolean
      -
      -  Whether this report part is formatted
      -
   *  -  **selectedMetric** |br|
         string
      -
      -  The selected metric value on Chart/Gauge/Map
      -
   *  -  **vizState** |br|
         object

         .. versionadded:: 3.5.0
      -
      -  A :doc:`VizState` object
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "showDataInOneGroupNextTogether" : false,
         "columns" : {
            "text" : null,
            "properties" : {},
            "settings" : {},
            "elements" : [{
                  "name" : "ShipCountry",
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
                     },
                     "otherProps" : {}
                  },
                  "settings" : {},
                  "chartType" : null,
                  "showTotal" : false,
                  "position" : 1,
                  "field" : {
                     "fieldId" : "d300a6bd-f218-46c8-a262-3b9fa5ee0382",
                     "originalName" : null,
                     "fieldName" : "ShipCountry",
                     "fieldNameAlias" : "ShipCountry",
                     "dataFieldType" : "Text",
                     "querySourceId" : "d609ecdc-2afc-43ce-a0a4-0583ed667c8f",
                     "querySourceType" : "Table",
                     "sourceAlias" : "Orders",
                     "relationshipId" : "00000000-0000-0000-0000-000000000000",
                     "visible" : true,
                     "filterable" : false,
                     "reportId" : null,
                     "fieldFunctionExpression" : "",
                     "expression" : null,
                     "grandTotalExpression" : "",
                     "subTotalExpression" : "",
                     "sort" : "Unsorted",
                     "function" : null,
                     "calculatedTree" : null,
                     "grandTotalTree" : null,
                     "isCalculated" : false
                  }
               }
            ]
         },
         "rows" : {
            "text" : null,
            "properties" : {},
            "settings" : {},
            "elements" : []
         },
         "values" : {
            "text" : null,
            "properties" : {},
            "settings" : {},
            "elements" : []
         },
         "separators" : {
            "text" : null,
            "properties" : {},
            "settings" : {},
            "elements" : [{
                  "name" : "Group (Freight)",
                  "properties" : {
                     "isDirty" : false,
                     "fieldItemVisible" : true,
                     "dataFormattings" : {
                        "function" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                        "functionInfo" : {
                           "id" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                           "name" : "Group",
                           "expression" : null,
                           "dataType" : "Money",
                           "formatDataType" : "Money",
                           "syntax" : null,
                           "expressionSyntax" : null,
                           "isOperator" : false,
                           "extendedProperties" : {}
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
                     },
                     "otherProps" : {}
                  },
                  "settings" : {},
                  "chartType" : null,
                  "showTotal" : false,
                  "position" : 1,
                  "field" : {
                     "fieldId" : "fa47d01d-e055-43ad-b1ec-891b1685b9fe",
                     "originalName" : null,
                     "fieldName" : "Freight",
                     "fieldNameAlias" : "Group (Freight)",
                     "dataFieldType" : "Money",
                     "querySourceId" : "d609ecdc-2afc-43ce-a0a4-0583ed667c8f",
                     "querySourceType" : "Table",
                     "sourceAlias" : "Orders",
                     "relationshipId" : "00000000-0000-0000-0000-000000000000",
                     "visible" : true,
                     "filterable" : false,
                     "reportId" : null,
                     "fieldFunctionExpression" : "",
                     "expression" : null,
                     "grandTotalExpression" : "",
                     "subTotalExpression" : "",
                     "sort" : "Unsorted",
                     "function" : "Group",
                     "calculatedTree" : null,
                     "grandTotalTree" : null,
                     "isCalculated" : false
                  }
               }
            ]
         },
         "type" : 3,
         "properties" : {
            "isDirty" : false,
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
         },
         "expandedLevel" : -1
      }
