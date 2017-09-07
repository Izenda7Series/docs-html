=========================================================
Build a Generic Report
=========================================================

#. Save as draft the report with name, category and selected data sources

   #. Prepare an empty :doc:`/ref/models/ReportDefinition` object.
   #. Populate report name and categories.
   #. Populate selected data sources.
   #. Prepare a :doc:`/ref/models/ReportSavingParameter` object as API input.
   #. Call :ref:`Save report as draft <POST_report/draft>` API, then receive back the :doc:`/ref/models/ReportSavingResult` object.
#. Populate the draft with report parts

   #. Extract the ``report`` field from the :doc:`/ref/models/ReportSavingResult` object. This is a :doc:`/ref/models/ReportDefinition` object which has been assigned a report id.
   #. Populate the report parts:

      *  :doc:`code_javascript_build_a_simple_grid`
      *  :doc:`code_javascript_build_a_simple_chart`
      *  :doc:`code_javascript_build_a_simple_gauge`
      *  :doc:`code_javascript_build_a_simple_map`
      *  :doc:`code_javascript_build_a_simple_form`
#. Save the report

   #. Prepare a :doc:`/ref/models/ReportSavingParameter` object as API input.
   #. Call :ref:`Save report <POST_report>` API.

Prepare an Empty Report Object
------------------------------

