

============================
Misc System Settings APIs
============================


Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 35 40
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET accessRight/reportDashboard/{type}`_
     - Returns access right for report/template (type=0) or dashboard (type=1).
     -
   * - `GET accessRight/authentication/{type}`_
     - Returns access right for authentication setup for report/template (type=0) or dashboard (type=1).
     -
   * - `POST accessRight/load`_
     - Searches for access rights.
     -
   * - `POST accessRight/validate`_
     - Validates an array of user permissions.
     -
   * - `POST authorization/checkPermissions`_
     - Returns an array of permissions with boolean values depending on permissions of current user.
     -
   * - `GET authorization/permission/(section)`_
     - Returns an array of permissions for current user.
     -
   * - `GET accessRight/loadAccessDefaults/{reportingType}`_
     - Returns an array of access defaults for report (reportingType=1), dashboard (reportingType=2), or both (reportingType=0).
     -
   * - `GET systemSetting/status`_
     - Returns system time, for system alive check.
     -
   * - `GET systemSetting/reset`_
     - Resets system settings.
     -
   * - `GET systemSetting/systemVariables`_
     - Returns an array of system variable names.
     -
   * - `GET systemSetting/supportedDataSourceTypes`_
     - Returns an array of supported data source types.
     -
   * - `POST systemSetting/loadEmailVariables`_
     - Returns an array of supported email variables.
     -
   * - GET systemSetting/securityQuestions
     - Returns an array of security questions.

       .. note::

          Removed

     -
   * - POST systemSetting/securityQuestions
     - Saves a new security question.

       .. note::

          Removed
     -
   * - PUT systemSetting/securityQuestions
     - Updates an existing security question.

       .. note::

          Removed
     -
   * - DELETE systemSetting/securityQuestions/{security_question_id}
     - Deletes a security question.

       .. note::

          Removed
     -
   * - `GET systemSetting/securityQuestions/{user_name}/(tenant_display_id)`_
     - Returns security question for a user and tenant display id.
     -
   * - `GET systemSetting/email/(tenant_id)`_
     - Returns email setting.
     -
   * - `POST systemSetting/email`_
     - Saves email setting.
     -
   * - `GET systemSetting/email/status/(tenant_id)`_
     - Returns email setting status.
     -
   * - `GET systemSetting/language`_
     - Returns all supported languages.
     -
   * - `GET systemSetting/dateFormat`_
     - Returns all supported date formats.
     -

GET accessRight/reportDashboard/{type}
--------------------------------------------------------------

Returns access right for report/template (type=0) or dashboard (type=1).

**Request**

    No payload

**Response**

    An array of :doc:`models/AccessRight` objects

**Samples**

   .. code-block:: http

      GET /api/accessRight/reportDashboard/0 HTTP/1.1

   Sample response::

      [{
           "name" : "Full Access",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d010",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "Locked",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d003",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "No Access",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d005",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "Quick Edit",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d001",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "Save As",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d002",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "View Only",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d004",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
      ]



GET accessRight/authentication/{type}
--------------------------------------------------------------

Returns access right for authentication setup for report/template (type=0) or dashboard (type=1).

**Request**

    No payload

**Response**

    An array of :doc:`models/AccessRight` objects

**Samples**

   .. code-block:: http

      GET /api/accessRight/authentication/1 HTTP/1.1

   Sample response::

      [{
           "name" : "Locked",
           "type" : 1,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d007",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "No Access",
           "type" : 1,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d009",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "Save As",
           "type" : 1,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d006",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "name" : "View Only",
           "type" : 1,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d008",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
      ]



POST accessRight/load
--------------------------------------------------------------

Searches for access rights.

**Request**

    Payload: an :doc:`models/AccessPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/UserPermission` objects

**Samples**

   .. code-block:: http

      POST /api/accessRight/load HTTP/1.1

   Request payload::

      {
        "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "shareWith",
              "descending" : true
           }
        ]
      }

   Sample response::

      {
        "result" : [{
              "reportId" : null,
              "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
              "assignedType" : 2,
              "accessRightId" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d006",
              "accessRight" : "Save As",
              "shareWith" : "Role ReportCreator",
              "position" : 0,
              "accessors" : ["d8a30ef0-41b4-4c97-9b7a-9fcbe90db880"],
              "tempId" : null,
              "reportAccessRightId" : null,
              "reportAccessRights" : "",
              "dashboardAccessRightId" : null,
              "dashboardAccessRights" : "",
              "id" : "879472bc-3c7a-4f9c-a090-ea7882019885",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-18T07:24:56.887",
              "createdBy" : null,
              "modified" : "2016-10-18T07:24:56.887",
              "modifiedBy" : null
           }, {
              "reportId" : null,
              "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
              "assignedType" : 1,
              "accessRightId" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d008",
              "accessRight" : "View Only",
              "shareWith" : "Everyone",
              "position" : 0,
              "accessors" : [],
              "tempId" : null,
              "reportAccessRightId" : null,
              "reportAccessRights" : "",
              "dashboardAccessRightId" : null,
              "dashboardAccessRights" : "",
              "id" : "193c7f1b-5fcd-40ee-be09-0d7b96736115",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-18T07:24:41.387",
              "createdBy" : null,
              "modified" : "2016-10-18T07:24:41.387",
              "modifiedBy" : null
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "total" : 2
      }



POST accessRight/validate
--------------------------------------------------------------

Validates an array of user permissions.

**Request**

    Payload: an array of :doc:`models/UserPermission` objects

**Response**

    * true if valid
    * false if not

**Samples**

   .. code-block:: http

      POST /api/accessRight/validate HTTP/1.1

   Request payload::

      [{
              "reportId" : null,
              "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
              "assignedType" : 2,
              "accessRightId" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d006",
              "accessRight" : "Save As",
              "shareWith" : "Role ReportCreator",
              "position" : 0,
              "accessors" : ["d8a30ef0-41b4-4c97-9b7a-9fcbe90db880"],
              "tempId" : null,
              "reportAccessRightId" : null,
              "reportAccessRights" : "",
              "dashboardAccessRightId" : null,
              "dashboardAccessRights" : "",
              "id" : "879472bc-3c7a-4f9c-a090-ea7882019885",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-18T07:24:56.887",
              "createdBy" : null,
              "modified" : "2016-10-18T07:24:56.887",
              "modifiedBy" : null
           }, {
              "reportId" : null,
              "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
              "assignedType" : 1,
              "accessRightId" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d008",
              "accessRight" : "View Only",
              "shareWith" : "Everyone",
              "position" : 0,
              "accessors" : [],
              "tempId" : null,
              "reportAccessRightId" : null,
              "reportAccessRights" : "",
              "dashboardAccessRightId" : null,
              "dashboardAccessRights" : "",
              "id" : "193c7f1b-5fcd-40ee-be09-0d7b96736115",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-18T07:24:41.387",
              "createdBy" : null,
              "modified" : "2016-10-18T07:24:41.387",
              "modifiedBy" : null
           }
        ]

   Sample response::

      true



POST authorization/checkPermissions
--------------------------------------------------------------

Returns an array of permissions with boolean values depending on permissions of current user.

**Request**

    Payload: an array of permissions (strings)

**Response**

    A dynamic object with permission names as fields, and boolean values to specify if current user has this permission or not.

**Samples**

   .. code-block:: http

      POST /api/authorization/checkPermissions HTTP/1.1

   Request payload::

      ["reports","dashboards","scheduling"]

   Sample response::

      To be updated



GET authorization/permission/(section)
--------------------------------------------------------------

Returns an array of permissions for current user.

**Request**

    No payload

    Possible **section** values:

    .. hlist::
       :columns: 3

       * systemconfiguration
       * datasetup
       * usersetup
       * rolesetup
       * reports
       * dashboards
       * access
       * scheduling
       * emailing
       * exporting
       * systemwide

**Response**

    A dynamic object, either the full :doc:`models/Permission` object or a section of it depending on the section parameter.

**Samples**

   .. code-block:: http

      GET /api/authorization/permission HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "fullReportAndDashboardAccess" : false,
           "systemConfiguration" : {
              "scheduledInstances" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "dataSetup" : {
              "dataModel" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "advancedSettings" : {
                 "category" : false,
                 "others" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "userSetup" : {
              "userRoleAssociation" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "actions" : {
                 "create" : false,
                 "edit" : false,
                 "del" : false,
                 "configureSecurityOptions" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "roleSetup" : {
              "actions" : {
                 "create" : false,
                 "edit" : false,
                 "del" : false,
                 "tenantAccess" : 0
              },
              "dataModelAccess" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "permissions" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "grantRoleWithFullReportAndDashboardAccess" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "reports" : {
              "canCreateNewReport" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "dataSources" : {
                 "simpleDataSources" : false,
                 "advancedDataSources" : false,
                 "tenantAccess" : 0
              },
              "reportPartTypes" : {
                 "chart" : false,
                 "form" : false,
                 "gauge" : false,
                 "map" : false,
                 "tenantAccess" : 0
              },
              "reportCategoriesSubcategories" : {
                 "canCreateNewCategory" : {
                    "value" : false,
                    "tenantAccess" : 0
                 },
                 "categoryAccessibility" : {
                    "categories" : [],
                    "tenantAccess" : 0
                 }
              },
              "filterProperties" : {
                 "filterLogic" : false,
                 "tenantAccess" : 0
              },
              "fieldProperties" : {
                 "customURL" : false,
                 "embeddedJavaScript" : false,
                 "subreport" : false,
                 "tenantAccess" : 0
              },
              "actions" : {
                 "schedule" : false,
                 "email" : false,
                 "viewReportHistory" : false,
                 "del" : false,
                 "registerForAlerts" : false,
                 "print" : false,
                 "unarchiveReportVersions" : false,
                 "overwriteExistingReport" : false,
                 "subscribe" : false,
                 "exporting" : false,
                 "configureAccessRights" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "dashboards" : {
              "canCreateNewDashboard" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "dashboardCategoriesSubcategories" : {
                 "canCreateNewCategory" : {
                    "value" : false,
                    "tenantAccess" : 0
                 },
                 "categoryAccessibility" : {
                    "categories" : [],
                    "tenantAccess" : 0
                 }
              },
              "actions" : {
                 "schedule" : false,
                 "email" : false,
                 "del" : false,
                 "subscribe" : false,
                 "print" : false,
                 "overwriteExistingDashboard" : false,
                 "configureAccessRights" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "access" : {
              "accessLimits" : {
                 "value" : [],
                 "tenantAccess" : 0
              },
              "accessDefaults" : {
                 "value" : [],
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "scheduling" : {
              "schedulingLimits" : {
                 "value" : [],
                 "tenantAccess" : 0
              },
              "schedulingScope" : {
                 "systemUsers" : false,
                 "externalUsers" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "emailing" : {
              "deliveryMethod" : {
                 "link" : false,
                 "embeddedHTML" : false,
                 "attachment" : false,
                 "tenantAccess" : 0
              },
              "attachmentType" : {
                 "word" : false,
                 "excel" : false,
                 "pdf" : false,
                 "csv" : false,
                 "xml" : false,
                 "json" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "exporting" : {
              "exportingFormat" : {
                 "word" : false,
                 "excel" : false,
                 "pdf" : false,
                 "csv" : false,
                 "xml" : false,
                 "json" : false,
                 "queryExecution" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           },
           "systemwide" : {
              "canSeeSystemMessages" : {
                 "value" : false,
                 "tenantAccess" : 0
              },
              "tenantAccess" : 0
           }
         }



GET accessRight/loadAccessDefaults/{reportingType}
--------------------------------------------------------------

Returns an array of access defaults for report (reportingType=1), dashboard (reportingType=2), or both (reportingType=0).

**Request**

    No payload

**Response**

    An array of :doc:`models/UserPermission` objects

**Samples**

   .. code-block:: http

      GET /api/accessRight/loadAccessDefaults/0 HTTP/1.1

   Sample response::

      To be updated



GET systemSetting/status
--------------------------------------------------------------

Returns system time, for system alive check.

**Request**

    No payload

**Response**

    The current date time if system is alive

**Samples**

   .. code-block:: http

      GET /api/systemSetting/status HTTP/1.1

   Sample response::

      "2016-12-05T03:24:09.5807888Z"



GET systemSetting/reset
--------------------------------------------------------------

Resets system settings.

**Request**

    No payload

**Response**

    The string "Done" if successful

**Samples**

   .. code-block:: http

      GET /api/systemSetting/reset HTTP/1.1

   Sample response::

      "Done"



GET systemSetting/systemVariables
--------------------------------------------------------------

Returns an array of system variable names.

**Request**

    No payload

**Response**

    An array of strings, which are system variable names

**Samples**

   .. code-block:: http

      GET /api/systemSetting/systemVariables HTTP/1.1

   Sample response::

      ["Tenant ID","User ID","Role ID"]



GET systemSetting/supportedDataSourceTypes
--------------------------------------------------------------

Returns an array of supported data source types.

**Request**

    No payload

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string
          -  The unique key of the data source type (same as the name)
          -
       *  -  **value** |br|
             string
          -  The name of the data source type
          -

**Samples**

   .. code-block:: http

      GET /api/systemSetting/supportedDataSourceTypes HTTP/1.1

   Sample response::

      [{
           "key" : "Table",
           "value" : "Table"
        }, {
           "key" : "View",
           "value" : "View"
        }, {
           "key" : "Stored Procedure",
           "value" : "Stored Procedure"
        }, {
           "key" : "Function",
           "value" : "Function"
        }
      ]



POST systemSetting/loadEmailVariables
--------------------------------------------------------------

Returns an array of supported email variables.

**Request**

    Payload: a :doc:`models/SystemVariablePagedRequest` object

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/SystemVariable` objects

