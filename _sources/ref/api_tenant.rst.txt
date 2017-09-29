

============================
Tenant APIs
============================

The **Tenant Setup** page allows user to

* manage tenants
* manage tenants' modules
* manage tenants' users and roles

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `GET tenant/allTenants`_
     - Returns an array of all tenants.
   * - `GET tenant/{tenant_id}`_
     - Returns the tenant specified by tenant_id.
   * - `POST tenant`_
     - Saves a tenant.
   * - `POST tenant/active/{tenant_id}`_
     - Sets active for the tenant specified by tenant_id.
   * - `POST tenant/deactive/{tenant_id}`_
     - Sets inactive for the tenant specified by tenant_id.
   * - `DELETE tenant/{tenant_id}`_
     - Deletes the tenant specified by tenant_id.
   * - `GET tenant/activeTenants`_
     - Returns an array of active tenants.
   * - `GET tenant/availableCategory/{type}`_
     - .. deprecated:: 2.0.0
            superseded by :ref:`POST_role/availableCategory` |br| |br|

       Returns an array of available categories for report/template (type=0) or dashboard (type=1).
   * - `POST tenant/intergration/saveTenant`_
     - Adds or updates external tenant.
     
       .. note::
          
          To be renamed to "integration"

   * - `GET tenant/basicInfos`_
     - Returns all active tenants with basic info.
   * - `GET tenant/namesOnly`_
     - Returns all active tenants with names only.

GET tenant/allTenants
--------------------------------------------------------------

Returns an array of all tenants.

**Request**

    No payload

**Response**

    An array of :doc:`models/Tenants` objects

**Samples**

   .. code-block:: http

      GET /api/tenant/allTenants HTTP/1.1

   Sample response::

      [{
           "id" : "e4c784eb-3e41-4849-925c-a9094b73dfb7",
           "tenantID" : "acme",
           "name" : "ACME Corporation",
           "description" : null,
           "active" : true,
           "deleted" : false,
           "modules" : "Report Template/ Component; Scheduling",
           "tenantModules" : ["Report Template/ Component", "Scheduling"],
           "permissionData" : null,
           "permission": null,
           "state" : 0,
           "inserted" : true,
           "version" : 2,
           "created" "2017-06-15T09:03:04.7770000+07:00",
           "createdBy": "System2 Admin2",
           "modified" : "2017-09-05T07:59:14.6970000+07:00",
           "modifiedBy": "System2 Admin2"
        }, {
           "id" : "811e2d3b-c656-46fa-b70e-7fe95bc6529f",
           "tenantID" : "doe",
           "name" : "John Doe",
           "description" : null,
           "active" : true,
           "deleted" : false,
           "modules" : "Report Template/ Component; Scheduling",
           "modified" : "2016-05-22T03:26:32.0000000+07:00",
           "tenantModules" : ["Report Template/ Component", "Scheduling"],
           "permissionData" : null,
           "permission": null,
           "state" : 0,
           "inserted" : true,
           "version" : 2,
           "created" "2017-06-23T08:07:50.5700000+07:00",
           "createdBy": "$RootAdmin$",
           "modified" : "2017-08-16T09:15:59.5400000+07:00",
           "modifiedBy": "$RootAdmin$"
        }
      ]


GET tenant/{tenant_id}
--------------------------------------------------------------

Returns the tenant specified by tenant_id.

**Request**

    No payload

**Response**

    A :doc:`models/Tenants` object

