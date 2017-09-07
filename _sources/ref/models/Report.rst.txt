


Report
------

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **name** |br|
         string
      -
      -  The name of the report
      -
   *  -  **reportDataSource** |br|
         array of objects
      -
      -  An array of :doc:`ReportDataSource` objects
      -
   *  -  **type** |br|
         integer
      -
      -  The report type

         - 0 = Reports
         - 1 = Templates
      -
   *  -  **previewRecord** |br|
         integer
      -
      -  The number of records to preview
      -
   *  -  **advancedMode** |br|
         boolean
      -
      -  Is the report in advanced mode
      -
   *  -  **allowNulls** |br|
         boolean
      -
      -  Does the report display null values in left join
      -
   *  -  **isDistinct** |br|
         boolean
      -
      -  Does the report allow duplicated data
      -
   *  -  **categoryId** |br|
         string (GUID)
      -  Y
      -  The id of the report category
      -
   *  -  **categoryName** |br|
         string
      -
      -  The name of the report category
      -
   *  -  **subCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the report sub-category
      -
   *  -  **subCategoryName** |br|
         string
      -
      -  The name of the report sub-category
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantName** |br|
         string
      -
      -  The name of the tenant if available
      -
   *  -  **description** |br|
         string
      -
      -  The report description
      -
   *  -  **title** |br|
         string
      -
      -  The report title
      -
   *  -  **lastViewed** |br|
         datetime
      -  Y
      -  The report's last view date and time
      -
   *  -  **owner** |br|
         string
      -
      -  The name of report's owner
      -
   *  -  **ownerId** |br|
         string (GUID)
      -  Y
      -  The id of report's owner
      -
   *  -  **headerContent** |br|
         string
      -
      -  The content of the header in json format
      -
   *  -  **footerContent** |br|
         string
      -
      -  The content of the footer in json format
      -
   *  -  **excludedRelationships** |br|
         string
      -
      -  The deleted relationships, which should not be displayed again
      -
   *  -  **numberOfView** |br|
         integer
      -
      -  The number of view
      -
   *  -  **renderingTime** |br|
         real number
      -
      -  The report rendering time
      -
   *  -  **createdById** |br|
         string (GUID)
      -  Y
      -  Id of user who created this report
      -
   *  -  **modifiedById** |br|
         string (GUID)
      -  Y
      -  Id of user who last modified this report
      -
   *  -  **snapToGrid** |br|
         boolean
      -
      -  Snap to Grid option
      -
   *  -  **usingFields** |br|
         string
      -
      -  The ids of the fields used in report, separated by comma |br|
         .. deprecated:: 2.0.0

      -
   *  -  **hasDeletedObjects** |br|
         boolean
      -
      -  True if using objects in deleted connections
      -
   *  -  **header** |br|
         object
      -
      -  Header content in a dynamic object
      -
   *  -  **footer** |br|
         object
      -
      -  Footer content in a dynamic object
      -
   *  -  **titleDescription** |br|
         object
      -
      -  Title description content in a dynamic object
      -
   *  -  **sourceId** |br|
         string (GUID)
      -  Y
      -  The id of the source report in case this was copied from that report
      -
   *  -  **checked** |br|
         boolean
      -
      -  Is selected for copy in Copy Management
      -
   *  -  **copyDashboard** |br|
         boolean
      -
      -  Whether this is copied because dashboard was copied
      -
   *  -  **exportFormatSetting** |br|
         object
      -
      -  An :doc:`ExportFormatSetting` object
      -
   *  -  **deletable** |br|
         boolean
      -
      -  True if report can be deleted
      -
   *  -  **editable** |br|
         boolean
      -
      -  True if report can be edited
      -
   *  -  **movable** |br|
         boolean
      -
      -  True if report can be moved
      -
   *  -  **copyable** |br|
         boolean
      -
      -  True if report can be copied
      -
   *  -  **accessPriority** |br|
         integer
      -
      -  The access priority
      -
   *  -  **active** |br|
         boolean
      -
      -  True if this is the latest version
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Whether this is a global report
      -
   *  -  **isCheck** |br|
         boolean
      -
      -  True if this is selected in copy workspace
      -

Inherited fields:

.. include:: Entity.rst


.. container:: toggle

   .. container:: header

      **Report Sample**:

   .. code-block:: json

      {
       "name": "FactInternetSales DayOfWeek",
       "type": 0,
       "previewRecord": 10,
       "advancedMode": true,
       "allowNulls": false,
       "isDistinct": false,
       "categoryId": "93de93b9-d5d1-48f1-800d-1db1ffc02614",
       "categoryName": null,
       "subCategoryId": "5d034fc7-0cc8-46b7-beb3-35b22c57827c",
       "subCategoryName": null,
       "tenantId": null,
       "tenantName": null,
       "description": "",
       "title": "",
       "lastViewed": "2016-11-22T09:38:45.18",
       "owner": "John Doe",
       "ownerId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
       "excludedRelationships": "",
       "numberOfView": 1,
       "renderingTime": 1644,
       "createdById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
       "modifiedById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
       "snapToGrid": false,
       "usingFields": "78c99b13-af5d-47b9-9d2a-9fae8bc2b51c,191f91cb-29dc-4dd0-8223-e86180c449fe",
       "hasDeletedObjects": false,
       "header": {
         "visible": false,
         "items": [
           {
             "isDirty": false,
             "type": "image",
             "label": "Image",
             "id": "formatDetails_21",
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
             "id": "formatDetails_22",
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
             "id": "formatDetails_23",
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
             "id": "formatDetails_24",
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
             "id": "formatDetails_25",
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
             "id": "formatDetails_26",
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
             "id": "formatDetails_27",
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
             "id": "formatDetails_28",
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
             "id": "formatDetails_29",
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
             "id": "formatDetails_30",
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
             "id": "formatDetails_31",
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
             "id": "formatDetails_32",
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
             "id": "formatDetails_33",
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
             "id": "formatDetails_34",
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
             "id": "formatDetails_35",
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
             "id": "formatDetails_36",
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
       "id": "45f17b8a-3708-4f36-80ef-9178b7124841",
       "state": 0,
       "deleted": false,
       "inserted": true,
       "version": 2,
       "created": "2016-11-21T08:53:58.94",
       "createdBy": "John Doe",
       "modified": "2016-11-22T09:38:51.837",
       "modifiedBy": "John Doe"
      }