**Samples**

   .. code-block:: http

      POST /api/systemSetting/loadEmailVariables HTTP/1.1

   Request payload::

      {
        "reportingType" : 0,
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "name",
              "descending" : true
           }
        ],
        "criteria" : []
      }

   Sample response::

      {
        "result" : [{
              "id" : "5cd4d4be-96d9-4c30-8680-04bd602bccd7",
              "name" : "{reportName}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 0
           }, {
              "id" : "b22170b0-48a6-45fa-8254-04be7843b9f9",
              "name" : "{currentDateTime}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 0
           }, {
              "id" : "18a820bf-9c48-465d-83ef-05511ab491cf",
              "name" : "{currentUserName}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 0
           }, {
              "id" : "e3dcd547-d9ac-417d-b42e-056358bf508c",
              "name" : "{tenantName}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 0
           }, {
              "id" : "0645098c-cb7c-4da5-aa98-059eb8fbdc16",
              "name" : "{reportLink}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 2
           }, {
              "id" : "6e204246-c212-4115-805b-0628d89c8ce2",
              "name" : "{embedReportHTML}",
              "dataType" : "Lob",
              "description" : "",
              "scope" : 2
           }, {
              "id" : "673ad95a-7cc3-4a7e-b3d0-0643913359de",
              "name" : "{recipientName}",
              "dataType" : "Text",
              "description" : "",
              "scope" : 1
           }
        ],
        "pageIndex" : 0,
        "pageSize" : 1000,
        "total" : 7
      }



