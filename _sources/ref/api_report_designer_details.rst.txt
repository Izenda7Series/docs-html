

============================
Report Designer Details APIs
============================

The **Report Designer** page allows user to

-  create a report
-  select report data sources
-  create report filters
-  design report layout
-  set up report schedule

This page documents the APIs related to report details.

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 45 30
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET report/category/{type}/(tenant\_id)`_
     - Returns an array of allowed saving categories for Report (type=0), Template (type=1) or Dashboard (type=2).
     - \- Report Designer > Save (As) > Category |br|
       \- Report List > Expand a report > Copy/Move > Category
   * - `POST report/allowedSavingCategories`_
     - Returns an array of allowed saving categories for Report, with total number of items.
     - To be updated
   * - `POST report/allowedSavingSubCategories`_
     - Returns an array of allowed saving sub-categories for Report, with total number of items.
     - To be updated
   * - `GET report/subcategory/{parent\_category\_id}`_
     - Returns an array of allowed saving sub-categories under the Report category specified by parent_category_id.
     - \- Report Designer > Save (As) > Category > Sub-category |br|
       \- Report List > Expand a report > Copy/Move > Category > Sub-category
   * - `GET report/allCategories/{type}/(tenant\_id)`_
     - Returns the list of categories by type (Reports/Templates/Dashboards) in parent-child hierarchy.
     - Not used
   * - `POST report/allCategories`_
     - Returns the list of categories in parent-child hierarchy, with total number of items.
     - Report List
   * - `POST report/category`_
     - Renames a report category.
     - Report List > Rename icon > Update change
   * - `DELETE report/category/{report\_category\_id}`_
     - Removes the report category specified by report_category_id.
     - Not used
   * - `POST report/validateCategoryName`_
     - Validates a report category name.
     - To be updated
   * - `GET report/reportByProperty/{report\_id}/{property}`_
     - Returns a report section.
     - Dashboard Designer
   * - `POST report`_
     - Saves a report.
     - Report Designer > Save (As)
   * - `POST report/draft`_
     - Saves a report as draft.
     - Report Designer, when switching between Data Source, Fields, Format.. sections - to store unsaved changes
   * - `POST report/cancel`_
     - Deletes temporary data of a report.
     - Report Designer > Cancel
   * - `POST report/loadReport`_
     - Returns a report's details. |br|
       Deprecated, please use `POST report/loadForEdit`_ instead.
     - Not used
   * - `POST report/loadForEdit`_
     - Returns an object with report key and report's data.
     - \- Report List > Expand a report > Edit > Design |br|
       \- Report Viewer > Edit > Design
   * - `GET report/(tenant\_id)`_
     - Returns all report categories together with the reports inside.
     - Not used
   * - `POST report/validateReportName`_
     - Validates that a report name is unique and not empty.
     - \- Report Designer > Save (As) > OK |br|
       \- Report Designer > Rename icon > Update change |br|
       \- Report List > Expand a report > Rename icon > Update change |br|
       \- Report Viewer > Rename icon > Update change
   * - `POST report/validate`_
     - Validates that a report name is unique and its filter and relationships are valid.
     - Report Designer > Update Result
   * - `POST report/search`_
     - .. deprecated:: 2.0.0
          superseded by `POST report/search2`_ |br| |br|

       Searches for reports.
     - Not used
   * - `POST report/search2`_
     - Searches for reports, with total number of items.
     - Not used, replaced by :ref:`POST_report/list2`
   * - `POST report/advancedSearch`_
     - Searches for reports with advanced options.
     - Not used, replaced by :ref:`POST_report/list2`
   * - `GET report/reportMode`_
     - Returns the report mode.
     - Report Designer
   * - `POST report/reportMode/{value}`_
     - Sets the report mode to Simple or Advanced.
     - To be updated
   * - `POST report/detectReportChange`_
     - Verifies that all report details are up to date, without physical changes, and valid.
     - Report Designer, when switching between Data Source, Fields, Format.. sections
   * - `POST report/function/{function\_mode}/{data\_type}/(tenant\_id)`_
     - Returns a list of report functions filtered by mode (field, sub-total, grand-total), data type, tenant_id, and optionally filtered by connections of the selected query source ids in payload.

       .. versionchanged:: 1.25
          Changed from GET to POST
     - Report Designer, when adding a data source field to a report part
   * - `GET report/allReports/(tenant\_id)`_
     - Returns a list of all reports filtered by tenant_id if provided.
     - To be updated
   * - `POST report/detectSchemaChange`_
     - Verifies that all report filter fields are without changes.
     - \- Report Designer, when switching between Data Source, Fields, Format.. sections |br|
       \- Report Designer > Update Result
   * - `POST report/updateResults`_
     - Updates the report data model.
     - Report Designer > Update Result when there are schema changes
   * - `POST report/loadAccesses`_
     - Returns a list of all accesses.
     - Report Designer > Access
   * - `POST report/loadSchedules`_
     - Returns a list of all scheduled deliveries.
     - Report Designer > Schedules
   * - `GET report/reportPart/{report\_part\_id}/(report\_id)`_
     - Returns the report part definition specified by report_part_id from draft (using report_id) or from database (without report_id).
     - Dashboard Designer
   * - `POST report/validateExistingField`_
     - Validates that some fields exist in a report.
     - To be updated
   * - `GET report/reportId/(tenant\_id)?reportName=value&categoryName=value`_
     - Returns report id from report name and category name.
     - To be updated
   * - `POST report/validateExistingReport`_
     - Validates that a report exists in a category.
     - To be updated
   * - `GET report/reportsByTenant/(tenant\_id)`_
     - Returns list of reports by tenant, with each report containing a list of report parts.
     - To be updated
   * - `POST report/updateRenderingTime`_
     - Updates the rendering time of a report.
     - \- Report Viewer |br|
       \- Report List > Expand a report > Edit > Quick Edit
   * - `GET report/isReportValid/(report\_id)`_
     - Returns true if there is a report definition for the specified report_id.
     - \- Report Designer for an existing report |br|
       \- Report Viewer |br|
       \- Report List > Expand a report > Edit > Quick Edit |br|
       \- Dashboard Viewer
   * - `POST report/areReportsValid`_
     - Validates if reports are valid.
     - To be updated
   * - `POST report/printDraft`_
     - Saves report as draft and print.
     - Report Designer > Export - to allow printing unsaved changes
   * - `GET report/printDraft/{report\_id}`_
     - Gets report as draft for printing.
     - To be updated
   * - `GET report/accessPriority/(report\_dashboard\_id)`_
     - Returns access priority for report/dashboard.
     - To be updated
   * - `POST report/timePeriod`_
     - Saves a customed InTimePeriod.
     - Not used
   * - `DELETE report/timePeriod/{time_period_id}`_
     - Deletes the customed InTimePeriod specified by time_period_id.
     - Not used
   * - `GET report/reportPart/crossfiltering/{report_part_id}`_
     - Returns a list of ids of cross-filtering report parts in the same report as the specified report part, including itself.

       .. versionadded:: 2.0.6
     - To be updated
   * - `GET report/validateEmbeddedReport/(tenant_id)?reportId=value&reportName=value&reportPartName=value`_
     - Validates that logged in user can access one and only one report part from the specified reportName and reportPartName.

       .. versionadded:: 2.2.2
     - To be updated

GET report/category/{type}/(tenant\_id)
---------------------------------------

Returns an array of allowed saving categories by type (Reports/Templates/Dashboards), filtered by tenant_id if given.

   type
      - 0 = Reports
      - 1 = Templates
      - 2 = Dashboards

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET /api/report/category/1 HTTP/1.1

   Sample response::

      [{
         "name": "Category 1",
         "type": "Templates",
         "parentId": null,
         "tenantId": null,
         "status": 2,
         "id": "17c176e1-500b-4378-8c59-1f69e84e425b",
         "state": 0,
         "modified": null"
     }, {
         "name": "Sub Category 1",
         "type": "Templates",
         "parentId": "17c176e1-500b-4378-8c59-1f69e84e425b",
         "tenantId": null,
         "status": 2,
         "id": "14b3f8c7-c4e8-4730-a57e-3b28ad75b097",
         "state": 0,
         "modified": null"
     }, {
         "name": "Sub Category 2",
         "type": "Templates",
         "parentId": "17c176e1-500b-4378-8c59-1f69e84e425b",
         "tenantId": null,
         "status": 2,
         "id": "72d44e10-a707-455e-99dc-054088b6b2f3",
         "state": 0,
         "modified": null"
     }]

POST report/allowedSavingCategories
--------------------------------------------------------------

Returns an array of allowed saving categories for report, with total number of items.

**Request**

   Payload: a :doc:`models/ReportDashboardSearchCriteria` object

**Response**

   The following object:

      .. list-table::
         :header-rows: 1

         *  -  Field
            -  Description
            -  Note
         *  -  **data** |br|
               array of objects
            -  An array of :doc:`models/Category` objects
            -
         *  -  **totalItems** |br|
               string
            -  The number of all reports
            -
         *  -  **numOfChilds** |br|
               integer
            -  The number of children
            -
         *  -  **numOfCheckedChilds** |br|
               integer
            -  The number of selected children
            -
         *  -  **indeterminate** |br|
               boolean
            -  *  true if 0 < numOfCheckedChilds < numOfChilds
               *  false if not
            -
         *  -  **isLastPage** |br|
               boolean
            -  Whether this is the last page
            -

**Samples**

   .. code-block:: http

      POST /api/report/allowedSavingCategories HTTP/1.1

   To be updated

POST report/allowedSavingSubCategories
--------------------------------------------------------------

Returns an array of allowed saving sub-categories for report, with total number of items.

   The following object:

      .. list-table::
         :header-rows: 1

         *  -  Field
            -  Description
            -  Note
         *  -  **data** |br|
               array of objects
            -  An array of :doc:`models/Category` objects
            -
         *  -  **totalItems** |br|
               string
            -  The number of all reports
            -
         *  -  **numOfChilds** |br|
               integer
            -  The number of children
            -
         *  -  **numOfCheckedChilds** |br|
               integer
            -  The number of selected children
            -
         *  -  **indeterminate** |br|
               boolean
            -  *  true if 0 < numOfCheckedChilds < numOfChilds
               *  false if not
            -
         *  -  **isLastPage** |br|
               boolean
            -  Whether this is the last page
            -

**Samples**

   .. code-block:: http

      POST /api/report/allowedSavingSubCategories HTTP/1.1

   To be updated

GET report/subcategory/{parent\_category\_id}
---------------------------------------------

Returns an array of allowed saving sub-categories under the Report category specified by parent\_category\_id.

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET /api/report/subcategory/17c176e1-500b-4378-8c59-1f69e84e425b HTTP/1.1

   Sample response::

      [{
         "name": "Sub Category 1",
         "type": null,
         "parentId": "17c176e1-500b-4378-8c59-1f69e84e425b",
         "tenantId": null,
         "status": 2,
         "id": "72d44e10-a707-455e-99dc-054088b6b2f3",
         "state": 0,
         "modified": null
     }, {
         "name": "Sub Category 2",
         "type": null,
         "parentId": "17c176e1-500b-4378-8c59-1f69e84e425b",
         "tenantId": null,
         "status": 2,
         "id": "14b3f8c7-c4e8-4730-a57e-3b28ad75b097",
         "state": 0,
         "modified": null
     }]


.. _GET_report/allCategories/{type}/(tenant_id):

GET report/allCategories/{type}/(tenant_id)
--------------------------------------------

Returns the list of categories by type (Reports/Templates/Dashboards) in parent-child hierarchy.

   type
      - 0 = Reports
      - 1 = Templates
      - 2 = Dashboards

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET /api/report/allCategories/0 HTTP/1.1

   Sample response::

      [{
         "name": "Category 1",
         "type": 0,
         "parentId": null,
         "tenantId": null,
         "subReportCategories": null,
         "canDelete": false,
         "status": 2,
         "id": "f2d79ff5-3aa8-4ae6-b0d0-e47687a77380",
         "state": 0,
         "inserted": true,
         "version": null,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
     }, {
         "name": "Category 2",
         "type": 0,
         "parentId": null,
         "tenantId": null,
         "subReportCategories": [{
             "name": "Sub-category 1",
             "type": 0,
             "parentId": "f514e26f-501c-4369-8ea9-de4eba208bdf",
             "tenantId": null,
             "subReportCategories": null,
             "canDelete": false,
             "status": 2,
             "id": "81517214-273b-42e9-91b5-8ef766cc5761",
             "state": 0,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
         }],
         "canDelete": false,
         "status": 2,
         "id": "f514e26f-501c-4369-8ea9-de4eba208bdf",
         "state": 0,
         "inserted": true,
         "version": null,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
     }]

POST report/allCategories
--------------------------------------------

Returns the list of categories in parent-child hierarchy, with total number of items.

**Request**

    Payload: a :doc:`models/ReportDashboardSearchCriteria` object

**Response**

    The following object:

      .. list-table::
         :header-rows: 1

         *  -  Field
            -  Description
            -  Note
         *  -  **data** |br|
               array of objects
            -  An array of :doc:`models/Category` objects
            -
         *  -  **totalItems** |br|
               string
            -  The number of all items
            -
         *  -  **numOfChilds** |br|
               integer
            -  The number of children
            -
         *  -  **numOfCheckedChilds** |br|
               integer
            -  The number of selected children
            -
         *  -  **indeterminate** |br|
               boolean
            -  *  true if 0 < numOfCheckedChilds < numOfChilds
               *  false if not
            -
         *  -  **isLastPage** |br|
               boolean
            -  Whether this is the last page
            -

**Samples**

   .. code-block:: http

      POST /api/report/allCategories HTTP/1.1

   To be updated


POST report/category
---------------------------------------

Renames a report category.

**Request**

    A :doc:`models/Category` object

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -  Is the rename successful
          -
       *  -  **messages** |br|
             array of strings
          -  The error messages
          -

**Samples**

   .. code-block:: http

      POST /api/report/category HTTP/1.1

   Request Payload::

      {
        	"id" : "f2d79ff5-3aa8-4ae6-b0d0-e47687a77380",
        	"type" : 1,
        	"name" : "Category 1 renamed",
        	"parentId" : null,
        	"tenantId" : null,
        	"status" : 2,
        	"state" : 0,
        	"modified" : null,
        	"canDelete" : false,
        	"subCategories" : [],
        	"subReportCategories" : null,
        	"reports" : []
      }

   Successful response::

      {
         "success": true,
         "messages": null
     }


DELETE report/category/{report\_category\_id}
----------------------------------------------

Removes the report category specified by report_category_id.

**Request**

    No payload

**Response**

   An :doc:`models/OperationResult` object with the **success** field populated:

   .. list-table::
      :header-rows: 1

      *  -  Field
         -  Description
         -  Note
      *  -  | **success**
            | boolean
         -  Is the rename successful
         -

**Samples**

   .. code-block:: http

      DELETE /api/report/category/f285a869-25fb-428e-8cef-856241ba4249 HTTP/1.1

   Sample response in case of error::

      {
     	"success" : false,
        	"messages" : [{
        			"key" : "",
        			"messages" : ["This category (or its sub-category) containing report(s)."]
        		}
        	]
      }


POST report/validateCategoryName
---------------------------------------

Validates a report category name.

**Request**

    Payload: a :doc:`models/Category` object

**Response**

    - true if the category name is valid and not duplicated
    - false if not

**Samples**

   .. code-block:: http

      POST /api/report/validateCategoryName HTTP/1.1

   With payload::

      {
        "name": "InternetSales",
        "type": 0,
        "parentId": "5d034fc7-0cc8-46b7-beb3-35b22c57827c",
        "id": "45f17b8a-3708-4f36-80ef-9178b7124841"
      }

   Sample response::

      true

GET report/reportByProperty/{report\_id}/{property}
------------------------------------------------------------

Returns a report section.

**Request**

    property
      * 0 = All
      * 1 = DataSource
      * 2 = Relationship
      * 3 = Filter
      * 4 = ReportPart
      * 5 = CalculatedField
      * 6 = DynamicQuerySourceField
      * 7 = Scheduling
      * 8 = Access
      * 9 = Report

**Response**

    A :doc:`models/ReportDefinition` object

**Samples**

   .. code-block:: http

      GET /api/report/reportByProperty/e09f9d45-b721-4012-b8e7-c31c58d52af3/3 HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "inaccessible": false,
           "category": {
             "name": "Sales",
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
             "id": "93de93b9-d5d1-48f1-800d-1db1ffc02614",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": "John Doe",
             "modified": null,
             "modifiedBy": null
           },
           "subCategory": null,
           "reportRelationship": [],
           "reportPart": [],
           "reportFilter": {
             "filterFields": [],
             "logic": "",
             "visible": true,
             "reportId": "e09f9d45-b721-4012-b8e7-c31c58d52af3",
             "id": "93f2af72-1309-46fe-a779-ff426574619f",
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
           "name": "FactInternetSales Date",
           "reportDataSource": [],
           "type": 0,
           "previewRecord": 10,
           "advancedMode": true,
           "allowNulls": false,
           "isDistinct": false,
           "categoryId": "93de93b9-d5d1-48f1-800d-1db1ffc02614",
           "categoryName": "Sales",
           "subCategoryId": null,
           "subCategoryName": null,
           "tenantId": null,
           "tenantName": null,
           "description": "",
           "title": "",
           "lastViewed": "2017-01-05T07:25:53.557",
           "owner": "John Doe",
           "ownerId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
           "excludedRelationships": "",
           "numberOfView": 7,
           "renderingTime": 1359.8571428571429,
           "createdById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
           "modifiedById": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
           "snapToGrid": false,
           "usingFields": "78c99b13-af5d-47b9-9d2a-9fae8bc2b51c,80d98874-67fd-49f7-8755-497c0393736b",
           "hasDeletedObjects": false,
           "header": { "removed": "for brevity" },
           "footer": { "removed": "for brevity" },
           "titleDescription": { "removed": "for brevity" },
           "sourceId": null,
           "checked": false,
           "copyDashboard": false,
           "exportFormatSetting": { "removed": "for brevity" },
           "deletable": true,
           "editable": true,
           "movable": true,
           "copyable": true,
           "accessPriority": 1,
           "active": true,
           "id": "e09f9d45-b721-4012-b8e7-c31c58d52af3",
           "state": 0,
           "deleted": false,
           "inserted": true,
           "version": 6,
           "created": "2016-11-21T07:22:01",
           "createdBy": "John Doe",
           "modified": "2016-11-21T08:42:07.763",
           "modifiedBy": "John Doe"
         }

.. _POST_report:

POST report
---------------------------------------

Saves a report.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object

**Response**

    A :doc:`models/ReportSavingResult` object

**Samples**

   .. code-block:: http

      POST /api/report HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
           	"reportKey" : {
           		"key" : "b95d2611-10c5-4808-aa68-9db2ccc719ff",
           		"modified" : null
           	},
           	"section" : 2,
           	"saveAs" : false,
           	"ignoreCheckChange" : false,
           	"report" : {
           		"name" : "Report01",
           		"type" : "Templates",
           		"previewRecord" : 10,
           		"advancedMode" : false,
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
           				"aliasId" : "1a67e4e1-7b76-4aac-b905-027bb4302845_Categories",
           				"querySourceId" : "1a67e4e1-7b76-4aac-b905-027bb4302845",
           				"querySourceName" : "Categories",
           				"selected" : true,
           				"categoryId" : "00000000-0000-0000-0000-000000000000",
           				"primaryFields" : [{
           						"name" : "CategoryID",
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
           						"originalName" : "CategoryID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"querySource" : null,
           						"id" : "9fd3b009-4809-47ad-845b-96a9dc4cf71e",
           						"state" : 0,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"dateTimeNow" : "2016-06-10T07:29:35.9754058Z"
           					}
           				]
           			}
           		],
           		"reportRelationship" : [{
           				"id" : "1a67e4e1-7b76-4aac-b905-027bb4302845",
           				"category" : null,
           				"databaseName" : "Northwind",
           				"schemaName" : "dbo",
           				"dataObject" : "Categories",
           				"dataObjectType" : "Table",
           				"relationshipKeyJoins" : [],
           				"relationshipPosition" : 0,
           				"level" : 1
           			}
           		],
           		"reportFilter" : {
           			"status" : 0,
           			"logic" : "",
           			"visible" : false,
           			"filterFields" : [],
           			"id" : "19578f3d-ce47-4e94-a46b-2f7216e059b7",
           			"reportId" : "b95d2611-10c5-4808-aa68-9db2ccc719ff"
           		},
           		"reportPart" : [{
           				"isDirty" : true,
           				"reportPartContent" : {
           					"isDirty" : false,
           					"type" : 3,
           					"columns" : {
           						"elements" : [{
           								"isDirty" : false,
           								"name" : "CategoryName",
           								"properties" : {
           									"isDirty" : false,
           									"dataFormattings" : {
           										"function" : "",
           										"functionInfo" : {},
           										"format" : "Format",
           										"font" : {
           											"family" : "Georgia",
           											"size" : 8,
           											"bold" : true,
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
           										"alternativeText" : {},
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
           									}
           								},
           								"position" : 1,
           								"field" : {
           									"fieldId" : "0c140c5a-fa48-46f8-91ae-656a394c48ce",
           									"fieldName" : "CategoryName",
           									"fieldNameAlias" : "CategoryName",
           									"dataFieldType" : "Text",
           									"querySourceId" : "1a67e4e1-7b76-4aac-b905-027bb4302845",
           									"querySourceType" : "Table",
           									"sourceAlias" : "Categories",
           									"relationshipId" : null,
           									"visible" : true,
           									"calculatedTree" : null
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}
           						]
           					},
           					"rows" : {
           						"elements" : []
           					},
           					"values" : {
           						"elements" : []
           					},
           					"separators" : {
           						"elements" : []
           					},
           					"groups" : {
           						"elements" : []
           					},
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
           								"value" : 60,
           								"unit" : "Pixels"
           							},
           							"alterBackgroundColor" : false
           						},
           						"rows" : {
           							"height" : 15,
           							"alterBackgroundColor" : false
           						},
           						"headers" : {
           							"font" : {
           								"family" : "Georgia",
           								"size" : 12,
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
           					"title" : {
           						"text" : "title",
           						"properties" : {},
           						"settings" : {
           							"font" : {
           								"family" : "",
           								"size" : 0,
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
           						"text" : "desc",
           						"properties" : {},
           						"settings" : {
           							"font" : {
           								"family" : "",
           								"size" : 0,
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
           					}
           				},
           				"positionX" : 0,
           				"positionY" : 0,
           				"width" : 12,
           				"height" : 4,
           				"state" : 1,
           				"modified" : null,
           				"isBackSide" : true,
           				"title" : "Grid"
           			}
           		]
           	}
         }

   Successful response::

      {
         "reportKey": {
            "key": "b95d2611-10c5-4808-aa68-9db2ccc719ff",
            "tenantId": null
         },
         "report": {
            "fields": "omitted",
         },
         "success": true,
         "messages": null,
         "data": null
      }

.. _POST_report/draft:

POST report/draft
---------------------------------------

Saves a report as draft.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object

**Response**

    An :doc:`models/OperationResult` object

**Samples**

   .. code-block:: http

      POST /api/report/draft HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
           	"reportKey" : {
           		"key" : null,
           		"modified" : null
           	},
           	"saveAs" : false,
           	"report" : {
           		"name" : "TestReport",
           		"type" : "Reports",
           		"previewRecord" : 100,
           		"advancedMode" : true,
           		"allowNulls" : false,
           		"distinct" : false,
           		"category" : null,
           		"subCategory" : null,
           		"reportDataSource" : [{
           				"querySourceId" : "aff154e4-af1f-4b57-8e80-72400ca6deac",
           				"querySourceName" : "CustOrdersDetail",
           				"selected" : true,
           				"categoryId" : "00000000-0000-0000-0000-000000000000",
           				"primaryFields" : []
           			}
           		],
           		"reportRelationship" : [],
           		"reportFilter" : null
           	}
         }

   Sample response::

      {
         "success": true,
         "messages": null
      }


POST report/cancel
---------------------------------------

Deletes temporary data of a report.

**Request**

    Payload: a :doc:`models/ReportParameter` object

**Response**
    A :doc:`models/ReportSavingResult` object

**Samples**

   .. code-block:: http

      POST /api/report/cancel HTTP/1.1

   Request Payload::

      {
        	"reportKey" : {
        		"key" : "4fd37956-4b97-4efb-9d71-c750b0c36474"
        	}
      }

   Successful response::

      {
         "reportKey": {
             "key": null,
             "tenantId": null
         },
         "report": null
      }


POST report/loadReport
---------------------------------------

Returns a report's details.

.. warning::

   This API is obsolete, use `POST report/loadForEdit`_ instead.

POST report/loadForEdit
---------------------------------------

Returns an object with report key and report's details.

**Request**

    Payload: a :doc:`models/ReportParameter` object

**Response**

    A :doc:`models/ReportSavingParameter` object, with the **report** field fully populated

**Samples**

   .. code-block:: http

      POST /api/report/loadForEdit HTTP/1.1

   Payload::

      {"reportKey":{"key":"9d34d5d2-447f-465e-8223-d7f66378b5f9"}}

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           	"saveAs" : false,
           	"report" : {
           		"category" : {
           			"name" : "",
           			"type" : 1,
           			"parentId" : null,
           			"tenantId" : null,
           			"subReportCategories" : null,
           			"id" : "00000000-0000-0000-0000-000000000000",
           			"state" : 0,
           			"modified" : null
           		},
           		"subCategory" : {
           			"name" : "",
           			"type" : 1,
           			"parentId" : null,
           			"tenantId" : null,
           			"subReportCategories" : null,
           			"id" : "00000000-0000-0000-0000-000000000000",
           			"state" : 0,
           			"modified" : null
           		},
           		"reportDataSource" : [{
           				"reportId" : "00000000-0000-0000-0000-000000000000",
           				"querySourceId" : "e1bc2021-3874-4e5a-b51e-d799cef5e29a",
           				"id" : "bc4cabe6-6f64-473d-b5c8-d3faf314e1fb",
           				"state" : 0,
           				"modified" : null
           			}
           		],
           		"reportRelationship" : [],
           		"reportPart" : [],
           		"reportFilter" : {
           			"filterFields" : [],
           			"logic" : "",
           			"visible" : false,
           			"reportId" : "00000000-0000-0000-0000-000000000000",
           			"id" : "e610c0a9-c074-47ec-a633-1195a589549c",
           			"state" : 0,
           			"modified" : null
           		},
           		"calculatedFields" : [],
           		"name" : "",
           		"type" : 1,
           		"previewRecord" : 10,
           		"advancedMode" : true,
           		"allowNulls" : false,
           		"isDistinct" : false,
           		"categoryId" : null,
           		"categoryName" : null,
           		"subCategoryId" : null,
           		"subCategoryName" : null,
           		"tenantId" : null,
           		"description" : null,
           		"createdBy" : null,
           		"createdDate" : "0001-01-01T00:00:00",
           		"modifiedBy" : null,
           		"version" : null,
           		"numberOfViews" : 0,
           		"averageRenderingTime" : 0.0,
           		"id" : "00000000-0000-0000-0000-000000000000",
           		"state" : 1,
           		"modified" : null
           	},
           	"section" : 0,
           	"tenantId" : null,
           	"ignoreCheckChange" : false,
           	"reportKey" : {
           		"key" : "9d34d5d2-447f-465e-8223-d7f66378b5f9",
           		"tenantId" : null
           	}
         }

GET report/(tenant\_id)
---------------------------------------

Returns all report categories together with the reports inside.

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET /api/report HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
           {
             "reports": [],
             "name": null,
             "type": 0,
             "parentId": null,
             "tenantId": null,
             "canDelete": false,
             "editable": false,
             "savable": false,
             "subCategories": [
               {
                 "reports": [
                   {
                     "name": "Example Report Name",
                     "type": 0,
                     "previewRecord": 0,
                     "advancedMode": false,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "00000000-0000-0000-0000-000000000000",
                     "tenantName": null,
                     "description": null,
                     "title": null,
                     "lastViewed": null,
                     "owner": null,
                     "ownerId": null,
                     "excludedRelationships": null,
                     "numberOfView": 0,
                     "renderingTime": 0,
                     "createdById": null,
                     "modifiedById": null,
                     "snapToGrid": false,
                     "usingFields": null,
                     "hasDeletedObjects": false,
                     "header": null,
                     "footer": null,
                     "titleDescription": null,
                     "exportFormatSetting": null,
                     "deletable": false,
                     "editable": false,
                     "movable": false,
                     "copyable": false,
                     "accessPriority": 0,
                     "active": false,
                     "id": "b166877f-bf1f-4adc-9dac-7575dd5e5183",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 0,
                     "created": null,
                     "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "modified": null,
                     "modifiedBy": null
                   }
                 ],
                 "name": null,
                 "type": 0,
                 "parentId": null,
                 "tenantId": null,
                 "canDelete": false,
                 "editable": false,
                 "savable": false,
                 "subCategories": [],
                 "id": null,
                 "state": 0,
                 "deleted": false,
                 "inserted": true,
                 "version": null,
                 "created": null,
                 "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                 "modified": null,
                 "modifiedBy": null
               }
             ],
             "id": null,
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
             "modified": null,
             "modifiedBy": null
           }
         ]

POST report/validateReportName
---------------------------------------

Validates that a report name is unique and not empty.

**Request**

    Payload: a :doc:`models/ReportDefinition` object, with **name**, **type**, **category** and **subCategory** fields populated.

**Response**

    A :doc:`models/OperationResult` object, with **success** field means whether the report name is unique (in the specified category and sub-category)

**Samples**

   .. code-block:: http

      POST /api/report/validateReportName HTTP/1.1

   Request payload::

      {
         "id": null,
         "name": "AnExistingName",
         "type": 1,
         "category": {
            "id": "b45d865c-bea2-41be-9986-8a912981bfed",
            "name": "Category A",
            "type": 1,
            "tenantId": null
         },
         "subCategory": {
            "id": null,
            "name": "",
            "type": 1,
            "tenantId": null
         }
      }

   Response when that report name already exists in Category A::

      {
         "success": false,
         "messages": [
            {
               "key": "Name",
               "detail": null,
               "messages": [
                  "This template name already exists in the \"Category A\" category."
               ]
            }
         ],
         "data": null
      }


POST report/validate
---------------------------------------

Validates that a report name is unique and its filter and relationships are valid.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object

**Response**

    An :doc:`models/OperationResult` object, with **success** field means whether the validation is successful

**Samples**

   .. code-block:: http

      POST /api/report/validate HTTP/1.1

   Request payload::

      {
        	"reportKey" : {
        		"key" : "940529fd-f1fb-4d98-8def-c8dcfa7eba84",
        		"tenantId" : null
        	},
        	"report" : {
        		"id" : "940529fd-f1fb-4d98-8def-c8dcfa7eba84",
        		"type" : "Templates",
        		"category" : {
        			"id" : "0adae39c-1db0-466d-820b-9f3f59c8e199"
        		},
        		"subCategory" : {
        			"id" : null
        		}
        	}
      }

   Sample response::

      {
         "success": true,
         "message": null,
         "errors": []
     }


POST report/search
---------------------------------------

.. deprecated:: 2.0.0
     superseded by `POST report/search2`_

Searches for reports.

**Request**

    Payload: a :doc:`models/ReportDashboardSearchCriteria` object

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      POST api/report/search HTTP/1.1

   Request payload::

      {
        	"criterias" : [{
        			"key" : "All",
        			"value" : "fil"
        		}
        	],
        	"isUncategorized" : false,
        	"sortCriteria" : {
        		"key" : "ReportName",
        		"descending" : false
        	},
        	"tenantId" : null,
        	"type" : "0"
     }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
        		"reports" : [],
        		"name" : "0",
        		"type" : 0,
        		"parentId" : null,
        		"tenantId" : null,
        		"canDelete" : false,
        		"savable" : false,
        		"subCategories" : [{
        				"reports" : [{
        						"name" : "filter",
        						"type" : 0,
        						"previewRecord" : 0,
        						"advancedMode" : false,
        						"allowNulls" : false,
        						"isDistinct" : false,
        						"categoryId" : "8da86160-ab16-4f4b-a439-729c8b82b1c6",
        						"categoryName" : null,
        						"subCategoryId" : "6dee7a46-cfab-477a-a952-be4471eab1a0",
        						"subCategoryName" : null,
        						"tenantId" : "00000000-0000-0000-0000-000000000000",
        						"tenantName" : null,
        						"description" : "",
        						"title" : null,
        						"lastViewed" : null,
        						"owner" : null,
        						"ownerId" : null,
        						"headerContent" : null,
        						"footerContent" : null,
        						"excludedRelationships" : null,
        						"numberOfView" : 0,
        						"renderingTime" : 0,
        						"createdById" : null,
        						"modifiedById" : null,
        						"excludedRelationshipIds" : [],
        						"header" : null,
        						"footer" : null,
        						"titleDescriptionContent" : null,
        						"titleDescription" : null,
        						"id" : "df3c8552-1505-4905-9d1d-9574ac1b92de",
        						"state" : 0,
        						"inserted" : true,
        						"version" : 2,
        						"created" : "2016-09-16T08:07:48.1630000-07:00",
        						"createdBy" : null,
        						"modified" : "2016-09-16T08:08:36.2430000-07:00",
        						"modifiedBy" : null
        					}, {
        						"name" : "filter1",
        						"type" : 0,
        						"previewRecord" : 0,
        						"advancedMode" : false,
        						"allowNulls" : false,
        						"isDistinct" : false,
        						"categoryId" : "8da86160-ab16-4f4b-a439-729c8b82b1c6",
        						"categoryName" : null,
        						"subCategoryId" : "6dee7a46-cfab-477a-a952-be4471eab1a0",
        						"subCategoryName" : null,
        						"tenantId" : "00000000-0000-0000-0000-000000000000",
        						"tenantName" : null,
        						"description" : "",
        						"title" : null,
        						"lastViewed" : null,
        						"owner" : null,
        						"ownerId" : null,
        						"headerContent" : null,
        						"footerContent" : null,
        						"excludedRelationships" : null,
        						"numberOfView" : 0,
        						"renderingTime" : 0,
        						"createdById" : null,
        						"modifiedById" : null,
        						"excludedRelationshipIds" : [],
        						"header" : null,
        						"footer" : null,
        						"titleDescriptionContent" : null,
        						"titleDescription" : null,
        						"id" : "c7b52014-ca40-4aad-9a8c-07887743aec4",
        						"state" : 0,
        						"inserted" : true,
        						"version" : 1,
        						"created" : "2016-09-16T08:09:48.3830000-07:00",
        						"createdBy" : null,
        						"modified" : "2016-09-16T08:09:48.3830000-07:00",
        						"modifiedBy" : null
        					}
        				],
        				"name" : "0",
        				"type" : 0,
        				"parentId" : null,
        				"tenantId" : null,
        				"canDelete" : false,
        				"savable" : false,
        				"subCategories" : [],
        				"status" : 2,
        				"id" : "6dee7a46-cfab-477a-a952-be4471eab1a0",
        				"state" : 0,
        				"inserted" : true,
        				"version" : null,
        				"created" : null,
        				"createdBy" : null,
        				"modified" : null,
        				"modifiedBy" : null
        			}
        		],
        		"status" : 2,
        		"id" : "8da86160-ab16-4f4b-a439-729c8b82b1c6",
        		"state" : 0,
        		"inserted" : true,
        		"version" : null,
        		"created" : null,
        		"createdBy" : null,
        		"modified" : null,
        		"modifiedBy" : null
         }]

POST report/search2
---------------------------------------

Searches for reports, with total number of items.

**Request**

    Payload: a :doc:`models/ReportDashboardSearchCriteria` object

**Response**

    The following object:

      .. list-table::
         :header-rows: 1

         *  -  Field
            -  Description
            -  Note
         *  -  **data** |br|
               array of objects
            -  An array of :doc:`models/Category` objects
            -
         *  -  **totalItems** |br|
               string
            -  The number of all items
            -
         *  -  **numOfChilds** |br|
               integer
            -  The number of children
            -
         *  -  **numOfCheckedChilds** |br|
               integer
            -  The number of selected children
            -
         *  -  **indeterminate** |br|
               boolean
            -  *  true if 0 < numOfCheckedChilds < numOfChilds
               *  false if not
            -
         *  -  **isLastPage** |br|
               boolean
            -  Whether this is the last page
            -

**Samples**

   .. code-block:: http

      POST /api/report/search2 HTTP/1.1

   Payload::

      {
         "criterias": [
            {
               "key": "All",
               "value": "chart"
            }
         ],
         "isUncategorized": false,
         "sortCriteria": {
            "key": "ReportName",
            "descending": false
         },
         "tenantId": null,
         "type": "0",
         "skipItems": 0,
         "pageSize": 63,
         "parentIds": [],
         "includeGlobalCategory": true
      }

   .. container:: toggle

      .. container:: header

         Response

      .. code-block:: json

         {
            "data": [
               {
                  "name": "Local Categories",
                  "type": 0,
                  "parentId": null,
                  "tenantId": null,
                  "isGlobal": false,
                  "canDelete": false,
                  "editable": false,
                  "savable": false,
                  "subCategories": [
                     {
                        "name": "AAA",
                        "type": 0,
                        "parentId": null,
                        "tenantId": null,
                        "isGlobal": false,
                        "canDelete": false,
                        "editable": false,
                        "savable": false,
                        "subCategories": [
                           {
                              "name": null,
                              "type": 0,
                              "parentId": "88618780-df81-44c7-b137-c2556e63afc6",
                              "tenantId": null,
                              "isGlobal": false,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "Chart_copy",
                                    "reportDataSource": [],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "88618780-df81-44c7-b137-c2556e63afc6",
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-05-05T03:08:05.273",
                                    "owner": "test 1",
                                    "ownerId": "3e451735-ee3c-42d2-8fe7-1d36d2244d2d",
                                    "excludedRelationships": null,
                                    "numberOfView": 16,
                                    "renderingTime": 603.625,
                                    "createdById": "3e451735-ee3c-42d2-8fe7-1d36d2244d2d",
                                    "modifiedById": null,
                                    "snapToGrid": false,
                                    "usingFields": "764ae5f1-7c8b-4ab9-8a3d-398acf9808e7,9d4ae367-b3e6-4aae-b617-d5a84c2bf46a",
                                    "hasDeletedObjects": false,
                                    "header": null,
                                    "footer": null,
                                    "titleDescription": null,
                                    "sourceId": null,
                                    "checked": false,
                                    "copyDashboard": false,
                                    "exportFormatSetting": null,
                                    "deletable": true,
                                    "editable": true,
                                    "movable": true,
                                    "copyable": true,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": false,
                                    "id": "5e23512e-7fd9-4211-bdf4-3d4ebe56f620",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-03-23T06:22:25.697",
                                    "createdBy": "test 1",
                                    "modified": "2017-03-23T06:22:25.697",
                                    "modifiedBy": "test 1"
                                 }
                              ],
                              "dashboards": [],
                              "numOfChilds": 1,
                              "numOfCheckedChilds": 0,
                              "indeterminate": false,
                              "fullPath": null,
                              "computeNameSettings": null,
                              "id": null,
                              "state": 0,
                              "deleted": false,
                              "inserted": true,
                              "version": null,
                              "created": null,
                              "createdBy": "John Doe",
                              "modified": null,
                              "modifiedBy": null
                           }
                        ],
                        "checked": false,
                        "reports": [],
                        "dashboards": [],
                        "numOfChilds": 1,
                        "numOfCheckedChilds": 0,
                        "indeterminate": false,
                        "fullPath": null,
                        "computeNameSettings": null,
                        "id": "88618780-df81-44c7-b137-c2556e63afc6",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "John Doe",
                        "modified": null,
                        "modifiedBy": null
                     },
                     {
                        "name": "Migration",
                        "type": 0,
                        "parentId": null,
                        "tenantId": null,
                        "isGlobal": false,
                        "canDelete": false,
                        "editable": false,
                        "savable": false,
                        "subCategories": [
                           {
                              "name": null,
                              "type": 0,
                              "parentId": "707ce889-710b-4964-89e2-f1d85959fe13",
                              "tenantId": null,
                              "isGlobal": false,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "Chart_copy",
                                    "reportDataSource": [],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "707ce889-710b-4964-89e2-f1d85959fe13",
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-04-19T02:46:33.14",
                                    "owner": "test 1",
                                    "ownerId": "3e451735-ee3c-42d2-8fe7-1d36d2244d2d",
                                    "excludedRelationships": null,
                                    "numberOfView": 4,
                                    "renderingTime": 643,
                                    "createdById": "3e451735-ee3c-42d2-8fe7-1d36d2244d2d",
                                    "modifiedById": null,
                                    "snapToGrid": false,
                                    "usingFields": "764ae5f1-7c8b-4ab9-8a3d-398acf9808e7,9d4ae367-b3e6-4aae-b617-d5a84c2bf46a",
                                    "hasDeletedObjects": false,
                                    "header": null,
                                    "footer": null,
                                    "titleDescription": null,
                                    "sourceId": null,
                                    "checked": false,
                                    "copyDashboard": false,
                                    "exportFormatSetting": null,
                                    "deletable": true,
                                    "editable": true,
                                    "movable": true,
                                    "copyable": true,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": false,
                                    "id": "dda48c8e-9069-4137-8644-b30fa621eb65",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-03-23T06:22:25.697",
                                    "createdBy": "test 1",
                                    "modified": "2017-03-23T06:22:25.697",
                                    "modifiedBy": "test 1"
                                 }
                              ],
                              "dashboards": [],
                              "numOfChilds": 1,
                              "numOfCheckedChilds": 0,
                              "indeterminate": false,
                              "fullPath": null,
                              "computeNameSettings": null,
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
                           {
                              "name": "Migration",
                              "type": 0,
                              "parentId": "707ce889-710b-4964-89e2-f1d85959fe13",
                              "tenantId": null,
                              "isGlobal": false,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "Chart",
                                    "reportDataSource": [],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "707ce889-710b-4964-89e2-f1d85959fe13",
                                    "categoryName": null,
                                    "subCategoryId": "14df5f75-5036-4508-8893-7db29d7693c9",
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-04-21T06:21:41.78",
                                    "owner": "duc duc",
                                    "ownerId": "0b5f7896-cad5-442d-b3c4-0167e7e72ec9",
                                    "excludedRelationships": null,
                                    "numberOfView": 5,
                                    "renderingTime": 540.6,
                                    "createdById": "0b5f7896-cad5-442d-b3c4-0167e7e72ec9",
                                    "modifiedById": null,
                                    "snapToGrid": false,
                                    "usingFields": "764ae5f1-7c8b-4ab9-8a3d-398acf9808e7,9d4ae367-b3e6-4aae-b617-d5a84c2bf46a",
                                    "hasDeletedObjects": false,
                                    "header": null,
                                    "footer": null,
                                    "titleDescription": null,
                                    "sourceId": null,
                                    "checked": false,
                                    "copyDashboard": false,
                                    "exportFormatSetting": null,
                                    "deletable": true,
                                    "editable": true,
                                    "movable": true,
                                    "copyable": true,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": false,
                                    "id": "d69311fc-2cd4-4211-96b5-9032d436e5a3",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-03-23T06:22:25.697",
                                    "createdBy": "John Doe",
                                    "modified": "2017-03-23T06:22:25.697",
                                    "modifiedBy": "John Doe"
                                 }
                              ],
                              "dashboards": [],
                              "numOfChilds": 1,
                              "numOfCheckedChilds": 0,
                              "indeterminate": false,
                              "fullPath": null,
                              "computeNameSettings": null,
                              "id": "14df5f75-5036-4508-8893-7db29d7693c9",
                              "state": 0,
                              "deleted": false,
                              "inserted": true,
                              "version": null,
                              "created": null,
                              "createdBy": "John Doe",
                              "modified": null,
                              "modifiedBy": null
                           }
                        ],
                        "checked": false,
                        "reports": [],
                        "dashboards": [],
                        "numOfChilds": 2,
                        "numOfCheckedChilds": 0,
                        "indeterminate": false,
                        "fullPath": null,
                        "computeNameSettings": null,
                        "id": "707ce889-710b-4964-89e2-f1d85959fe13",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "John Doe",
                        "modified": null,
                        "modifiedBy": null
                     },
                     {
                        "name": null,
                        "type": 0,
                        "parentId": null,
                        "tenantId": null,
                        "isGlobal": false,
                        "canDelete": false,
                        "editable": false,
                        "savable": false,
                        "subCategories": [
                           {
                              "name": null,
                              "type": 0,
                              "parentId": "00000000-0000-0000-0000-000000000000",
                              "tenantId": null,
                              "isGlobal": false,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "test chart",
                                    "reportDataSource": [],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": null,
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-05-04T10:08:14.85",
                                    "owner": "System Admin",
                                    "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                                    "excludedRelationships": null,
                                    "numberOfView": 5,
                                    "renderingTime": 582,
                                    "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                                    "modifiedById": null,
                                    "snapToGrid": false,
                                    "usingFields": null,
                                    "hasDeletedObjects": false,
                                    "header": null,
                                    "footer": null,
                                    "titleDescription": null,
                                    "sourceId": null,
                                    "checked": false,
                                    "copyDashboard": false,
                                    "exportFormatSetting": null,
                                    "deletable": true,
                                    "editable": true,
                                    "movable": true,
                                    "copyable": true,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": false,
                                    "id": "d661cf7f-d3b1-4cf3-af1d-02edae924f1c",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-04-19T02:47:25.12",
                                    "createdBy": "System Admin",
                                    "modified": "2017-04-19T02:47:25.12",
                                    "modifiedBy": "System Admin"
                                 }
                              ],
                              "dashboards": [],
                              "numOfChilds": 1,
                              "numOfCheckedChilds": 0,
                              "indeterminate": false,
                              "fullPath": null,
                              "computeNameSettings": null,
                              "id": null,
                              "state": 0,
                              "deleted": false,
                              "inserted": true,
                              "version": null,
                              "created": null,
                              "createdBy": "John Doe",
                              "modified": null,
                              "modifiedBy": null
                           }
                        ],
                        "checked": false,
                        "reports": [],
                        "dashboards": [],
                        "numOfChilds": 1,
                        "numOfCheckedChilds": 0,
                        "indeterminate": false,
                        "fullPath": null,
                        "computeNameSettings": null,
                        "id": null,
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "John Doe",
                        "modified": null,
                        "modifiedBy": null
                     }
                  ],
                  "checked": false,
                  "reports": [],
                  "dashboards": [],
                  "numOfChilds": 3,
                  "numOfCheckedChilds": 0,
                  "indeterminate": false,
                  "fullPath": null,
                  "computeNameSettings": null,
                  "id": "09f8c4ab-0fe8-4e03-82d1-7949e3738f87",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "John Doe",
                  "modified": null,
                  "modifiedBy": null
               }
            ],
            "totalItems": 9,
            "numOfChilds": 1,
            "numOfCheckedChilds": 0,
            "indeterminate": false,
            "isLastPage": true
         }

POST report/advancedSearch
---------------------------------------

Searches for reports with advanced options.

**Request**

    Payload: a :doc:`models/ReportPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/ReportDefinition` objects

**Samples**

   .. code-block:: http

      POST /api/report/advancedSearch HTTP/1.1

   Request payload::

      {
        	"subcategoryid" : null,
        	"categoryId" : null,
        	"tenantId" : null,
        	"pageSize" : 10,
        	"pageIndex" : 1,
        	"sortOrders" : [{
        			"key" : "reportname",
        			"descending" : true
        		}
        	],
        	"criteria" : [{
        			"key" : "reportName",
        			"value" : "test",
        			"operation" : 1
        		}
        	]
      }

   Sample response:

   .. code-block:: json
      :emphasize-lines: 2

      {
         "result" : [],
         "pageIndex" : 1,
         "pageSize" : 10,
         "total" : 0
      }

.. _GET_report/reportMode:

GET report/reportMode
---------------------------------------

Returns the report mode.

**Request**

    No payload

**Response**

    The value of the report mode

    - 0 = Simple
    - 1 = Advanced

**Samples**

   .. code-block:: http

      GET /api/report/reportMode HTTP/1.1

   Sample response::

      1

.. _POST_report/reportMode/{value}:

POST report/reportMode/{value}
---------------------------------------

Sets the report mode to Simple or Advanced.

**Request**

    * call report/reportMode/0 to set Simple mode
    * call report/reportMode/1 to set Advanced mode

**Response**

    * true if succeeded
    * false if there was an error

**Samples**

   .. code-block:: http

      POST /api/report/reportMode/0 HTTP/1.1

   Successful response::

      true


POST report/detectReportChange
---------------------------------------

Verifies that all report details are up to date, without physical changes, and valid.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object, with **section** field specifies where to detect changes

     * 0 = All
     * 1 = DataSource
     * 2 = Fields
     * 3 = CalculatedField

**Response**

    An :doc:`models/OperationResult` object, with **success** field means whether the report is up to date, without physical changes, and valid

**Samples**

   .. code-block:: http

      POST /api/report/detectReportChange HTTP/1.1

   Request Payload to check if a new report with only one data source has physical changes:

   .. code-block:: json
      :emphasize-lines: 6

      {
        	"reportKey" : {
        		"key" : null,
        		"modified" : null
        	},
        	"section" : 1,
        	"report" : {
        		"reportDataSource" : [{
        				"querySourceId" : "1a67e4e1-7b76-4aac-b905-027bb4302845"
        			}
        		]
        	}
      }

   Successful response::

      {
         "success": true,
         "messages": null
      }

   .. container:: toggle

      .. container:: header

         Request Payload for an existing report with two data sources, filter and report part:

      .. code-block:: json

         {
           	"reportKey" : {
           		"key" : "37e99389-fa8a-4f9f-9d03-f6362240c931",
           		"modified" : null
           	},
           	"section" : 2,
           	"report" : {
           		"reportDataSource" : [{
           				"aliasId" : "84340ae7-275e-4bd5-bd77-89916341f20e_Order Details",
           				"querySourceId" : "84340ae7-275e-4bd5-bd77-89916341f20e",
           				"querySourceName" : "Order Details",
           				"selected" : true,
           				"categoryId" : "00000000-0000-0000-0000-000000000000",
           				"primaryFields" : [{
           						"name" : "OrderID",
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
           						"originalName" : "OrderID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"querySource" : null,
           						"id" : "9a4c52a4-f931-40d0-88b9-7f914d49581b",
           						"state" : 0,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"dateTimeNow" : "2016-06-13T07:22:35.8918127Z"
           					}, {
           						"name" : "ProductID",
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
           						"originalName" : "ProductID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"querySource" : null,
           						"id" : "1d379f29-02ae-4f51-ac3a-a627694c3539",
           						"state" : 0,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"dateTimeNow" : "2016-06-13T07:22:35.8918127Z"
           					}
           				]
           			}, {
           				"aliasId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d_Orders",
           				"querySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
           				"querySourceName" : "Orders",
           				"selected" : true,
           				"categoryId" : "00000000-0000-0000-0000-000000000000",
           				"primaryFields" : [{
           						"name" : "orderid_alias",
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
           						"originalName" : "OrderID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"querySource" : null,
           						"id" : "93157476-d4e6-49bb-8900-2fda43e46f87",
           						"state" : 0,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"dateTimeNow" : "2016-06-13T07:22:35.8918127Z"
           					}
           				]
           			}
           		],
           		"reportRelationship" : [{
           				"tempId" : "6da998ae-5451-4a45-ab86-69894e1b3a13",
           				"joinConnectionId" : "a0028b41-f820-4640-927c-68f6ef730b0f",
           				"foreignConnectionId" : "a0028b41-f820-4640-927c-68f6ef730b0f",
           				"joinQuerySourceId" : "84340ae7-275e-4bd5-bd77-89916341f20e",
           				"joinQuerySourceName" : "Order Details",
           				"joinDataSourceCategoryName" : "",
           				"joinDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
           				"foreignDataSourceCategoryName" : "",
           				"foreignDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
           				"foreignQuerySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
           				"foreignQuerySourceName" : "Orders",
           				"joinFieldId" : "9a4c52a4-f931-40d0-88b9-7f914d49581b",
           				"joinFieldName" : "OrderID",
           				"foreignFieldId" : "93157476-d4e6-49bb-8900-2fda43e46f87",
           				"foreignFieldName" : "orderid_alias",
           				"alias" : "",
           				"systemRelationship" : true,
           				"joinType" : "Inner",
           				"parentRelationshipId" : "5147885d-0bac-4252-8d33-f9fd96bd3b8e",
           				"position" : null,
           				"relationshipKeyJoins" : [],
           				"reportId" : "00000000-0000-0000-0000-000000000000",
           				"selectedForeignAlias" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d_Orders",
           				"id" : "6da998ae-5451-4a45-ab86-69894e1b3a13",
           				"state" : 1,
           				"validationKey" : "5147885d-0bac-4252-8d33-f9fd96bd3b8e",
           				"relationshipPosition" : 0,
           				"invalidAlias" : null,
           				"hidden" : false,
           				"level" : 1
           			}
           		],
           		"reportFilter" : {
           			"status" : 0,
           			"logic" : null,
           			"visible" : false,
           			"filterFields" : [{
           					"connectionName" : "Northwind",
           					"querySourceCategoryName" : "dbo",
           					"sourceFieldName" : "ShipCountry",
           					"sourceFieldVisible" : true,
           					"sourceFieldFilterable" : true,
           					"sourceDataObjectName" : "Orders",
           					"dataType" : "Text",
           					"filterId" : "00000000-0000-0000-0000-000000000000",
           					"querySourceFieldId" : "d0f88020-8d3f-4f80-a1ac-0c187f87dfd3",
           					"querySourceType" : "Table",
           					"querySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
           					"relationshipId" : null,
           					"alias" : "ShipCountry",
           					"position" : 1,
           					"visible" : false,
           					"required" : false,
           					"cascading" : true,
           					"operatorId" : "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
           					"operatorSetting" : null,
           					"value" : "'US'",
           					"sortType" : "Unsorted",
           					"fontFamily" : null,
           					"fontSize" : 0,
           					"textColor" : null,
           					"backgroundColor" : null,
           					"fontBold" : false,
           					"fontItalic" : false,
           					"fontUnderline" : false,
           					"id" : "00000000-0000-0000-0000-000000000000",
           					"status" : 0,
           					"modified" : null,
           					"dateTimeNow" : "2016-06-13T07:23:25.9138114Z",
           					"isParameter" : false,
           					"sourceDataObjectFullName" : "Northwind.dbo.Orders",
           					"selected" : false
           				}
           			],
           			"id" : "00000000-0000-0000-0000-000000000000",
           			"reportId" : "37e99389-fa8a-4f9f-9d03-f6362240c931"
           		},
           		"reportPart" : [{
           				"isDirty" : true,
           				"reportPartContent" : {
           					"isDirty" : false,
           					"type" : 3,
           					"columns" : {
           						"elements" : [{
           								"isDirty" : false,
           								"name" : "ShipCity",
           								"properties" : {
           									"isDirty" : false,
           									"dataFormattings" : {
           										"function" : "",
           										"functionInfo" : {},
           										"format" : "Format",
           										"font" : {
           											"family" : "Georgia",
           											"size" : 8,
           											"bold" : true,
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
           										"alternativeText" : {},
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
           								"position" : 1,
           								"field" : {
           									"fieldId" : "f5b9bac6-aa76-402c-8ade-6b8f619e9ced",
           									"fieldName" : "ShipCity",
           									"fieldNameAlias" : "ShipCity",
           									"dataFieldType" : "Text",
           									"querySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
           									"querySourceType" : "Table",
           									"sourceAlias" : "Orders",
           									"relationshipId" : null,
           									"visible" : true,
           									"calculatedTree" : null
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}, {
           								"isDirty" : false,
           								"name" : "ProductID",
           								"properties" : {
           									"isDirty" : false,
           									"dataFormattings" : {
           										"function" : "",
           										"functionInfo" : {},
           										"format" : "Format",
           										"font" : {
           											"family" : "Georgia",
           											"size" : 8,
           											"bold" : true,
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
           										"alternativeText" : {},
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
           								"position" : 2,
           								"field" : {
           									"fieldId" : "1d379f29-02ae-4f51-ac3a-a627694c3539",
           									"fieldName" : "ProductID",
           									"fieldNameAlias" : "ProductID",
           									"dataFieldType" : "Numeric",
           									"querySourceId" : "84340ae7-275e-4bd5-bd77-89916341f20e",
           									"querySourceType" : "Table",
           									"sourceAlias" : "Order Details",
           									"relationshipId" : null,
           									"visible" : true,
           									"calculatedTree" : null
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}, {
           								"isDirty" : false,
           								"name" : "Quantity",
           								"properties" : {
           									"isDirty" : false,
           									"dataFormattings" : {
           										"function" : "",
           										"functionInfo" : {},
           										"format" : "Format",
           										"font" : {
           											"family" : "Georgia",
           											"size" : 8,
           											"bold" : true,
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
           										"alternativeText" : {},
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
           								"position" : 3,
           								"field" : {
           									"fieldId" : "1eaa3d97-da56-45ca-b61a-8bf3bb253fea",
           									"fieldName" : "Quantity",
           									"fieldNameAlias" : "Quantity",
           									"dataFieldType" : "Numeric",
           									"querySourceId" : "84340ae7-275e-4bd5-bd77-89916341f20e",
           									"querySourceType" : "Table",
           									"sourceAlias" : "Order Details",
           									"relationshipId" : null,
           									"visible" : true,
           									"calculatedTree" : null
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}
           						]
           					},
           					"rows" : {
           						"elements" : []
           					},
           					"values" : {
           						"elements" : []
           					},
           					"separators" : {
           						"elements" : []
           					},
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
           								"value" : 100,
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
           								"family" : "Georgia",
           								"size" : 12,
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
           					"title" : {
           						"text" : "Title",
           						"properties" : {},
           						"settings" : {
           							"font" : {
           								"family" : "",
           								"size" : 0,
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
           						"text" : "Description line",
           						"properties" : {},
           						"settings" : {
           							"font" : {
           								"family" : "",
           								"size" : 0,
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
           					}
           				},
           				"positionX" : 0,
           				"positionY" : 0,
           				"width" : 12,
           				"height" : 4,
           				"state" : 1,
           				"modified" : null,
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
           				"title" : "Grid"
           			}
           		]
           	}
         }

.. _POST_report/function/{function_mode}/{data_type}/(tenant_id):

POST report/function/{function_mode}/{data_type}/(tenant_id)
---------------------------------------------------------------

Returns a list of report functions filtered by mode (field, sub-total, grand-total), data type, tenant_id, and optionally filtered by connections of the selected query source ids in payload.

.. versionchanged:: 1.25
   Changed from GET to POST

**Request**

   Available values for ``function_mode``:

      *  0 = Field
      *  1 = Sub-total
      *  2 = Grand total

   Optional payload: the following object:

   .. list-table::
      :header-rows: 1

      *  -  Field
         -  Description
         -  Note
      *  -  **querySourceIds** |br|
            array of strings (GUIDs)
         -  An array of ids of query sources 
         -

**Response**

    An array of :doc:`models/ReportFunction` objects

**Samples**

   .. code-block:: http

      POST /api/report/function/0/Text HTTP/1.1

   Case 1: no Payload

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
            {
               "id": "8a74f4e0-b845-4b9e-adfa-bb678a116878",
               "name": "Count",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Numeric",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
               "id": "e3e16575-9739-4ff3-950a-7d149f96b4f0",
               "name": "Count Distinct",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Numeric",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
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
            {
               "id": "10a6655f-6954-462d-a57e-5df3c17089d5",
               "name": "Maximum",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Text",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
               "id": "36d8f605-1242-4c43-9b46-aced94b62709",
               "name": "Minimum",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Text",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            }
         ]

   .. code-block:: http

      POST /api/report/function/0/Text HTTP/1.1

   Case 2: with Request Payload::

      {
         "querySourceIds": [
            "35af86ee-6e8b-4e9b-829d-ea0b38ec575b"
         ]
      }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
            {
               "id": "8a74f4e0-b845-4b9e-adfa-bb678a116878",
               "name": "Count",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Numeric",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
               "id": "e3e16575-9739-4ff3-950a-7d149f96b4f0",
               "name": "Count Distinct",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Numeric",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
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
            {
               "id": "10a6655f-6954-462d-a57e-5df3c17089d5",
               "name": "Maximum",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Text",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            },
            {
               "id": "36d8f605-1242-4c43-9b46-aced94b62709",
               "name": "Minimum",
               "expression": null,
               "dataType": "Text",
               "formatDataType": "Text",
               "syntax": null,
               "expressionSyntax": null,
               "isOperator": false,
               "userDefined": false,
               "extendedProperties": {}
            }
         ]

GET report/allReports/(tenant\_id)
---------------------------------------

Returns a list of all reports filtered by tenant_id if provided.

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   To be updated

POST report/detectSchemaChange
---------------------------------------

Verifies that all report filter fields are without changes.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object

**Response**

   .. list-table::
      :header-rows: 1


      *  -  Field
         -  Required
         -  Description
         -  Note
      *  -  **hasChanged** |br|
            boolean
         -  R
         -  * true if there is no change
            * false if there is any change
         -
      *  -  **filterFields** |br|
            array of objects
         -	R
         -  An array of :doc:`models/ReportFilterField` objects
         -

**Samples**

   .. code-block:: http

      POST /api/report/detectSchemaChange HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
           	"reportKey" : {
           		"key" : "d797d877-6ae1-443a-b5f4-e9fbaeb884a8",
           		"modified" : null
           	},
           	"section" : 2,
           	"saveAs" : false,
           	"ignoreCheckChange" : true,
           	"report" : {
           		"name" : "don't know 2",
           		"type" : 0,
           		"previewRecord" : 10,
           		"advancedMode" : true,
           		"allowNulls" : false,
           		"isDistinct" : false,
           		"category" : {
           			"id" : "97bbeef3-0a80-4a0e-9640-962af1f3f1dc",
           			"name" : "",
           			"type" : 0
           		},
           		"subCategory" : {
           			"id" : null,
           			"name" : "",
           			"type" : 0
           		},
           		"reportDataSource" : [{
           				"aliasId" : "d4ed8e8e-3cc1-4815-a5c9-30602847345b_order_details",
           				"querySourceId" : "d4ed8e8e-3cc1-4815-a5c9-30602847345b",
           				"querySourceName" : "order_details",
           				"selected" : true,
           				"categoryId" : "3c88fe79-4284-4abe-8b25-5cff7b132474",
           				"primaryFields" : [{
           						"name" : "OrderID",
           						"alias" : "",
           						"dataType" : "smallint",
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
           						"originalName" : "OrderID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"hasAggregatedFunction" : false,
           						"querySource" : null,
           						"fullPath" : null,
           						"id" : "b5b95958-24f9-40a1-b95b-5e22c2d658d0",
           						"state" : 0,
           						"inserted" : true,
           						"version" : null,
           						"created" : null,
           						"createdBy" : null,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"modifiedBy" : null
           					}, {
           						"name" : "ProductID",
           						"alias" : "",
           						"dataType" : "smallint",
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
           						"originalName" : "ProductID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"hasAggregatedFunction" : false,
           						"querySource" : null,
           						"fullPath" : null,
           						"id" : "9c9f3f50-e223-41f4-adfe-0ff407e3bd4c",
           						"state" : 0,
           						"inserted" : true,
           						"version" : null,
           						"created" : null,
           						"createdBy" : null,
           						"modified" : "0001-01-01T00:00:00.0000000-08:00",
           						"modifiedBy" : null
           					}
           				]
           			}, {
           				"aliasId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc_orders",
           				"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           				"querySourceName" : "orders",
           				"selected" : true,
           				"categoryId" : "3c88fe79-4284-4abe-8b25-5cff7b132474",
           				"primaryFields" : [{
           						"name" : "OrderID",
           						"alias" : "",
           						"dataType" : "smallint",
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
           						"originalName" : "OrderID",
           						"isParameter" : false,
           						"isCalculated" : false,
           						"hasAggregatedFunction" : false,
           						"querySource" : null,
           						"fullPath" : null,
           						"id" : "0f19cd74-e4e3-4ada-acea-03f9c98a8e3b",
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
           		"reportRelationship" : [{
           				"tempId" : "73880663-9fe1-4e70-a02b-ea4471978a73",
           				"joinConnectionId" : "b513ddd4-ef23-4dbb-901d-2be802896616",
           				"foreignConnectionId" : "b513ddd4-ef23-4dbb-901d-2be802896616",
           				"joinQuerySourceId" : "d4ed8e8e-3cc1-4815-a5c9-30602847345b",
           				"joinQuerySourceName" : "order_details",
           				"joinDataSourceCategoryName" : "postgres",
           				"joinDataSourceCategoryId" : "3c88fe79-4284-4abe-8b25-5cff7b132474",
           				"foreignDataSourceCategoryName" : "postgres",
           				"foreignDataSourceCategoryId" : "3c88fe79-4284-4abe-8b25-5cff7b132474",
           				"foreignQuerySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           				"foreignQuerySourceName" : "orders",
           				"joinFieldId" : "b5b95958-24f9-40a1-b95b-5e22c2d658d0",
           				"joinFieldName" : "OrderID",
           				"foreignFieldId" : "0f19cd74-e4e3-4ada-acea-03f9c98a8e3b",
           				"foreignFieldName" : "OrderID",
           				"alias" : "",
           				"aliasTempId" : "alias_709",
           				"systemRelationship" : false,
           				"joinType" : "Inner",
           				"parentRelationshipId" : "aa176ab4-15cb-451f-8f6a-a46272cf0e15",
           				"position" : null,
           				"relationshipKeyJoins" : [],
           				"reportId" : "d797d877-6ae1-443a-b5f4-e9fbaeb884a8",
           				"selectedForeignAlias" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc_orders",
           				"id" : "73880663-9fe1-4e70-a02b-ea4471978a73",
           				"state" : 0,
           				"validationKey" : "73880663-9fe1-4e70-a02b-ea4471978a73",
           				"relationshipPosition" : 0,
           				"needAlias" : false,
           				"previousAlias" : "",
           				"invalidAlias" : null,
           				"hidden" : false,
           				"level" : 1
           			}
           		],
           		"reportFilter" : {
           			"logic" : "",
           			"visible" : true,
           			"filterFields" : [{
           					"connectionName" : "postgres",
           					"querySourceCategoryName" : "public",
           					"sourceFieldName" : "Freight",
           					"sourceFieldVisible" : true,
           					"sourceFieldFilterable" : true,
           					"sourceDataObjectName" : "orders",
           					"dataType" : "Numeric",
           					"filterId" : "8c572300-61ad-47ef-8496-94686f7f1301",
           					"querySourceFieldId" : "46875d94-d79e-4b39-a863-aaede78e176b",
           					"querySourceType" : "Table",
           					"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           					"relationshipId" : null,
           					"alias" : "Freight",
           					"position" : 1,
           					"visible" : false,
           					"required" : false,
           					"cascading" : true,
           					"operatorId" : null,
           					"operatorSetting" : null,
           					"value" : null,
           					"sortType" : "Unsorted",
           					"fontFamily" : "Roboto",
           					"fontSize" : 8,
           					"textColor" : null,
           					"backgroundColor" : null,
           					"fontBold" : false,
           					"fontItalic" : false,
           					"fontUnderline" : false,
           					"id" : "6f31e0cb-1cdf-416a-a5c5-8a89236903e3",
           					"state" : 0,
           					"modified" : null,
           					"dateTimeNow" : "",
           					"isParameter" : false,
           					"sourceDataObjectFullName" : "postgres.public.orders",
           					"selected" : false,
           					"dataFormatId" : null
           				}
           			],
           			"id" : "8c572300-61ad-47ef-8496-94686f7f1301",
           			"reportId" : "d797d877-6ae1-443a-b5f4-e9fbaeb884a8"
           		},
           		"reportPart" : [{
           				"isDirty" : false,
           				"reportPartContent" : {
           					"isDirty" : false,
           					"type" : 3,
           					"columns" : {
           						"text" : null,
           						"properties" : {
           							"addSideTotal" : false,
           							"useExpanders" : false
           						},
           						"settings" : {},
           						"elements" : [{
           								"reportPartContent" : null,
           								"isDirty" : false,
           								"name" : "Group (ShipCountry)",
           								"properties" : {
           									"isDirty" : true,
           									"fieldItemVisible" : true,
           									"dataFormattings" : {
           										"function" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
           										"functionInfo" : {
           											"id" : "7f942ac7-08d8-41fa-9e89-bad96f07f102",
           											"name" : "Group",
           											"expression" : null,
           											"dataType" : "Text",
           											"formatDataType" : "Text",
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
           								"position" : 1,
           								"field" : {
           									"fieldId" : "8e65a222-66f1-470b-9f53-7f6481110d5e",
           									"fieldName" : "ShipCountry",
           									"fieldNameAlias" : "Group (ShipCountry)",
           									"dataFieldType" : "Text",
           									"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           									"querySourceType" : "Table",
           									"sourceAlias" : "orders",
           									"relationshipId" : "00000000-0000-0000-0000-000000000000",
           									"visible" : true,
           									"calculatedTree" : null,
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
           						"properties" : {
           							"useExpanders" : false
           						},
           						"settings" : {},
           						"elements" : [{
           								"reportPartContent" : null,
           								"isDirty" : false,
           								"name" : "ShipCity",
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
           								"position" : 1,
           								"field" : {
           									"fieldId" : "63cb0d69-1451-4c51-b825-6946975e58c5",
           									"fieldName" : "ShipCity",
           									"fieldNameAlias" : "ShipCity",
           									"dataFieldType" : "Text",
           									"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           									"querySourceType" : "Table",
           									"sourceAlias" : "orders",
           									"relationshipId" : "00000000-0000-0000-0000-000000000000",
           									"visible" : true,
           									"calculatedTree" : null,
           									"isCalculated" : false
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}, {
           								"reportPartContent" : null,
           								"isDirty" : false,
           								"name" : "ShipName",
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
           								"position" : 2,
           								"field" : {
           									"fieldId" : "a28f4649-bf0a-4d2f-ac4b-3ed9e2a4c2a5",
           									"fieldName" : "ShipName",
           									"fieldNameAlias" : "ShipName",
           									"dataFieldType" : "Text",
           									"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           									"querySourceType" : "Table",
           									"sourceAlias" : "orders",
           									"relationshipId" : "00000000-0000-0000-0000-000000000000",
           									"visible" : true,
           									"calculatedTree" : null,
           									"isCalculated" : false
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}
           						],
           						"name" : "rows"
           					},
           					"values" : {
           						"text" : null,
           						"properties" : {},
           						"settings" : {},
           						"elements" : [{
           								"reportPartContent" : null,
           								"isDirty" : false,
           								"name" : "Sum (OrderID)",
           								"properties" : {
           									"isDirty" : true,
           									"fieldItemVisible" : true,
           									"dataFormattings" : {
           										"function" : "902a9168-fc01-4a35-92fb-ea67942d099d",
           										"functionInfo" : {
           											"id" : "902a9168-fc01-4a35-92fb-ea67942d099d",
           											"name" : "Sum",
           											"expression" : null,
           											"dataType" : "Numeric",
           											"formatDataType" : "Numeric",
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
           								"position" : 1,
           								"field" : {
           									"fieldId" : "0f19cd74-e4e3-4ada-acea-03f9c98a8e3b",
           									"fieldName" : "OrderID",
           									"fieldNameAlias" : "Sum (OrderID)",
           									"dataFieldType" : "Numeric",
           									"querySourceId" : "b5f20d85-1a96-493a-8b1e-15dc9b1f26bc",
           									"querySourceType" : "Table",
           									"sourceAlias" : "orders",
           									"relationshipId" : "00000000-0000-0000-0000-000000000000",
           									"visible" : true,
           									"calculatedTree" : null,
           									"isCalculated" : false
           								},
           								"isDeleted" : false,
           								"isSelected" : false
           							}
           						],
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
           							"gridStyle" : "Pivot",
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
           				"reportId" : "d797d877-6ae1-443a-b5f4-e9fbaeb884a8",
           				"positionX" : 0,
           				"positionY" : 0,
           				"width" : 12,
           				"height" : 4,
           				"state" : 3,
           				"modified" : null,
           				"numberOfRecord" : 0,
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
           				"configField" : {},
           				"expandedLevel" : 0,
           				"title" : "Grid",
           				"id" : "9e632295-41c6-41ba-a235-29c525d6ef59"
           			}
           		],
           		"header" : {
           			"visible" : false,
           			"items" : [{
           					"isDirty" : false,
           					"type" : "image",
           					"label" : "Image",
           					"id" : "formatDetails_17",
           					"positionX" : 0,
           					"positionY" : 0,
           					"width" : 6,
           					"height" : 6,
           					"name" : "Logo Image",
           					"value" : "",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"imageUrl" : "http://",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_18",
           					"positionX" : 20,
           					"positionY" : 0,
           					"width" : 12,
           					"height" : 2,
           					"name" : "Report Name",
           					"value" : "{reportName}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "thinHorizontalRule",
           					"label" : "Horizontal Rule",
           					"id" : "formatDetails_19",
           					"positionX" : 20,
           					"positionY" : 4,
           					"width" : 12,
           					"height" : 1,
           					"name" : "Upper Separator Line",
           					"value" : "{horizontalRule}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 2
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_20",
           					"positionX" : 20,
           					"positionY" : 5,
           					"width" : 6,
           					"height" : 2,
           					"name" : "Report Generated",
           					"value" : "Report Generated:",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_21",
           					"positionX" : 20,
           					"positionY" : 7,
           					"width" : 6,
           					"height" : 2,
           					"name" : "User",
           					"value" : "User:",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_22",
           					"positionX" : 20,
           					"positionY" : 9,
           					"width" : 6,
           					"height" : 2,
           					"name" : "Tenant",
           					"value" : "Tenant:",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "dateTime",
           					"label" : "Date Time",
           					"id" : "formatDetails_23",
           					"positionX" : 26,
           					"positionY" : 5,
           					"width" : 6,
           					"height" : 2,
           					"name" : "Current Date Time",
           					"value" : "{currentDateTime}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_24",
           					"positionX" : 26,
           					"positionY" : 7,
           					"width" : 6,
           					"height" : 2,
           					"name" : "Current User Name",
           					"value" : "{currentUserName}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_25",
           					"positionX" : 26,
           					"positionY" : 9,
           					"width" : 6,
           					"height" : 2,
           					"name" : "Tenant Name",
           					"value" : "{tenantName}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "horizontalRule",
           					"label" : "Horizontal Rule",
           					"id" : "formatDetails_26",
           					"positionX" : 0,
           					"positionY" : 11,
           					"width" : 32,
           					"height" : 1,
           					"name" : "Lower Separator Line",
           					"value" : "{horizontalRule}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 4
           				}
           			]
           		},
           		"footer" : {
           			"visible" : false,
           			"items" : [{
           					"isDirty" : false,
           					"type" : "horizontalRule",
           					"label" : "Horizontal Rule",
           					"id" : "formatDetails_27",
           					"positionX" : 0,
           					"positionY" : 0,
           					"width" : 32,
           					"height" : 1,
           					"name" : "Separator Line",
           					"value" : "{horizontalRule}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 4
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_28",
           					"positionX" : 0,
           					"positionY" : 1,
           					"width" : 10,
           					"height" : 2,
           					"name" : "Footer Text",
           					"value" : "Footer Text",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "text",
           					"label" : "Text",
           					"id" : "formatDetails_29",
           					"positionX" : 20,
           					"positionY" : 1,
           					"width" : 4,
           					"height" : 2,
           					"name" : "Page",
           					"value" : "Page",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "pageNumber",
           					"label" : "Page Number",
           					"id" : "formatDetails_30",
           					"positionX" : 24,
           					"positionY" : 1,
           					"width" : 8,
           					"height" : 2,
           					"name" : "Page Number",
           					"value" : "{pageNumber}",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}
           			]
           		},
           		"titleDescription" : {
           			"visible" : false,
           			"items" : [{
           					"isDirty" : false,
           					"type" : "title",
           					"label" : "Title",
           					"id" : "formatDetails_31",
           					"name" : "Title",
           					"value" : "",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}, {
           					"isDirty" : false,
           					"type" : "description",
           					"label" : "Description",
           					"id" : "formatDetails_32",
           					"name" : "Description",
           					"value" : "",
           					"font" : {
           						"family" : "Roboto",
           						"size" : 14,
           						"bold" : false,
           						"italic" : false,
           						"underline" : false,
           						"color" : "#000",
           						"backgroundColor" : "#fff"
           					},
           					"color" : "#000",
           					"dashStyle" : "solid",
           					"thickness" : 1
           				}
           			]
           		},
           		"version" : 0,
           		"schedules" : []
           	},
           	"expandedLevel" : 0
         }

   Sample response::

      {
         "hasChanged" : false,
         "filterFields" : []
      }

POST report/updateResults
---------------------------------------

Updates the report data model.

**Request**

      Payload: a :doc:`models/ReportSavingParameter` object

**Response**

      A :doc:`models/ReportSavingResult` object

**Samples**

      To be updated

POST report/loadAccesses
---------------------------------------

Returns a list of all accesses.

**Request**

      Payload: an :doc:`models/AccessPagedRequest` object

**Response**

      A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/UserPermission` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadAccesses HTTP/1.1

   Request Payload:

      .. code-block:: json

         {
           "reportId": "840ba6a8-dfe3-4d92-8341-63e56b95a038",
           "accesses": [],
           "criteria": [
             {
               "key": "All",
               "value": "",
               "operation": 1
             }
           ],
           "pageIndex": 1,
           "pageSize": 10,
           "sortOrders": [
             {
               "key": "shareWith",
               "descending": true
             }
           ]
         }

   Successful response::

      {
        "result": [],
        "pageIndex": 1,
        "pageSize": 10,
        "total": 0
      }