.. container:: toggle

   .. container:: header

      Empty ReportDefinition object:

   |br|
   
   *  The highlighted ``name``  is where the report name will be inserted
   *  The highlighted ``categoryId``, ``category``, ``subCategoryId`` and ``subCategory``  is where the categories and sub-categories will be updated
   *  The highlighted ``reportDataSource``  is where the selected data source will be added

   .. code-block:: json
      :linenos:
      :emphasize-lines: 2,8-21,22

      {
         "name": "",
         "type": 0,
         "previewRecord": 10,
         "advancedMode": true,
         "allowNulls": false,
         "isDistinct": false,
         "categoryId": null,
         "category": {
            "id": null,
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
         "reportDataSource": [],
         "reportRelationship": [],
         "reportFilter": {
            "logic": "",
            "visible": true,
            "filterFields": [],
            "id": null,
            "reportId": null
         },
         "reportPart": [],
         "header": {
            "visible": false,
            "items": [
               {
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
         "version": 0,
         "schedules": [],
         "ownerId": "",
         "accesses": [],
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
               }
            ]
         },
         "createdById": null,
         "dynamicQuerySourceFields": [],
         "snapToGrid": false,
         "excludedRelationships": null
      }

Populate Report Name and Categories
------------------------------------

Populate the fields:

*  ``name`` with the actual report name
*  ``category`` and ``subCategory`` with the actual categories |br|
   Get the list of categories from :ref:`GET_report/allCategories/{type}/(tenant_id)`


.. container:: toggle

   .. container:: header

      Sample populated ReportDefinition object:

   .. code-block:: json
      :emphasize-lines: 2,8-14
      :linenos:

      {
         "name": "Example Report Name",
         "type": 0,
         "previewRecord": 10,
         "advancedMode": true,
         "allowNulls": false,
         "isDistinct": false,
         "categoryId": "0ecf1821-dc37-43dd-8b4c-654961b37038",
         "category": {
            "id": "0ecf1821-dc37-43dd-8b4c-654961b37038",
            "name": "TestCategory",
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
         "reportDataSource": [],
         "reportRelationship": [],
         "reportFilter": {
            "logic": "",
            "visible": true,
            "filterFields": [],
            "id": null,
            "reportId": null
         },
         "reportPart": [],
         "remaining_fields": "are omitted"
      }

Populate selected data sources
------------------------------

#. Get the list of available data sources grouped by data source categories from :ref:`POST_report/loadDataSourceCategory` with this payload:

   .. code-block:: json

      {
         "tenantId": null,
         "reportKey": {
            "key": null
         }
      }

#. For each selected data source (:doc:`/ref/models/ReportQuerySource` object), build a corresponding :doc:`/ref/models/ReportDataSource` object

   .. code-block:: json

      {
         "querySourceId": "<id of the selected ReportQuerySource>",
         "querySourceName": "<name of the selected ReportQuerySource>",
         "aliasId": "<querySourceId>_<querySourceName>",
         "selected": true,
         "categoryId": "00000000-0000-0000-0000-000000000000",
         "primaryFields": ["<populated by an array of only primary key fields>"]
      }

   .. list-table::
      :header-rows: 1

      * - :download:`Sample ReportQuerySource <included_samples/ReportQuerySource_Orders.json>`
        - :download:`Sample ReportDataSource  <included_samples/ReportDataSource_Orders.json>`
      * - .. literalinclude:: included_samples/ReportQuerySource_Orders.json
             :lines: 1-3
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 1-4
      * - .. literalinclude:: included_samples/ReportQuerySource_Orders.json
             :lines: 6
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 5
      * -
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 6
      * - .. literalinclude:: included_samples/ReportQuerySource_Orders.json
             :lines: 12
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 7
      * - .. literalinclude:: included_samples/ReportQuerySource_Orders.json
             :lines: 197-242
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 8-53
      * - .. literalinclude:: included_samples/ReportQuerySource_Orders.json
             :lines: 657-
        - .. literalinclude:: included_samples/ReportDataSource_Orders.json
              :lines: 54-

#. Populate the field ``reportDataSource`` with the array of :doc:`/ref/models/ReportDataSource` objects. 

.. container:: toggle

   .. container:: header

       Populated ReportDefinition object:

   .. code-block:: json
      :linenos:
      :emphasize-lines: 22-78

      {
         "name": "Example Report Name",
         "type": 0,
         "previewRecord": 10,
         "advancedMode": true,
         "allowNulls": false,
         "isDistinct": false,
         "categoryId": "0ecf1821-dc37-43dd-8b4c-654961b37038",
         "category": {
            "id": "0ecf1821-dc37-43dd-8b4c-654961b37038",
            "name": "TestCategory",
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
         "reportDataSource": [
            {
               "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
               "querySourceName": "Orders",
               "aliasId": "af773c7b-878e-461b-9345-27ee6592db1a_Orders",
               "selected": true,
               "categoryId": "00000000-0000-0000-0000-000000000000",
               "primaryFields": [
                  {
                     "name": "OrderID",
                     "alias": "",
                     "dataType": "int",
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
                     "fullName": null,
                     "calculatedTree": null,
                     "reportId": null,
                     "originalName": "OrderID",
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
                     "id": "b648344c-526e-4984-bfc3-7be462b800fe",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": null,
                     "created": null,
                     "createdBy": null,
                     "modified": "0001-01-01T00:00:00.0000000+07:00",
                     "modifiedBy": null
                  }
               ]
            }
         ],
         "reportRelationship": [],
         "reportFilter": {
            "logic": "",
            "visible": true,
            "filterFields": [],
            "id": null,
            "reportId": null
         },
         "reportPart": [],
         "remaining_fields": "are omitted"
      }

Call Save report as draft API
------------------------------

1. Prepare the :doc:`/ref/models/ReportSavingParameter` object

.. container:: toggle

   .. container:: header

      Sample object:

   |br|
   
   The highlighted ``report``  is where the ReportDefinition object will be inserted

   .. code-block:: json
      :linenos:
      :emphasize-lines: 10

      {
         "reportKey": {
            "key": null,
            "modified": null,
            "tenantId": null
         },
         "section": 0,
         "saveAs": false,
         "ignoreCheckChange": false,
         "report": {},
         "expandedLevel": 0
      }

2. Populate the ReportSavingParameter object with the ReportDefinition then call the :ref:`Save report as draft <POST_report/draft>` API
3. Receive back the :doc:`/ref/models/ReportSavingResult` object

.. container:: toggle

   .. container:: header

      Sample object

   |br|
   ReportSavingResult object with the **success** field true and report id assigned in ``reportKey.key`` and **report** field populated:

   .. code-block:: json
      :linenos:
      :emphasize-lines: 3,574

      {
         "reportKey": {
            "key": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
            "tenantId": null
         },
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
               "id": "0ecf1821-dc37-43dd-8b4c-654961b37038",
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
            "reportPart": [],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": true,
               "reportId": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
               "id": "96bb6406-621d-4375-8cef-1ae9c31c5ac8",
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
            "name": "Example Report Name",
            "reportDataSource": [
               {
                  "reportId": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
                  "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": true,
                  "id": "3067c607-e143-47ed-8ab5-b6c3ad918f75",
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
            "categoryId": "0ecf1821-dc37-43dd-8b4c-654961b37038",
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
            "id": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
            "state": 1,
            "deleted": false,
            "inserted": false,
            "version": 0,
            "created": null,
            "createdBy": "John Doe",
            "modified": null,
            "modifiedBy": "John Doe"
         },
         "success": true,
         "messages": null,
         "data": null
      }

.. _Populate_the_report_parts:

Populate the report parts
-------------------------------------

#. Extract the populated ReportDefinition from ``report`` field.
#. Prepare the report part objects:

   *  :doc:`code_javascript_build_a_simple_grid`
   *  :doc:`code_javascript_build_a_simple_chart`
   *  :doc:`code_javascript_build_a_simple_gauge`
   *  :doc:`code_javascript_build_a_simple_map`
   *  :doc:`code_javascript_build_a_simple_form`
#. For each report part object, build a corresponding :doc:`/ref/models/ReportPartDefinition` object

   *  Highlighted ``reportPartContent`` is to be updated by the report part object 
   *  Highlighted ``title`` field is to be updated by the user-selected title |br|

   .. code-block:: json
      :linenos:
      :emphasize-lines: 2,7

      {
         "reportPartContent": {},
         "width": 12,
         "height": 4,
         "positionY": 0,
         "positionX": 0,
         "title": "Grid"
      }

#. Update the ``reportPart`` field of the extracted ReportDefinition  with the array of ReportPartDefinition objects. (example in the step below)

Call Save report API
------------------------------

1. Prepare the :doc:`/ref/models/ReportSavingParameter` object and call :ref:`Save report <POST_report>` API similarly to `Call Save report as draft API`_ step.

.. container:: toggle

   .. container:: header

      ReportSavingParameter object

   |br|

   *  ``reportKey.key`` filled with the assigned id
   *  ``section`` = 2 (Fields) to save the report parts section only
   *  ``report`` extracted from `Call Save report as draft API`_ step
   *  ``report.reportPart`` populated with the sample grid in :ref:`Build a simple Grid <Sample_full_ReportPartGrid_object>` |br|

   .. code-block:: json
      :linenos:
      :emphasize-lines: 3, 7, 10, 57

      {
         "reportKey": {
            "key": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
            "modified": null,
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
               "id": "0ecf1821-dc37-43dd-8b4c-654961b37038",
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
                  },
                  "width": 0,
                  "height": 0,
                  "positionY": 0,
                  "positionX": 0,
                  "title": "Grid"
               }
            ],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": true,
               "reportId": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
               "id": "96bb6406-621d-4375-8cef-1ae9c31c5ac8",
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
            "name": "Example Report Name",
            "reportDataSource": [
               {
                  "reportId": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
                  "querySourceId": "af773c7b-878e-461b-9345-27ee6592db1a",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": true,
                  "id": "3067c607-e143-47ed-8ab5-b6c3ad918f75",
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
            "categoryId": "0ecf1821-dc37-43dd-8b4c-654961b37038",
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
            "id": "796c20b6-d42e-4a46-b143-6d16eecc78ac",
            "state": 1,
            "deleted": false,
            "inserted": false,
            "version": 0,
            "created": null,
            "createdBy": "John Doe",
            "modified": null,
            "modifiedBy": "John Doe"
         },
         "expandedLevel": 0
      }

2. Receive back the :doc:`/ref/models/ReportSavingResult` object and check that ``success`` field is true.