GET systemSetting/securityQuestions/{user_name}/(tenant_display_id)
---------------------------------------------------------------------------

Returns security question for a user and tenant display id.

**Request**

    No payload

**Response**

    An array of :doc:`models/SecurityQuestion` objects

**Samples**

   .. code-block:: http

      GET /api/systemSetting/securityQuestions/jdoe/acme HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
          {
            "tenantId": null,
            "question": "What is the first and last name of your first boyfriend or girlfriend?",
            "orderNumber": 1,
            "id": "5784ece5-d2e7-42b1-89bb-859737b7b2a9",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "Which phone number do you remember most from your childhood?",
            "orderNumber": 2,
            "id": "3771bdc2-1add-481a-9649-18a7e494860b",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What was your favorite place to visit as a child?",
            "orderNumber": 3,
            "id": "1704f7c3-0911-40cc-88c5-3c496613f96a",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "Who is your favorite actor, musician, or artist?",
            "orderNumber": 4,
            "id": "c054397d-e371-4694-ad71-162174f39b2f",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is the name of your first pet?",
            "orderNumber": 5,
            "id": "bf8e6807-6dbf-48a7-a5d9-121a46014d41",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "In what city were you born?",
            "orderNumber": 6,
            "id": "036e00b9-09e9-411a-9b9b-74f90f9a1289",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What high school did you attend?",
            "orderNumber": 7,
            "id": "732fc020-8ac2-40ae-9d22-00d36f034552",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is the name of your first school?",
            "orderNumber": 8,
            "id": "89eed492-d117-4c42-a4b2-ab88cfb109df",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is your favorite movie?",
            "orderNumber": 9,
            "id": "2042a60d-1894-49e7-a194-77c24917f2c1",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is your mother’s maiden name?",
            "orderNumber": 10,
            "id": "470bae4e-0cb4-443d-9d75-ca91fdd81ce8",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What street did you grow up on?",
            "orderNumber": 11,
            "id": "c57e2ec2-4114-43c4-99fe-80ef9e0b8c11",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What was the make of your first car?",
            "orderNumber": 12,
            "id": "fd247bfd-3269-4425-a9a9-1239901611b7",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "When is your anniversary?",
            "orderNumber": 13,
            "id": "087a3c5b-ebff-4f96-ba7d-ffede847e09c",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is your favorite color?",
            "orderNumber": 14,
            "id": "a8201224-ddd8-4fc1-9573-82e754eb5ce1",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is your father’s middle name?",
            "orderNumber": 15,
            "id": "e30524f4-5799-4fcd-ac86-9098571303a6",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What is the name of your first grade teacher?",
            "orderNumber": 16,
            "id": "c48320ec-763f-48be-a689-8840f26cb5d6",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          },
          {
            "tenantId": null,
            "question": "What was your high school mascot?",
            "orderNumber": 17,
            "id": "20cfa68c-5398-46cf-acf8-b1c2bff297c5",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
          }
         ]


