

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
        "category" : null,
        "subCategory" : null,
        "reportDataSource" : [{
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "querySourceId" : "198465a3-d521-47d4-8e52-bc8638beeae5",
              "id" : "4b99b54a-cd5f-47ed-94c1-31bfe61d9336",
              "state" : 0,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-07-13T08:05:25.603",
              "createdBy" : null,
              "modified" : "2016-07-13T08:05:25.603",
              "modifiedBy" : null
           }
        ],
        "reportRelationship" : [],
        "reportPart" : [{
              "reportPartContent" : {
                 "showDataInOneGroupNextTogether" : false,
                 "labels" : {
                    "text" : null,
                    "properties" : {},
                    "settings" : {},
                    "elements" : [{
                          "name" : "Group (ProductName)",
                          "properties" : {
                             "isDirty" : false,
                             "fieldItemVisible" : true,
                             "dataFormattings" : {
                                "function" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                "functionInfo" : {
                                   "id" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
                                   "name" : "Group",
                                   "expression" : null,
                                   "dataType" : "Text",
                                   "formatDataType" : null,
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
                          "settings" : {},
                          "chartType" : null,
                          "showTotal" : false,
                          "position" : 1,
                          "field" : {
                             "fieldId" : "176cfcd2-aef0-417b-a85b-3b3aa4ecab02",
                             "originalName" : null,
                             "fieldName" : "ProductName",
                             "fieldNameAlias" : "Group (ProductName)",
                             "dataFieldType" : "Text",
                             "querySourceId" : "198465a3-d521-47d4-8e52-bc8638beeae5",
                             "querySourceType" : "Table",
                             "sourceAlias" : "Products",
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
                 "values" : {
                    "text" : null,
                    "properties" : {},
                    "settings" : {},
                    "elements" : [{
                          "name" : "Sum (UnitPrice)",
                          "properties" : {
                             "isDirty" : false,
                             "fieldItemVisible" : true,
                             "dataFormattings" : {
                                "function" : "902a9168-fc01-4a35-92fb-ea67942d099d",
                                "functionInfo" : {
                                   "id" : "902a9168-fc01-4a35-92fb-ea67942d099d",
                                   "name" : "Sum",
                                   "expression" : null,
                                   "dataType" : "Money",
                                   "formatDataType" : "Money",
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
                          "settings" : {},
                          "chartType" : null,
                          "showTotal" : false,
                          "position" : 1,
                          "field" : {
                             "fieldId" : "de9558b7-4f0c-43bc-b8ac-d939057909c5",
                             "originalName" : null,
                             "fieldName" : "UnitPrice",
                             "fieldNameAlias" : "Sum (UnitPrice)",
                             "dataFieldType" : "Money",
                             "querySourceId" : "198465a3-d521-47d4-8e52-bc8638beeae5",
                             "querySourceType" : "Table",
                             "sourceAlias" : "Products",
                             "relationshipId" : "00000000-0000-0000-0000-000000000000",
                             "visible" : true,
                             "filterable" : false,
                             "reportId" : null,
                             "fieldFunctionExpression" : "SUM([UnitPrice])",
                             "expression" : null,
                             "grandTotalExpression" : "",
                             "subTotalExpression" : "",
                             "sort" : "Unsorted",
                             "function" : "Sum",
                             "calculatedTree" : null,
                             "grandTotalTree" : null,
                             "isCalculated" : false
                          }
                       }
                    ]
                 },
                 "valuesLabels" : {
                    "text" : null,
                    "properties" : {},
                    "settings" : {},
                    "elements" : []
                 },
                 "bubbleSize" : {
                    "text" : null,
                    "properties" : {},
                    "settings" : {},
                    "elements" : []
                 },
                 "separators" : {
                    "text" : null,
                    "properties" : {},
                    "settings" : {},
                    "elements" : []
                 },
                 "type" : 0,
                 "properties" : {
                    "chartType" : "Donut",
                    "commonOptions" : {
                       "izHoverLabels" : true,
                       "izDataRefreshInterval" : 0,
                       "izLegend.visibility" : true,
                       "izLegend.horizontalAlign" : "Left",
                       "izLegend.verticalAlign" : "Top"
                    },
                    "optionByType" : {
                       "izUseSeparator" : null,
                       "izInverted" : null,
                       "izStep" : null,
                       "izSpline" : null,
                       "izStacking" : null,
                       "izRange" : null,
                       "izPieChartStyle" : null,
                       "izShowPercentage" : false,
                       "izBottomXpercent" : null
                    },
                    "xAxis" : [{
                          "izLabelOrientation" : null
                       }
                    ],
                    "yAxis" : [{
                          "izLabelOrientation" : null
                       }
                    ],
                    "xThresholdLines" : [],
                    "yThresholdLines" : []
                 },
                 "settings" : {},
                 "title" : {
                    "text" : "Title",
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
                    "text" : "Desc",
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
              },
              "title" : "Chart",
              "positionX" : 0,
              "positionY" : 0,
              "width" : 12,
              "height" : 4,
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "numberOfRecord" : 0,
              "id" : "61f21e6a-a333-4bc1-954a-8b9d8dfd82ee",
              "state" : 0,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-07-13T08:05:25.603",
              "createdBy" : null,
              "modified" : "2016-07-13T08:05:25.603",
              "modifiedBy" : null
           }
        ],
        "reportFilter" : {
           "filterFields" : [],
           "logic" : "",
           "visible" : false,
           "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
           "id" : "dfd1597f-d6cc-4a4e-9de5-97180bf63f2c",
           "state" : 0,
           "inserted" : true,
           "version" : null,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        },
        "calculatedFields" : [],
        "dynamicQuerySourceFields" : [],
        "name" : "TestReport02",
        "type" : 1,
        "previewRecord" : 10,
        "advancedMode" : true,
        "allowNulls" : false,
        "isDistinct" : false,
        "categoryId" : "1c0060df-ebf9-4287-a67a-900b014afc0d",
        "categoryName" : null,
        "subCategoryId" : "8ca0e7c5-b2ef-4ecd-a663-6620a63d1dae",
        "subCategoryName" : null,
        "tenantId" : null,
        "description" : null,
        "title" : null,
        "lastViewed" : null,
        "owner" : null,
        "header" : null,
        "footer" : null,
        "titleDescription" : null,
        "id" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "state" : 0,
        "inserted" : true,
        "version" : 2,
        "created" : "2016-07-13T08:05:25.587",
        "createdBy" : null,
        "modified" : "2016-07-14T03:51:38",
        "modifiedBy" : null
      }