**Samples**

   .. code-block:: http

      GET /api/tenant/e4c784eb-3e41-4849-925c-a9094b73dfb7 HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample Response :

      .. code-block:: json

         {
            "tenantID": "acme",
            "name": "ACME Corporation",
            "description": null,
            "active": true,
            "modules": "maUqbVKEX7hSyzaUp2nEAdVdmBVmue6S2e72m8XBl/OHx7ysEcRYz7YEjYqMhOnL0jpxXGB7saUIPgZ+58bWkH+ZBadLbo4SqixBr9Dtv+uIrVWFs1JJDdudOyn+nSr+sjPDAbD/BzjU3NGFV9mjBA==",
            "tenantModules": [
               "Alerting",
               "Report Templates",
               "Report Designer",
               "Form",
               "Scheduling",
               "Charting",
               "Dashboard",
               "Exporting",
               "Maps"
            ],
            "permission": {
               "systemAdmin": false,
               "fullReportAndDashboardAccess": false,
               "systemConfiguration": {
                     "scheduledInstances": {
                        "value": true,
                        "tenantAccess": 1
                     },
                     "tenantAccess": 1
               },
               "dataSetup": {
                     "dataModel": {
                        "value": true,
                        "customView": {
                           "create": true,
                           "edit": true,
                           "delete": true,
                           "tenantAccess": 1
                        },
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
                        "simpleDataSources": false,
                        "advancedDataSources": true,
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
                           "categories": [],
                           "tenantAccess": 1
                        }
                     },
                     "filterProperties": {
                        "filterLogic": true,
                        "crossFiltering": true,
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
                           "categories": [],
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
                        "value": [
                           {
                                 "users": [],
                                 "tenantUniqueName": null,
                                 "permission": null,
                                 "visibleQuerySources": null,
                                 "name": "Manager",
                                 "tenantId": null,
                                 "active": false,
                                 "notAllowSharing": false,
                                 "id": "d256d058-aeb7-468f-9f95-962d65979707",
                                 "state": 0,
                                 "deleted": false,
                                 "inserted": true,
                                 "version": null,
                                 "created": null,
                                 "createdBy": "$RootAdmin$",
                                 "modified": null,
                                 "modifiedBy": null
                           }
                        ],
                        "tenantAccess": 1
                     },
                     "accessDefaults": {
                        "value": [],
                        "tenantAccess": 1
                     },
                     "tenantAccess": 1
               },
               "scheduling": {
                     "schedulingLimits": {
                        "value": [
                           {
                                 "users": [],
                                 "tenantUniqueName": null,
                                 "permission": null,
                                 "visibleQuerySources": null,
                                 "name": "Manager",
                                 "tenantId": null,
                                 "active": false,
                                 "notAllowSharing": false,
                                 "id": "d256d058-aeb7-468f-9f95-962d65979707",
                                 "state": 0,
                                 "deleted": false,
                                 "inserted": true,
                                 "version": null,
                                 "created": null,
                                 "createdBy": "$RootAdmin$",
                                 "modified": null,
                                 "modifiedBy": null
                           }
                        ],
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
            "id": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 6,
            "created": "2017-09-08T07:11:10.857",
            "createdBy": "$RootAdmin$",
            "modified": "2017-09-14T02:30:28.627",
            "modifiedBy": "$RootAdmin$"
         }

.. _POST_tenant:

POST tenant
--------------------------------------------------------------

Saves a tenant.

**Request**

    Payload: a :doc:`models/Tenants` object

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
       *  -  **tenant** |br|
             object
          -  The saved :doc:`models/Tenants` object
          -

**Samples**

   .. code-block:: http

      POST /api/tenant HTTP/1.1

   Simple Request payload::

      {
        "tenantID" : "doe",
        "name" : "DOE",
        "tenantModules" : ["Report Template/ Component", "Scheduling"]
      }

   .. container:: toggle

      .. container:: header

         Request payload with full permission (see :doc:`models/Permission` object) :

      .. code-block:: json

         {
           "tenantID": "stark",
           "name": "Stark Industries",
           "description": "Fictional Company",
           "active": true,
           "tenantModules": ["Alerting", "Form", "Dashboard", "Report Templates", "Scheduling", "Exporting", "Report Designer", "Charting", "Maps"],
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
                 "simpleDataSources": false,
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
                   "categories": [],
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
                   "categories": [],
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
                 "value": [{
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
           "version": 0
         }

POST tenant/active/{tenant_id}
--------------------------------------------------------------

Sets active for the tenant specified by tenant_id.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/tenant/active/e2bae114-11d6-4c29-ab2b-2c3d3f6ba751 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data": null
      }


POST tenant/deactive/{tenant_id}
--------------------------------------------------------------

Sets inactive for the tenant specified by tenant_id.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/tenant/deactive/e2bae114-11d6-4c29-ab2b-2c3d3f6ba751 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data": null
      }


DELETE tenant/{tenant_id}
--------------------------------------------------------------

Deletes the tenant specified by tenant_id.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the deletion is successful

**Samples**

   .. code-block:: http

      DELETE /api/tenant/811e2d3b-c656-46fa-b70e-7fe95bc6529f HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data": null
      }

.. _GET_tenant/activeTenants:

GET tenant/activeTenants
--------------------------------------------------------------

Returns an array of active tenants.

**Request**

    No payload

**Response**

    An array of :doc:`models/Tenants` objects

**Samples**

   .. code-block:: http

      GET /api/tenant/activeTenants HTTP/1.1

   Sample response::

      [{
        "tenantID": "acme",
        "name": "ACME Corporation",
        "description": null,
        "active": true,
        "modules": null,
        "permissionData": null,
        "tenantModules": [],
        "permission": null,
        "id": "1658c545-2ee4-4952-98f8-7d4e8b6c4e04",
        "state": 0,
        "deleted": false,
        "inserted": true,
        "version": null,
        "created": null,
        "createdBy": null,
        "modified": null,
        "modifiedBy": null
      }]


GET tenant/availableCategory/{type}
--------------------------------------------------------------

.. deprecated:: 2.0.0
   superseded by :ref:`POST_role/availableCategory`

Returns an array of available categories for report/template (type=0) or dashboard (type=1).

**Request**

    No payload

**Response**

    An array of :doc:`models/Category` objects

**Samples**

   .. code-block:: http

      GET /api/tenant/availableCategory/0 HTTP/1.1

   Sample response::

      [{
            "name": "0 july 19",
            "type": 0,
            "parentId": null,
            "tenantId": null,
            "isGlobal": false,
            "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
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
            "status": 2,
            "fullPath": null,
            "computeNameSettings": null,
            "isCheck": false,
            "id": "e6b0d0e1-85f0-4708-bd3e-6ca074de94c8",
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
            "name": "12062017",
            "type": 0,
            "parentId": null,
            "tenantId": null,
            "isGlobal": false,
            "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
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
            "status": 2,
            "fullPath": null,
            "computeNameSettings": null,
            "isCheck": false,
            "id": "f0e8668a-ff01-4d94-8f59-3dab8bf373ff",
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


POST tenant/intergration/saveTenant
--------------------------------------------------------------

Adds or updates external tenant.

**Request**

    Payload: a :doc:`models/Tenants` object

**Response**

    Should be true

**Samples**

   .. code-block:: http

      POST /api/tenant/intergration/saveTenant HTTP/1.1

   Simple Request payload::

      {
         "tenantID": "Pikachu",
         "name": "Pikachu",
         "description": "abc",
         "active": true,
         "modules": null,
         "tenantModules": [],
         "permission": null,
         "id": "c1703d12-6f50-454a-82bc-16efc00bbedd",
         "state": 0,
         "deleted": false,
         "inserted": true,
         "version": 1,
         "created": "2017-09-11T09:14:39.7",
         "createdBy": "$RootAdmin$",
         "modified": "2017-09-11T09:14:39.7",
         "modifiedBy": "$RootAdmin$"
      }

   Response::

      true

GET tenant/basicInfos
--------------------------------------------------------------

Returns all active tenants with basic info.

Returns only the current tenant with basic info if logged in user is a tenant user.

**Request**

    No payload

**Response**

   An array of the following objects:

   .. list-table::
      :header-rows: 1

      *  -  Field
         -  Description
         -  Note
      *  -  **id** |br|
            string (GUID)
         - The id of the tenant
         -
      *  -  **tenantId** |br|
            string
         - The user-selected id of the tenant
         -
      *  -  **name** |br|
            string
         - The name of the tenant
         -
      *  -  **active** |br|
            boolean
         - Whether the tenant is active
         -
      *  -  **description** |br|
            string
         - The description of the tenant
         -
      *  -  **tenantModules** |br|
            array of strings
         -  An array of selected module names for the tenant
         -

**Samples**

   .. code-block:: http

      GET /api/tenant/basicInfos HTTP/1.1

   Sample response::

      [
         {
            "id": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
            "tenantID": "acme",
            "name": "Acme Yo",
            "active": true,
            "description": null,
            "tenantModules": [
                  "Alerting",
                  "Report Templates",
                  "Report Designer",
                  "Form",
                  "Scheduling",
                  "Charting",
                  "Dashboard",
                  "Exporting",
                  "Maps"
            ]
         },
         {
            "id": "6d775a01-f6c4-48f2-8678-4f8aa081db49",
            "tenantID": "System",
            "name": "System",
            "active": true,
            "description": null,
            "tenantModules": [
                  "Alerting",
                  "Report Templates",
                  "Report Designer",
                  "Form",
                  "Scheduling",
                  "Charting",
                  "Exporting",
                  "Dashboard",
                  "Maps"
            ]
         }
      ]

GET tenant/namesOnly
--------------------------------------------------------------

Returns all active tenants with names only.

Returns only the current tenant with name only if logged in user is a tenant user.

**Request**

    No payload

**Response**

   An array of the following objects:

   .. list-table::
      :header-rows: 1

      *  -  Field
         -  Description
         -  Note
      *  -  **id** |br|
            string (GUID)
         - The id of the tenant
         -
      *  -  **tenantId** |br|
            string
         - The user-selected id of the tenant
         -
      *  -  **name** |br|
            string
         - The name of the tenant
         -

**Samples**

   .. code-block:: http

      GET /api/tenant/namesOnly HTTP/1.1

   Sample response::

      [
         {
            "id": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
            "tenantID": "acme",
            "name": "Acme Yo"
         },
         {
            "id": "6d775a01-f6c4-48f2-8678-4f8aa081db49",
            "tenantID": "System",
            "name": "System"
         }
      ]