GET systemSetting/email/(tenant_id)
--------------------------------------------------------------

Returns email setting.

**Request**

    No payload

**Response**

    An :doc:`models/EmailSetting` object

**Samples**

   .. code-block:: http

      GET /api/systemSetting/email HTTP/1.1

   Sample response::

      {
       "displayName": null,
       "emailFromAddress": "contact@izenda.com",
       "useSystemConfiguration": false,
       "server": "localhost",
       "port": 25,
       "secureConnection": false,
       "login": "mail",
       "password": "EW+9H/VRg8TH0sWNiPuwpg==",
       "tenantId": null,
       "id": "1262295f-2b44-4fa2-9446-cda5e029a15c",
       "state": 0,
       "deleted": false,
       "inserted": true,
       "version": 1,
       "created": "2017-01-05T04:58:20.6430000+07:00",
       "createdBy": "John Doe",
       "modified": "2017-01-05T04:58:20.6430000+07:00",
       "modifiedBy": "John Doe"
      }



POST systemSetting/email
--------------------------------------------------------------

Saves email setting.

**Request**

    Payload: an :doc:`models/EmailSetting` object

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
       *  -  **emailSetting** |br|
             string
          -  The saved :doc:`models/EmailSetting` object
          -

**Samples**

   .. code-block:: http

      POST /api/systemSetting/email HTTP/1.1

   Request payload::

      {
        "isDirty": true,
        "id": "1262295f-2b44-4fa2-9446-cda5e029a15c",
        "tenantId": null,
        "server": "localhost",
        "port": 25,
        "secureConnection": false,
        "login": "mail",
        "password": "EW+9H/VRg8TH0sWNiPuwpg==",
        "displayName": null,
        "emailFromAddress": "contact@izenda.com",
        "version": 1,
        "created": null,
        "createdBy": null,
        "modified": "2017-01-05T04:58:20.6430000+07:00",
        "modifiedBy": "John Doe"
      }

   Sample response::

      {
        "success": true,
        "emailSetting": {
          "displayName": null,
          "emailFromAddress": "contact@izenda.com",
          "useSystemConfiguration": false,
          "server": "localhost",
          "port": 25,
          "secureConnection": false,
          "login": "mail",
          "password": "EW+9H/VRg8TH0sWNiPuwpg==",
          "tenantId": null,
          "id": "1262295f-2b44-4fa2-9446-cda5e029a15c",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": 1,
          "created": null,
          "createdBy": "John Doe",
          "modified": "2017-01-06T06:27:51.0508642",
          "modifiedBy": "John Doe"
        }
      }



