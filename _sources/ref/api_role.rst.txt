

============================
Role APIs
============================

The '''Role Setup''' page allows user to manage roles.

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `GET role/all/(tenant_id)`_
     - Returns an array of roles, filtered by tenant_id if available.
   * - `POST role/active/{role_id}/(tenant_id)`_
     - Sets a role to be active.
   * - `POST role/deactive/{role_id}/(tenant_id)`_
     - Sets a role to be inactive.
   * - `DELETE role/{role_id}`_
     - Deletes a role.
   * - `GET role/{role_id}`_
     - Returns a role.
   * - `GET role/availableRole/{type}/(tenant_id)`_
     - Returns a list of available roles for Access (type=0) or Scheduling (type=1), filtered by tenant_id if available.
   * - `GET role/availableCategory/{type}/(tenant_id)`_
     - .. deprecated:: 2.0.0
            superseded by `POST role/availableCategory`_ |br| |br|

       Returns a list of available categories for Report/Template (type=0) or Dashboard (type=1), filtered by tenant_id if available.
   * - `POST role/availableCategory`_
     - Returns a list of available categories, with total number of items.
   * - `POST role`_
     - Saves a role.
   * - `GET role/summaries/(tenant_id)`_
     - Returns an array of roles filtered by tenant_id.
   * - `POST role/allowedSharingRoles`_
     - Returns a list of roles allowed to be selected in report/dashboard access.
   * - `POST role/intergration/saveRole`_
     - Adds or updates an external role.

.. _GET_role/all/(tenant_id):

GET role/all/(tenant_id)
--------------------------------------------------------------

Returns an array of roles, filtered by tenant_id if available.

**Request**

    No payload

**Response**

    An array of :doc:`models/Role` objects

