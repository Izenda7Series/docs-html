

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
   :widths: 25 40 35
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `POST report/list`_
     - .. deprecated:: 2.0.0
          superseded by `POST report/list2(?includeHashCode=true)`_

       Returns reports for the report list.
     -
       \- Setting > Copy Managerment |br|
       \- Add New Workspace |br|
       \- Choose Source  and Destination |br|
       \- Check on Report checkbox
   * - `POST report/list2(?includeHashCode=true)`_
     - Returns reports for the report list with total number of items.
     - 
   * - `GET report/info/{report_id}/(version)`_
     - Returns report properties for the report specified by report_id and version. |br|
       Returns latest version if version parameter is null.

       .. versionchanged:: 2.2

          Added optional version parameter
     - Not used
   * - `POST report/copy`_
     - Copies report to another name or category.
     -
   * - `POST report/move`_
     - Moves report to another name or category.
     -
   * - `POST report/history`_
     - Returns report history.
     -
   * - `GET report/history/{report_id}/(version)`_
     - Returns a specific version of a report. |br|
       Returns oldest available version when version parameter is missing.
     - Not used
   * - `POST report/version/{report_id}/(version)`_
     - Returns a specific version of a report. 
     - 
       \- In Report List, expand a report |br|
       \- Click on View History icon |br|
       \- On Report History pop-up, click on an archive version
   * - `DELETE report/history/{report_id}/(version)`_
     - Deletes a specific version of a report. |br|
       Deletes oldest available version when version parameter is missing.
     - 
       \- In Report List, expand a report |br|
       \- Click on View History icon |br|
       \- On Report History pop-up, click Delete icon
   * - `GET report/tenants/(tenant_id)/categories/(category_id)/reports`_
     - Returns all reports in the category specified by category_id and in the tenant specified by tenant_id.
     - Not used
   * - `POST report/delete`_
     - Deletes a report.
     -
   * - `POST report/loadSubscriptions`_
     - Returns a list of report subscriptions.
     -
   * - `POST report/emailTemplates/{isSubscription}`_
     - Returns a list of report email templates.
     -
   * - `POST report/subscription/validate`_
     - Validates a subscription schedule and delivery template.
     -
   * - `POST report/subscriptions`_
     - Saves a list of report subscriptions.
     -
   * - `POST report/deleteAllArchiveVersions`_
     - Removes all archived versions of all reports.
     -
   * - `POST report/findByName`_
     - Returns the first report definition matching specified name and other criteria. |br|
       Needs SystemAdmin permission.

       .. versionadded:: 2.0.3
     - Not used

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

    A :doc:`models/ReportDefinition` object