GET systemSetting/email/status/(tenant_id)
--------------------------------------------------------------

Returns email setting status.

**Request**

    No payload

**Response**

    * true if email setting exists
    * false if not

**Samples**

   .. code-block:: http

      GET /api/systemSetting/email/status HTTP/1.1

   Sample response::

      true



GET systemSetting/language
--------------------------------------------------------------

Returns all supported languages.

**Request**

    No payload

**Response**

    An array of :doc:`models/IzendaLanguage` objects

**Samples**

   .. code-block:: http

      GET /api/systemSetting/language HTTP/1.1

   Sample response::

      [
        {
          "language": "English - United States",
          "cultureName": "en-US",
          "id": "c6e7d7b5-4e15-44b7-9538-fd1ab38783f0",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": null,
          "created": null,
          "createdBy": null,
          "modified": null,
          "modifiedBy": null
        },
        {
          "language": "French - Canada",
          "cultureName": "fr-CA",
          "id": "de80459f-cd0a-4443-93c4-a3f87eb0a78f",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": null,
          "created": null,
          "createdBy": null,
          "modified": null,
          "modifiedBy": null
        },
        {
          "language": "Arabic",
          "cultureName": "ar",
          "id": "15f7bd94-ae10-4fd7-91ed-cae10da3bd9d",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": null,
          "created": null,
          "createdBy": null,
          "modified": null,
          "modifiedBy": null
        }
      ]



GET systemSetting/dateFormat
--------------------------------------------------------------

Returns all supported date formats.

**Request**

    No payload

**Response**

    An array of strings (date formats)

**Samples**

   .. code-block:: http

      GET /api/systemSetting/dateFormat HTTP/1.1

   Sample response::

      [
       "MM/DD/YYYY",
       "DD/MM/YYYY",
       "YYYY/MM/DD"
      ]
