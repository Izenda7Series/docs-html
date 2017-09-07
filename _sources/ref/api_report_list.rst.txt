

============================
Report List APIs
============================

The **Report List** page allows user to

.. hlist::
   :columns: 2

   * browse reports by type, categories and sub-categories
   * view report history
   * copy and move reports between categories
   * print and export reports
   * set up subscriptions
   * delete reports
   * rename and delete report categories

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `POST report/list`_
     - .. deprecated:: 2.0.0
          superseded by `POST report/list2(?includeHashCode=true)`_

       Returns reports for the report list.
   * - `POST report/list2(?includeHashCode=true)`_
     - Returns reports for the report list with total number of items.
   * - `GET report/info/{report_id}/(version)`_
     - Returns report properties for the report specified by report_id and version. |br|
       Returns latest version if version parameter is null.

       .. versionchanged:: 2.2

          Added optional version parameter
   * - `POST report/copy`_
     - Copies report to another name or category.
   * - `POST report/move`_
     - Moves report to another name or category.
   * - `POST report/history`_
     - Returns report history.
   * - `POST report/history/{report_id}/(version)`_
     - Returns a specific version of a report. |br|
       Returns oldest available version when version parameter is missing.
   * - `DELETE report/history/{report_id}/(version)`_
     - Deletes a specific version of a report. |br|
       Deletes oldest available version when version parameter is missing.
   * - `GET report/tenants/(tenant_id)/categories/(category_id)/reports`_
     - Returns all reports in the category specified by category_id and in the tenant specified by tenant_id.
   * - `POST report/delete`_
     - Deletes a report.
   * - `POST report/loadSubscriptions`_
     - Returns a list of report subscriptions.
   * - `POST report/emailTemplates/{isSubscription}`_
     - Returns a list of report email templates.
   * - `POST report/subscription/validate`_
     - Validates a subscription schedule and delivery template.
   * - `POST report/subscriptions`_
     - Saves a list of report subscriptions.
   * - `POST report/deleteAllArchiveVersions`_
     - Removes all archived versions of all reports.
   * - `POST report/findByName`_
     - Returns the first report definition matching specified name and other criteria. |br|
       Needs SystemAdmin permission.

       .. versionadded:: 2.0.3

POST report/list
------------------------------------------------

.. deprecated:: 2.0.0
     superseded by `POST report/list2(?includeHashCode=true)`_

Returns reports for the report list.

**Request**

    Payload: a :doc:`models/ReportDashboardSearchCriteria` object

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      POST /api/report/list HTTP/1.1

   Request payload::

      {
         "tenantId" : null,
         "type" : 0
      }

   Excerpt of the response::

      [{
           "reports" : [],
           "subCategories" : [{
                 "reports" : [{
                       "name" : "Report in Category 1",
                    }
                 ],
                 "subCategories" : null,
                 "name" : null,
              }, {
                 "reports" : [{
                       "name" : "Report #1 in Category 1 - Sub-category 2",
                    }, {
                       "name" : "Report #2 in Category 1 - Sub-category 2",
                    }
                 ],
                 "subCategories" : null,
                 "name" : "Sub-category 2",
              }
           ],
           "name" : "Category 1",
        }, {
           "reports" : [],
           "subCategories" : [{
                 "reports" : [{
                       "name" : null,
                    }
                 ],
                 "subCategories" : null,
                 "name" : null,
              }
           ],
           "name" : "Category 2",
        }, {
           "reports" : [],
           "subCategories" : [{
                 "reports" : [{
                       "name" : "Report #1 in Uncategorized",
                    }, {
                       "name" : "Report #2 in Uncategorized",
                    }
                 ],
                 "subCategories" : null,
                 "name" : null,
              }
           ],
           "name" : null,
        }
      ]

.. _POST_report/list2:

POST report/list2(?includeHashCode=true)
------------------------------------------------

Returns reports for the report list with total number of item

**Request**

    Payload: a :doc:`models/ReportDashboardSearchCriteria` object

    Optional query string: includeHashCode=true