**Samples**

   .. code-block:: http

      GET /api/report/info/5447a5c1-a0c8-4bf6-bd68-f09234ba5e84/1 HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "inaccessible": false,
            "category": {
               "name": "CN",
               "type": 0,
               "parentId": null,
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "subCategory": {
               "name": "Example",
               "type": 0,
               "parentId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "reportRelationship": [],
            "reportPart": [],
            "reportFilter": {
               "filterFields": [],
               "baseFilterLogic": null,
               "logic": null,
               "visible": false,
               "reportId": "00000000-0000-0000-0000-000000000000",
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "calculatedFields": [],
            "accesses": [],
            "schedules": [],
            "reportParams": [{
               "categories": [{
                  "querySourceNames": ["Shippers"],
                  "id": "942c529a-38c7-4ffc-9e46-044c3f364130",
                  "name": "dbo"
               }],
               "id": "5e97b5e4-bf85-4be8-8244-cf195bdf4739",
               "name": "SQL-Northwind"
            }],
            "dynamicQuerySourceFields": [],
            "name": "ExampleReport",
            "reportDataSource": [{
               "reportId": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
               "querySourceId": null,
               "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
               "querySourceCategoryId": null,
               "connectionId": null,
               "selected": false,
               "id": "3c0ea817-d230-4a1b-8ec5-0b836b824da3",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-27T10:20:46.45",
               "createdBy": "System5 Admin5",
               "modified": "2017-09-27T10:20:46.45",
               "modifiedBy": "System5 Admin5"
            }],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
            "categoryName": "CN",
            "subCategoryId": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
            "subCategoryName": "Example",
            "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
            "tenantName": "ACME",
            "description": "",
            "title": "",
            "lastViewed": "2017-09-27T10:21:16.503",
            "owner": "System5 Admin5",
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "excludedRelationships": "",
            "numberOfView": 1,
            "renderingTime": 112,
            "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "snapToGrid": false,
            "usingFields": "d5a8a521-6832-4973-8b2c-3360dc52814c,fe0d4e44-cf3e-43a3-a575-02b086d6da71",
            "hasDeletedObjects": false,
            "header": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "image",
                  "label": "Image",
                  "id": "formatDetails_42",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_43",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "thinHorizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_44",
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
                  "thickness": 2,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_45",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_46",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_47",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "dateTime",
                  "label": "Date Time",
                  "id": "formatDetails_48",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_49",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_50",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_51",
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
                  "thickness": 4,
                  "isSelected": false
               }]
            },
            "footer": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_52",
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
                  "thickness": 4,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_53",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_54",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "pageNumber",
                  "label": "Page Number",
                  "id": "formatDetails_55",
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
                  "thickness": 1,
                  "isSelected": false
               }]
            },
            "titleDescription": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "title",
                  "label": "Title",
                  "id": "formatDetails_56",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "description",
                  "label": "Description",
                  "id": "formatDetails_57",
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
                  "thickness": 1,
                  "isSelected": false
               }]
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
               "marginSettings": [{
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
               }]
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
            "isCheck": false,
            "id": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-09-27T10:20:46.277",
            "createdBy": "System5 Admin5",
            "modified": "2017-09-27T10:20:46.277",
            "modifiedBy": "System5 Admin5"
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

GET report/history/{report_id}/(version)
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
            "inaccessible": false,
            "category": {
               "name": "CN",
               "type": 0,
               "parentId": null,
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "subCategory": {
               "name": "Example",
               "type": 0,
               "parentId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "reportRelationship": [],
            "reportPart": [],
            "reportFilter": {
               "filterFields": [],
               "baseFilterLogic": null,
               "logic": null,
               "visible": false,
               "reportId": "00000000-0000-0000-0000-000000000000",
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "calculatedFields": [],
            "accesses": [],
            "schedules": [],
            "reportParams": [{
               "categories": [{
                  "querySourceNames": ["Shippers"],
                  "id": "942c529a-38c7-4ffc-9e46-044c3f364130",
                  "name": "dbo"
               }],
               "id": "5e97b5e4-bf85-4be8-8244-cf195bdf4739",
               "name": "SQL-Northwind"
            }],
            "dynamicQuerySourceFields": [],
            "name": "ExampleReport",
            "reportDataSource": [{
               "reportId": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
               "querySourceId": null,
               "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
               "querySourceCategoryId": null,
               "connectionId": null,
               "selected": false,
               "id": "3c0ea817-d230-4a1b-8ec5-0b836b824da3",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-27T10:20:46.45",
               "createdBy": "System5 Admin5",
               "modified": "2017-09-27T10:20:46.45",
               "modifiedBy": "System5 Admin5"
            }],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
            "categoryName": "CN",
            "subCategoryId": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
            "subCategoryName": "Example",
            "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
            "tenantName": "ACME",
            "description": "",
            "title": "",
            "lastViewed": "2017-09-27T10:21:16.503",
            "owner": "System5 Admin5",
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "excludedRelationships": "",
            "numberOfView": 1,
            "renderingTime": 112,
            "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "snapToGrid": false,
            "usingFields": "d5a8a521-6832-4973-8b2c-3360dc52814c,fe0d4e44-cf3e-43a3-a575-02b086d6da71",
            "hasDeletedObjects": false,
            "header": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "image",
                  "label": "Image",
                  "id": "formatDetails_42",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_43",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "thinHorizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_44",
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
                  "thickness": 2,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_45",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_46",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_47",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "dateTime",
                  "label": "Date Time",
                  "id": "formatDetails_48",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_49",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_50",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_51",
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
                  "thickness": 4,
                  "isSelected": false
               }]
            },
            "footer": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_52",
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
                  "thickness": 4,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_53",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_54",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "pageNumber",
                  "label": "Page Number",
                  "id": "formatDetails_55",
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
                  "thickness": 1,
                  "isSelected": false
               }]
            },
            "titleDescription": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "title",
                  "label": "Title",
                  "id": "formatDetails_56",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "description",
                  "label": "Description",
                  "id": "formatDetails_57",
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
                  "thickness": 1,
                  "isSelected": false
               }]
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
               "marginSettings": [{
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
               }]
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
            "isCheck": false,
            "id": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-09-27T10:20:46.277",
            "createdBy": "System5 Admin5",
            "modified": "2017-09-27T10:20:46.277",
            "modifiedBy": "System5 Admin5"
         }

