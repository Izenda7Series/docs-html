=========================================================
Build a simple Form
=========================================================

Steps:

#. Follow :doc:`code_javascript_build_a_generic_report` until the step to add report parts.
#. Prepare an empty :doc:`/ref/models/ReportPartForm` object with default properties.
#. For each selected data source fields, populate a :doc:`/ref/models/ReportPartElement` object with default properties.
#. Add the :doc:`/ref/models/ReportPartElement` objects into ``columns.elements`` in :doc:`/ref/models/ReportPartForm` object.
#. Update the properties of the map in ``properties`` field per user selection (See :doc:`/ref/models/ReportPartFormProperties`).
#. Back to the steps in :doc:`code_javascript_build_a_generic_report`.

Prepare an empty ReportPartForm object
----------------------------------------

.. container:: toggle

   .. container:: header

      Empty ReportPartForm object

   |br|

   *  The highlighted ``properties`` contains the default properties
   *  The highlighted ``columns.elements`` contains the selected data source fields

   .. code-block:: json
      :linenos:
      :emphasize-lines: 2,71

      {
         "properties": {
            "format": {
               "heading": {
                  "h1": false,
                  "h2": false,
                  "h3": false,
                  "h4": false,
                  "h5": false,
                  "h6": false
               },
               "block": {
                  "p": true,
                  "blockquote": false,
                  "div": true,
                  "pre": false
               },
               "font": {
                  "bold": false,
                  "italic": false,
                  "underline": false,
                  "strikethrough": false,
                  "superscript": false,
                  "subscript": false,
                  "code": false,
                  "fontFamily": "Roboto",
                  "fontSize": 14,
                  "textColor": "#000",
                  "backgroundColor": "#fff"
               },
               "alignment": {
                  "alignleft": false,
                  "aligncenter": false,
                  "alignright": false,
                  "alignjustify": false
               },
               "list": {
                  "bullet": "",
                  "numbered": ""
               }
            },
            "pasteAsText": false,
            "highlightCode": true,
            "wrapText": true,
            "mceDirectionRTL": false,
            "mceDirectionLTR": false,
            "mceVisualChars": false,
            "mceToggleVisualAid": true,
            "usePagination": true,
            "pageSize": 10,
            "pageBreakAfterEachEntry": false,
            "dataRefreshInterval": {
               "enable": false,
               "updateInterval": 0,
               "isAll": true,
               "latestRecord": 0
            }
         },
         "reportPartFormRepeater": {},
         "reportPartFormEmbeddedReport": {},
         "reportPartFormSmartTag": {},
         "reportPartFormField": {},
         "formState": {},
         "htmlContent": "",
         "dataTree": null,
         "type": 1,
         "columns": {
            "text": null,
            "properties": {},
            "settings": {},
            "elements": [],
            "name": "columns"
         },
         "selectedFieldElement": {},
         "activeTabKey": "",
         "isSelectedCell": false,
         "isActiveForEdit": false,
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

Populate selected data sources fields
---------------------------------------

#. Refer to the :ref:`similar step in Building a Grid guide <Grid_Populate_selected_data_sources_fields>` to:

   #. Get the list of available data sources fields from :ref:`POST_report/availableQuerySourceFields`
   #. Build a corresponding ReportPartElement object for each selected data source field
   #. Populate a default ReportPartElementProperties for ``properties`` field in each ReportPartElement object

   See :doc:`code_javascript_sample_properties_for_a_reportpartelement` for some samples.

#. Add the :doc:`/ref/models/ReportPartElement` objects into ``columns.elements`` in :doc:`/ref/models/ReportPartForm` object.
#. Build the HTML to display selected data source fields in ``htmlContent``. |br|

   .. note::

      The double quotes must be escaped before adding to json, e.g. "htmlContent": "<div><field class=\ **\\"**\ field-wrapper\ **\\"**\  ..."

   .. code-block:: html

      <div>
          <custom-HTML-tags...>
          <field class="field-wrapper" field-name="[connection].[schema].[table].[field 1]">
              <field-prop key="subTotalFieldDataType" value="Izenda data type for sub total calculation"></field-prop>
              <field-prop key="grandTotalFieldDataType" value="Izenda data type for grand total calculation"></field-prop>
              <field-prop key="fieldId" value="id of field 1"></field-prop>
              <field-prop key="dataFieldType" value="Izenda data type"></field-prop>
              <field-prop key="querySourceId" value="id of parent query source of field 1"></field-prop>
              Display text in Report Designer for field 1
          </field>
          </custom-HTML-tags...>
      </div>

   The whole ``<field>..</field>`` tag will be replaced by the value of selected data source field in Report Viewer.

.. _Sample_full_ReportPartForm_object:

.. container:: toggle

   .. container:: header

      Sample full ReportPartForm object

   |br|

   *  ``htmlContent`` displays this line: Order #[OrderID] for Customer# [CustomerID] by Employee# [EmployeeID]
   *  The double quotes in ``htmlContent`` have been escaped

   .. code-block:: json
      :emphasize-lines: 64

      {
         "properties": {
            "format": {
               "heading": {
                  "h1": false,
                  "h2": false,
                  "h3": false,
                  "h4": false,
                  "h5": false,
                  "h6": false
               },
               "block": {
                  "p": true,
                  "blockquote": false,
                  "div": true,
                  "pre": false
               },
               "font": {
                  "bold": false,
                  "italic": false,
                  "underline": false,
                  "strikethrough": false,
                  "superscript": false,
                  "subscript": false,
                  "code": false,
                  "fontFamily": "Roboto",
                  "fontSize": 14,
                  "textColor": "#000",
                  "backgroundColor": "#fff"
               },
               "alignment": {
                  "alignleft": false,
                  "aligncenter": false,
                  "alignright": false,
                  "alignjustify": false
               },
               "list": {
                  "bullet": "",
                  "numbered": ""
               }
            },
            "pasteAsText": false,
            "highlightCode": true,
            "wrapText": true,
            "mceDirectionRTL": false,
            "mceDirectionLTR": false,
            "mceVisualChars": false,
            "mceToggleVisualAid": true,
            "usePagination": true,
            "pageSize": 10,
            "pageBreakAfterEachEntry": false,
            "dataRefreshInterval": {
               "enable": false,
               "updateInterval": 0,
               "isAll": true,
               "latestRecord": 0
            }
         },
         "reportPartFormRepeater": {},
         "reportPartFormEmbeddedReport": {},
         "reportPartFormSmartTag": {},
         "reportPartFormField": {},
         "formState": {},
         "htmlContent": "<div>Order #<field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[OrderID]\"><field-prop key=\"subTotalFieldDataType\" value=\"Numeric\"></field-prop><field-prop key=\"grandTotalFieldDataType\" value=\"Numeric\"></field-prop><field-prop key=\"fieldId\" value=\"07ed1f4c-f30d-4759-bfc5-0e4636d446cd\"></field-prop><field-prop key=\"dataFieldType\" value=\"Numeric\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop>OrderID<span class=\"icon-cancel\"></span></field> for Customer# <field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[CustomerID]\"><field-prop key=\"fieldId\" value=\"ab4e3871-76ba-4604-8a8d-97fbfbca7144\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop><field-prop key=\"dataFieldType\" value=\"Text\"></field-prop>CustomerID<span class=\"icon-cancel\"></span></field> by Employee#&nbsp;<field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[EmployeeID]\"><field-prop key=\"fieldId\" value=\"2bc3a102-6621-4713-a167-3579b664dd3e\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop><field-prop key=\"dataFieldType\" value=\"Numeric\"></field-prop>EmployeeID<span class=\"icon-cancel\"></span></field></div>",
         "dataTree": null,
         "type": 1,
         "columns": {
            "text": null,
            "properties": {},
            "settings": {},
            "elements": [
               {
                  "name": "OrderID",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "",
                        "functionInfo": {
                           "id": null
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
                     "otherProps": {
                        "hasRepeaterPart": false
                     }
                  },
                  "position": 1,
                  "field": {
                     "fieldId": "07ed1f4c-f30d-4759-bfc5-0e4636d446cd",
                     "fieldName": "OrderID",
                     "fieldNameAlias": "OrderID",
                     "dataFieldType": "Numeric",
                     "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                     "querySourceType": "Table",
                     "sourceAlias": "Orders",
                     "relationshipId": "00000000-0000-0000-0000-000000000000",
                     "visible": true,
                     "calculatedTree": null,
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false,
                  "isSelected": false
               },
               {
                  "name": "CustomerID",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "",
                        "functionInfo": {
                           "id": null
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
                     "otherProps": {
                        "hasRepeaterPart": false
                     }
                  },
                  "position": 2,
                  "field": {
                     "fieldId": "ab4e3871-76ba-4604-8a8d-97fbfbca7144",
                     "fieldName": "CustomerID",
                     "fieldNameAlias": "CustomerID",
                     "dataFieldType": "Text",
                     "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                     "querySourceType": "Table",
                     "sourceAlias": "Orders",
                     "relationshipId": "00000000-0000-0000-0000-000000000000",
                     "visible": true,
                     "calculatedTree": null,
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false,
                  "isSelected": false
               },
               {
                  "name": "EmployeeID",
                  "properties": {
                     "fieldItemVisible": true,
                     "dataFormattings": {
                        "function": "",
                        "functionInfo": {
                           "id": null
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
                     "otherProps": {
                        "hasRepeaterPart": false
                     }
                  },
                  "position": 3,
                  "field": {
                     "fieldId": "2bc3a102-6621-4713-a167-3579b664dd3e",
                     "fieldName": "EmployeeID",
                     "fieldNameAlias": "EmployeeID",
                     "dataFieldType": "Numeric",
                     "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                     "querySourceType": "Table",
                     "sourceAlias": "Orders",
                     "relationshipId": "00000000-0000-0000-0000-000000000000",
                     "visible": true,
                     "calculatedTree": null,
                     "isCalculated": false,
                     "hasAggregatedFunction": false
                  },
                  "isDeleted": false,
                  "isSelected": false
               }
            ],
            "name": "columns"
         },
         "selectedFieldElement": {},
         "activeTabKey": "",
         "isSelectedCell": false,
         "isActiveForEdit": false,
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

Update the properties of the Form in "properties" field per user selection
------------------------------------------------------------------------------

Please see :doc:`/ref/models/ReportPartFormProperties` for the purpose of each field.

Back to the Save step in :ref:`Build a Generic Report <Populate_the_report_parts>`
----------------------------------------------------------------------------------------

.. container:: toggle

   .. container:: header

      Sample full ReportSavingParameter object for Save report API

   .. code-block:: json

      {
         "reportKey": {
            "key": "e22406a0-4f6d-4077-bac2-3877b7233986",
            "tenantId": null
         },
         "section": 2,
         "saveAs": false,
         "ignoreCheckChange": false,
         "report": {
            "inaccessible": false,
            "category": {
               "name": "",
               "type": 1,
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
               "name": "",
               "type": 1,
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
                     "properties": {
                        "format": {
                           "heading": {
                              "h1": false,
                              "h2": false,
                              "h3": false,
                              "h4": false,
                              "h5": false,
                              "h6": false
                           },
                           "block": {
                              "p": true,
                              "blockquote": false,
                              "div": true,
                              "pre": false
                           },
                           "font": {
                              "bold": false,
                              "italic": false,
                              "underline": false,
                              "strikethrough": false,
                              "superscript": false,
                              "subscript": false,
                              "code": false,
                              "fontFamily": "Roboto",
                              "fontSize": 14,
                              "textColor": "#000",
                              "backgroundColor": "#fff"
                           },
                           "alignment": {
                              "alignleft": false,
                              "aligncenter": false,
                              "alignright": false,
                              "alignjustify": false
                           },
                           "list": {
                              "bullet": "",
                              "numbered": ""
                           }
                        },
                        "pasteAsText": false,
                        "highlightCode": true,
                        "wrapText": true,
                        "mceDirectionRTL": false,
                        "mceDirectionLTR": false,
                        "mceVisualChars": false,
                        "mceToggleVisualAid": true,
                        "usePagination": true,
                        "pageSize": 10,
                        "pageBreakAfterEachEntry": false,
                        "dataRefreshInterval": {
                           "enable": false,
                           "updateInterval": 0,
                           "isAll": true,
                           "latestRecord": 0
                        }
                     },
                     "reportPartFormRepeater": {},
                     "reportPartFormEmbeddedReport": {},
                     "reportPartFormSmartTag": {},
                     "reportPartFormField": {},
                     "formState": {},
                     "htmlContent": "<div>Order #<field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[OrderID]\"><field-prop key=\"subTotalFieldDataType\" value=\"Numeric\"></field-prop><field-prop key=\"grandTotalFieldDataType\" value=\"Numeric\"></field-prop><field-prop key=\"fieldId\" value=\"07ed1f4c-f30d-4759-bfc5-0e4636d446cd\"></field-prop><field-prop key=\"dataFieldType\" value=\"Numeric\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop>OrderID<span class=\"icon-cancel\"></span></field> for Customer# <field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[CustomerID]\"><field-prop key=\"fieldId\" value=\"ab4e3871-76ba-4604-8a8d-97fbfbca7144\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop><field-prop key=\"dataFieldType\" value=\"Text\"></field-prop>CustomerID<span class=\"icon-cancel\"></span></field> by Employee#&nbsp;<field class=\"field-wrapper\" field-name=\"[Northwind].[dbo].[Orders].[EmployeeID]\"><field-prop key=\"fieldId\" value=\"2bc3a102-6621-4713-a167-3579b664dd3e\"></field-prop><field-prop key=\"querySourceId\" value=\"f4ae63fc-4c10-4672-9cd2-4a9d40434a4c\"></field-prop><field-prop key=\"dataFieldType\" value=\"Numeric\"></field-prop>EmployeeID<span class=\"icon-cancel\"></span></field></div>",
                     "dataTree": null,
                     "type": 1,
                     "columns": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "elements": [
                           {
                              "name": "OrderID",
                              "properties": {
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "",
                                    "functionInfo": {
                                       "id": null
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
                                 "otherProps": {
                                    "hasRepeaterPart": false
                                 }
                              },
                              "position": 1,
                              "field": {
                                 "fieldId": "07ed1f4c-f30d-4759-bfc5-0e4636d446cd",
                                 "fieldName": "OrderID",
                                 "fieldNameAlias": "OrderID",
                                 "dataFieldType": "Numeric",
                                 "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "calculatedTree": null,
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false
                           },
                           {
                              "name": "CustomerID",
                              "properties": {
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "",
                                    "functionInfo": {
                                       "id": null
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
                                 "otherProps": {
                                    "hasRepeaterPart": false
                                 }
                              },
                              "position": 2,
                              "field": {
                                 "fieldId": "ab4e3871-76ba-4604-8a8d-97fbfbca7144",
                                 "fieldName": "CustomerID",
                                 "fieldNameAlias": "CustomerID",
                                 "dataFieldType": "Text",
                                 "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "calculatedTree": null,
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false
                           },
                           {
                              "name": "EmployeeID",
                              "properties": {
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "",
                                    "functionInfo": {
                                       "id": null
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
                                 "otherProps": {
                                    "hasRepeaterPart": false
                                 }
                              },
                              "position": 3,
                              "field": {
                                 "fieldId": "2bc3a102-6621-4713-a167-3579b664dd3e",
                                 "fieldName": "EmployeeID",
                                 "fieldNameAlias": "EmployeeID",
                                 "dataFieldType": "Numeric",
                                 "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "calculatedTree": null,
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false
                              },
                              "isDeleted": false,
                              "isSelected": false
                           }
                        ],
                        "name": "columns"
                     },
                     "selectedFieldElement": {},
                     "activeTabKey": "",
                     "isSelectedCell": false,
                     "isActiveForEdit": false,
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
                  },
                  "width": 12,
                  "height": 4,
                  "positionY": 0,
                  "positionX": 0,
                  "title": "Form"
               }
            ],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": false,
               "reportId": "e22406a0-4f6d-4077-bac2-3877b7233986",
               "id": "3920d594-f813-4b90-995a-42dbe9e4858a",
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
            "name": "Example Form 2",
            "reportDataSource": [
               {
                  "reportId": "e22406a0-4f6d-4077-bac2-3877b7233986",
                  "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": true,
                  "id": "3f8129f1-7ebb-43f8-b7f7-100d1e58cf8e",
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
            "ownerId": "d928e941-19ef-4382-ba60-7238cb555631",
            "excludedRelationships": null,
            "numberOfView": 0,
            "renderingTime": 0,
            "createdById": "d928e941-19ef-4382-ba60-7238cb555631",
            "modifiedById": "d928e941-19ef-4382-ba60-7238cb555631",
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
                     "id": "formatDetails_209",
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
                     "id": "formatDetails_210",
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
                     "id": "formatDetails_211",
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
                     "id": "formatDetails_212",
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
                     "id": "formatDetails_213",
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
                     "id": "formatDetails_214",
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
                     "id": "formatDetails_215",
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
                     "id": "formatDetails_216",
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
                     "id": "formatDetails_217",
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
                     "id": "formatDetails_218",
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
                     "id": "formatDetails_219",
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
                     "id": "formatDetails_220",
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
                     "id": "formatDetails_221",
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
                     "id": "formatDetails_222",
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
                     "id": "formatDetails_223",
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
                     "id": "formatDetails_224",
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
            "id": "e22406a0-4f6d-4077-bac2-3877b7233986",
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