**Response**

   *  Without includeHashCode: an array of :doc:`models/Category` objects
   *  With includeHashCode=true: the following object:

      .. list-table::
         :header-rows: 1

         *  -  Field
            -  Description
            -  Note
         *  -  **data** |br|
               array of objects
            -  An array of :doc:`models/Category` objects
            -
         *  -  **hashcode** |br|
               string
            -  The hashcode
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

      POST /api/report/list2?includeHashCode=true HTTP/1.1

   Sample payload::

      {
         "tenantId": "b930adf8-5bfd-4214-97e3-f709f10721fb",
         "isUncategorized": false,
         "skipItems": 0,
         "pageSize": 100,
         "parentIds": [],
         "includeGlobalCategory": true,
         "isGlobal": null,
         "criterias": [
            {
               "key": "CategoryId"
            }
         ]
      }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "data": [
               {
                  "name": "Global Categories",
                  "type": 0,
                  "parentId": null,
                  "tenantId": null,
                  "isGlobal": true,
                  "canDelete": false,
                  "editable": false,
                  "savable": false,
                  "subCategories": [
                     {
                        "name": "Common Reports",
                        "type": 0,
                        "parentId": null,
                        "tenantId": null,
                        "isGlobal": true,
                        "canDelete": false,
                        "editable": false,
                        "savable": false,
                        "subCategories": [
                           {
                              "name": null,
                              "type": 0,
                              "parentId": "b5f6be66-9a00-4422-ad2f-31e00ecfd2f9",
                              "tenantId": null,
                              "isGlobal": true,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "Example Report Name",
                                    "reportDataSource": [
                                       {
                                          "reportId": "daefaa42-75b2-4b07-8ef8-019134109054",
                                          "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                                          "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                                          "querySourceCategoryId": "0e8d2b0b-010d-46e5-8dc4-ff048d6f5e07",
                                          "connectionId": "ca12331b-f917-47ae-8397-3758bc393bdb",
                                          "selected": false,
                                          "id": null,
                                          "state": 0,
                                          "deleted": false,
                                          "inserted": true,
                                          "version": null,
                                          "created": null,
                                          "createdBy": "User1 ACME",
                                          "modified": null,
                                          "modifiedBy": null
                                       }
                                    ],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "b5f6be66-9a00-4422-ad2f-31e00ecfd2f9",
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-04-26T14:12:21.023",
                                    "owner": "John Doe",
                                    "ownerId": "d928e941-19ef-4382-ba60-7238cb555631",
                                    "excludedRelationships": null,
                                    "numberOfView": 1,
                                    "renderingTime": 301,
                                    "createdById": "d928e941-19ef-4382-ba60-7238cb555631",
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
                                    "deletable": false,
                                    "editable": false,
                                    "movable": false,
                                    "copyable": false,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": true,
                                    "id": "daefaa42-75b2-4b07-8ef8-019134109054",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-04-26T14:07:20.527",
                                    "createdBy": "John Doe",
                                    "modified": "2017-04-26T14:07:20.527",
                                    "modifiedBy": "John Doe"
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
                              "createdBy": "User1 ACME",
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
                        "id": "b5f6be66-9a00-4422-ad2f-31e00ecfd2f9",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "User1 ACME",
                        "modified": null,
                        "modifiedBy": null
                     },
                     {
                        "name": "Sample Reports",
                        "type": 0,
                        "parentId": null,
                        "tenantId": null,
                        "isGlobal": true,
                        "canDelete": false,
                        "editable": false,
                        "savable": false,
                        "subCategories": [
                           {
                              "name": null,
                              "type": 0,
                              "parentId": "7f4adac8-df78-4aa0-8695-b78c55b7a47c",
                              "tenantId": null,
                              "isGlobal": true,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "Sample Orders Report",
                                    "reportDataSource": [
                                       {
                                          "reportId": "f9348e0e-7572-426d-bf83-0d6a043aaeb8",
                                          "querySourceId": "f4ae63fc-4c10-4672-9cd2-4a9d40434a4c",
                                          "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                                          "querySourceCategoryId": "0e8d2b0b-010d-46e5-8dc4-ff048d6f5e07",
                                          "connectionId": "ca12331b-f917-47ae-8397-3758bc393bdb",
                                          "selected": false,
                                          "id": null,
                                          "state": 0,
                                          "deleted": false,
                                          "inserted": true,
                                          "version": null,
                                          "created": null,
                                          "createdBy": "User1 ACME",
                                          "modified": null,
                                          "modifiedBy": null
                                       }
                                    ],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "7f4adac8-df78-4aa0-8695-b78c55b7a47c",
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "00000000-0000-0000-0000-000000000000",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": "2017-04-26T05:17:30.237",
                                    "owner": "John Doe",
                                    "ownerId": "d928e941-19ef-4382-ba60-7238cb555631",
                                    "excludedRelationships": null,
                                    "numberOfView": 1,
                                    "renderingTime": 395,
                                    "createdById": "d928e941-19ef-4382-ba60-7238cb555631",
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
                                    "deletable": false,
                                    "editable": false,
                                    "movable": false,
                                    "copyable": false,
                                    "accessPriority": 1,
                                    "active": true,
                                    "fullPath": null,
                                    "computeNameSettings": null,
                                    "isGlobal": true,
                                    "id": "f9348e0e-7572-426d-bf83-0d6a043aaeb8",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 2,
                                    "created": "2017-04-26T04:58:33.193",
                                    "createdBy": "John Doe",
                                    "modified": "2017-04-26T14:03:58.093",
                                    "modifiedBy": "John Doe"
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
                              "createdBy": "User1 ACME",
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
                        "id": "7f4adac8-df78-4aa0-8695-b78c55b7a47c",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "User1 ACME",
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
                  "id": "2a83e3ce-f91b-4f14-910d-76cadf42d0fe",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "User1 ACME",
                  "modified": null,
                  "modifiedBy": null
               },
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
                        "name": "ACME User1 Reports",
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
                              "parentId": "41e231f8-cde8-450d-bad3-6c029839024c",
                              "tenantId": null,
                              "isGlobal": false,
                              "canDelete": false,
                              "editable": false,
                              "savable": false,
                              "subCategories": [],
                              "checked": false,
                              "reports": [
                                 {
                                    "name": "ACME Orders Report",
                                    "reportDataSource": [
                                       {
                                          "reportId": "d574770e-e7ad-4a0a-a228-44f387e27a91",
                                          "querySourceId": "6b33591c-4fe5-47cd-8195-58be404deca3",
                                          "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                                          "querySourceCategoryId": "62e49cf3-4513-49ea-a710-b9630b6b9f20",
                                          "connectionId": "f9fc7a8c-39b3-4d05-bc2c-cb194ef2d6f5",
                                          "selected": false,
                                          "id": null,
                                          "state": 0,
                                          "deleted": false,
                                          "inserted": true,
                                          "version": null,
                                          "created": null,
                                          "createdBy": "User1 ACME",
                                          "modified": null,
                                          "modifiedBy": null
                                       }
                                    ],
                                    "type": 0,
                                    "previewRecord": 0,
                                    "advancedMode": false,
                                    "allowNulls": false,
                                    "isDistinct": false,
                                    "categoryId": "41e231f8-cde8-450d-bad3-6c029839024c",
                                    "categoryName": null,
                                    "subCategoryId": null,
                                    "subCategoryName": null,
                                    "tenantId": "b930adf8-5bfd-4214-97e3-f709f10721fb",
                                    "tenantName": null,
                                    "description": "",
                                    "title": null,
                                    "lastViewed": null,
                                    "owner": "User1 ACME",
                                    "ownerId": "ea22549d-4384-4b3c-9ae7-1f73ca16ad27",
                                    "excludedRelationships": null,
                                    "numberOfView": 0,
                                    "renderingTime": 0,
                                    "createdById": "ea22549d-4384-4b3c-9ae7-1f73ca16ad27",
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
                                    "id": "d574770e-e7ad-4a0a-a228-44f387e27a91",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": 1,
                                    "created": "2017-04-26T04:54:59.84",
                                    "createdBy": "User1 ACME",
                                    "modified": "2017-04-26T04:54:59.84",
                                    "modifiedBy": "User1 ACME"
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
                              "createdBy": "User1 ACME",
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
                        "id": "41e231f8-cde8-450d-bad3-6c029839024c",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "User1 ACME",
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
                  "id": "09f8c4ab-0fe8-4e03-82d1-7949e3738f87",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "User1 ACME",
                  "modified": null,
                  "modifiedBy": null
               }
            ],
            "hashcode": "f567df70cd9be737e65afd3b95d",
            "totalItems": 8,
            "numOfChilds": 2,
            "numOfCheckedChilds": 0,
            "indeterminate": false,
            "isLastPage": true
         }

GET report/info/{report_id}/(version)
------------------------------------------------

Returns report properties for the report specified by report_id and version. |br|
Returns latest version if version parameter is null.

.. versionchanged:: 2.2

   Added optional version parameter

**Request**

    No payload

**Response**

    A :doc:`models/Report` object

**Samples**

   .. code-block:: http

      GET /api/report/info/41023c5b-3fe5-4a62-8ecf-7aae8974f63f HTTP/1.1

   Response::

      {
         "name": "TestReport02",
         "type": 1,
         "previewRecord": 10,
         "advancedMode": true,
         "allowNulls": false,
         "isDistinct": false,
         "categoryId": "1c0060df-ebf9-4287-a67a-900b014afc0d",
         "categoryName": null,
         "subCategoryId": "8ca0e7c5-b2ef-4ecd-a663-6620a63d1dae",
         "subCategoryName": null,
         "tenantId": null,
         "description": null,
         "title": null,
         "lastViewed": null,
         "owner": null,
         "header": null,
         "footer": null,
         "titleDescription": null,
         "id": "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
         "state": 0,
         "inserted": true,
         "version": 2,
         "created": "2016-07-13T08:05:25.587",
         "createdBy": null,
         "modified": "2016-07-14T03:51:38",
         "modifiedBy": null
      }

POST report/copy
------------------------------------------------

Copies report to another name or category.

**Request**

    Payload: a :doc:`models/ReportDefinition` object

**Response**

    * The new id string value if success
    * Empty string value if not.

**Samples**

   .. code-block:: http

      POST /api/report/copy HTTP/1.1

   Request payload::

      {
        "id" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "name" : "TestReport02_copied",
        "version" : 0,
        "category" : {
           "id" : "1c0060df-ebf9-4287-a67a-900b014afc0d",
           "name" : "Category01_renamed",
           "type" : 1
        },
        "subCategory" : {
           "type" : 1,
           "parentId" : "1c0060df-ebf9-4287-a67a-900b014afc0d"
        },
        "type" : 1,
        "tenantId" : null
      }

   Response::

      "552d20ce-1269-4cb4-a679-0cd51d3e2058"

POST report/move
------------------------------------------------

Moves report to another name or category.

**Request**

    Payload: a :doc:`models/ReportDefinition` object

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/report/list HTTP/1.1

   Request payload::

      {
        "id" : "552d20ce-1269-4cb4-a679-0cd51d3e2058",
        "name" : "TestReport02_copied",
        "version" : 0,
        "category" : {
           "id" : "98fb305b-b340-4245-88da-bb7f34b4211e",
           "name" : "Category02",
           "type" : 1
        },
        "subCategory" : {
           "type" : 1,
           "parentId" : "98fb305b-b340-4245-88da-bb7f34b4211e"
        },
        "type" : 1,
        "tenantId" : null
      }

   Response::

      true

POST report/history
------------------------------------------------

Returns report history.

**Request**

    Payload: a :doc:`models/ReportHistoryPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/ReportHistory` objects

**Samples**

   .. code-block:: http

      POST /api/report/history HTTP/1.1

   Request payload::

      {
        "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "tenantId" : null,
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "version",
              "descending" : true
           }
        ]
      }

   Response::

      {
        "result" : [{
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "reportName" : "TestReport02",
              "description" : null,
              "definition" : null,
              "status" : "Active",
              "id" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "state" : 0,
              "inserted" : true,
              "version" : 2,
              "created" : "2016-07-13T08:05:25.587",
              "createdBy" : null,
              "modified" : "2016-07-14T03:51:38",
              "modifiedBy" : null
           }, {
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "reportName" : "Report01",
              "description" : null,
              "definition" : null,
              "status" : "Archived",
              "id" : "abd8102b-b807-4ac5-9520-812a21e44b55",
              "state" : 0,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-07-13T08:05:25.587",
              "createdBy" : null,
              "modified" : "2016-07-13T08:05:25.587",
              "modifiedBy" : null
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "total" : 2
      }

POST report/history/{report_id}/(version)
------------------------------------------------

Returns a specific version of a report.

Returns oldest available version when version parameter is missing.

**Request**

    No payload

**Response**

    An :doc:`models/ReportDefinition` object

**Samples**

   .. code-block:: http

      GET /api/report/history/41023c5b-3fe5-4a62-8ecf-7aae8974f63f/ HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

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


DELETE report/history/{report_id}/(version)
------------------------------------------------

Deletes a specific version of a report.

Deletes oldest available version when version parameter is missing.

**Request**

    No payload

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      DELETE /api/report/history/41023c5b-3fe5-4a62-8ecf-7aae8974f63f/1 HTTP/1.1

   Response::

      true

GET report/tenants/(tenant_id)/categories/(category_id)/reports
--------------------------------------------------------------------

Returns all reports in the category specified by category_id and in the tenant specified by tenant_id.

**Request**

    No payload

**Response**

    An array of :doc:`models/Report` objects

**Samples**

   .. code-block:: http

      GET /api/report/tenants//categories/5d034fc7-0cc8-46b7-beb3-35b22c57827c/reports HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
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
         ]

POST report/rename
------------------------------------------------

Renames a report.

**Request**

    Payload: a :doc:`models/ReportRenameParameter` object

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/report/rename HTTP/1.1

   Request payload::

      {
        "name": "FactInternetSales DayOfWk",
        "reportKey": {
          "key": "45f17b8a-3708-4f36-80ef-9178b7124841"
        }
      }

   Response::

      true

POST report/delete
------------------------------------------------

Deletes a report.

**Request**

    Payload: a :doc:`models/ReportKey` object

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/report/delete HTTP/1.1

   Request payload::

      {
        "reportKey" : {
           "key" : "552d20ce-1269-4cb4-a679-0cd51d3e2058"
        }
      }

   Response::

      true

POST report/loadSubscriptions
------------------------------------------------

Returns a list of report subscriptions.

**Request**

    Payload: a :doc:`models/SubscriptionPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/Subscription` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadSubscriptions HTTP/1.1

   Request payload::

      {
        "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "tenantId" : null,
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

   Response::

      {
        "result" : [{
              "name" : "Weekly",
              "schedule" : "Occurs every week on Friday effective 07/15/2016 at 11:33 PM (UTC-08:00) Pacific Time (US & Canada)",
              "type" : "Subscription Report",
              "timeZoneName" : "(UTC-08:00) Pacific Time (US & Canada)",
              "timeZoneValue" : "Pacific Standard Time",
              "startDate" : "2016-07-15T00:00:00",
              "startDateUtc" : "0001-01-01T00:00:00",
              "startTime" : "2016-07-14T23:33:05.433",
              "recurrenceType" : 4,
              "recurrencePattern" : 0,
              "recurrencePatternSetting" : {},
              "isEndless" : true,
              "isScheduled" : false,
              "occurrence" : 0,
              "endDate" : null,
              "endDateUtc" : null,
              "deliveryType" : "Email",
              "deliveryMethod" : "Link",
              "exportFileType" : null,
              "exportAttachmentType" : null,
              "emailSubject" : "{reportName}",
              "emailBody" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,",
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "filterValueSelection" : "",
              "subscriptionFilterFields" : [],
              "id" : "09e596c9-ff2b-4694-b469-81c8b1af591c",
              "state" : 0,
              "inserted" : true,
              "version" : 1,
              "created" : null,
              "createdBy" : "",
              "modified" : "2016-07-15T06:41:35.81",
              "modifiedBy" : ""
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "total" : 1
      }

POST report/emailTemplates/{isSubscription}
------------------------------------------------

Returns a list of report email templates.

**Request**

    No payload

    isSubscription

      * 1 = for Subcriptions
      * 0 = not

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string
          -  The type of the template
          -
       *  -  **value** |br|
             string
          -  The content of the template
          -

**Samples**

   .. code-block:: http

      GET /api/report/emailTemplates/0 HTTP/1.1

   Response::

      [{
           "key" : "Attachment",
           "value" : "Dear {currentUserName},\n    \n    Please see report in the attachment.\n    \n    Regards,"
        }, {
           "key" : "Embedded HTML",
           "value" : "Dear {currentUserName},\n    \n    Please see the following report.\n    \n    {embedReportHTML}\n    \n    Regards,"
        }, {
           "key" : "Link",
           "value" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,"
        }
      ]

POST report/subscription/validate
------------------------------------------------

Validates a subscription schedule and delivery template.

**Request**

    Payload: a :doc:`models/Subscription` object

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -  Should be true
          -
       *  -  **subscription** |br|
             object
          -  A :doc:`models/Subscription` object (with adjusted start date and end date)
          -

**Samples**

   .. code-block:: http

      POST /api/report/subscription/validate HTTP/1.1

   Request payload::

      {
        "isDirty" : false,
        "name" : "Weekly Alert",
        "schedule" : "Occurs every day effective 07/17/2016 at 08:06 PM (UTC+07:00) Bangkok, Hanoi, Jakarta",
        "filterValueSelection" : "",
        "type" : "Subscription Alert",
        "timeZoneName" : "(UTC-08:00) Pacific Time (US & Canada)",
        "timeZoneValue" : "Pacific Standard Time",
        "startDate" : "2016-07-17T00:00:00",
        "startTime" : "2016-07-16T20:06:44.77",
        "recurrenceType" : 1,
        "recurrencePattern" : 2,
        "recurrencePatternSetting" : {
           "useOrdinalDay" : false,
           "day" : 18,
           "month" : 1,
           "ordinalDay" : 3,
           "ordinalDayName" : 2,
           "ordinalMonth" : 0
        },
        "isEndless" : true,
        "occurrence" : 0,
        "endDate" : null,
        "deliveryType" : "Email",
        "deliveryMethod" : "Link",
        "exportFileType" : null,
        "exportAttachmentType" : null,
        "emailSubject" : "{reportName}",
        "emailBody" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,",
        "subscriptionFilterFields" : [],
        "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
        "createdBy" : "",
        "id" : "ed3acac9-8196-478b-a7fd-123959220b0f",
        "state" : 3,
        "modified" : "2016-07-18T03:08:51.93",
        "version" : 1,
        "isEndAfter" : false,
        "isEndBy" : false
      }

   Response with startDate adjusted to 2016-07-18 (Monday) since 2016-07-17 is Sunday:

      .. code-block:: json
         :emphasize-lines: 9

         {
           "success" : true,
           "subscription" : {
              "name" : "Weekly Alert",
              "schedule" : "Occurs every day effective 07/17/2016 at 08:06 PM (UTC-08:00) Pacific Time (US & Canada)",
              "type" : "Subscription Alert",
              "timeZoneName" : "(UTC-08:00) Pacific Time (US & Canada)",
              "timeZoneValue" : "Pacific Standard Time",
              "startDate" : "2016-07-18T00:00:00",
              "startDateUtc" : "2016-07-19T03:06:00",
              "startTime" : "2016-07-16T20:06:44.77",
              "recurrenceType" : 1,
              "recurrencePattern" : 2,
              "recurrencePatternSetting" : {
                 "useOrdinalDay" : false,
                 "day" : 18,
                 "month" : 1,
                 "ordinalDay" : 3,
                 "ordinalDayName" : 2,
                 "ordinalMonth" : 0
              },
              "isEndless" : true,
              "isScheduled" : false,
              "occurrence" : 0,
              "endDate" : null,
              "endDateUtc" : null,
              "deliveryType" : "Email",
              "deliveryMethod" : "Link",
              "exportFileType" : null,
              "exportAttachmentType" : null,
              "emailSubject" : "{reportName}",
              "emailBody" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,",
              "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
              "filterValueSelection" : "",
              "subscriptionFilterFields" : [],
              "id" : "ed3acac9-8196-478b-a7fd-123959220b0f",
              "state" : 3,
              "inserted" : true,
              "version" : 1,
              "created" : null,
              "createdBy" : "",
              "modified" : "2016-07-18T03:08:51.93",
              "modifiedBy" : null
           }
         }

POST report/subscriptions
------------------------------------------------

Saves a list of report subscriptions.

**Request**

    Payload: an array of :doc:`models/Subscription` objects

**Response**

    An :doc:`models/OperationResult` object with the **success** field updated

**Samples**

   .. code-block:: http

      POST /api/report/subscriptions HTTP/1.1

   Request payload::

      [{
           "isDirty" : true,
           "name" : "Weekly Alert",
           "schedule" : "Occurs every day effective 07/18/2016 at 08:06 PM (UTC-08:00) Pacific Time (US & Canada)",
           "filterValueSelection" : "",
           "type" : "Subscription Alert",
           "timeZoneName" : "(UTC-08:00) Pacific Time (US & Canada)",
           "timeZoneValue" : "Pacific Standard Time",
           "startDate" : "2016-07-18T00:00:00",
           "startTime" : "2016-07-17T20:06:44.77",
           "recurrenceType" : 1,
           "recurrencePattern" : 2,
           "recurrencePatternSetting" : {
              "useOrdinalDay" : false,
              "day" : 18,
              "month" : 1,
              "ordinalDay" : 3,
              "ordinalDayName" : 2,
              "ordinalMonth" : 0
           },
           "isEndless" : true,
           "occurrence" : 0,
           "endDate" : null,
           "deliveryType" : "Email",
           "deliveryMethod" : "Link",
           "exportFileType" : null,
           "exportAttachmentType" : null,
           "emailSubject" : "{reportName}",
           "emailBody" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,",
           "subscriptionFilterFields" : [],
           "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
           "createdBy" : "",
           "id" : "ed3acac9-8196-478b-a7fd-123959220b0f",
           "state" : 3,
           "modified" : "2016-07-18T03:08:51.93",
           "version" : 1,
           "emailTemplates" : [{
                 "key" : "Attachment",
                 "value" : "Dear {currentUserName},\n    \n    Please see report in the attachment.\n    \n    Regards,"
              }, {
                 "key" : "Embedded HTML",
                 "value" : "Dear {currentUserName},\n    \n    Please see the following report.\n    \n    {embedReportHTML}\n    \n    Regards,"
              }, {
                 "key" : "Link",
                 "value" : "Dear {currentUserName},\n    \n    Please see report in the following link.\n    \n    {reportLink}\n    \n    Regards,"
              }
           ],
           "isEndAfter" : false,
           "isEndBy" : false
        }
      ]

   Response::

      {
        "success" : true,
        "messages" : null
      }

POST report/deleteAllArchiveVersions
------------------------------------------------

Removes all archived versions of all reports.

**Request**

    No payload

**Response**

    ``true`` after all versions have been removed.

**Samples**

   .. code-block:: http

      POST /api/report/deleteAllArchiveVersions HTTP/1.1

   Response::

      true


POST report/findByName
--------------------------------------------------------------

Returns the first report definition matching specified name and other criteria. |br|
Needs SystemAdmin permission.

.. versionadded:: 2.0.3

**Request**

    Payload: a :doc:`models/ReportDefinition` object with **name**, **tenantId** and **isGlobal** fields populated, and optional **category.Name** and **subCategory.Name** values.

**Response**

   *  A full :doc:`models/ReportDefinition` object if found
   *  null if not found

**Samples**

   .. code-block:: http

      POST /api/report/findByName HTTP/1.1

   Request payload::

      {
         "name" : "CalculatedFieldHalfFreight",
         "tenantId" : null,
         "isGlobal" : false,
         "category" : {
            "name" : "Category 1"
         }
      }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "inaccessible": false,
            "category": {
               "name": "Category 1",
               "type": 0,
               "parentId": null,
               "tenantId": null,
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": null,
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "id": "35229a62-72a5-4052-b576-64caff988b29",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "john doe",
               "modified": null,
               "modifiedBy": null
            },
            "subCategory": null,
            "reportRelationship": [],
            "reportPart": [
               {
                  "reportPartContent": {
                     "columns": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "elements": [
                           {
                              "name": "OrderID",
                              "properties": {
                                 "isDirty": false,
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "",
                                    "functionInfo": {},
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
                                    "sort": "Unsort",
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
                              "settings": {},
                              "chartType": null,
                              "showTotal": false,
                              "position": 1,
                              "field": {
                                 "fieldId": "5f24170b-14a0-4ff8-933c-2816d50d2dcb",
                                 "fieldUniqueName": "[con;#0].[cat;#0].[Orders].[OrderID]",
                                 "originalName": null,
                                 "fieldName": "OrderID",
                                 "fieldNameAlias": "OrderID",
                                 "dataFieldType": "Numeric",
                                 "querySourceId": "ab5b596a-6d35-45a0-ad9b-d3188326bafb",
                                 "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                                 "querySourceType": "Table",
                                 "sourceAlias": "Orders",
                                 "querySourceAlias": null,
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "filterable": false,
                                 "reportId": null,
                                 "fieldFunctionExpression": "",
                                 "expression": null,
                                 "grandTotalExpression": "",
                                 "grandTotalFormat": null,
                                 "subTotalExpression": "",
                                 "subtotalFormat": null,
                                 "sort": "Unsorted",
                                 "autoSort": false,
                                 "function": null,
                                 "formating": {
                                    "format": null,
                                    "createNewHiddenPercenOfGroupField": false
                                 },
                                 "functionDataType": "",
                                 "isCalculated": false,
                                 "hasAggregatedFunction": false,
                                 "invalidField": 0,
                                 "isCrossFilter": false
                              }
                           },
                           {
                              "name": "HalfFreight",
                              "properties": {
                                 "isDirty": false,
                                 "fieldItemVisible": true,
                                 "dataFormattings": {
                                    "function": "",
                                    "functionInfo": {},
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
                                    "sort": "Unsort",
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
                                       "previewResult": "",
                                       "fieldDataType": "Money",
                                       "previewRecord": 10
                                    },
                                    "grandTotal": {
                                       "label": "",
                                       "function": "",
                                       "expression": "",
                                       "dataType": "",
                                       "format": {},
                                       "previewResult": "",
                                       "fieldDataType": "Money",
                                       "previewRecord": 10
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
                              "settings": {},
                              "chartType": null,
                              "showTotal": false,
                              "position": 2,
                              "field": {
                                 "fieldId": "f0db2f29-77d6-4269-bfd6-9b8e2c3a1374",
                                 "fieldUniqueName": "[HalfFreight]",
                                 "originalName": null,
                                 "fieldName": "HalfFreight",
                                 "fieldNameAlias": "HalfFreight",
                                 "dataFieldType": "Money",
                                 "querySourceId": "00000000-0000-0000-0000-000000000000",
                                 "querySourceUniqueName": null,
                                 "querySourceType": "",
                                 "sourceAlias": "Calculated Fields",
                                 "querySourceAlias": null,
                                 "relationshipId": "00000000-0000-0000-0000-000000000000",
                                 "visible": true,
                                 "filterable": false,
                                 "reportId": null,
                                 "fieldFunctionExpression": "",
                                 "expression": null,
                                 "grandTotalExpression": "",
                                 "grandTotalFormat": null,
                                 "subTotalExpression": "",
                                 "subtotalFormat": null,
                                 "sort": "Unsorted",
                                 "autoSort": false,
                                 "function": null,
                                 "formating": {
                                    "format": null,
                                    "createNewHiddenPercenOfGroupField": false
                                 },
                                 "functionDataType": "",
                                 "isCalculated": true,
                                 "hasAggregatedFunction": false,
                                 "invalidField": 0,
                                 "isCrossFilter": false
                              }
                           }
                        ]
                     },
                     "rows": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "elements": []
                     },
                     "values": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "elements": []
                     },
                     "separators": {
                        "text": null,
                        "properties": {},
                        "settings": {},
                        "elements": []
                     },
                     "type": 3,
                     "properties": {
                        "isDirty": false,
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
                              "color": "#000000",
                              "backgroundColor": "#E4E4E4"
                           },
                           "alignment": "center",
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
                     },
                     "expandedLevel": -1,
                     "isCrossFiltering": false
                  },
                  "title": "Grid",
                  "positionX": 0,
                  "positionY": 0,
                  "width": 0,
                  "height": 0,
                  "reportId": "37045413-72d6-43fe-aa07-83c722b49bb3",
                  "numberOfRecord": null,
                  "sourceId": null,
                  "id": "71f1422b-adca-46a8-87d9-6b866ef17f57",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-06-09T04:15:35.803",
                  "createdBy": "john doe",
                  "modified": "2017-06-09T04:15:35.803",
                  "modifiedBy": "john doe"
               }
            ],
            "reportFilter": {
               "filterFields": [],
               "logic": "",
               "visible": false,
               "reportId": "37045413-72d6-43fe-aa07-83c722b49bb3",
               "id": "e2c2162b-5650-4784-bf8e-2fe8fcce9b23",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-06-09T04:15:35.79",
               "createdBy": "john doe",
               "modified": "2017-06-09T04:15:35.79",
               "modifiedBy": "john doe"
            },
            "calculatedFields": [
               {
                  "name": "HalfFreight",
                  "alias": "",
                  "dataType": "",
                  "izendaDataType": "Money",
                  "allowDistinct": true,
                  "visible": true,
                  "filterable": true,
                  "querySourceId": "00000000-0000-0000-0000-000000000000",
                  "parentId": null,
                  "expressionFields": [
                     {
                        "fieldId": "6fb58da5-a0ce-4b3b-bd86-3ed0214f84e2",
                        "fieldUniqueName": "[con;#0].[cat;#0].[Orders].[Freight]",
                        "originalName": "Freight",
                        "fieldName": "Freight",
                        "fieldNameAlias": "",
                        "dataFieldType": null,
                        "querySourceId": "ab5b596a-6d35-45a0-ad9b-d3188326bafb",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                        "querySourceType": null,
                        "sourceAlias": "",
                        "querySourceAlias": null,
                        "relationshipId": "00000000-0000-0000-0000-000000000000",
                        "visible": false,
                        "filterable": false,
                        "reportId": null,
                        "fieldFunctionExpression": null,
                        "expression": null,
                        "grandTotalExpression": null,
                        "grandTotalFormat": null,
                        "subTotalExpression": null,
                        "subtotalFormat": null,
                        "sort": "Unsorted",
                        "autoSort": false,
                        "function": null,
                        "formating": null,
                        "functionDataType": null,
                        "isCalculated": false,
                        "hasAggregatedFunction": false,
                        "invalidField": 0,
                        "isCrossFilter": false
                     }
                  ],
                  "filteredValue": "",
                  "type": 0,
                  "groupPosition": 0,
                  "position": 0,
                  "extendedProperties": "[{\"FieldId\":\"6fb58da5-a0ce-4b3b-bd86-3ed0214f84e2\",\"FieldUniqueName\":\"[con;#0].[cat;#0].[Orders].[Freight]\",\"OriginalName\":\"Freight\",\"FieldName\":\"Freight\",\"FieldNameAlias\":\"\",\"DataFieldType\":null,\"QuerySourceId\":\"ab5b596a-6d35-45a0-ad9b-d3188326bafb\",\"QuerySourceUniqueName\":\"[con;#0].[cat;#0].[Orders]\",\"QuerySourceType\":null,\"SourceAlias\":\"\",\"QuerySourceAlias\":null,\"RelationshipId\":\"00000000-0000-0000-0000-000000000000\",\"Visible\":false,\"Filterable\":false,\"ReportId\":null,\"FieldFunctionExpression\":null,\"Expression\":null,\"GrandTotalExpression\":null,\"GrandTotalFormat\":null,\"SubTotalExpression\":null,\"SubtotalFormat\":null,\"Sort\":\"Unsorted\",\"AutoSort\":false,\"Function\":null,\"Formating\":null,\"FunctionDataType\":null,\"IsCalculated\":false,\"HasAggregatedFunction\":false,\"InvalidField\":0,\"IsCrossFilter\":false}]",
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "matchedTenant": false,
                  "functionName": "",
                  "expression": "[Freight]/2",
                  "fullName": null,
                  "calculatedTree": null,
                  "reportId": "37045413-72d6-43fe-aa07-83c722b49bb3",
                  "originalName": null,
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isParameter": false,
                  "isCalculated": true,
                  "hasAggregatedFunction": false,
                  "querySource": null,
                  "querySourceName": null,
                  "categoryName": null,
                  "inaccessible": false,
                  "originalAlias": null,
                  "fullPath": null,
                  "id": "f0db2f29-77d6-4269-bfd6-9b8e2c3a1374",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-06-09T04:15:35.76",
                  "createdBy": "john doe",
                  "modified": "2017-06-09T04:15:35.76",
                  "modifiedBy": "john doe"
               }
            ],
            "accesses": [],
            "schedules": [],
            "reportParams": [
               {
                  "categories": [
                     {
                        "querySourceNames": [
                           "Orders"
                        ],
                        "id": "571f2b7c-a301-4957-8568-50510637023d",
                        "name": "dbo"
                     }
                  ],
                  "id": "99f0fc49-6937-492e-bfd0-04c7c887fec7",
                  "name": "Northwind"
               }
            ],
            "dynamicQuerySourceFields": [],
            "name": "CalculatedFieldHalfFreight",
            "reportDataSource": [
               {
                  "reportId": "37045413-72d6-43fe-aa07-83c722b49bb3",
                  "querySourceId": "ab5b596a-6d35-45a0-ad9b-d3188326bafb",
                  "querySourceUniqueName": "[con;#0].[cat;#0].[Orders]",
                  "querySourceCategoryId": null,
                  "connectionId": null,
                  "selected": false,
                  "id": "be8eb462-111a-4957-916f-2c30f828f9fc",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-06-09T04:15:35.75",
                  "createdBy": "john doe",
                  "modified": "2017-06-09T04:15:35.75",
                  "modifiedBy": "john doe"
               }
            ],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": "35229a62-72a5-4052-b576-64caff988b29",
            "categoryName": "Category 1",
            "subCategoryId": null,
            "subCategoryName": null,
            "tenantId": null,
            "tenantName": null,
            "description": "",
            "title": "",
            "lastViewed": null,
            "owner": "john doe",
            "ownerId": "dc18316c-bd87-4af2-9d98-e196a5c1fa6c",
            "excludedRelationships": "",
            "numberOfView": 0,
            "renderingTime": 0,
            "createdById": "dc18316c-bd87-4af2-9d98-e196a5c1fa6c",
            "modifiedById": "dc18316c-bd87-4af2-9d98-e196a5c1fa6c",
            "snapToGrid": false,
            "usingFields": "5f24170b-14a0-4ff8-933c-2816d50d2dcb",
            "hasDeletedObjects": false,
            "header": {
               "visible": false,
               "items": [
                  {
                     "isDirty": false,
                     "type": "image",
                     "label": "Image",
                     "id": "formatDetails_56",
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
                     "id": "formatDetails_57",
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
                     "id": "formatDetails_58",
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
                     "id": "formatDetails_59",
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
                     "id": "formatDetails_60",
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
                     "id": "formatDetails_61",
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
                     "id": "formatDetails_62",
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
                     "id": "formatDetails_63",
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
                     "id": "formatDetails_64",
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
                     "id": "formatDetails_65",
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
                     "id": "formatDetails_66",
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
                     "id": "formatDetails_67",
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
                     "id": "formatDetails_68",
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
                     "id": "formatDetails_69",
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
                     "id": "formatDetails_70",
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
                     "id": "formatDetails_71",
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
            "fullPath": null,
            "computeNameSettings": null,
            "isGlobal": false,
            "id": "37045413-72d6-43fe-aa07-83c722b49bb3",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-06-09T04:15:35.647",
            "createdBy": "john doe",
            "modified": "2017-06-09T04:15:35.647",
            "modifiedBy": "john doe"
         }