**Samples**

   .. code-block:: http

      GET /api/role/all HTTP/1.1

   Sample response::

      [{
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Actor",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd284",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [{
                 "password" : null,
                 "roles" : null,
                 "userName" : "User1",
                 "emailAddress" : "katty@email.com",
                 "firstName" : "Katty",
                 "lastName" : "Doe",
                 "passwordHash" : null,
                 "passwordSalt" : null,
                 "currentTokenHash" : null,
                 "tenantId" : null,
                 "active" : false,
                 "deleted" : false,
                 "dataOffset" : 0,
                 "timestampOffset" : 0,
                 "fullName" : "Katty Doe",
                 "id" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
                 "state" : 0,
                 "inserted" : true,
                 "version" : 1,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Analyst",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd281",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [{
                 "password" : null,
                 "roles" : null,
                 "userName" : "Member1",
                 "emailAddress" : "justin@thisispopstart.com",
                 "firstName" : "Justin",
                 "lastName" : "Timber",
                 "passwordHash" : null,
                 "passwordSalt" : null,
                 "currentTokenHash" : null,
                 "tenantId" : null,
                 "active" : false,
                 "deleted" : false,
                 "dataOffset" : 0,
                 "timestampOffset" : 0,
                 "fullName" : "Justin Timber",
                 "id" : "9f58703e-0dff-4690-9dc6-c595a6fd84e3",
                 "state" : 0,
                 "inserted" : true,
                 "version" : 1,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Singer",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd283",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
      ]

POST role/active/{role_id}/(tenant_id)
--------------------------------------------------------------

Sets a role to be active.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST api/role/active/0d030b1a-9568-4c98-8b1e-5dcc94dbd282 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

POST role/deactive/{role_id}/(tenant_id)
--------------------------------------------------------------

Sets a role to be inactive.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST api/role/deactive/0d030b1a-9568-4c98-8b1e-5dcc94dbd282 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

DELETE role/{role_id}
--------------------------------------------------------------

Deletes a role.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      DELETE api/role/0d030b1a-9568-4c98-8b1e-5dcc94dbd281 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

GET role/{role_id}
--------------------------------------------------------------

Returns a role.

**Request**

    No payload

**Response**

    A :doc:`models/RoleDetail` object

**Samples**

   .. code-block:: http

      GET /api/role/0d030b1a-9568-4c98-8b1e-5dcc94dbd281 HTTP/1.1

   Sample response::

      {
         "users": [],
         "permission": null,
         "visibleQuerySourceFields": null,
         "name": "Analyst",
         "tenantId": null,
         "active": true,
         "deleted": false,
         "permissionData": "",
         "querySourceFields": "",
         "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd281",
         "state": 0,
         "inserted": true,
         "version": 1,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
      }

GET role/availableRole/{type}/(tenant_id)
--------------------------------------------------------------

Returns a list of available roles for Access (type=0) or Scheduling (type=1), filtered by tenant_id if available.

**Request**

    No payload

**Response**

    An array of :doc:`models/RoleDetail` object

**Samples**

   .. code-block:: http

      GET api/role/availableRole/0 HTTP/1.1

   Sample response::

      [{
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Anonymous",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd284",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [{
                 "password" : null,
                 "roles" : null,
                 "userRoles" : null,
                 "userSecurityQuestions" : null,
                 "userName" : "User1",
                 "emailAddress" : "katty@email.com",
                 "firstName" : "Katty",
                 "lastName" : "Doe",
                 "passwordHash" : null,
                 "passwordSalt" : null,
                 "currentTokenHash" : null,
                 "tenantId" : null,
                 "deleted" : false,
                 "dataOffset" : 0,
                 "timestampOffset" : 0,
                 "initPassword" : false,
                 "active" : false,
                 "fullName" : "Katty Doe",
                 "id" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
                 "state" : 0,
                 "inserted" : true,
                 "version" : 1,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Analyst",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd281",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Reviewer",
           "tenantId" : null,
           "active" : true,
           "deleted" : false,
           "permissionData" : "",
           "querySourceFields" : "",
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd282",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
      ]

GET role/availableCategory/{type}/(tenant_id)
--------------------------------------------------------------

.. deprecated:: 2.0.0
   superseded by `POST role/availableCategory`_

Returns a list of available categories for Report/Template (type=0) or Dashboard (type=1), filtered by tenant_id if available.

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET api/role/availableCategory/0 HTTP/1.1

   Sample response::

      [
       {
         "name": "Sales",
         "type": 0,
         "parentId": null,
         "tenantId": null,
         "canDelete": false,
         "editable": false,
         "savable": false,
         "subCategories": [
           {
            "name": "InternetSales",
            "type": 0,
            "parentId": "93de93b9-d5d1-48f1-800d-1db1ffc02614",
            "tenantId": null,
            "canDelete": false,
            "editable": false,
            "savable": false,
            "subCategories": [],
            "checked": false,
            "reports": null,
            "dashboards": null,
            "status": 2,
            "id": "5d034fc7-0cc8-46b7-beb3-35b22c57827c",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
           }
         ],
         "checked": false,
         "reports": null,
         "dashboards": null,
         "status": 2,
         "id": "93de93b9-d5d1-48f1-800d-1db1ffc02614",
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
         "name": "TestCategory",
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
         "status": 2,
         "id": "0ecf1821-dc37-43dd-8b4c-654961b37038",
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
         "name": "Uncategorized",
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
         "status": 1,
         "id": "00000000-0000-0000-0000-000000000000",
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

.. _POST_role/availableCategory:

POST role/availableCategory
--------------------------------------------------------------

Returns a list of available categories, with total number of items.

**Request**

   Payload: a :doc:`models/CategoryPagedRequest` object

**Response**

   A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/Category` objects.

**Samples**

   .. code-block:: http

      POST api/role/availableCategory HTTP/1.1

   Request payload::

      {
         "type": 0,
         "tenantId": null,
         "skipItems": 0,
         "pageSize": -1,
         "parentIds": [],
         "defaultChecked": false,
         "isUncategorized": false
      }

   Sample response::

      {
         "result": [
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
                     "name": "Uncategorized",
                     "type": 0,
                     "parentId": null,
                     "tenantId": null,
                     "isGlobal": true,
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
               "reports": null,
               "dashboards": null,
               "numOfChilds": 1,
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
               "createdBy": "John Doe",
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
                     "name": "A",
                     "type": 1,
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
                     "id": "680af264-a2a1-43da-9ab5-7bfaf2a42025",
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
                     "name": "Uncategorized",
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
               "reports": null,
               "dashboards": null,
               "numOfChilds": 2,
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
         "pageIndex": 0,
         "pageSize": 0,
         "total": 8,
         "skipItems": 0,
         "isLastPage": true
      }

.. _POST_role:

POST role
--------------------------------------------------------------

Saves a role.

**Request**

    Payload: a :doc:`models/RoleDetail` object

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
       *  -  **role** |br|
             object
          -  The saved :doc:`models/RoleDetail` object
          -

.. note::

   The user password is not required in this API.

**Samples**

   .. code-block:: http

      POST api/role HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload to add new role with permission and visible data sources:

      .. code-block:: json

         {
            "users": [],
            "permission": {
               "fullReportAndDashboardAccess": false,
               "systemConfiguration": {
                  "scheduledInstances": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "tenantSetup": {
                  "actions": {
                     "create": false,
                     "edit": false,
                     "del": false,
                     "tenantAccess": 1
                  },
                  "permissions": {
                     "value": false,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "dataSetup": {
                  "dataModel": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "advancedSettings": {
                     "category": true,
                     "others": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "userSetup": {
                  "userRoleAssociation": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "actions": {
                     "create": true,
                     "edit": true,
                     "del": true,
                     "configureSecurityOptions": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "roleSetup": {
                  "actions": {
                     "create": true,
                     "edit": true,
                     "del": true,
                     "tenantAccess": 1
                  },
                  "dataModelAccess": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "permissions": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "grantRoleWithFullReportAndDashboardAccess": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "reports": {
                  "canCreateNewReport": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "dataSources": {
                     "simpleDataSources": true,
                     "advancedDataSources": false,
                     "tenantAccess": 1
                  },
                  "reportPartTypes": {
                     "chart": true,
                     "form": true,
                     "gauge": true,
                     "map": true,
                     "tenantAccess": 1
                  },
                  "reportCategoriesSubcategories": {
                     "canCreateNewCategory": {
                        "value": true,
                        "tenantAccess": 1
                     },
                     "categoryAccessibility": {
                        "categories": [
                           {
                              "id": "2a83e3ce-f91b-4f14-910d-76cadf42d0fe",
                              "savable": false,
                              "tenantId": null,
                              "name": "Global Categories",
                              "subCategories": [
                                 {
                                    "id": null,
                                    "savable": false,
                                    "tenantId": null,
                                    "name": "Uncategorized",
                                    "subCategories": []
                                 }
                              ]
                           },
                           {
                              "id": "09f8c4ab-0fe8-4e03-82d1-7949e3738f87",
                              "savable": true,
                              "tenantId": null,
                              "name": "Local Categories",
                              "subCategories": [
                                 {
                                    "id": null,
                                    "savable": true,
                                    "tenantId": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
                                    "name": "Uncategorized",
                                    "subCategories": []
                                 }
                              ]
                           }
                        ],
                        "tenantAccess": 1
                     }
                  },
                  "filterProperties": {
                     "filterLogic": true,
                     "tenantAccess": 1
                  },
                  "fieldProperties": {
                     "customURL": true,
                     "embeddedJavaScript": true,
                     "subreport": true,
                     "tenantAccess": 1
                  },
                  "actions": {
                     "schedule": true,
                     "email": true,
                     "viewReportHistory": true,
                     "del": true,
                     "registerForAlerts": true,
                     "print": true,
                     "unarchiveReportVersions": true,
                     "overwriteExistingReport": true,
                     "subscribe": true,
                     "exporting": true,
                     "configureAccessRights": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "dashboards": {
                  "canCreateNewDashboard": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "dashboardCategoriesSubcategories": {
                     "canCreateNewCategory": {
                        "value": true,
                        "tenantAccess": 1
                     },
                     "categoryAccessibility": {
                        "categories": [
                           {
                              "id": "2a83e3ce-f91b-4f14-910d-76cadf42d0fe",
                              "savable": false,
                              "tenantId": null,
                              "name": "Global Categories",
                              "subCategories": [
                                 {
                                    "id": null,
                                    "savable": false,
                                    "tenantId": null,
                                    "name": "Uncategorized",
                                    "subCategories": []
                                 }
                              ]
                           },
                           {
                              "id": "09f8c4ab-0fe8-4e03-82d1-7949e3738f87",
                              "savable": true,
                              "tenantId": null,
                              "name": "Local Categories",
                              "subCategories": [
                                 {
                                    "id": null,
                                    "savable": true,
                                    "tenantId": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
                                    "name": "Uncategorized",
                                    "subCategories": []
                                 }
                              ]
                           }
                        ],
                        "tenantAccess": 1
                     }
                  },
                  "actions": {
                     "schedule": true,
                     "email": true,
                     "del": true,
                     "subscribe": true,
                     "print": true,
                     "overwriteExistingDashboard": true,
                     "configureAccessRights": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "access": {
                  "accessLimits": {
                     "value": [],
                     "tenantAccess": 1
                  },
                  "accessDefaults": {
                     "value": [
                        {
                           "assignedType": 1,
                           "accessors": [],
                           "tempId": "4",
                           "id": null,
                           "reportAccessRightId": "13698ebf-3e8e-43e1-9e2b-ad3f17d7d004",
                           "dashboardAccessRightId": "13698ebf-3e8e-43e1-9e2b-ad3f17d7d008"
                        }
                     ],
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "scheduling": {
                  "schedulingLimits": {
                     "value": [],
                     "tenantAccess": 1
                  },
                  "schedulingScope": {
                     "systemUsers": true,
                     "externalUsers": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "emailing": {
                  "deliveryMethod": {
                     "link": true,
                     "embeddedHTML": true,
                     "attachment": true,
                     "tenantAccess": 1
                  },
                  "attachmentType": {
                     "word": true,
                     "excel": true,
                     "pdf": true,
                     "csv": true,
                     "xml": true,
                     "json": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "exporting": {
                  "exportingFormat": {
                     "word": true,
                     "excel": true,
                     "pdf": true,
                     "csv": true,
                     "xml": true,
                     "json": true,
                     "queryExecution": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               },
               "systemwide": {
                  "canSeeSystemMessages": {
                     "value": true,
                     "tenantAccess": 1
                  },
                  "tenantAccess": 1
               }
            },
            "visibleQuerySources": [
               {
                  "id": "3f4ed154-4b0e-47e6-a873-4dc807a216c0",
                  "querySourceFields": [
                     {
                        "id": "2d9bc2e8-4c8f-4791-a093-6e222da5d5ed"
                     },
                     {
                        "id": "52b366e6-81c4-44e6-8104-c8ae61220fea"
                     }
                  ]
               },
               {
                  "id": "22940912-9016-4c18-942b-bf7b4de5f4cd",
                  "querySourceFields": [
                     {
                        "id": "a56c409d-6f96-41e9-ad6d-882176cfcc92"
                     },
                     {
                        "id": "942640af-9743-463f-a2dd-55fe4244a6ce"
                     }
                  ]
               }
            ],
            "name": "Report Designer",
            "tenantId": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
            "active": true,
            "deleted": false,
            "state": 0,
            "inserted": false,
            "version": 0,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }

   .. container:: toggle

      .. container:: header

         Request payload to add an existing user to role:

      .. code-block:: json

         {
           "users": [
             {
               "id": "493ec9c6-9cb1-4a02-a4bc-505f684b3b4d",
               "userName": "jdoe",
               "emailAddress": "jdoe@acme.com",
               "firstName": "John",
               "lastName": "Doe",
               "fullName": "John Doe",
               "state": 0,
               "checkedAvailable": false,
               "checkedAssigned": false,
               "showInAvailable": false,
               "showInAssigned": true
             }
           ],
           "permission": {
             "fullReportAndDashboardAccess": false,
             "systemConfiguration": {
               "scheduledInstances": {
                 "value": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "tenantSetup": {
               "actions": {
                 "create": true,
                 "edit": true,
                 "del": true,
                 "tenantAccess": 0
               },
               "permissions": {
                 "value": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "dataSetup": {
               "dataModel": {
                 "value": true,
                 "tenantAccess": 0
               },
               "advancedSettings": {
                 "category": true,
                 "others": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "userSetup": {
               "userRoleAssociation": {
                 "value": true,
                 "tenantAccess": 0
               },
               "actions": {
                 "create": true,
                 "edit": true,
                 "del": true,
                 "configureSecurityOptions": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "roleSetup": {
               "actions": {
                 "create": true,
                 "edit": true,
                 "del": false,
                 "tenantAccess": 0
               },
               "dataModelAccess": {
                 "value": true,
                 "tenantAccess": 0
               },
               "permissions": {
                 "value": true,
                 "tenantAccess": 0
               },
               "grantRoleWithFullReportAndDashboardAccess": {
                 "value": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "reports": {
               "canCreateNewReport": {
                 "value": true,
                 "tenantAccess": 0
               },
               "dataSources": {
                 "simpleDataSources": true,
                 "advancedDataSources": false,
                 "tenantAccess": 0
               },
               "reportPartTypes": {
                 "chart": true,
                 "form": true,
                 "gauge": true,
                 "map": true,
                 "tenantAccess": 0
               },
               "reportCategoriesSubcategories": {
                 "canCreateNewCategory": {
                   "value": false,
                   "tenantAccess": 0
                 },
                 "categoryAccessibility": {
                   "categories": [
                     {
                       "name": "Category 1",
                       "type": 0,
                       "parentId": null,
                       "tenantId": null,
                       "canDelete": false,
                       "editable": false,
                       "savable": true,
                       "subCategories": [],
                       "id": "81411428-0aad-4a6b-b292-a26f75b83938",
                       "state": 0,
                       "deleted": false,
                       "inserted": true,
                       "version": null,
                       "created": null,
                       "createdBy": "493ec9c6-9cb1-4a02-a4bc-505f684b3b4d",
                       "modified": null,
                       "modifiedBy": null
                     }
                   ],
                   "tenantAccess": 0
                 }
               },
               "filterProperties": {
                 "filterLogic": true,
                 "tenantAccess": 0
               },
               "fieldProperties": {
                 "customURL": true,
                 "embeddedJavaScript": true,
                 "subreport": true,
                 "tenantAccess": 0
               },
               "actions": {
                 "schedule": true,
                 "email": true,
                 "viewReportHistory": true,
                 "del": true,
                 "registerForAlerts": true,
                 "print": true,
                 "unarchiveReportVersions": true,
                 "overwriteExistingReport": true,
                 "subscribe": true,
                 "exporting": true,
                 "configureAccessRights": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "dashboards": {
               "canCreateNewDashboard": {
                 "value": true,
                 "tenantAccess": 0
               },
               "dashboardCategoriesSubcategories": {
                 "canCreateNewCategory": {
                   "value": true,
                   "tenantAccess": 0
                 },
                 "categoryAccessibility": {
                   "categories": [],
                   "tenantAccess": 0
                 }
               },
               "actions": {
                 "schedule": true,
                 "email": true,
                 "del": true,
                 "subscribe": true,
                 "print": true,
                 "overwriteExistingDashboard": true,
                 "configureAccessRights": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "access": {
               "accessLimits": {
                 "value": [],
                 "tenantAccess": 0
               },
               "accessDefaults": {
                 "value": [],
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "scheduling": {
               "schedulingLimits": {
                 "value": [],
                 "tenantAccess": 0
               },
               "schedulingScope": {
                 "systemUsers": false,
                 "externalUsers": false,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "emailing": {
               "deliveryMethod": {
                 "link": true,
                 "embeddedHTML": true,
                 "attachment": true,
                 "tenantAccess": 0
               },
               "attachmentType": {
                 "word": true,
                 "excel": true,
                 "pdf": true,
                 "csv": true,
                 "xml": true,
                 "json": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "exporting": {
               "exportingFormat": {
                 "word": true,
                 "excel": true,
                 "pdf": true,
                 "csv": true,
                 "xml": true,
                 "json": true,
                 "queryExecution": true,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             },
             "systemwide": {
               "canSeeSystemMessages": {
                 "value": false,
                 "tenantAccess": 0
               },
               "tenantAccess": 0
             }
           },
           "visibleQuerySources": [],
           "name": "role 1",
           "tenantId": null,
           "active": true,
           "deleted": false,
           "state": 0,
           "inserted": true,
           "version": 6,
           "created": "2016-11-05T10:08:12.513",
           "createdBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe",
           "modified": "2016-11-15T09:09:55.18",
           "modifiedBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe",
           "id": "7a119576-de72-4268-9685-f0676aeb428a"
         }


GET role/summaries/(tenant_id)
--------------------------------------------------------------

Returns an array of roles filtered by tenant_id.

**Request**

    No payload

**Response**

    An array of :doc:`models/RoleDetail` objects

**Samples**

   .. code-block:: http

      GET api/role/summaries HTTP/1.1

   Sample response::

      [{
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Anonymous",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd285",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Reviewer",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd282",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }, {
           "users" : [],
           "permission" : null,
           "visibleQuerySourceFields" : null,
           "name" : "Designer",
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "id" : "0d030b1a-9568-4c98-8b1e-5dcc94dbd283",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
      ]

POST role/allowedSharingRoles
--------------------------------------------------------------

Returns a list of roles allowed to be selected in report/dashboard access.

**Request**

    Payload: a :doc:`models/SharingRoleUserParameter` object

**Response**

    An array of :doc:`models/RoleDetail` objects

**Samples**

   .. code-block:: http

      POST api/role/allowedSharingRoles HTTP/1.1

   Request payload::

      {
        "reportId": "63d50ed1-5323-47a1-bc11-3a03a070ec34",
        "tenantId": null
      }

   Sample response::

      [
        {
          "users": [
            {
              "password": null,
              "roles": [],
              "userRoles": null,
              "userSecurityQuestions": null,
              "status": 1,
              "issueDate": "0001-01-01T00:00:00",
              "autoLogin": false,
              "newPassword": null,
              "userName": "admintest",
              "emailAddress": null,
              "firstName": "admin",
              "lastName": "test",
              "tenantId": null,
              "tenantDisplayId": null,
              "tenantName": null,
              "dataOffset": 0,
              "timestampOffset": 0,
              "initPassword": true,
              "active": true,
              "retryLoginTime": 0,
              "lastTimeAccessed": "2016-12-19T10:00:38.54",
              "passwordLastChanged": "2016-11-04T09:54:22.417",
              "locked": false,
              "lockedDate": null,
              "cultureName": "en-US",
              "securityQuestionLastChanged": "2016-11-04T09:54:22.417",
              "dateFormat": "MM/DD/YYYY",
              "systemAdmin": true,
              "notAllowSharing": false,
              "numberOfFailedSecurityQuestion": 0,
              "fullName": "admin test",
              "currentModules": null,
              "id": "65a2e205-bbe3-4e75-8766-28aeaaf44f5d",
              "state": 0,
              "deleted": false,
              "inserted": true,
              "version": 2,
              "created": "2016-11-04T09:53:58.613",
              "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
              "modified": "2016-12-19T10:00:38.54",
              "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
            }
          ],
          "tenantUniqueName": null,
          "permission": null,
          "visibleQuerySources": null,
          "name": "new system role",
          "tenantId": null,
          "active": true,
          "notAllowSharing": false,
          "id": "1bbc0a0a-fb1b-444c-a355-63b32ef7aabb",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": 9,
          "created": "2016-11-05T09:57:06.393",
          "createdBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe",
          "modified": "2016-11-12T10:19:14.797",
          "modifiedBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe"
        },
        {
          "users": [],
          "tenantUniqueName": null,
          "permission": null,
          "visibleQuerySources": null,
          "name": "No Permission Role",
          "tenantId": null,
          "active": true,
          "notAllowSharing": false,
          "id": "7faab1a0-8ca3-4dc2-af86-19e5396b76a9",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": 1,
          "created": "2016-11-28T06:54:29.493",
          "createdBy": "9feea667-0bef-4dc7-bf6c-d7259f334fde",
          "modified": "2016-11-28T06:54:29.493",
          "modifiedBy": "9feea667-0bef-4dc7-bf6c-d7259f334fde"
        },
        {
          "users": [],
          "tenantUniqueName": null,
          "permission": null,
          "visibleQuerySources": null,
          "name": "role 1",
          "tenantId": null,
          "active": true,
          "notAllowSharing": false,
          "id": "7a119576-de72-4268-9685-f0676aeb428a",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": 7,
          "created": "2016-11-05T10:08:12.513",
          "createdBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe",
          "modified": "2016-12-14T08:51:37.32",
          "modifiedBy": "0fa44ace-abd7-4a8d-928e-c84ec2999dfe"
        }
      ]

POST role/intergration/saveRole
--------------------------------------------------------------

Adds or updates an external role.

**Request**

    Payload: a :doc:`models/RoleDetail` object

**Response**

    * true if the call is successful
    * false if not

**Samples**

    To be updated