POST report/loadSchedules
---------------------------------------

Returns a list of all scheduled deliveries.

**Request**

      Payload: an :doc:`models/SubscriptionPagedRequest` object

**Response**

      A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/Subscription` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadSchedules HTTP/1.1

   Request Payload::

      {
         "reportId" : "17bbaf02-0b59-4224-93b3-41bb14da516f",
         "subscriptions" : [],
         "criteria" : [{
               "key" : "All",
               "value" : "",
               "operation" : 1
            }
         ],
         "pageIndex" : 1,
         "pageSize" : 10,
         "sortOrders" : [{
               "key" : "name",
               "descending" : true
            }
         ]
      }

   Successful response::

      {
         "result" : [],
         "pageIndex" : 1,
         "pageSize" : 10,
         "total" : 0
      }

GET report/reportPart/{report_part_id}/(report_id)
---------------------------------------------------

Returns the report part definition specified by report_part_id from draft (using report_id) or from database (without report_id).

**Request**

      No payload

**Response**

   A :doc:`models/ReportPartDefinition` object.

**Samples**

   .. code-block:: http

      GET /api/report/reportPart/7391FEC3-53A1-411D-B92E-02C007FB4DD6 HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
        	"reportPartContent" : {
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
        	},
        	"title" : "Grid",
        	"positionX" : 0,
        	"positionY" : 0,
        	"width" : 12,
        	"height" : 4,
        	"reportId" : "055899a3-8886-4099-b360-fabf4656f5ce",
        	"numberOfRecord" : 0,
        	"id" : "7391fec3-53a1-411d-b92e-02c007fb4dd6",
        	"state" : 0,
        	"inserted" : true,
        	"version" : 1,
        	"created" : "2016-08-29T09:17:05.13",
        	"createdBy" : null,
        	"modified" : "2016-08-29T09:17:05.13",
        	"modifiedBy" : null
        }

.. _POST_report/validateExistingField:

POST report/validateExistingField
---------------------------------------

Validates that some fields exist in a report.

**Request**

      Payload: a :doc:`models/ReportValidation` object.

**Response**

      An :doc:`models/OperationResult` object with the **data** field populated:

      * true: the fields exist

**Samples**

   .. code-block:: http

      POST /api/report/validateExistingField HTTP/1.1

   Request payload::

      To be updated

   Successful response::

      {
         "success": true,
         "data": true
      }


GET report/reportId/(tenant_id)?reportName=value&categoryName=value
--------------------------------------------------------------------

Returns report id from report name and category name.

**Request**

      No payload

**Response**

      An :doc:`models/OperationResult` object with **data** field populated with the id of the report if found.

**Samples**

   .. code-block:: http

      GET /api/report/reportId?reportName=Test%20Report&categoryName=Category%201 HTTP/1.1

   No payload

   Sample response::

      {
         "success": true,
         "data": "4e2d54c8-20e7-437f-a5ce-43e963c763a2"
      }

.. _POST_report/validateExistingReport:

POST report/validateExistingReport
---------------------------------------

Validates that a report exists in a category.

**Request**

      Payload: a :doc:`models/ReportValidation` object.

**Response**

      An :doc:`models/OperationResult` object with **data** field populated

      * true if the report exists
      * false if not

**Samples**

   .. code-block:: http

      POST /api/report/validateExistingReport HTTP/1.1

   Request Payload::

      {
      	"tenantId": "de0c01f3-63ab-4f85-90ff-fe2f1d4fa00b",
      	"reportName": "TestReport",
      	"categoryName": "Category 1"
      }

   Successful response::

      {
         "success": true,
         "messages":null,
         "data": true
      }

GET report/reportsByTenant/(tenant_id)
---------------------------------------

Returns list of reports by tenant, with each report containing a list of report parts.

**Request**

   No payload

**Response**

   An array of :doc:`models/ReportPartDefinition` objects.

**Samples**

   .. code-block:: http

      GET /api/report/reportsByTenant HTTP/1.1

   Request:

      No payload

   Sample response::

      To be updated


POST report/updateRenderingTime
---------------------------------------

Updates the rendering time of a report.

**Request**

   Payload: a :doc:`models/ReportDefinition` object.

**Response**

   An :doc:`models/OperationResult` object with the **success** field populated.

**Samples**

   .. code-block:: http

      POST /api/report/updateRenderingTime HTTP/1.1

   Request payload::

      To be updated

   Sample response::

      To be updated


GET report/isReportValid/(report_id)
---------------------------------------

Returns true if there is a report definition for the specified report_id.

**Request**

   No payload

**Response**

   * true if there is a report definition for the specified report_id
   * false if report_id is null or there is no report definition

**Samples**

   .. code-block:: http

      GET /api/report/isReportValid/3501e30d-6ded-4f26-9922-011633ace5ab HTTP/1.1

   Sample response::

      true

POST report/areReportsValid
---------------------------------------

Validates if reports are valid.

**Request**

   Payload: an array of report ids (GUIDs).

**Response**

   An array of :doc:`models/OperationResult` objects, with **success** field true if that report is valid.

**Samples**

   To be updated

POST report/printDraft
---------------------------------------

Saves report as draft for printing.

**Request**

   Payload: a :doc:`models/ReportSavingParameter` object.

**Response**

   The id of the report in draft.

**Samples**

   To be updated

GET report/printDraft/{report_id}
---------------------------------------

Gets report as draft for printing.

**Request**

   No payload

**Response**

   A :doc:`models/ReportDefinition` object.

**Samples**

   To be updated

GET report/accessPriority/(report_dashboard_id)
------------------------------------------------

Returns access priority for report/dashboard.

**Request**

   No payload

**Response**

   The access priority

**Samples**

   .. code-block:: http

      GET /api/report/accessPriority/e09f9d45-b721-4012-b8e7-c31c58d52af3 HTTP/1.1

   Response::

      1

.. _POST_report/timePeriod:

POST report/timePeriod
------------------------------------------------

Saves a customed InTimePeriod.

**Request**

   A :doc:`models/TimePeriod` object

**Response**

   true if the save is successful

**Samples**

   To be updated

DELETE report/timePeriod/{time_period_id}
------------------------------------------------

Deletes the customed InTimePeriod specified by time_period_id.

**Request**

   No payload

**Response**

   true if the deletion is successful

**Samples**

   To be updated

GET report/reportPart/crossfiltering/{report_part_id}
------------------------------------------------------------------

Returns a list of ids of cross-filtering report parts in the same report as the specified report part, including itself.

.. versionadded:: 2.0.6

**Request**

   No payload

**Response**

   An array of strings (GUIDs)

**Samples**

   .. code-block:: http

      GET /api/report/reportPart/crossfiltering/04192bb1-7138-4e45-8fd4-506793a29704 HTTP/1.1

   Response::

      ["04192bb1-7138-4e45-8fd4-506793a29704","edaf3f13-7ff8-4d0f-a99b-56396080155a"]


GET report/validateEmbeddedReport/(tenant_id)?reportId=value&reportName=value&reportPartName=value
-----------------------------------------------------------------------------------------------------

Validates that logged in user can access one and only one report part from the specified reportName and reportPartName.

.. versionadded:: 2.2.2

**Request**

   .. list-table::
      :header-rows: 1
      :widths: 20 10 70

      *  -  Parameter
         -  Required
         -  Description
      *  -  **reportId** |br|
            string (GUID)
         -  O
         -  The id of the embedded report. |br|
            If not available, all reports containing the specified reportPartName will be checked.
      *  -  **reportName** |br|
            string
         -  R
         -  The name of the embedded report.
      *  -  **reportPartName** |br|
            string
         -  R
         -  The name of the embedded report part.

**Response**

   .. list-table::
      :header-rows: 1

      *  -  Field
         -  Description
      *  - **reportId** |br|
           string (GUID)
         -  The id of the unique report
      *  - **reportPartId** |br|
           string (GUID)
         -  The id of the unique report part

**Samples**

   To be updated
