

=========================================
ReportPartPreviewParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **title** |br|
         string
      -
      -  The report part title
      -
   *  -  **expandedLevel** |br|
         integer
      -
      -  The expanded level
      -
   *  -  **filters** |br|
         array of objects
      -
      - An array of :doc:`FilterItem` objects
      -
   *  -  **reportField** |br|
         object
      -
      - A :doc:`ReportField` object
      -
   *  -  **calculatedField** |br|
         object
      -
      - A :doc:`QuerySourceField` object
      -
   *  -  **paging** |br|
         object
      -
      - A :doc:`PagingInfo` object
      -
   *  -  **loadAll** |br|
         boolean
      -
      - Whether to load all rows for printing
      -
   *  -  **overridingFilterValue** |br|
         object
         
         .. versionadded:: 3.0
      -
      - A dynamic object to store filter values to override |br| |br|
        For example:

        .. code-block:: json

            overridingFilterValue: {
               p1value: "Brazil",
               p2value: "6"
            },
      -


Inherited fields:

.. include:: ReportSavingParameter.rst

.. container:: toggle

   .. container:: header

      **Sample**:

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