POST report/version/{report_id}/(version)
------------------------------------------------

Returns a specific version of a report. 

**Request**

    No payload

**Response**

    A :doc:`models/ReportDefinition` object.

**Samples**

   .. code-block:: http

      POST report/version/0ef9192c-121c-421a-8562-0a1fe8b0ade0/1/ HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample Response:

      .. code-block:: json

         {
            "inaccessible": false,
            "category": {
               "name": "aaa",
               "type": 0,
               "parentId": null,
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "5265bffb-dc9b-4403-afa2-a736ec69cfd5",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "subCategory": {
               "name": "bbb",
               "type": 0,
               "parentId": "5265bffb-dc9b-4403-afa2-a736ec69cfd5",
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [],
               "checked": false,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false,
               "id": "d1d41128-ab4b-44ed-a5b4-73dadbdd8178",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            },
            "reportRelationship": [],
            "reportPart": [{
               "reportPartContent": {
                  "columns": {
                     "text": null,
                     "properties": {
                        
                     },
                     "settings": {
                        
                     },
                     "elements": [{
                        "name": "OrderID",
                        "properties": {
                           "isDirty": false,
                           "fieldItemVisible": true,
                           "dataFormattings": {
                              "function": "",
                              "functionInfo": {
                                 "id": null,
                                 "name": ""
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
                                 "format": {
                                    
                                 },
                                 "previewResult": ""
                              },
                              "grandTotal": {
                                 "label": "",
                                 "function": "",
                                 "expression": "",
                                 "dataType": "",
                                 "format": {
                                    
                                 },
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
                              
                           }
                        },
                        "settings": {
                           
                        },
                        "chartType": null,
                        "showTotal": false,
                        "position": 1,
                        "field": {
                           "fieldId": "b5ea4297-8fe1-47d2-bfde-13b2eef6c36d",
                           "fieldUniqueName": "[con;#0].[cat;#0].[orders].[OrderID]",
                           "originalName": null,
                           "fieldName": "OrderID",
                           "fieldNameAlias": "OrderID",
                           "dataFieldType": "Numeric",
                           "querySourceId": "5eec76ff-4de9-403a-a7dd-66a9db4e6eba",
                           "querySourceUniqueName": "[con;#0].[cat;#0].[orders]",
                           "querySourceType": "Table",
                           "sourceAlias": "orders",
                           "querySourceAlias": null,
                           "runningDeep": -1,
                           "isRunningField": false,
                           "builtRunningField": false,
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
                           "function": "",
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
                     }]
                  },
                  "rows": {
                     "text": null,
                     "properties": {
                        
                     },
                     "settings": {
                        
                     },
                     "elements": []
                  },
                  "values": {
                     "text": null,
                     "properties": {
                        
                     },
                     "settings": {
                        
                     },
                     "elements": []
                  },
                  "separators": {
                     "text": null,
                     "properties": {
                        
                     },
                     "settings": {
                        
                     },
                     "elements": []
                  },
                  "paginable": true,
                  "type": "3",
                  "properties": {
                     "isDirty": true,
                     "generalInfo": {
                        "gridStyle": "Vertical",
                        "separatorStyle": "Comma"
                     },
                     "table": {
                        "border": {
                           "top": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           },
                           "right": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           },
                           "bottom": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           },
                           "midVer": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           },
                           "left": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           },
                           "midHor": {
                              "color": null,
                              "dashStyle": null,
                              "thinkness": null
                           }
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
                        "collapseDrilldownByDefault": false,
                        "pageSize": 10,
                        "pivotColumnsPerExportedPage": ""
                     },
                     "printing": {
                        "usePageBreakAfterSeparator": false
                     }
                  },
                  "settings": {
                     
                  },
                  "title": {
                     "text": "",
                     "properties": {
                        
                     },
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
                     "properties": {
                        
                     },
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
                  "isCrossFiltering": false,
                  "isFormatted": false
               },
               "title": "Grid",
               "positionX": 0,
               "positionY": 0,
               "width": 0,
               "height": 0,
               "reportId": "0ef9192c-121c-421a-8562-0a1fe8b0ade0",
               "numberOfRecord": null,
               "sourceId": null,
               "id": "2297e2ca-420b-499c-b628-c4f64ec60375",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-22T10:10:22.567",
               "createdBy": "ACME Cooperation",
               "modified": "2017-09-22T10:10:22.567",
               "modifiedBy": "ACME Cooperation"
            }],
            "reportFilter": {
               "filterFields": [],
               "baseFilterLogic": "",
               "logic": "",
               "visible": false,
               "reportId": "0ef9192c-121c-421a-8562-0a1fe8b0ade0",
               "id": "03a2bc07-6c19-4038-8f03-786e6050cd43",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-22T10:10:22.563",
               "createdBy": "ACME Cooperation",
               "modified": "2017-09-22T10:10:22.563",
               "modifiedBy": "ACME Cooperation"
            },
            "calculatedFields": [],
            "accesses": [],
            "schedules": [],
            "reportParams": [{
               "categories": [{
                  "querySourceNames": ["orders"],
                  "id": "94454a0a-17a2-49e5-bebf-9c0d07d95587",
                  "name": "northwind"
               }],
               "id": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
               "name": "northwind"
            }],
            "dynamicQuerySourceFields": [],
            "name": "test5",
            "reportDataSource": [{
               "reportId": "0ef9192c-121c-421a-8562-0a1fe8b0ade0",
               "querySourceId": "5eec76ff-4de9-403a-a7dd-66a9db4e6eba",
               "querySourceUniqueName": "[con;#0].[cat;#0].[orders]",
               "querySourceCategoryId": null,
               "connectionId": null,
               "selected": false,
               "id": "2455781c-0daa-4e46-b9f0-3780b518fdce",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-22T10:10:22.563",
               "createdBy": "ACME Cooperation",
               "modified": "2017-09-22T10:10:22.563",
               "modifiedBy": "ACME Cooperation"
            }],
            "type": 0,
            "previewRecord": 10,
            "advancedMode": true,
            "allowNulls": false,
            "isDistinct": false,
            "categoryId": "5265bffb-dc9b-4403-afa2-a736ec69cfd5",
            "categoryName": "aaa",
            "subCategoryId": "d1d41128-ab4b-44ed-a5b4-73dadbdd8178",
            "subCategoryName": "bbb",
            "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
            "tenantName": "ACME",
            "description": "",
            "title": "",
            "lastViewed": "2017-09-28T02:47:52.19",
            "owner": "ACME Cooperation",
            "ownerId": "88ca2835-81e0-443b-b29e-e694a66b8e7a",
            "excludedRelationships": "",
            "numberOfView": 1,
            "renderingTime": 359.0,
            "createdById": "88ca2835-81e0-443b-b29e-e694a66b8e7a",
            "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "snapToGrid": false,
            "usingFields": "b5ea4297-8fe1-47d2-bfde-13b2eef6c36d",
            "hasDeletedObjects": false,
            "header": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "image",
                  "label": "Image",
                  "id": "formatDetails_40",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_41",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "thinHorizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_42",
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
                  "thickness": 2,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_43",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_44",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_45",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "dateTime",
                  "label": "Date Time",
                  "id": "formatDetails_46",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_47",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_48",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_49",
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
                  "thickness": 4,
                  "isSelected": false
               }]
            },
            "footer": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "horizontalRule",
                  "label": "Horizontal Rule",
                  "id": "formatDetails_50",
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
                  "thickness": 4,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_51",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "text",
                  "label": "Text",
                  "id": "formatDetails_52",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "pageNumber",
                  "label": "Page Number",
                  "id": "formatDetails_53",
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
                  "thickness": 1,
                  "isSelected": false
               }]
            },
            "titleDescription": {
               "visible": false,
               "items": [{
                  "isDirty": false,
                  "type": "title",
                  "label": "Title",
                  "id": "formatDetails_54",
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
                  "thickness": 1,
                  "isSelected": false
               },
               {
                  "isDirty": false,
                  "type": "description",
                  "label": "Description",
                  "id": "formatDetails_55",
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
                  "thickness": 1,
                  "isSelected": false
               }]
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
               "marginSettings": [{
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
                  "topValue": 1.0,
                  "bottomValue": 1.0,
                  "leftValue": 1.0,
                  "rightValue": 1.0,
                  "headerValue": 0.5,
                  "footerValue": 0.5
               }]
            },
            "deletable": true,
            "editable": true,
            "movable": true,
            "copyable": true,
            "accessPriority": 1,
            "active": true,
            "fullPath": null,
            "computeNameSettings": null,
            "isGlobal": false,
            "isCheck": false,
            "id": "0ef9192c-121c-421a-8562-0a1fe8b0ade0",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-09-22T10:10:22.447",
            "createdBy": "ACME Cooperation",
            "modified": "2017-09-26T08:52:48.553",
            "modifiedBy": "System5 Admin5"
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
               "name": "abc",
               "reportDataSource": [],
               "type": 0,
               "previewRecord": 10,
               "advancedMode": true,
               "allowNulls": false,
               "isDistinct": false,
               "categoryId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
               "categoryName": null,
               "subCategoryId": null,
               "subCategoryName": null,
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "tenantName": null,
               "description": "",
               "title": "",
               "lastViewed": "2017-09-19T10:19:24.9",
               "owner": "System5 Admin5",
               "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
               "excludedRelationships": "",
               "numberOfView": 1,
               "renderingTime": 933,
               "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
               "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
               "snapToGrid": false,
               "usingFields": null,
               "hasDeletedObjects": false,
               "header": {
                  "visible": false,
                  "items": [{
                     "isDirty": false,
                     "type": "image",
                     "label": "Image",
                     "id": "formatDetails_190",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_191",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "thinHorizontalRule",
                     "label": "Horizontal Rule",
                     "id": "formatDetails_192",
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
                     "thickness": 2,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_193",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_194",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_195",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "dateTime",
                     "label": "Date Time",
                     "id": "formatDetails_196",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_197",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_198",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "horizontalRule",
                     "label": "Horizontal Rule",
                     "id": "formatDetails_199",
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
                     "thickness": 4,
                     "isSelected": false
                  }]
               },
               "footer": {
                  "visible": false,
                  "items": [{
                     "isDirty": false,
                     "type": "horizontalRule",
                     "label": "Horizontal Rule",
                     "id": "formatDetails_200",
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
                     "thickness": 4,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_201",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "text",
                     "label": "Text",
                     "id": "formatDetails_202",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "pageNumber",
                     "label": "Page Number",
                     "id": "formatDetails_203",
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
                     "thickness": 1,
                     "isSelected": false
                  }]
               },
               "titleDescription": {
                  "visible": false,
                  "items": [{
                     "isDirty": false,
                     "type": "title",
                     "label": "Title",
                     "id": "formatDetails_204",
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
                     "thickness": 1,
                     "isSelected": false
                  },
                  {
                     "isDirty": false,
                     "type": "description",
                     "label": "Description",
                     "id": "formatDetails_205",
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
                     "thickness": 1,
                     "isSelected": false
                  }]
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
                  "marginSettings": [{
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
                  }]
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
               "isCheck": false,
               "id": "1f2f69fd-3430-445f-ad74-36a7f46f71fe",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-19T10:19:19.97",
               "createdBy": "System5 Admin5",
               "modified": "2017-09-19T10:19:19.97",
               "modifiedBy": "System5 Admin5"
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

   * true if user has System Admin Permission
   * Error message if user does not have System Admin Permission

**Samples**

   .. code-block:: http

      POST /api/report/deleteAllArchiveVersions HTTP/1.1

   Sample response in case user has  System Admin Permission::

      true

   Sample response in case user does not have System Admin Permission::

    {
      "message" : "You don't have permission to perform this action",
      "detail" : "NoPermission"
    }


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
        "inaccessible": false,
        "category": {
            "name": "ACME"
        },
        "subCategory": {
            "name": "Example"
        },
        "name": "ExampleReport",   
        "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e"
        }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

            {
                "inaccessible": false,
                "category": {
                    "name": "ACME",
                    "type": 0,
                    "parentId": null,
                    "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
                    "isGlobal": false,
                    "canDelete": false,
                    "editable": false,
                    "savable": false,
                    "subCategories": [],
                    "checked": false,
                    "reports": [],
                    "dashboards": null,
                    "numOfChilds": 0,
                    "numOfCheckedChilds": 0,
                    "indeterminate": false,
                    "fullPath": null,
                    "computeNameSettings": null,
                    "isCheck": false,
                    "id": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
                    "state": 0,
                    "deleted": false,
                    "inserted": true,
                    "version": null,
                    "created": null,
                    "createdBy": "ACME Cooperation",
                    "modified": null,
                    "modifiedBy": null
                },
                "subCategory": {
                    "name": "Example",
                    "type": 0,
                    "parentId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
                    "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
                    "isGlobal": false,
                    "canDelete": false,
                    "editable": false,
                    "savable": false,
                    "subCategories": [],
                    "checked": false,
                    "reports": [],
                    "dashboards": null,
                    "numOfChilds": 0,
                    "numOfCheckedChilds": 0,
                    "indeterminate": false,
                    "fullPath": null,
                    "computeNameSettings": null,
                    "isCheck": false,
                    "id": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
                    "state": 0,
                    "deleted": false,
                    "inserted": true,
                    "version": null,
                    "created": null,
                    "createdBy": "ACME Cooperation",
                    "modified": null,
                    "modifiedBy": null
                },
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
                                        "name": "ShipperID",
                                        "properties": {
                                            "isDirty": false,
                                            "fieldItemVisible": true,
                                            "dataFormattings": {
                                                "function": "",
                                                "functionInfo": {
                                                    "id": null,
                                                    "name": ""
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
                                            "fieldId": "d5a8a521-6832-4973-8b2c-3360dc52814c",
                                            "fieldUniqueName": "[con;#0].[cat;#0].[Shippers].[ShipperID]",
                                            "originalName": null,
                                            "fieldName": "ShipperID",
                                            "fieldNameAlias": "ShipperID",
                                            "dataFieldType": "Numeric",
                                            "querySourceId": "14239815-b494-4fc4-87e6-a9fec70dc10e",
                                            "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
                                            "querySourceType": "Table",
                                            "sourceAlias": "Shippers",
                                            "querySourceAlias": null,
                                            "runningDeep": -1,
                                            "isRunningField": false,
                                            "builtRunningField": false,
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
                                            "function": "",
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
                                        "name": "CompanyName",
                                        "properties": {
                                            "isDirty": false,
                                            "fieldItemVisible": true,
                                            "dataFormattings": {
                                                "function": "",
                                                "functionInfo": {
                                                    "id": null,
                                                    "name": ""
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
                                        "position": 2,
                                        "field": {
                                            "fieldId": "fe0d4e44-cf3e-43a3-a575-02b086d6da71",
                                            "fieldUniqueName": "[con;#0].[cat;#0].[Shippers].[CompanyName]",
                                            "originalName": null,
                                            "fieldName": "CompanyName",
                                            "fieldNameAlias": "CompanyName",
                                            "dataFieldType": "Text",
                                            "querySourceId": "14239815-b494-4fc4-87e6-a9fec70dc10e",
                                            "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
                                            "querySourceType": "Table",
                                            "sourceAlias": "Shippers",
                                            "querySourceAlias": null,
                                            "runningDeep": -1,
                                            "isRunningField": false,
                                            "builtRunningField": false,
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
                                            "function": "",
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
                            "paginable": true,
                            "type": "3",
                            "properties": {
                                "isDirty": true,
                                "generalInfo": {
                                    "gridStyle": "Vertical",
                                    "separatorStyle": "Comma"
                                },
                                "table": {
                                    "border": {
                                        "top": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        },
                                        "right": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        },
                                        "bottom": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        },
                                        "midVer": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        },
                                        "left": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        },
                                        "midHor": {
                                            "color": null,
                                            "dashStyle": null,
                                            "thinkness": null
                                        }
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
                                    "collapseDrilldownByDefault": false,
                                    "pageSize": 10,
                                    "pivotColumnsPerExportedPage": ""
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
                            "isCrossFiltering": false,
                            "isFormatted": false
                        },
                        "title": "Grid",
                        "positionX": 0,
                        "positionY": 0,
                        "width": 4,
                        "height": 4,
                        "reportId": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
                        "numberOfRecord": null,
                        "sourceId": null,
                        "id": "f36e3dcc-21d3-4996-aeb8-5f78c34048d9",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 2,
                        "created": "2017-09-27T10:20:46.477",
                        "createdBy": "ACME Cooperation",
                        "modified": "2017-09-28T07:49:39.267",
                        "modifiedBy": null
                    }
                ],
                "reportFilter": {
                    "filterFields": [
                        {
                            "connectionName": "SQL-Northwind",
                            "querySourceCategoryName": "dbo",
                            "sourceFieldName": "ShipperID",
                            "sourceFieldVisible": true,
                            "sourceFieldFilterable": true,
                            "sourceDataObjectName": "Shippers",
                            "sourceDataObjectFullName": "SQL-Northwind.dbo.Shippers",
                            "dataType": "Numeric",
                            "isParameter": false,
                            "isCalculated": false,
                            "calculatedTree": null,
                            "compareFieldCalculatedTree": null,
                            "compareValueCalculatedTree": null,
                            "compareField": null,
                            "selected": false,
                            "dataFormat": null,
                            "reportId": null,
                            "useMappedFieldAlias": false,
                            "uniqueId": null,
                            "comparisionValue": null,
                            "inTimePeriodType": null,
                            "valueInTimePeriod": null,
                            "hasModifiedCalculatedTree": false,
                            "isHiddenFilter": false,
                            "isInheritableFilter": false,
                            "operatorName": "Equals (Manual Entry)",
                            "type": 0,
                            "isRunningField": false,
                            "isDrillDown": false,
                            "filterId": "021c76a2-b108-4dd3-962c-4d5d2d1b22fe",
                            "reportFieldAlias": null,
                            "reportPartTitle": null,
                            "querySourceFieldId": "d5a8a521-6832-4973-8b2c-3360dc52814c",
                            "querySourceType": "Table",
                            "querySourceId": "14239815-b494-4fc4-87e6-a9fec70dc10e",
                            "relationshipId": null,
                            "alias": "ShipperID",
                            "position": 1,
                            "visible": true,
                            "required": false,
                            "cascading": true,
                            "operatorId": "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
                            "operatorSetting": null,
                            "value": "",
                            "dataFormatId": null,
                            "sortType": "ASC",
                            "fontFamily": "Roboto",
                            "fontSize": 14,
                            "textColor": "#000",
                            "backgroundColor": "#fff",
                            "fontBold": false,
                            "fontItalic": false,
                            "fontUnderline": false,
                            "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
                            "querySourceFieldName": "ShipperID",
                            "comparisonFieldUniqueName": "",
                            "isNegative": false,
                            "id": "4f43a428-6e23-42c9-bb51-ab19f7966943",
                            "state": 0,
                            "deleted": false,
                            "inserted": true,
                            "version": 1,
                            "created": "2017-09-28T07:49:39.263",
                            "createdBy": "ACME Cooperation",
                            "modified": "2017-09-28T07:49:39.263",
                            "modifiedBy": "ACME Cooperation"
                        }
                    ],
                    "baseFilterLogic": null,
                    "logic": "",
                    "visible": false,
                    "reportId": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
                    "id": "021c76a2-b108-4dd3-962c-4d5d2d1b22fe",
                    "state": 0,
                    "deleted": false,
                    "inserted": true,
                    "version": 2,
                    "created": "2017-09-27T10:20:46.46",
                    "createdBy": "ACME Cooperation",
                    "modified": "2017-09-28T07:49:39.263",
                    "modifiedBy": null
                },
                "calculatedFields": [],
                "accesses": [],
                "schedules": [],
                "reportParams": [
                    {
                        "categories": [
                            {
                                "querySourceNames": [
                                    "Shippers"
                                ],
                                "id": "942c529a-38c7-4ffc-9e46-044c3f364130",
                                "name": "dbo"
                            }
                        ],
                        "id": "5e97b5e4-bf85-4be8-8244-cf195bdf4739",
                        "name": "SQL-Northwind"
                    }
                ],
                "dynamicQuerySourceFields": [],
                "name": "ExampleReport",
                "reportDataSource": [
                    {
                        "reportId": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
                        "querySourceId": "14239815-b494-4fc4-87e6-a9fec70dc10e",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
                        "querySourceCategoryId": null,
                        "connectionId": null,
                        "selected": false,
                        "id": "3c0ea817-d230-4a1b-8ec5-0b836b824da3",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 1,
                        "created": "2017-09-27T10:20:46.45",
                        "createdBy": "ACME Cooperation",
                        "modified": "2017-09-27T10:20:46.45",
                        "modifiedBy": "ACME Cooperation"
                    }
                ],
                "type": 0,
                "previewRecord": 10,
                "advancedMode": true,
                "allowNulls": false,
                "isDistinct": false,
                "categoryId": "5ca51cd0-1f63-44ca-9711-ba6c988a520a",
                "categoryName": "ACME",
                "subCategoryId": "41a3dff9-d1da-48e5-b4fb-50775324bd3d",
                "subCategoryName": "Example",
                "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
                "tenantName": "ACME",
                "description": "",
                "title": "",
                "lastViewed": "2017-09-28T07:50:02.533",
                "owner": "ACME Cooperation",
                "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                "excludedRelationships": "",
                "numberOfView": 3,
                "renderingTime": 646.66667,
                "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                "modifiedById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                "snapToGrid": false,
                "usingFields": "d5a8a521-6832-4973-8b2c-3360dc52814c,fe0d4e44-cf3e-43a3-a575-02b086d6da71",
                "hasDeletedObjects": false,
                "header": {
                    "visible": false,
                    "items": [
                        {
                            "isDirty": false,
                            "type": "image",
                            "label": "Image",
                            "id": "formatDetails_87",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_88",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "thinHorizontalRule",
                            "label": "Horizontal Rule",
                            "id": "formatDetails_89",
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
                            "thickness": 2,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_90",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_91",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_92",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "dateTime",
                            "label": "Date Time",
                            "id": "formatDetails_93",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_94",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_95",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "horizontalRule",
                            "label": "Horizontal Rule",
                            "id": "formatDetails_96",
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
                            "thickness": 4,
                            "isSelected": false
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
                            "id": "formatDetails_97",
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
                            "thickness": 4,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_98",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "text",
                            "label": "Text",
                            "id": "formatDetails_99",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "pageNumber",
                            "label": "Page Number",
                            "id": "formatDetails_100",
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
                            "thickness": 1,
                            "isSelected": false
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
                            "id": "formatDetails_101",
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
                            "thickness": 1,
                            "isSelected": false
                        },
                        {
                            "isDirty": false,
                            "type": "description",
                            "label": "Description",
                            "id": "formatDetails_102",
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
                            "thickness": 1,
                            "isSelected": false
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
                "isCheck": false,
                "id": "5447a5c1-a0c8-4bf6-bd68-f09234ba5e84",
                "state": 0,
                "deleted": false,
                "inserted": true,
                "version": 2,
                "created": "2017-09-27T10:20:46.277",
                "createdBy": "ACME Cooperation",
                "modified": "2017-09-28T07:49:39.25",
                "modifiedBy": "ACME Cooperation"
            }
