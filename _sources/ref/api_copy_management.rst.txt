

============================
Copy Management APIs
============================

The **Copy Management** page allows user to:

*  define rules to copy data among system and tenants, including:

   .. hlist::
      :columns: 2
      
      * logical data model
      * advanced data settings
      * dashboards
      * reports
      * tenant permissions
      * role names
      * roles and their permissions
*  validate data model consistency between two locations
*  save mapping rules into workspaces

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 30 35 35
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET copyManagement/workspace/{workspace_id}`_
     - Returns details of the workspace specified by workspace_id.
     -
   * - `GET copyManagement/workspaces/{tenant_id}/{onlyMyWorkspace}`_
     - Returns a list of workspaces filtered by tenant_id if not null, and by current logged on user if onlyMyWorkspace equals true.
     - Setting > Data Setup > Copy Management > Show only my workspaces OR make some changes and Save
   * - `POST copyManagement/workspace/validateName`_
     - Validates if workspace name is unique.
     -
   * - `POST copyManagement`_
     - Saves a workspace.

       .. note::

          Not POST copyManagement/workspace
     -
   * - `DELETE copyManagement/workspace/{workspace_id}`_
     - Deletes the workspace specified by workspace_id.
     - 
   * - `POST copyManagement/copy`_
     - Run the copy operation based on settings in a workspace.
     -
   * - `POST copyManagement/connectionsHasDataModel`_
     - Checks if connections have already had data model.
     -
   * - POST copyManagement/workspace/loadDestinationConnections
     - Returns a list of connections for destination drop-down.

       .. note::

          Obsolete, use :ref:`POST_connection/loadDistinctConnections` instead
     -
   * - `POST copyManagement/workspace/validate`_
     - Validates the workspace.
     - Not used
   * - `POST copyManagement/workspace/validateWorkspaceTenant`_
     - Validates that the mappings are valid, destination tenants have the same connections, and have no physical changes.
     -
   * - `POST copyManagement/workspace/validateConcurrency`_
     - Validates workspace concurrency.
     -
   * - `POST copyManagement/workspace/detectConflictingTenantPermissions`_
     - Detect conflicting tenant's permissions.
     -
   * - `POST copyManagement/workspace/detectConflictingAdvancedSettings`_
     - Detect conflicting tenant's advanced settings.
     -
   * - `POST copyManagement/workspace/detectConflictingReport`_
     - Detect conflicting tenant's reports.
     -
   * - `POST copyManagement/workspace/detectConflictingRolePermission`_
     - Detect role names already existing in destination tenants.
     -
   * - `POST copyManagement/workspace/detectConflictingTemplate`_
     - Detect conflicting tenant's templates.
     -
   * - `POST copyManagement/workspace/detectConflictingDashboard`_
     - Detect conflicting tenant's dashboards.
     -


GET copyManagement/workspace/{workspace_id}
--------------------------------------------------------------

Returns details of the workspace specified by workspace_id.

**Request**

    No payload

**Response**

    A :doc:`models/WorkspaceDetail` object

**Samples**

   .. code-block:: http

      GET api/copyManagement/workspace/49d886bc-45be-4acf-8ebe-4de775546f8c HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "workspaceTenants" : [{
                 "destinationConnections" : [],
                 "sourceConnections" : [],
                 "tenantName" : "Tenant 1",
                 "tenantUniqueName" : "T1",
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "tenantId" : "9ef4b0af-2485-4050-91b9-cf149d999afd",
                 "status" : 0,
                 "id" : null,
                 "state" : 0,
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "workspaceMappings" : [{
                 "workspaceMappingTenants" : [],
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "fromDatabaseName" : "[MSSQL] Northwind",
                 "type" : 2,
                 "fromObject" : "",
                 "toDatabaseName" : "",
                 "toObject" : "",
                 "isGlobal" : false,
                 "id" : "b0cd65d5-762a-48be-afc8-5bc9678aebd0",
                 "state" : 0,
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "copyOption" : null,
           "sourceConnections" : [{
                 "id" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                 "name" : "1234 1351",
                 "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                 "serverTypeName" : "MSSQL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                          "querySources" : [{
                                "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                "name" : "Categories",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceFields" : [{
                                      "name" : "CategoryID",
                                      "alias" : "",
                                      "dataType" : "int",
                                      "izendaDataType" : "Numeric",
                                      "allowDistinct" : true,
                                      "visible" : true,
                                      "filterable" : true,
                                      "deleted" : false,
                                      "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "parentId" : null,
                                      "expressionFields" : [],
                                      "filteredValue" : "",
                                      "type" : 0,
                                      "groupPosition" : 0,
                                      "position" : 1,
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
                                      "originalName" : null,
                                      "isParameter" : false,
                                      "isCalculated" : false,
                                      "hasAggregatedFunction" : false,
                                      "querySource" : null,
                                      "fullPath" : null,
                                      "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                      "state" : 0,
                                      "inserted" : true,
                                      "version" : null,
                                      "created" : null,
                                      "createdBy" : null,
                                      "modified" : "2016-08-22T04:32:32.173",
                                      "modifiedBy" : null
                                   }],
                                "querySourceCategoryName" : null,
                                "querySourceCategory" : null,
                                "modified" : "2016-08-22T04:32:31.85",
                                "extendedProperties" : null,
                                "physicalChange" : 0,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : 0,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : 0,
                 "checked" : true,
                 "databaseName" : "Northwind",
                 "fullPath" : null
              }
           ],
           "name" : "235",
           "description" : "dgsd",
           "tenantId" : null,
           "ownerId" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
           "deleted" : false,
           "copyRoles" : false,
           "copyRolePermission" : false,
           "copyAdvancedSettings" : false,
           "copyDataModel" : false,
           "sourceId" : "00000000-0000-0000-0000-000000000000",
           "selectAllTenants" : false,
           "id" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
           "state" : 0,
           "inserted" : true,
           "version" : null,
           "created" : "2016-08-22T04:36:09.063",
           "createdBy" : null,
           "modified" : "2016-08-22T04:36:09.063",
           "modifiedBy" : null
         }

GET copyManagement/workspaces/{tenant_id}/{onlyMyWorkspace}
--------------------------------------------------------------

Returns a list of workspaces filtered by tenant_id if not null, and by current logged on user if onlyMyWorkspace equals true.

**Request**

    No payload

**Response**

    An array of :doc:`models/Workspace` objects

**Samples**

   .. code-block:: http

      GET /api/copyManagement/workspaces/null/false HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
              "name" : "Workspace01",
              "description" : "Workspace for copying rule 01",
              "tenantId" : null,
              "ownerId" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
              "deleted" : false,
              "copyRoles" : false,
              "copyRolePermission" : false,
              "copyAdvancedSettings" : false,
              "copyDataModel" : false,
              "sourceId" : "00000000-0000-0000-0000-000000000000",
              "selectAllTenants" : false,
              "id" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
              "state" : 0,
              "inserted" : true,
              "version" : null,
              "created" : "2016-08-22T04:36:09.063",
              "createdBy" : null,
              "modified" : "2016-08-22T04:36:09.063",
              "modifiedBy" : null
           }
         ]

POST copyManagement/workspace/validateName
--------------------------------------------------------------

Validates if workspace name is unique.

**Request**

    Payload: a :doc:`models/Workspace` object

**Response**

    * true if the name is valid
    * false if not

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/validateName HTTP/1.1

   Request payload::

      {
        "Id" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
        "Name" : "Workspace01"
      }

   Sample success response::

      true

   Sample failure response::

      {
         "success": false,
         "messages": [
            {
                  "key": "Name",
                  "detail": null,
                  "messages": [
                     "The workspace Workspace01 already exists"
                  ]
            }
         ],
         "data": null
      }

POST copyManagement
--------------------------------------------------------------

Saves a workspace.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    The saved :doc:`models/WorkspaceDetail` object

**Samples**

   .. code-block:: http

      POST /api/copyManagement HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "id" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
           "name" : "Workspace01",
           "description" : "dgsd",
           "tenantId" : null,
           "ownerId" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
           "created" : "2016-08-22T04:36:09.063",
           "createdBy" : null,
           "deleted" : false,
           "modified" : "2016-08-22T04:36:09.063",
           "copyRoles" : false,
           "copyRolePermission" : false,
           "copyAdvancedSettings" : false,
           "sourceId" : "00000000-0000-0000-0000-000000000000",
           "state" : 0,
           "inserted" : null,
           "selectAllTenants" : false,
           "sourceConnections" : [{
                 "id" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                 "name" : "1234 1351",
                 "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                 "serverTypeName" : "MSSQL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                          "querySources" : [{
                                "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                "name" : "Categories",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceFields" : [{
                                      "name" : "CategoryID",
                                      "alias" : "",
                                      "dataType" : "int",
                                      "izendaDataType" : "Numeric",
                                      "allowDistinct" : true,
                                      "visible" : true,
                                      "filterable" : true,
                                      "deleted" : false,
                                      "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "parentId" : null,
                                      "expressionFields" : [],
                                      "filteredValue" : "",
                                      "type" : 0,
                                      "groupPosition" : 0,
                                      "position" : 1,
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
                                      "originalName" : null,
                                      "isParameter" : false,
                                      "isCalculated" : false,
                                      "hasAggregatedFunction" : false,
                                      "querySource" : null,
                                      "fullPath" : null,
                                      "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                      "state" : 0,
                                      "inserted" : true,
                                      "version" : null,
                                      "created" : null,
                                      "createdBy" : null,
                                      "modified" : "2016-08-22T04:32:32.173",
                                      "modifiedBy" : null
                                   }],
                                "querySourceCategoryName" : null,
                                "querySourceCategory" : null,
                                "modified" : "2016-08-22T04:32:31.85",
                                "extendedProperties" : null,
                                "physicalChange" : 0,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : 0,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : 0,
                 "checked" : true,
                 "databaseName" : "Northwind",
                 "fullPath" : null,
                 "fullDBName" : "[MSSQL] Northwind",
                 "querySources" : [{
                       "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                       "name" : "dbo",
                       "parentCategoryId" : null,
                       "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                       "querySources" : [{
                             "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                             "name" : "Categories",
                             "type" : "Table",
                             "parentQuerySourceId" : null,
                             "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                             "selected" : false,
                             "connectionId" : "00000000-0000-0000-0000-000000000000",
                             "connectionName" : null,
                             "childs" : null,
                             "dataSourceCategoryId" : null,
                             "dataSourceCategoryName" : null,
                             "alias" : null,
                             "querySourceFields" : [{
                                   "name" : "CategoryID",
                                   "alias" : "",
                                   "dataType" : "int",
                                   "izendaDataType" : "Numeric",
                                   "allowDistinct" : true,
                                   "visible" : true,
                                   "filterable" : true,
                                   "deleted" : false,
                                   "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "parentId" : null,
                                   "expressionFields" : [],
                                   "filteredValue" : "",
                                   "type" : 0,
                                   "groupPosition" : 0,
                                   "position" : 1,
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
                                   "originalName" : null,
                                   "isParameter" : false,
                                   "isCalculated" : false,
                                   "hasAggregatedFunction" : false,
                                   "querySource" : null,
                                   "fullPath" : null,
                                   "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                   "state" : 0,
                                   "inserted" : true,
                                   "version" : null,
                                   "created" : null,
                                   "createdBy" : null,
                                   "modified" : "2016-08-22T04:32:32.173",
                                   "modifiedBy" : null
                                }, {
                                   "name" : "CategoryName",
                                   "alias" : "",
                                   "dataType" : "nvarchar",
                                   "izendaDataType" : "Text",
                                   "allowDistinct" : true,
                                   "visible" : true,
                                   "filterable" : true,
                                   "deleted" : false,
                                   "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "parentId" : null,
                                   "expressionFields" : [],
                                   "filteredValue" : "",
                                   "type" : 0,
                                   "groupPosition" : 0,
                                   "position" : 2,
                                   "extendedProperties" : "",
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "matchedTenant" : false,
                                   "functionName" : null,
                                   "expression" : null,
                                   "fullName" : null,
                                   "calculatedTree" : null,
                                   "reportId" : null,
                                   "originalName" : null,
                                   "isParameter" : false,
                                   "isCalculated" : false,
                                   "hasAggregatedFunction" : false,
                                   "querySource" : null,
                                   "fullPath" : null,
                                   "id" : "d202ef02-14ae-4f1a-8364-d7ac7d89ac1f",
                                   "state" : 0,
                                   "inserted" : true,
                                   "version" : null,
                                   "created" : null,
                                   "createdBy" : null,
                                   "modified" : "2016-08-22T04:32:32.173",
                                   "modifiedBy" : null
                                }, {
                                   "name" : "Description",
                                   "alias" : "",
                                   "dataType" : "ntext",
                                   "izendaDataType" : "Lob",
                                   "allowDistinct" : false,
                                   "visible" : true,
                                   "filterable" : true,
                                   "deleted" : false,
                                   "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "parentId" : null,
                                   "expressionFields" : [],
                                   "filteredValue" : "",
                                   "type" : 0,
                                   "groupPosition" : 0,
                                   "position" : 3,
                                   "extendedProperties" : "",
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "matchedTenant" : false,
                                   "functionName" : null,
                                   "expression" : null,
                                   "fullName" : null,
                                   "calculatedTree" : null,
                                   "reportId" : null,
                                   "originalName" : null,
                                   "isParameter" : false,
                                   "isCalculated" : false,
                                   "hasAggregatedFunction" : false,
                                   "querySource" : null,
                                   "fullPath" : null,
                                   "id" : "06cb8ba9-e719-4dfd-a903-7512d6555a7b",
                                   "state" : 0,
                                   "inserted" : true,
                                   "version" : null,
                                   "created" : null,
                                   "createdBy" : null,
                                   "modified" : "2016-08-22T04:32:32.173",
                                   "modifiedBy" : null
                                }, {
                                   "name" : "Picture",
                                   "alias" : "",
                                   "dataType" : "image",
                                   "izendaDataType" : "Image",
                                   "allowDistinct" : false,
                                   "visible" : true,
                                   "filterable" : true,
                                   "deleted" : false,
                                   "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "parentId" : null,
                                   "expressionFields" : [],
                                   "filteredValue" : "",
                                   "type" : 0,
                                   "groupPosition" : 0,
                                   "position" : 4,
                                   "extendedProperties" : "",
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "matchedTenant" : false,
                                   "functionName" : null,
                                   "expression" : null,
                                   "fullName" : null,
                                   "calculatedTree" : null,
                                   "reportId" : null,
                                   "originalName" : null,
                                   "isParameter" : false,
                                   "isCalculated" : false,
                                   "hasAggregatedFunction" : false,
                                   "querySource" : null,
                                   "fullPath" : null,
                                   "id" : "003c2e54-58ff-4fe1-bfb2-16efd0fcdbda",
                                   "state" : 0,
                                   "inserted" : true,
                                   "version" : null,
                                   "created" : null,
                                   "createdBy" : null,
                                   "modified" : "2016-08-22T04:32:32.173",
                                   "modifiedBy" : null
                                }
                             ],
                             "querySourceCategoryName" : null,
                             "querySourceCategory" : null,
                             "modified" : "2016-08-22T04:32:31.85",
                             "extendedProperties" : null,
                             "physicalChange" : 0,
                             "approval" : 0,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }
                       ],
                       "childs" : null,
                       "connection" : null,
                       "physicalChange" : 0,
                       "existed" : false,
                       "checked" : true,
                       "fullPath" : null
                    }
                 ]
              }
           ],
           "workspaceTenants" : [{
                 "isDirty" : false,
                 "tenantName" : "Tenant 1",
                 "tenantUniqueName" : "T1",
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "tenantId" : "9ef4b0af-2485-4050-91b9-cf149d999afd",
                 "status" : 0,
                 "state" : 0,
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null,
                 "destinationConnections" : [],
                 "sourceConnections" : [{
                       "id" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                       "name" : "1234 1351",
                       "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                       "serverTypeName" : "MSSQL",
                       "connectionString" : "secret",
                       "visible" : true,
                       "deleted" : false,
                       "relateToConnectionId" : null,
                       "tenantId" : null,
                       "dbSource" : {
                          "querySources" : [{
                                "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "name" : "dbo",
                                "parentCategoryId" : null,
                                "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                                "querySources" : [{
                                      "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "name" : "Categories",
                                      "type" : "Table",
                                      "parentQuerySourceId" : null,
                                      "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                      "selected" : false,
                                      "connectionId" : "00000000-0000-0000-0000-000000000000",
                                      "connectionName" : null,
                                      "childs" : null,
                                      "dataSourceCategoryId" : null,
                                      "dataSourceCategoryName" : null,
                                      "alias" : null,
                                      "querySourceFields" : [{
                                            "name" : "CategoryID",
                                            "alias" : "",
                                            "dataType" : "int",
                                            "izendaDataType" : "Numeric",
                                            "allowDistinct" : true,
                                            "visible" : true,
                                            "filterable" : true,
                                            "deleted" : false,
                                            "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                            "parentId" : null,
                                            "expressionFields" : [],
                                            "filteredValue" : "",
                                            "type" : 0,
                                            "groupPosition" : 0,
                                            "position" : 1,
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
                                            "originalName" : null,
                                            "isParameter" : false,
                                            "isCalculated" : false,
                                            "hasAggregatedFunction" : false,
                                            "querySource" : null,
                                            "fullPath" : null,
                                            "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                            "state" : 0,
                                            "inserted" : true,
                                            "version" : null,
                                            "created" : null,
                                            "createdBy" : null,
                                            "modified" : "2016-08-22T04:32:32.173",
                                            "modifiedBy" : null
                                         }],
                                      "querySourceCategoryName" : null,
                                      "querySourceCategory" : null,
                                      "modified" : "2016-08-22T04:32:31.85",
                                      "extendedProperties" : null,
                                      "physicalChange" : 0,
                                      "approval" : 0,
                                      "existed" : false,
                                      "checked" : true,
                                      "fullPath" : null
                                   }
                                ],
                                "childs" : null,
                                "connection" : null,
                                "physicalChange" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ]
                       },
                       "relationships" : null,
                       "physicalChange" : 0,
                       "checked" : true,
                       "databaseName" : "Northwind",
                       "fullPath" : null,
                       "fullDBName" : "[MSSQL] Northwind",
                       "querySources" : [{
                             "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                             "name" : "dbo",
                             "parentCategoryId" : null,
                             "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                             "querySources" : [{
                                   "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "name" : "Categories",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "CategoryID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
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
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "CategoryName",
                                         "alias" : "",
                                         "dataType" : "nvarchar",
                                         "izendaDataType" : "Text",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 2,
                                         "extendedProperties" : "",
                                         "physicalChange" : 0,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "d202ef02-14ae-4f1a-8364-d7ac7d89ac1f",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "Description",
                                         "alias" : "",
                                         "dataType" : "ntext",
                                         "izendaDataType" : "Lob",
                                         "allowDistinct" : false,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 3,
                                         "extendedProperties" : "",
                                         "physicalChange" : 0,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "06cb8ba9-e719-4dfd-a903-7512d6555a7b",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "Picture",
                                         "alias" : "",
                                         "dataType" : "image",
                                         "izendaDataType" : "Image",
                                         "allowDistinct" : false,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 4,
                                         "extendedProperties" : "",
                                         "physicalChange" : 0,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "003c2e54-58ff-4fe1-bfb2-16efd0fcdbda",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }
                                   ],
                                   "querySourceCategoryName" : null,
                                   "querySourceCategory" : null,
                                   "modified" : "2016-08-22T04:32:31.85",
                                   "extendedProperties" : null,
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : null
                                }
                             ],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : 0,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }
                       ]
                    }
                 ],
                 "dataMapping" : [],
                 "databaseSources" : []
              }
           ],
           "workspaceMappings" : [{
                 "isDirty" : false,
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "fromDatabaseName" : "[MSSQL] Northwind",
                 "type" : 2,
                 "fromObject" : "",
                 "toDatabaseName" : "",
                 "toObject" : "",
                 "isGlobal" : false,
                 "id" : "b0cd65d5-762a-48be-afc8-5bc9678aebd0",
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null,
                 "workspaceMappingTenants" : []
              }
           ]
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "workspaceTenants" : [{
                 "destinationConnections" : [],
                 "sourceConnections" : [{
                       "id" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                       "name" : "1234 1351",
                       "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                       "serverTypeName" : "MSSQL",
                       "connectionString" : "secret",
                       "visible" : true,
                       "deleted" : false,
                       "relateToConnectionId" : null,
                       "tenantId" : null,
                       "dbSource" : {
                          "querySources" : [{
                                "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "name" : "dbo",
                                "parentCategoryId" : null,
                                "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                                "querySources" : [{
                                      "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "name" : "Categories",
                                      "type" : "Table",
                                      "parentQuerySourceId" : null,
                                      "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                      "selected" : false,
                                      "connectionId" : "00000000-0000-0000-0000-000000000000",
                                      "connectionName" : null,
                                      "childs" : null,
                                      "dataSourceCategoryId" : null,
                                      "dataSourceCategoryName" : null,
                                      "alias" : null,
                                      "querySourceFields" : [{
                                            "name" : "CategoryID",
                                            "alias" : "",
                                            "dataType" : "int",
                                            "izendaDataType" : "Numeric",
                                            "allowDistinct" : true,
                                            "visible" : true,
                                            "filterable" : true,
                                            "deleted" : false,
                                            "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                            "parentId" : null,
                                            "expressionFields" : [],
                                            "filteredValue" : "",
                                            "type" : 0,
                                            "groupPosition" : 0,
                                            "position" : 1,
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
                                            "originalName" : null,
                                            "isParameter" : false,
                                            "isCalculated" : false,
                                            "hasAggregatedFunction" : false,
                                            "querySource" : null,
                                            "fullPath" : null,
                                            "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                            "state" : 0,
                                            "inserted" : true,
                                            "version" : null,
                                            "created" : null,
                                            "createdBy" : null,
                                            "modified" : "2016-08-22T04:32:32.173",
                                            "modifiedBy" : null
                                         }],
                                      "querySourceCategoryName" : null,
                                      "querySourceCategory" : null,
                                      "modified" : "2016-08-22T04:32:31.85",
                                      "extendedProperties" : null,
                                      "physicalChange" : 0,
                                      "approval" : 0,
                                      "existed" : false,
                                      "checked" : true,
                                      "fullPath" : null
                                   }
                                ],
                                "childs" : null,
                                "connection" : null,
                                "physicalChange" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ]
                       },
                       "relationships" : null,
                       "physicalChange" : 0,
                       "checked" : true,
                       "databaseName" : "Northwind",
                       "fullPath" : null
                    }
                 ],
                 "tenantName" : "Tenant 1",
                 "tenantUniqueName" : "T1",
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "tenantId" : "9ef4b0af-2485-4050-91b9-cf149d999afd",
                 "status" : 0,
                 "id" : "351c3c7d-e0ab-47b4-8dad-558e2f86ff03",
                 "state" : 0,
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "workspaceMappings" : [{
                 "workspaceMappingTenants" : [],
                 "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
                 "fromDatabaseName" : "[MSSQL] Northwind",
                 "type" : 2,
                 "fromObject" : "",
                 "toDatabaseName" : "",
                 "toObject" : "",
                 "isGlobal" : false,
                 "id" : "b0cd65d5-762a-48be-afc8-5bc9678aebd0",
                 "state" : 0,
                 "inserted" : true,
                 "version" : null,
                 "created" : null,
                 "createdBy" : null,
                 "modified" : null,
                 "modifiedBy" : null
              }
           ],
           "copyOption" : null,
           "sourceConnections" : [{
                 "id" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                 "name" : "1234 1351",
                 "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                 "serverTypeName" : "MSSQL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                          "querySources" : [{
                                "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                "name" : "Categories",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceFields" : [{
                                      "name" : "CategoryID",
                                      "alias" : "",
                                      "dataType" : "int",
                                      "izendaDataType" : "Numeric",
                                      "allowDistinct" : true,
                                      "visible" : true,
                                      "filterable" : true,
                                      "deleted" : false,
                                      "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "parentId" : null,
                                      "expressionFields" : [],
                                      "filteredValue" : "",
                                      "type" : 0,
                                      "groupPosition" : 0,
                                      "position" : 1,
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
                                      "originalName" : null,
                                      "isParameter" : false,
                                      "isCalculated" : false,
                                      "hasAggregatedFunction" : false,
                                      "querySource" : null,
                                      "fullPath" : null,
                                      "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                      "state" : 0,
                                      "inserted" : true,
                                      "version" : null,
                                      "created" : null,
                                      "createdBy" : null,
                                      "modified" : "2016-08-22T04:32:32.173",
                                      "modifiedBy" : null
                                   }],
                                "querySourceCategoryName" : null,
                                "querySourceCategory" : null,
                                "modified" : "2016-08-22T04:32:31.85",
                                "extendedProperties" : null,
                                "physicalChange" : 0,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : 0,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : 0,
                 "checked" : true,
                 "databaseName" : "Northwind",
                 "fullPath" : null
              }, {
                 "id" : "df727741-c608-42bd-9b64-5c0679fc0c3e",
                 "name" : "orcl",
                 "serverTypeId" : "93942448-c715-4f98-85e2-9292ed7ca4bc",
                 "serverTypeName" : "ORACL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                          "querySources" : [{
                                "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                "name" : "Categories",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceFields" : [{
                                      "name" : "CategoryID",
                                      "alias" : "",
                                      "dataType" : "int",
                                      "izendaDataType" : "Numeric",
                                      "allowDistinct" : true,
                                      "visible" : true,
                                      "filterable" : true,
                                      "deleted" : false,
                                      "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                      "parentId" : null,
                                      "expressionFields" : [],
                                      "filteredValue" : "",
                                      "type" : 0,
                                      "groupPosition" : 0,
                                      "position" : 1,
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
                                      "originalName" : null,
                                      "isParameter" : false,
                                      "isCalculated" : false,
                                      "hasAggregatedFunction" : false,
                                      "querySource" : null,
                                      "fullPath" : null,
                                      "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                      "state" : 0,
                                      "inserted" : true,
                                      "version" : null,
                                      "created" : null,
                                      "createdBy" : null,
                                      "modified" : "2016-08-22T04:32:32.173",
                                      "modifiedBy" : null
                                   }],
                                "querySourceCategoryName" : null,
                                "querySourceCategory" : null,
                                "modified" : "2016-08-22T04:32:31.85",
                                "extendedProperties" : null,
                                "physicalChange" : 0,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : 0,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : 0,
                 "checked" : false,
                 "databaseName" : "orcl",
                 "fullPath" : null
              }
           ],
           "name" : "Workspace01",
           "description" : "dgsd",
           "tenantId" : null,
           "ownerId" : "9f58703e-0dff-4690-9dc6-c595a6fd84e1",
           "deleted" : false,
           "copyRoles" : false,
           "copyRolePermission" : false,
           "copyAdvancedSettings" : false,
           "copyDataModel" : false,
           "sourceId" : "00000000-0000-0000-0000-000000000000",
           "selectAllTenants" : false,
           "id" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
           "state" : 0,
           "inserted" : false,
           "version" : null,
           "created" : "2016-08-22T04:36:09.063",
           "createdBy" : null,
           "modified" : "2016-08-22T08:58:22.2373183",
           "modifiedBy" : null
         }


DELETE copyManagement/workspace/{workspace_id}
--------------------------------------------------------------

Deletes the workspace specified by workspace_id.

**Request**

    No payload

**Response**

    * true if the deletion was successful
    * false if not

**Samples**

   .. code-block:: http

      DELETE /api/copyManagement/workspace/49d886bc-45be-4acf-8ebe-4de775546f8c HTTP/1.1

   Sample response::

      true


POST copyManagement/copy
--------------------------------------------------------------

Run the copy operation based on settings in a workspace.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST api/copyManagement/copy HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "workspace" : {
              "id" : null,
              "name" : "Workspace",
              "description" : "",
              "tenantId" : null,
              "ownerId" : null,
              "created" : null,
              "createdBy" : null,
              "modified" : null,
              "copyDataModel" : true,
              "copyRoles" : false,
              "copyRolePermission" : false,
              "copyAdvancedSettings" : true,
              "copyTenantPermissions" : false,
              "sourceId" : "00000000-0000-0000-0000-000000000000",
              "sourceHashCode" : "507706696",
              "state" : 0,
              "selectAllTenants" : false,
              "workspaceTenants" : [{
                    "isDirty" : false,
                    "tenantName" : "01 - Tenant 01",
                    "tenantUniqueName" : "01",
                    "workspaceId" : null,
                    "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                    "status" : 1,
                    "state" : 0,
                    "inserted" : true,
                    "version" : 1,
                    "created" : "2016-09-12T04:37:14.62",
                    "createdBy" : null,
                    "modified" : "2016-09-12T04:37:14.62",
                    "modifiedBy" : null,
                    "destinationHashCode" : "1184854008",
                    "dataMapping" : [],
                    "databaseSources" : []
                 }
              ],
              "workspaceMappings" : []
           },
           "selectedSources" : [{
                 "id" : "67d99576-027d-495a-8fd8-ae382a901a06",
                 "name" : "AdventureWorks2008R2",
                 "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                 "serverTypeName" : "MSSQL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e0ad1a32-43e0-43ff-b9c0-a9f74802223d",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }, {
                          "id" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                          "name" : "HumanResources",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [{
                                "id" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                "name" : "JobCandidate",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "HumanResources",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T06:55:34.76",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : false,
                                "fullPath" : null
                             }, {
                                "id" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                "name" : "Shift",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "HumanResources",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T06:55:34.76",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : false,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : false,
                          "fullPath" : null
                       }, {
                          "id" : "000619e2-ad9b-4e56-95dd-1d9daf6a7978",
                          "name" : "Person",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : false,
                          "fullPath" : null
                       }, {
                          "id" : "4dcd6eae-b663-4d16-96f1-47623f411e85",
                          "name" : "Production",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : false,
                          "fullPath" : null
                       }, {
                          "id" : "c6641d0c-6afe-4c3f-9385-4af884ce54d3",
                          "name" : "Purchasing",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : false,
                          "fullPath" : null
                       }, {
                          "id" : "844a493c-623e-446a-b032-0e8cbc79a3bd",
                          "name" : "Sales",
                          "parentCategoryId" : null,
                          "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "querySources" : [],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : false,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : -1,
                 "checked" : true,
                 "databaseName" : "AdventureWorks2008R2",
                 "fullPath" : null,
                 "fullDBName" : "[MSSQL] AdventureWorks2008R2"
              }
           ]
         }

   Sample response::

      {
        "success" : true,
        "messages" : null
      }


POST copyManagement/connectionsHasDataModel
--------------------------------------------------------------

Checks if connections have already had data model.

**Request**

    Payload: an array of strings (GUIDs) which are ids of connections to check for

**Response**

    An array of strings (GUIDs) which are ids of connections with data model already set up

**Samples**

   .. code-block:: http

      POST /api/copyManagement/connectionsHasDataModel HTTP/1.1

   Request payload::

      ["861f9379-00c0-47e0-a718-080a4e9792d9"]

   Response in case it already has data model set up::

      ["861f9379-00c0-47e0-a718-080a4e9792d9"]


POST copyManagement/workspace/validate
--------------------------------------------------------------

Validates the workspace.

**Request**

    Payload:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **workspace** |br|
             object
          -  A :doc:`models/WorkspaceDetail` object
          -
       *  -  **selectedSources** |br|
             array of objects
          -  An array of :doc:`models/Connection` objects
          -

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -  Is the workspace valid
          -
       *  -  **workspace** |br|
             object
          -  The validated :doc:`models/WorkspaceDetail` object
          -


**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/validate HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
         "workspace" : {
            "id" : null,
            "name" : "Workspace",
            "description" : "",
            "tenantId" : null,
            "ownerId" : null,
            "created" : null,
            "createdBy" : null,
            "modified" : null,
            "copyDataModel" : true,
            "copyRoles" : false,
            "copyRolePermission" : false,
            "copyAdvancedSettings" : true,
            "copyTenantPermissions" : false,
            "sourceId" : "00000000-0000-0000-0000-000000000000",
            "sourceHashCode" : "507706696",
            "state" : 0,
            "selectAllTenants" : false,
            "workspaceTenants" : [{
                  "isDirty" : false,
                  "tenantName" : "01 - Tenant 01",
                  "tenantUniqueName" : "01",
                  "workspaceId" : null,
                  "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                  "status" : 1,
                  "state" : 0,
                  "inserted" : true,
                  "version" : 1,
                  "created" : "2016-09-12T04:37:14.62",
                  "createdBy" : null,
                  "modified" : "2016-09-12T04:37:14.62",
                  "modifiedBy" : null,
                  "destinationHashCode" : "1184854008",
                  "dataMapping" : [],
                  "databaseSources" : []
               }
            ],
            "workspaceMappings" : [{
                  "isDirty" : false,
                  "workspaceId" : null,
                  "fromDatabaseName" : "[MSSQL] AdventureWorks2008R2",
                  "type" : 1,
                  "fromObject" : "dbo",
                  "toDatabaseName" : "[MSSQL] T1_Northwind",
                  "toObject" : "dbo",
                  "isGlobal" : false,
                  "id" : null,
                  "inserted" : false,
                  "version" : null,
                  "created" : null,
                  "createdBy" : null,
                  "modified" : null,
                  "modifiedBy" : null,
                  "workspaceMappingTenants" : [{
                        "isDirty" : false,
                        "workspaceMappingId" : null,
                        "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                        "tenantName" : "",
                        "id" : null,
                        "state" : 0,
                        "inserted" : true,
                        "version" : null,
                        "created" : null,
                        "createdBy" : null,
                        "modified" : null,
                        "modifiedBy" : null
                     }
                  ]
               }
            ]
         },
         "selectedSources" : [{
               "id" : "67d99576-027d-495a-8fd8-ae382a901a06",
               "name" : "AdventureWorks2008R2",
               "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
               "serverTypeName" : "MSSQL",
               "connectionString" : "secret",
               "visible" : true,
               "deleted" : false,
               "relateToConnectionId" : null,
               "tenantId" : null,
               "dbSource" : {
                  "querySources" : [{
                        "id" : "e0ad1a32-43e0-43ff-b9c0-a9f74802223d",
                        "name" : "dbo",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : true,
                        "fullPath" : null
                     }, {
                        "id" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                        "name" : "HumanResources",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [{
                              "id" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                              "name" : "JobCandidate",
                              "type" : "Table",
                              "parentQuerySourceId" : null,
                              "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                              "selected" : false,
                              "connectionId" : "00000000-0000-0000-0000-000000000000",
                              "connectionName" : null,
                              "childs" : null,
                              "dataSourceCategoryId" : null,
                              "dataSourceCategoryName" : null,
                              "alias" : null,
                              "querySourceCategoryName" : "HumanResources",
                              "querySourceCategory" : null,
                              "modified" : "2016-09-12T06:55:34.76",
                              "extendedProperties" : null,
                              "physicalChange" : -1,
                              "approval" : 0,
                              "existed" : false,
                              "checked" : false,
                              "fullPath" : null
                           }, {
                              "id" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                              "name" : "Shift",
                              "type" : "Table",
                              "parentQuerySourceId" : null,
                              "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                              "selected" : false,
                              "connectionId" : "00000000-0000-0000-0000-000000000000",
                              "connectionName" : null,
                              "childs" : null,
                              "dataSourceCategoryId" : null,
                              "dataSourceCategoryName" : null,
                              "alias" : null,
                              "querySourceCategoryName" : "HumanResources",
                              "querySourceCategory" : null,
                              "modified" : "2016-09-12T06:55:34.76",
                              "extendedProperties" : null,
                              "physicalChange" : -1,
                              "approval" : 0,
                              "existed" : false,
                              "checked" : false,
                              "fullPath" : null
                           }
                        ],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : false,
                        "fullPath" : null
                     }, {
                        "id" : "000619e2-ad9b-4e56-95dd-1d9daf6a7978",
                        "name" : "Person",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : false,
                        "fullPath" : null
                     }, {
                        "id" : "4dcd6eae-b663-4d16-96f1-47623f411e85",
                        "name" : "Production",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : false,
                        "fullPath" : null
                     }, {
                        "id" : "c6641d0c-6afe-4c3f-9385-4af884ce54d3",
                        "name" : "Purchasing",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : false,
                        "fullPath" : null
                     }, {
                        "id" : "844a493c-623e-446a-b032-0e8cbc79a3bd",
                        "name" : "Sales",
                        "parentCategoryId" : null,
                        "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                        "querySources" : [],
                        "childs" : null,
                        "connection" : null,
                        "physicalChange" : -1,
                        "existed" : false,
                        "checked" : false,
                        "fullPath" : null
                     }
                  ]
               },
               "relationships" : null,
               "physicalChange" : -1,
               "checked" : true,
               "databaseName" : "AdventureWorks2008R2",
               "fullPath" : null,
               "fullDBName" : "[MSSQL] AdventureWorks2008R2"
            }
         ]
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "success" : true,
           "workspace" : {
              "workspaceTenants" : [{
                    "destinationConnections" : [{
                          "id" : "861f9379-00c0-47e0-a718-080a4e9792d9",
                          "name" : "T1_Northwind",
                          "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                          "serverTypeName" : "MSSQL",
                          "connectionString" : "secret",
                          "visible" : true,
                          "deleted" : false,
                          "relateToConnectionId" : null,
                          "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                          "dbSource" : {
                             "querySources" : [{
                                   "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                   "name" : "dbo",
                                   "parentCategoryId" : null,
                                   "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                                   "querySources" : [{
                                         "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "name" : "Categories",
                                         "type" : "Table",
                                         "parentQuerySourceId" : null,
                                         "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                         "selected" : false,
                                         "connectionId" : "00000000-0000-0000-0000-000000000000",
                                         "connectionName" : null,
                                         "childs" : null,
                                         "dataSourceCategoryId" : null,
                                         "dataSourceCategoryName" : null,
                                         "alias" : null,
                                         "querySourceFields" : [{
                                               "name" : "CategoryID",
                                               "alias" : "",
                                               "dataType" : "int",
                                               "izendaDataType" : "Numeric",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 1,
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
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : null,
                                               "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-08-22T04:32:32.173",
                                               "modifiedBy" : null
                                            }],
                                         "querySourceCategoryName" : null,
                                         "querySourceCategory" : null,
                                         "modified" : "2016-08-22T04:32:31.85",
                                         "extendedProperties" : null,
                                         "physicalChange" : 0,
                                         "approval" : 0,
                                         "existed" : false,
                                         "checked" : true,
                                         "fullPath" : null
                                      }
                                   ],
                                   "childs" : null,
                                   "connection" : null,
                                   "physicalChange" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : null
                                }
                             ]
                          },
                          "relationships" : null,
                          "physicalChange" : -1,
                          "checked" : true,
                          "databaseName" : "T1_Northwind",
                          "fullPath" : "[T1_Northwind]"
                       }
                    ],
                    "sourceConnections" : [{
                          "id" : "67d99576-027d-495a-8fd8-ae382a901a06",
                          "name" : "AdventureWorks2008R2",
                          "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                          "serverTypeName" : "MSSQL",
                          "connectionString" : "secret",
                          "visible" : true,
                          "deleted" : false,
                          "relateToConnectionId" : null,
                          "tenantId" : null,
                          "dbSource" : {
                             "querySources" : [{
                                   "id" : "e0ad1a32-43e0-43ff-b9c0-a9f74802223d",
                                   "name" : "dbo",
                                   "parentCategoryId" : null,
                                   "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                                   "querySources" : [],
                                   "childs" : null,
                                   "connection" : null,
                                   "physicalChange" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : "[AdventureWorks2008R2].[dbo]"
                                }
                             ]
                          },
                          "relationships" : null,
                          "physicalChange" : 0,
                          "checked" : true,
                          "databaseName" : "AdventureWorks2008R2",
                          "fullPath" : "[AdventureWorks2008R2]"
                       }
                    ],
                    "tenantName" : "01 - Tenant 01",
                    "tenantUniqueName" : "01",
                    "workspaceId" : null,
                    "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                    "status" : 1,
                    "destinationHashCode" : "1184854008",
                    "id" : null,
                    "state" : 0,
                    "inserted" : true,
                    "version" : 1,
                    "created" : "2016-09-12T04:37:14.62",
                    "createdBy" : null,
                    "modified" : "2016-09-12T04:37:14.62",
                    "modifiedBy" : null
                 }
              ],
              "workspaceMappings" : [{
                    "workspaceMappingTenants" : [{
                          "workspaceMappingId" : null,
                          "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                          "id" : null,
                          "state" : 0,
                          "inserted" : true,
                          "version" : null,
                          "created" : null,
                          "createdBy" : null,
                          "modified" : null,
                          "modifiedBy" : null
                       }
                    ],
                    "errorType" : 0,
                    "workspaceId" : null,
                    "fromDatabaseName" : "[MSSQL] AdventureWorks2008R2",
                    "type" : 1,
                    "fromObject" : "dbo",
                    "toDatabaseName" : "[MSSQL] T1_Northwind",
                    "toObject" : "dbo",
                    "isGlobal" : false,
                    "id" : null,
                    "state" : 0,
                    "inserted" : false,
                    "version" : null,
                    "created" : null,
                    "createdBy" : null,
                    "modified" : null,
                    "modifiedBy" : null
                 }
              ],
              "copyOption" : null,
              "sourceConnections" : [{
                    "id" : "67d99576-027d-495a-8fd8-ae382a901a06",
                    "name" : "AdventureWorks2008R2",
                    "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                    "serverTypeName" : "MSSQL",
                    "connectionString" : "secret",
                    "tenantId" : null,
                    "dbSource" : {
                       "querySources" : [{
                             "id" : "e0ad1a32-43e0-43ff-b9c0-a9f74802223d",
                             "name" : "dbo",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }, {
                             "id" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                             "name" : "HumanResources",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [{
                                   "id" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                   "name" : "JobCandidate",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "BusinessEntityID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 2,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "083cb2cc-95c3-483d-b00b-e6c77a9a05e9",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "JobCandidateID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
                                         "extendedProperties" : "{\"PrimaryKey\":true}",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "9c58d8a4-5086-4ddf-8703-02214cb8357f",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "ModifiedDate",
                                         "alias" : "",
                                         "dataType" : "datetime",
                                         "izendaDataType" : "Datetime",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 4,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "93728ada-9089-46bf-8f12-44f9af2873c1",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "Resume",
                                         "alias" : "",
                                         "dataType" : "xml",
                                         "izendaDataType" : "XML",
                                         "allowDistinct" : false,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "49ee729d-edfa-4448-ba2b-4a6aec65bfc9",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 3,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "a4d5c58b-5a64-4ae5-b70f-ee4e86384b26",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }
                                   ],
                                   "querySourceCategoryName" : "HumanResources",
                                   "querySourceCategory" : null,
                                   "modified" : "2016-09-12T06:55:34.76",
                                   "extendedProperties" : null,
                                   "physicalChange" : -1,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : false,
                                   "fullPath" : null
                                }, {
                                   "id" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                   "name" : "Shift",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "a7f2b50d-fb86-4907-91cb-473faec455df",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "EndTime",
                                         "alias" : "",
                                         "dataType" : "time",
                                         "izendaDataType" : "Time",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 4,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "4ea66d43-bba2-42f6-ba8d-c0d080fb13a8",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "ModifiedDate",
                                         "alias" : "",
                                         "dataType" : "datetime",
                                         "izendaDataType" : "Datetime",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 5,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "12bab662-ec4a-487a-9833-5b94b4c05aae",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "Name",
                                         "alias" : "",
                                         "dataType" : "nvarchar",
                                         "izendaDataType" : "Text",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 2,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "83f349c1-44c7-4ab3-9f07-33b307ce9cb0",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "ShiftID",
                                         "alias" : "",
                                         "dataType" : "tinyint",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
                                         "extendedProperties" : "{\"PrimaryKey\":true}",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "84950b1b-ba5a-42d0-b6f2-562b114b713c",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "StartTime",
                                         "alias" : "",
                                         "dataType" : "time",
                                         "izendaDataType" : "Time",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "d4a520fa-580a-4289-b45b-d41795fbe10e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 3,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "c0ccb8ac-be5e-42b8-8668-b878dd1d777a",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T06:55:34.853",
                                         "modifiedBy" : null
                                      }
                                   ],
                                   "querySourceCategoryName" : "HumanResources",
                                   "querySourceCategory" : null,
                                   "modified" : "2016-09-12T06:55:34.76",
                                   "extendedProperties" : null,
                                   "physicalChange" : -1,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : false,
                                   "fullPath" : null
                                }
                             ],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : false,
                             "fullPath" : null
                          }, {
                             "id" : "000619e2-ad9b-4e56-95dd-1d9daf6a7978",
                             "name" : "Person",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : false,
                             "fullPath" : null
                          }, {
                             "id" : "4dcd6eae-b663-4d16-96f1-47623f411e85",
                             "name" : "Production",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : false,
                             "fullPath" : null
                          }, {
                             "id" : "c6641d0c-6afe-4c3f-9385-4af884ce54d3",
                             "name" : "Purchasing",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : false,
                             "fullPath" : null
                          }, {
                             "id" : "844a493c-623e-446a-b032-0e8cbc79a3bd",
                             "name" : "Sales",
                             "parentCategoryId" : null,
                             "connectionId" : "67d99576-027d-495a-8fd8-ae382a901a06",
                             "querySources" : [],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : false,
                             "fullPath" : null
                          }
                       ]
                    },
                    "relationships" : null,
                    "physicalChange" : -1,
                    "checked" : true,
                    "databaseName" : "AdventureWorks2008R2",
                    "fullPath" : null
                 }
              ],
              "name" : "Workspace",
              "description" : "",
              "tenantId" : null,
              "ownerId" : null,
              "deleted" : false,
              "copyRoles" : false,
              "copyRolePermission" : false,
              "copyAdvancedSettings" : true,
              "copyDataModel" : true,
              "copyTenantPermissions" : false,
              "sourceId" : "00000000-0000-0000-0000-000000000000",
              "selectAllTenants" : false,
              "sourceHashCode" : "507706696",
              "id" : null,
              "state" : 0,
              "inserted" : true,
              "version" : null,
              "created" : null,
              "createdBy" : null,
              "modified" : null,
              "modifiedBy" : null
           }
         }


POST copyManagement/workspace/validateWorkspaceTenant
--------------------------------------------------------------

Validates that the mappings are valid, destination tenants have the same connections, and have no physical changes.

**Request**

    Payload:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **sourceId** |br|
             string (GUID)
          -  The id of the source connection
          -
       *  -  **sourceHashCode** |br|
             string
          -  Hashcode of source connection
          -
       *  -  **selectedSources** |br|
             array of objects
          -  An array of :doc:`models/Connection` objects
          -
       *  -  **selectedReports** |br|
             array of objects
          -  An array of :doc:`models/Category` objects
          -
       *  -  **selectedTemplates** |br|
             array of objects
          -  An array of :doc:`models/Category` objects
          -
       *  -  **selectedDashboards** |br|
             array of objects
          -  An array of :doc:`models/Category` objects
          -
       *  -  **workspaceTenant** |br|
             object
          -  A :doc:`models/WorkspaceTenantDetail` object
          -
       *  -  **mappings** |br|
             array of objects
          -  An array of :doc:`models/WorkspaceMappingDetail` objects
          -

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -  Is the workspace valid
          -
       *  -  **workspaceTenant** |br|
             object
          -  The validated :doc:`models/WorkspaceTenantDetail` object
          -


**Samples**

   .. code-block:: http

      POST api/copyManagement/workspace/validateWorkspaceTenant HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "workspace" : {
              "id" : null,
              "name" : "Workspace",
              "description" : "",
              "tenantId" : null,
              "ownerId" : null,
              "created" : null,
              "createdBy" : null,
              "modified" : null,
              "copyDataModel" : true,
              "copyRoles" : false,
              "copyRolePermission" : false,
              "copyAdvancedSettings" : false,
              "copyTenantPermissions" : false,
              "sourceId" : "00000000-0000-0000-0000-000000000000",
              "sourceHashCode" : "1123257498",
              "state" : 0,
              "selectAllTenants" : false,
              "workspaceTenants" : [{
                    "isDirty" : false,
                    "tenantName" : "01 - Tenant 01",
                    "tenantUniqueName" : "01",
                    "workspaceId" : null,
                    "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                    "status" : 0,
                    "state" : 0,
                    "inserted" : true,
                    "version" : 1,
                    "created" : "2016-09-12T04:37:14.6200000-07:00",
                    "createdBy" : null,
                    "modified" : "2016-09-12T04:37:14.6200000-07:00",
                    "modifiedBy" : null,
                    "dataMapping" : [],
                    "databaseSources" : []
                 }
              ],
              "workspaceMappings" : []
           },
           "selectedSources" : [{
                 "id" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                 "name" : "Northwind",
                 "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                 "serverTypeName" : "MSSQL",
                 "connectionString" : "secret",
                 "visible" : true,
                 "deleted" : false,
                 "relateToConnectionId" : null,
                 "tenantId" : null,
                 "dbSource" : {
                    "querySources" : [{
                          "id" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                          "name" : "dbo",
                          "parentCategoryId" : null,
                          "connectionId" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                          "querySources" : [{
                                "id" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                "name" : "Order Details",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "dbo",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T04:41:35",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }, {
                                "id" : "f6724b35-4e97-401a-adf7-95651fd57440",
                                "name" : "Orders",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "dbo",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T04:41:35",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : true,
                                "fullPath" : null
                             }, {
                                "id" : "3b7ba209-339a-48d7-a4ed-bc8ed959d5a6",
                                "name" : "Test",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "dbo",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T04:41:35",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : false,
                                "fullPath" : null
                             }, {
                                "id" : "f52184bf-c731-498f-8737-b45ea8e10cf2",
                                "name" : "Products",
                                "type" : "Table",
                                "parentQuerySourceId" : null,
                                "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                "selected" : false,
                                "connectionId" : "00000000-0000-0000-0000-000000000000",
                                "connectionName" : null,
                                "childs" : null,
                                "dataSourceCategoryId" : null,
                                "dataSourceCategoryName" : null,
                                "alias" : null,
                                "querySourceCategoryName" : "dbo",
                                "querySourceCategory" : null,
                                "modified" : "2016-09-12T04:41:35",
                                "extendedProperties" : null,
                                "physicalChange" : -1,
                                "approval" : 0,
                                "existed" : false,
                                "checked" : false,
                                "fullPath" : null
                             }
                          ],
                          "childs" : null,
                          "connection" : null,
                          "physicalChange" : -1,
                          "existed" : false,
                          "checked" : true,
                          "fullPath" : null
                       }
                    ]
                 },
                 "relationships" : null,
                 "physicalChange" : -1,
                 "checked" : true,
                 "databaseName" : "Northwind",
                 "fullPath" : null,
                 "fullDBName" : "[MSSQL] Northwind"
              }
           ]
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
           "success" : false,
           "workspace" : {
              "workspaceTenants" : [{
                    "destinationConnections" : [],
                    "sourceConnections" : [{
                          "id" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                          "name" : "Northwind",
                          "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                          "serverTypeName" : "MSSQL",
                          "connectionString" : "secret",
                          "visible" : true,
                          "deleted" : false,
                          "relateToConnectionId" : null,
                          "tenantId" : null,
                          "dbSource" : {
                             "querySources" : [{
                                   "id" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                   "name" : "dbo",
                                   "parentCategoryId" : null,
                                   "connectionId" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                                   "querySources" : [{
                                         "id" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "name" : "Order Details",
                                         "type" : "Table",
                                         "parentQuerySourceId" : null,
                                         "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                         "selected" : false,
                                         "connectionId" : "00000000-0000-0000-0000-000000000000",
                                         "connectionName" : null,
                                         "childs" : null,
                                         "dataSourceCategoryId" : null,
                                         "dataSourceCategoryName" : null,
                                         "alias" : null,
                                         "querySourceFields" : [{
                                               "name" : "Discount",
                                               "alias" : "",
                                               "dataType" : "real",
                                               "izendaDataType" : "Numeric",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 5,
                                               "extendedProperties" : "",
                                               "physicalChange" : 1,
                                               "approval" : 0,
                                               "existed" : false,
                                               "matchedTenant" : false,
                                               "functionName" : null,
                                               "expression" : null,
                                               "fullName" : null,
                                               "calculatedTree" : null,
                                               "reportId" : null,
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : "[Northwind].[dbo].[Order Details].[Discount]",
                                               "id" : "055b34ca-57c0-4c40-b930-78b0856db0fd",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-09-12T04:37:55.747",
                                               "modifiedBy" : null
                                            }, {
                                               "name" : "OrderID",
                                               "alias" : "",
                                               "dataType" : "int",
                                               "izendaDataType" : "Numeric",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 1,
                                               "extendedProperties" : "{\"PrimaryKey\":true}",
                                               "physicalChange" : 1,
                                               "approval" : 0,
                                               "existed" : false,
                                               "matchedTenant" : false,
                                               "functionName" : null,
                                               "expression" : null,
                                               "fullName" : null,
                                               "calculatedTree" : null,
                                               "reportId" : null,
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : "[Northwind].[dbo].[Order Details].[OrderID]",
                                               "id" : "a6326e4c-5984-4652-b3fa-a2dd439bebbc",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-09-12T04:37:55.747",
                                               "modifiedBy" : null
                                            }, {
                                               "name" : "ProductID",
                                               "alias" : "",
                                               "dataType" : "int",
                                               "izendaDataType" : "Numeric",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 2,
                                               "extendedProperties" : "{\"PrimaryKey\":true}",
                                               "physicalChange" : 1,
                                               "approval" : 0,
                                               "existed" : false,
                                               "matchedTenant" : false,
                                               "functionName" : null,
                                               "expression" : null,
                                               "fullName" : null,
                                               "calculatedTree" : null,
                                               "reportId" : null,
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : "[Northwind].[dbo].[Order Details].[ProductID]",
                                               "id" : "ec0bc4d5-bd03-4d14-ad18-ea76dc4e5f10",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-09-12T04:37:55.747",
                                               "modifiedBy" : null
                                            }, {
                                               "name" : "Quantity",
                                               "alias" : "",
                                               "dataType" : "smallint",
                                               "izendaDataType" : "Numeric",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 4,
                                               "extendedProperties" : "",
                                               "physicalChange" : 1,
                                               "approval" : 0,
                                               "existed" : false,
                                               "matchedTenant" : false,
                                               "functionName" : null,
                                               "expression" : null,
                                               "fullName" : null,
                                               "calculatedTree" : null,
                                               "reportId" : null,
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : "[Northwind].[dbo].[Order Details].[Quantity]",
                                               "id" : "7f83cacc-dfa3-43f3-b1e4-ad035dcaeb26",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-09-12T04:37:55.747",
                                               "modifiedBy" : null
                                            }, {
                                               "name" : "UnitPrice",
                                               "alias" : "",
                                               "dataType" : "money",
                                               "izendaDataType" : "Money",
                                               "allowDistinct" : true,
                                               "visible" : true,
                                               "filterable" : true,
                                               "deleted" : false,
                                               "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                               "parentId" : null,
                                               "expressionFields" : [],
                                               "filteredValue" : "",
                                               "type" : 0,
                                               "groupPosition" : 0,
                                               "position" : 3,
                                               "extendedProperties" : "",
                                               "physicalChange" : 1,
                                               "approval" : 0,
                                               "existed" : false,
                                               "matchedTenant" : false,
                                               "functionName" : null,
                                               "expression" : null,
                                               "fullName" : null,
                                               "calculatedTree" : null,
                                               "reportId" : null,
                                               "originalName" : null,
                                               "isParameter" : false,
                                               "isCalculated" : false,
                                               "hasAggregatedFunction" : false,
                                               "querySource" : null,
                                               "fullPath" : "[Northwind].[dbo].[Order Details].[UnitPrice]",
                                               "id" : "c683117c-43d3-4402-948b-27f68c3da948",
                                               "state" : 0,
                                               "inserted" : true,
                                               "version" : null,
                                               "created" : null,
                                               "createdBy" : null,
                                               "modified" : "2016-09-12T04:37:55.747",
                                               "modifiedBy" : null
                                            }
                                         ],
                                         "querySourceCategoryName" : "dbo",
                                         "querySourceCategory" : null,
                                         "modified" : "2016-09-12T04:41:35",
                                         "extendedProperties" : null,
                                         "physicalChange" : 2,
                                         "approval" : 0,
                                         "existed" : false,
                                         "checked" : true,
                                         "fullPath" : "[Northwind].[dbo].[Order Details]"
                                      }
                                   ],
                                   "childs" : null,
                                   "connection" : null,
                                   "physicalChange" : 2,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : "[Northwind].[dbo]"
                                }
                             ]
                          },
                          "relationships" : null,
                          "physicalChange" : 2,
                          "checked" : true,
                          "databaseName" : "Northwind",
                          "fullPath" : "[Northwind]"
                       }
                    ],
                    "tenantName" : "01 - Tenant 01",
                    "tenantUniqueName" : "01",
                    "workspaceId" : null,
                    "tenantId" : "468af427-ebe6-433d-97f3-aacd0c5a8e50",
                    "status" : 3,
                    "destinationHashCode" : "1184854008",
                    "id" : null,
                    "state" : 0,
                    "inserted" : true,
                    "version" : 1,
                    "created" : "2016-09-12T04:37:14.62",
                    "createdBy" : null,
                    "modified" : "2016-09-12T04:37:14.62",
                    "modifiedBy" : null
                 }
              ],
              "workspaceMappings" : [],
              "copyOption" : null,
              "sourceConnections" : [{
                    "id" : "aaa87c39-5730-438e-817e-5f7ffb46daff",
                    "name" : "MediumDB3M",
                    "serverTypeId" : "f2638ed5-70e5-47da-a052-4da0c1888fcf",
                    "serverTypeName" : "PGSQL",
                    "connectionString" : "secret",
                    "visible" : true,
                    "deleted" : false,
                    "relateToConnectionId" : null,
                    "tenantId" : null,
                    "dbSource" : {
                       "querySources" : [{
                             "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                             "name" : "dbo",
                             "parentCategoryId" : null,
                             "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                             "querySources" : [{
                                   "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "name" : "Categories",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "CategoryID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
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
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }],
                                   "querySourceCategoryName" : null,
                                   "querySourceCategory" : null,
                                   "modified" : "2016-08-22T04:32:31.85",
                                   "extendedProperties" : null,
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : null
                                }
                             ],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : 0,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }
                       ]
                    },
                    "relationships" : null,
                    "physicalChange" : -1,
                    "checked" : false,
                    "databaseName" : "MediumDB3M",
                    "fullPath" : null
                 }, {
                    "id" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                    "name" : "Northwind",
                    "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
                    "serverTypeName" : "MSSQL",
                    "connectionString" : "secret",
                    "visible" : true,
                    "deleted" : false,
                    "relateToConnectionId" : null,
                    "tenantId" : null,
                    "dbSource" : {
                       "querySources" : [{
                             "id" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                             "name" : "dbo",
                             "parentCategoryId" : null,
                             "connectionId" : "380d50fe-36bd-41d7-90fd-7c58236ad1f1",
                             "querySources" : [{
                                   "id" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                   "name" : "Order Details",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "e688be58-7234-41fa-a0e9-908a621ebc7c",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "Discount",
                                         "alias" : "",
                                         "dataType" : "real",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 5,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "055b34ca-57c0-4c40-b930-78b0856db0fd",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T04:37:55.747",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "OrderID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
                                         "extendedProperties" : "{\"PrimaryKey\":true}",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "a6326e4c-5984-4652-b3fa-a2dd439bebbc",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T04:37:55.747",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "ProductID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 2,
                                         "extendedProperties" : "{\"PrimaryKey\":true}",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "ec0bc4d5-bd03-4d14-ad18-ea76dc4e5f10",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T04:37:55.747",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "Quantity",
                                         "alias" : "",
                                         "dataType" : "smallint",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 4,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "7f83cacc-dfa3-43f3-b1e4-ad035dcaeb26",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T04:37:55.747",
                                         "modifiedBy" : null
                                      }, {
                                         "name" : "UnitPrice",
                                         "alias" : "",
                                         "dataType" : "money",
                                         "izendaDataType" : "Money",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "27d70c2d-ec3d-4fe8-8c22-7722bc4a1a6e",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 3,
                                         "extendedProperties" : "",
                                         "physicalChange" : -1,
                                         "approval" : 0,
                                         "existed" : false,
                                         "matchedTenant" : false,
                                         "functionName" : null,
                                         "expression" : null,
                                         "fullName" : null,
                                         "calculatedTree" : null,
                                         "reportId" : null,
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "c683117c-43d3-4402-948b-27f68c3da948",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-09-12T04:37:55.747",
                                         "modifiedBy" : null
                                      }
                                   ],
                                   "querySourceCategoryName" : "dbo",
                                   "querySourceCategory" : null,
                                   "modified" : "2016-09-12T04:41:35",
                                   "extendedProperties" : null,
                                   "physicalChange" : -1,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : null
                                }
                             ],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : -1,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }
                       ]
                    },
                    "relationships" : null,
                    "physicalChange" : -1,
                    "checked" : true,
                    "databaseName" : "Northwind",
                    "fullPath" : null
                 }, {
                    "id" : "7ef514d8-b494-4e07-9865-bff6a0592a9b",
                    "name" : "postgres",
                    "serverTypeId" : "f2638ed5-70e5-47da-a052-4da0c1888fcf",
                    "serverTypeName" : "PGSQL",
                    "connectionString" : "secret",
                    "visible" : true,
                    "deleted" : false,
                    "relateToConnectionId" : null,
                    "tenantId" : null,
                    "dbSource" : {
                       "querySources" : [{
                             "id" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                             "name" : "dbo",
                             "parentCategoryId" : null,
                             "connectionId" : "e3dfb160-0814-4d13-b801-29b5b0d97664",
                             "querySources" : [{
                                   "id" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                   "name" : "Categories",
                                   "type" : "Table",
                                   "parentQuerySourceId" : null,
                                   "categoryId" : "e7a70258-d781-45ac-a346-7e304f6c2291",
                                   "selected" : false,
                                   "connectionId" : "00000000-0000-0000-0000-000000000000",
                                   "connectionName" : null,
                                   "childs" : null,
                                   "dataSourceCategoryId" : null,
                                   "dataSourceCategoryName" : null,
                                   "alias" : null,
                                   "querySourceFields" : [{
                                         "name" : "CategoryID",
                                         "alias" : "",
                                         "dataType" : "int",
                                         "izendaDataType" : "Numeric",
                                         "allowDistinct" : true,
                                         "visible" : true,
                                         "filterable" : true,
                                         "deleted" : false,
                                         "querySourceId" : "8817a241-a858-423c-b64e-3bbf99e45318",
                                         "parentId" : null,
                                         "expressionFields" : [],
                                         "filteredValue" : "",
                                         "type" : 0,
                                         "groupPosition" : 0,
                                         "position" : 1,
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
                                         "originalName" : null,
                                         "isParameter" : false,
                                         "isCalculated" : false,
                                         "hasAggregatedFunction" : false,
                                         "querySource" : null,
                                         "fullPath" : null,
                                         "id" : "549a4a2b-216d-48f7-8e00-eec2277351ac",
                                         "state" : 0,
                                         "inserted" : true,
                                         "version" : null,
                                         "created" : null,
                                         "createdBy" : null,
                                         "modified" : "2016-08-22T04:32:32.173",
                                         "modifiedBy" : null
                                      }],
                                   "querySourceCategoryName" : null,
                                   "querySourceCategory" : null,
                                   "modified" : "2016-08-22T04:32:31.85",
                                   "extendedProperties" : null,
                                   "physicalChange" : 0,
                                   "approval" : 0,
                                   "existed" : false,
                                   "checked" : true,
                                   "fullPath" : null
                                }
                             ],
                             "childs" : null,
                             "connection" : null,
                             "physicalChange" : 0,
                             "existed" : false,
                             "checked" : true,
                             "fullPath" : null
                          }
                       ]
                    },
                    "relationships" : null,
                    "physicalChange" : -1,
                    "checked" : false,
                    "databaseName" : "Northwind",
                    "fullPath" : null
                 }
              ],
              "name" : "Workspace",
              "description" : "",
              "tenantId" : null,
              "ownerId" : null,
              "deleted" : false,
              "copyRoles" : false,
              "copyRolePermission" : false,
              "copyAdvancedSettings" : false,
              "copyDataModel" : true,
              "copyTenantPermissions" : false,
              "sourceId" : "00000000-0000-0000-0000-000000000000",
              "selectAllTenants" : false,
              "sourceHashCode" : "1123257498",
              "id" : null,
              "state" : 0,
              "inserted" : true,
              "version" : null,
              "created" : null,
              "createdBy" : null,
              "modified" : null,
              "modifiedBy" : null
           }
         }


POST copyManagement/workspace/validateConcurrency
--------------------------------------------------------------

Validates workspace concurrency.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -

             * true if there is no change in source and destination connections
             * false if not
          -

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/validateConcurrency HTTP/1.1

   Request payload::

      {
        "id" : "6992586c-5162-4807-9331-623081e12e05",
        "name" : "TestWorkspace",
        "description" : "",
        "tenantId" : null,
        "ownerId" : "75996c7c-06fe-4ad1-a05d-f8bd08198225",
        "created" : "2016-10-07T09:44:11.79",
        "createdBy" : null,
        "modified" : "2016-10-07T09:44:11.79",
        "copyDataModel" : true,
        "copyRoles" : false,
        "copyRolePermission" : false,
        "copyAdvancedSettings" : false,
        "copyTenantPermissions" : false,
        "sourceId" : "00000000-0000-0000-0000-000000000000",
        "sourceHashCode" : "4b147790614b2fd1cd48527976c8b44d",
        "state" : 0,
        "selectAllTenants" : false,
        "workspaceTenants" : [],
        "workspaceMappings" : []
      }

   Sample response::

      {"success":true}


POST copyManagement/workspace/detectConflictingTenantPermissions
------------------------------------------------------------------

Detect conflicting tenant's permissions.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    An array of ids of destination tenants that have different permission than source tenant.

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/detectConflictingTenantPermissions HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "id": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
           "name": "Test Workspace",
           "description": "",
           "tenantId": null,
           "ownerId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
           "created": "2017-01-05T04:31:44.087",
           "createdBy": "John Doe",
           "modified": "2017-01-09T03:32:42",
           "copyDataModel": true,
           "copyRoles": false,
           "copyRolePermission": false,
           "copyAdvancedSettings": false,
           "copyTenantPermissions": true,
           "copyDashboard": false,
           "copyReport": false,
           "sourceId": "b8c0674e-b71d-4041-9d7e-dc3d1aca5ab8",
           "sourceHashCode": "ee66d1d14317b3c151dfd1027df",
           "state": 0,
           "selectAllTenants": false,
           "workspaceTenants": [
             {
               "isDirty": true,
               "tenantName": "T1 - ACME Corp",
               "tenantUniqueName": "T1",
               "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
               "tenantId": "c771cf16-9a17-4bb8-ac0b-031eb8cbb26b",
               "status": 1,
               "state": 0,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "John Doe",
               "modified": null,
               "modifiedBy": null,
               "destinationHashCode": "ab6d43fa3f1c06a3aaf41773a5a",
               "dataMapping": [],
               "databaseSources": [],
               "querySourceTree": {
                 "filter": {
                   "text": "",
                   "isFilterFields": true
                 },
                 "querySources": []
               },
               "destinationQuerySourceTree": {
                 "filter": {
                   "text": "",
                   "isFilterFields": true
                 },
                 "querySources": []
               }
             }
           ],
           "workspaceMappings": [
             {
               "isDirty": false,
               "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
               "fromDatabaseName": "[MSSQL] Northwind",
               "type": 1,
               "fromObject": "dbo",
               "toDatabaseName": "[MSSQL] Northwind",
               "toObject": "dbo",
               "isGlobal": false,
               "id": "7c5ca8bd-1880-4174-8687-f5c95c76bc13",
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "John Doe",
               "modified": null,
               "modifiedBy": null,
               "workspaceMappingTenants": [
                 {
                   "isDirty": false,
                   "workspaceMappingId": "7c5ca8bd-1880-4174-8687-f5c95c76bc13",
                   "tenantId": "c771cf16-9a17-4bb8-ac0b-031eb8cbb26b",
                   "tenantName": "",
                   "id": null,
                   "state": 0,
                   "inserted": true,
                   "version": null,
                   "created": null,
                   "createdBy": "John Doe",
                   "modified": null,
                   "modifiedBy": null
                 }
               ]
             }
           ],
           "copyOption": {},
           "copyAdvancedSettingOption": {},
           "copyDashboardOption": {},
           "copyReportOption": {},
           "copyTemplateOption": {},
           "copyTenantPermissionOption": {},
           "copyRolePermissionOption": {},
           "copiedRoles": [],
           "copiedRolePermission": [],
           "allHashcodes": {
             "advancedSettings": "",
             "tenantPermission": "",
             "roles": "42031545714b1bb7736ad65ad22",
             "rolePermissions": "2b8e93dfe23526c2fdb2d31a3f0",
             "dashboards": "d41d8cd98f00b204e9800998ecf",
             "reports": "d41d8cd98f00b204e9800998ecf",
             "templates": "d41d8cd98f00b204e9800998ecf"
           },
           "sourceDashboards": []
         }

   Sample response::

      ["c771cf16-9a17-4bb8-ac0b-031eb8cbb26b"]


POST copyManagement/workspace/detectConflictingAdvancedSettings
--------------------------------------------------------------------

Detect conflicting tenant's advanced settings.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    An array of ids of destination tenants that have different advanced settings than source tenant.

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/detectConflictingAdvancedSettings HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

         {
           "workspace": {
             "id": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
             "name": "Test Workspace 2",
             "description": "",
             "tenantId": null,
             "ownerId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
             "created": "2017-01-05T04:31:44.087",
             "createdBy": "John Doe",
             "modified": "2017-01-10T03:09:13.3679866",
             "copyDataModel": false,
             "copyRoles": false,
             "copyRolePermission": false,
             "copyAdvancedSettings": true,
             "copyTenantPermissions": false,
             "copyDashboard": false,
             "copyReport": false,
             "sourceId": "b8c0674e-b71d-4041-9d7e-dc3d1aca5ab8",
             "sourceHashCode": "ee66d1d14317b3c151dfd1027df",
             "state": 0,
             "selectAllTenants": false,
             "workspaceTenants": [
               {
                 "isDirty": true,
                 "tenantName": "T1 - ACME Corp",
                 "tenantUniqueName": "T1",
                 "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
                 "tenantId": "c771cf16-9a17-4bb8-ac0b-031eb8cbb26b",
                 "status": 0,
                 "state": 0,
                 "inserted": true,
                 "version": null,
                 "created": null,
                 "createdBy": "John Doe",
                 "modified": null,
                 "modifiedBy": null,
                 "destinationHashCode": "374b3a468d99c518d931e3d16df",
                 "dataMapping": [],
                 "databaseSources": [],
                 "querySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 },
                 "destinationQuerySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 }
               },
               {
                 "isDirty": true,
                 "tenantName": "T3 - Stark Industries",
                 "tenantUniqueName": "T3",
                 "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
                 "tenantId": "d6d5cba5-c76c-467b-b5c5-6c54514b6e0c",
                 "status": 0,
                 "state": 0,
                 "inserted": true,
                 "version": 2,
                 "created": "2016-11-28T09:35:58.477",
                 "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                 "modified": "2016-11-28T10:07:17.947",
                 "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                 "destinationHashCode": null,
                 "dataMapping": [],
                 "databaseSources": [],
                 "querySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 },
                 "destinationQuerySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 }
               },
               {
                 "isDirty": true,
                 "tenantName": "T4 - Sterling Cooper",
                 "tenantUniqueName": "T4",
                 "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
                 "tenantId": "f6fbb432-1c3b-4815-81b6-1d2c0c268516",
                 "status": 0,
                 "state": 0,
                 "inserted": true,
                 "version": 2,
                 "created": "2016-11-28T09:35:25.167",
                 "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                 "modified": "2016-11-28T10:07:25.103",
                 "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                 "destinationHashCode": null,
                 "dataMapping": [],
                 "databaseSources": [],
                 "querySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 },
                 "destinationQuerySourceTree": {
                   "filter": {
                    "text": "",
                    "isFilterFields": true
                   },
                   "querySources": []
                 }
               }
             ],
             "workspaceMappings": [
               {
                 "isDirty": false,
                 "workspaceId": "604c4709-0c7e-4b6d-bea2-9f4800c932e2",
                 "fromDatabaseName": "[MSSQL] Northwind",
                 "type": 1,
                 "fromObject": "dbo",
                 "toDatabaseName": "[MSSQL] Northwind",
                 "toObject": "dbo",
                 "isGlobal": false,
                 "id": "7c5ca8bd-1880-4174-8687-f5c95c76bc13",
                 "inserted": true,
                 "version": null,
                 "created": null,
                 "createdBy": "John Doe",
                 "modified": null,
                 "modifiedBy": null,
                 "workspaceMappingTenants": [
                   {
                    "isDirty": false,
                    "workspaceMappingId": "7c5ca8bd-1880-4174-8687-f5c95c76bc13",
                    "tenantId": "c771cf16-9a17-4bb8-ac0b-031eb8cbb26b",
                    "tenantName": "",
                    "id": null,
                    "state": 0,
                    "inserted": true,
                    "version": null,
                    "created": null,
                    "createdBy": "John Doe",
                    "modified": null,
                    "modifiedBy": null
                   }
                 ]
               }
             ],
             "copyOption": {},
             "copyAdvancedSettingOption": {},
             "copyDashboardOption": {},
             "copyReportOption": {},
             "copyTemplateOption": {},
             "copyTenantPermissionOption": {},
             "copyRolePermissionOption": {},
             "copiedRoles": [],
             "copiedRolePermission": [],
             "allHashcodes": {
               "advancedSettings": "2e0884bb145346ce3bed99fa325",
               "tenantPermission": "",
               "roles": "42031545714b1bb7736ad65ad22",
               "rolePermissions": "2b8e93dfe23526c2fdb2d31a3f0",
               "dashboards": "d41d8cd98f00b204e9800998ecf",
               "reports": "d41d8cd98f00b204e9800998ecf",
               "templates": "d41d8cd98f00b204e9800998ecf"
             },
             "sourceDashboards": []
           },
           "selectedSources": []
         }

   Sample response::

      ["c771cf16-9a17-4bb8-ac0b-031eb8cbb26b","d6d5cba5-c76c-467b-b5c5-6c54514b6e0c"]


POST copyManagement/workspace/detectConflictingReport
--------------------------------------------------------------

Detect conflicting tenant's reports.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    An array of :doc:`models/ConflictReportDashboardItem` object

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/detectConflictingReport HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
            "id": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
            "name": "acme-wonka",
            "description": "",
            "tenantId": null,
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "created": "2017-10-18T03:06:40.467",
            "createdBy": "System5 Admin5",
            "modified": "2017-10-18T03:28:26",
            "copyDataModel": false,
            "copyRoles": false,
            "copyRolePermission": false,
            "copyAdvancedSettings": false,
            "copyTenantPermissions": false,
            "copyDashboard": false,
            "copyReport": true,
            "sourceId": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
            "sourceHashCode": "3b81ceb0de496d4f31d30619021",
            "state": 0,
            "selectAllTenants": false,
            "workspaceTenants": [{
               "isDirty": true,
               "tenantName": "Wonka - Wonka",
               "name": "Wonka",
               "tenantUniqueName": "Wonka",
               "workspaceId": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
               "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
               "status": 1,
               "state": 0,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null,
               "destinationHashCode": "3b81ceb0de496d4f31d30619021",
               "dataMapping": [],
               "databaseSources": [],
               "querySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               },
               "destinationQuerySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               }
            }],
            "workspaceMappings": [],
            "copyOption": {
               
            },
            "copyAdvancedSettingOption": {
               
            },
            "copyDashboardOption": {
               
            },
            "copyReportOption": {
               
            },
            "copyTemplateOption": {
               
            },
            "copyTenantPermissionOption": {
               
            },
            "copyRolePermissionOption": {
               
            },
            "copiedRoles": [],
            "copiedRolePermission": [],
            "allHashcodes": {
               "advancedSettings": "",
               "tenantPermission": "",
               "roles": "ae94be3cd532ce4a025884819eb",
               "rolePermissions": "e20838cf93c8cd6212cda1530d4",
               "dashboards": "",
               "reports": "8b6719a00dc9faec05ba1ec69ba",
               "templates": "0bea5c30063e9a627a31d8bf3fd"
            },
            "sourceDashboards": [],
            "sourceReports": [{
               "id": null,
               "type": 0,
               "name": null,
               "parentId": null,
               "state": 0,
               "modified": null,
               "canDelete": false,
               "subCategories": [{
                  "id": null,
                  "type": 0,
                  "name": null,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "state": 0,
                  "modified": null,
                  "canDelete": false,
                  "subCategories": [],
                  "dashboards": [],
                  "reports": [{
                     "reportDataSource": [{
                        "reportId": "a657c5f7-c361-422b-868c-d8e7b81a0184",
                        "querySourceId": "c7d1a927-dd58-4224-960e-a84e7de0b760",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[actor]",
                        "querySourceCategoryId": "7fb73c89-2821-489c-8e97-497eaf544568",
                        "connectionId": "30625587-4960-46aa-bfde-ae9aae18d32b",
                        "selected": false,
                        "id": null,
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "System5 Admin5",
                        "modified": null,
                        "modifiedBy": null
                     }],
                     "id": "a657c5f7-c361-422b-868c-d8e7b81a0184",
                     "name": "Ex01",
                     "type": 0,
                     "previewRecord": 0,
                     "advancedMode": false,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
                     "description": "",
                     "createdBy": "System5 Admin5",
                     "created": "2017-10-18T03:03:26.46",
                     "modifiedBy": "System5 Admin5",
                     "version": 1,
                     "numberOfView": 1,
                     "renderingTime": 4212,
                     "owner": "System5 Admin5",
                     "state": 0,
                     "modified": "2017-10-18T03:03:26.46",
                     "isShowDetail": false,
                     "lastViewed": "2017-10-18T06:48:31.647",
                     "isSubscribeMode": false,
                     "deletable": true,
                     "copyable": true,
                     "movable": true,
                     "accessPriority": 1,
                     "checked": true,
                     "indeterminate": false,
                     "isGlobal": false,
                     "isEditMode": false
                  }],
                  "checked": true,
                  "indeterminate": false,
                  "numOfCheckedChilds": 0,
                  "numOfChilds": 0,
                  "isGlobal": false,
                  "isEditing": false,
                  "editable": false,
                  "tenantId": null
               }],
               "dashboards": [],
               "reports": [],
               "checked": true,
               "indeterminate": false,
               "numOfCheckedChilds": 0,
               "numOfChilds": 0,
               "isGlobal": false,
               "isEditing": false,
               "editable": false,
               "tenantId": null
            }],
            "sourceTemplates": []
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
            "tenantName": "Wonka - Wonka",
            "categories": [{
               "name": null,
               "type": 0,
               "parentId": null,
               "tenantId": null,
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [{
                  "name": null,
                  "type": 0,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "tenantId": null,
                  "isGlobal": false,
                  "canDelete": false,
                  "editable": false,
                  "savable": false,
                  "subCategories": [],
                  "checked": true,
                  "reports": [{
                     "name": "Ex01",
                     "reportDataSource": [{
                        "reportId": "29e70154-17db-4ad3-b3df-cafff03309ef",
                        "querySourceId": "45a16d82-18be-4871-a530-783e09a6bac6",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[actor]",
                        "querySourceCategoryId": "6ebca7b7-c8f3-4b10-85af-9db3f582c307",
                        "connectionId": "b75f5e99-18c3-48c2-b9b6-959034edcbfb",
                        "selected": false,
                        "id": null,
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "System5 Admin5",
                        "modified": null,
                        "modifiedBy": null
                     }],
                     "type": 0,
                     "previewRecord": 0,
                     "advancedMode": false,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
                     "tenantName": null,
                     "description": "",
                     "title": null,
                     "lastViewed": "2017-10-18T07:56:41.453",
                     "owner": "IzendaAdmin@system.com",
                     "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "excludedRelationships": null,
                     "numberOfView": 0,
                     "renderingTime": 0.0,
                     "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "modifiedById": null,
                     "snapToGrid": false,
                     "usingFields": null,
                     "hasDeletedObjects": false,
                     "header": null,
                     "footer": null,
                     "titleDescription": null,
                     "sourceId": "a657c5f7-c361-422b-868c-d8e7b81a0184",
                     "checked": true,
                     "copyDashboard": false,
                     "exportFormatSetting": null,
                     "deletable": false,
                     "editable": false,
                     "movable": false,
                     "copyable": false,
                     "accessPriority": 0,
                     "active": false,
                     "fullPath": null,
                     "computeNameSettings": null,
                     "isGlobal": false,
                     "isCheck": true,
                     "id": "29e70154-17db-4ad3-b3df-cafff03309ef",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 1,
                     "created": "2017-10-18T07:56:41.453",
                     "createdBy": "System5 Admin5",
                     "modified": "2017-10-18T07:56:41.453",
                     "modifiedBy": "System5 Admin5"
                  }],
                  "dashboards": null,
                  "numOfChilds": 0,
                  "numOfCheckedChilds": 0,
                  "indeterminate": false,
                  "fullPath": null,
                  "computeNameSettings": null,
                  "isCheck": true,
                  "id": null,
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": null,
                  "modifiedBy": null
               }],
               "checked": true,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": true,
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            }],
            "checked": true
         }]


POST copyManagement/workspace/detectConflictingRolePermission
--------------------------------------------------------------

Detect role names already existing in destination tenants.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **id** |br|
             string (GUID)
          -  The id of the tenant
          -
       *  -  **name** |br|
             string
          -  The name of the tenant
          -
       *  -  **roles** |br|
             array of objects
          -  An array of objects with the following fields
          -
       *  -  .. container:: lpad2

                **id** |br|
                string (GUID)
          -  The id the existing role name
          -
       *  -  .. container:: lpad2

                **name** |br|
                string
          -  The existing role name
          -



**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/detectConflictingRolePermission HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
            "id": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
            "name": "acme-wonka",
            "description": "",
            "tenantId": null,
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "created": "2017-10-18T03:06:40.467",
            "createdBy": "System5 Admin5",
            "modified": "2017-10-18T03:28:26",
            "copyDataModel": false,
            "copyRoles": true,
            "copyRolePermission": true,
            "copyAdvancedSettings": false,
            "copyTenantPermissions": false,
            "copyDashboard": false,
            "copyReport": false,
            "sourceId": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
            "sourceHashCode": "3b81ceb0de496d4f31d30619021",
            "state": 0,
            "selectAllTenants": false,
            "workspaceTenants": [{
               "isDirty": false,
               "tenantName": "Wonka - Wonka",
               "name": "Wonka",
               "tenantUniqueName": "Wonka",
               "workspaceId": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
               "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
               "status": 0,
               "state": 0,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null,
               "destinationHashCode": "3b81ceb0de496d4f31d30619021",
               "dataMapping": [],
               "databaseSources": [],
               "querySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               },
               "destinationQuerySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               }
            }],
            "workspaceMappings": [{
               "isDirty": false,
               "workspaceId": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
               "fromDatabaseName": "[PGSQL] DVDRental",
               "type": 1,
               "fromObject": "public",
               "fromServer": "192.168.55.183",
               "toDatabaseName": "[PGSQL] DVDRental",
               "toObject": "public",
               "toServer": "192.168.55.183",
               "isGlobal": false,
               "id": "4a97058c-5d7e-424f-99ae-d463a9d665d5",
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null,
               "workspaceMappingTenants": [{
                  "isDirty": false,
                  "workspaceMappingId": "4a97058c-5d7e-424f-99ae-d463a9d665d5",
                  "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
                  "tenantName": "",
                  "id": null,
                  "state": 0,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": null,
                  "modifiedBy": null
               }]
            }],
            "copyOption": {
               
            },
            "copyAdvancedSettingOption": {
               
            },
            "copyDashboardOption": {
               
            },
            "copyReportOption": {
               
            },
            "copyTemplateOption": {
               
            },
            "copyTenantPermissionOption": {
               
            },
            "copyRolePermissionOption": {
               
            },
            "copiedRoles": ["e70f7958-c1a9-4eeb-8860-855332ee5930"],
            "copiedRolePermission": ["e70f7958-c1a9-4eeb-8860-855332ee5930"],
            "allHashcodes": {
               "advancedSettings": "",
               "tenantPermission": "",
               "roles": "ae94be3cd532ce4a025884819eb",
               "rolePermissions": "e20838cf93c8cd6212cda1530d4",
               "dashboards": "",
               "reports": "8b6719a00dc9faec05ba1ec69ba",
               "templates": "d41d8cd98f00b204e9800998ecf"
            },
            "sourceDashboards": []
         }

   Sample response::

      [{
         "id": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
         "name": "Wonka - Wonka",
         "roles": [{
            "id": "8f132fc0-963b-49bb-b41b-8f7c735c28c2",
            "name": "Manager"
         }]
      }]


POST copyManagement/workspace/detectConflictingTemplate
--------------------------------------------------------------

Detect conflicting tenant's templates.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    An array of :doc:`models/ConflictReportDashboardItem` objects

**Samples**

   .. code-block:: http

      POST /api/copyManagement/workspace/detectConflictingTemplate HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "id": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
            "name": "acme-wonka",
            "description": "",
            "tenantId": null,
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "created": "2017-10-18T03:06:40.467",
            "createdBy": "System5 Admin5",
            "modified": "2017-10-18T03:28:26",
            "copyDataModel": false,
            "copyRoles": false,
            "copyRolePermission": false,
            "copyAdvancedSettings": false,
            "copyTenantPermissions": false,
            "copyDashboard": false,
            "copyReport": true,
            "sourceId": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
            "sourceHashCode": "3b81ceb0de496d4f31d30619021",
            "state": 0,
            "selectAllTenants": false,
            "workspaceTenants": [{
               "isDirty": true,
               "tenantName": "Wonka - Wonka",
               "name": "Wonka",
               "tenantUniqueName": "Wonka",
               "workspaceId": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
               "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
               "status": 1,
               "state": 0,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null,
               "destinationHashCode": "3b81ceb0de496d4f31d30619021",
               "dataMapping": [],
               "databaseSources": [],
               "querySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               },
               "destinationQuerySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               }
            }],
            "workspaceMappings": [{
               "isDirty": false,
               "workspaceId": "291ddc27-126a-4e57-b7d3-1b09fc482d13",
               "fromDatabaseName": "[PGSQL] DVDRental",
               "type": 1,
               "fromObject": "public",
               "fromServer": "192.168.55.183",
               "toDatabaseName": "[PGSQL] DVDRental",
               "toObject": "public",
               "toServer": "192.168.55.183",
               "isGlobal": false,
               "id": "4a97058c-5d7e-424f-99ae-d463a9d665d5",
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null,
               "workspaceMappingTenants": [{
                  "isDirty": false,
                  "workspaceMappingId": "4a97058c-5d7e-424f-99ae-d463a9d665d5",
                  "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
                  "tenantName": "",
                  "id": null,
                  "state": 0,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": null,
                  "modifiedBy": null
               }]
            }],
            "copyOption": {
               
            },
            "copyAdvancedSettingOption": {
               
            },
            "copyDashboardOption": {
               
            },
            "copyReportOption": {
               
            },
            "copyTemplateOption": {
               
            },
            "copyTenantPermissionOption": {
               
            },
            "copyRolePermissionOption": {
               
            },
            "copiedRoles": [],
            "copiedRolePermission": [],
            "allHashcodes": {
               "advancedSettings": "",
               "tenantPermission": "",
               "roles": "ae94be3cd532ce4a025884819eb",
               "rolePermissions": "e20838cf93c8cd6212cda1530d4",
               "dashboards": "",
               "reports": "8b6719a00dc9faec05ba1ec69ba",
               "templates": "0bea5c30063e9a627a31d8bf3fd"
            },
            "sourceDashboards": [],
            "sourceReports": [],
            "sourceTemplates": [{
               "id": null,
               "type": 1,
               "name": null,
               "parentId": null,
               "state": 0,
               "modified": null,
               "canDelete": false,
               "subCategories": [{
                  "id": null,
                  "type": 1,
                  "name": null,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "state": 0,
                  "modified": null,
                  "canDelete": false,
                  "subCategories": [],
                  "dashboards": [],
                  "reports": [{
                     "reportDataSource": [{
                        "reportId": "ba219814-45d3-452a-8542-cacdb85162e9",
                        "querySourceId": "c7d1a927-dd58-4224-960e-a84e7de0b760",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[actor]",
                        "querySourceCategoryId": "7fb73c89-2821-489c-8e97-497eaf544568",
                        "connectionId": "30625587-4960-46aa-bfde-ae9aae18d32b",
                        "selected": false,
                        "id": null,
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "System5 Admin5",
                        "modified": null,
                        "modifiedBy": null
                     }],
                     "id": "ba219814-45d3-452a-8542-cacdb85162e9",
                     "name": "exTemplate",
                     "type": 1,
                     "previewRecord": 0,
                     "advancedMode": false,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "28788c9b-4e0d-464e-b588-ea5bee676bd3",
                     "description": "",
                     "createdBy": "System5 Admin5",
                     "created": "2017-10-18T03:44:37.473",
                     "modifiedBy": "System5 Admin5",
                     "version": 1,
                     "numberOfView": 0,
                     "renderingTime": 0,
                     "owner": "System5 Admin5",
                     "state": 0,
                     "modified": "2017-10-18T03:44:37.473",
                     "isShowDetail": false,
                     "lastViewed": null,
                     "isSubscribeMode": false,
                     "deletable": true,
                     "copyable": true,
                     "movable": true,
                     "accessPriority": 1,
                     "checked": true,
                     "indeterminate": false,
                     "isGlobal": false,
                     "isEditMode": false
                  }],
                  "checked": true,
                  "indeterminate": false,
                  "numOfCheckedChilds": 0,
                  "numOfChilds": 0,
                  "isGlobal": false,
                  "isEditing": false,
                  "editable": false,
                  "tenantId": null
               }],
               "dashboards": [],
               "reports": [],
               "checked": true,
               "indeterminate": false,
               "numOfCheckedChilds": 0,
               "numOfChilds": 0,
               "isGlobal": false,
               "isEditing": false,
               "editable": false,
               "tenantId": null
            }]
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
            "tenantName": "Wonka - Wonka",
            "categories": [{
               "name": null,
               "type": 1,
               "parentId": null,
               "tenantId": null,
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [{
                  "name": null,
                  "type": 1,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "tenantId": null,
                  "isGlobal": false,
                  "canDelete": false,
                  "editable": false,
                  "savable": false,
                  "subCategories": [],
                  "checked": true,
                  "reports": [{
                     "name": "exTemplate",
                     "reportDataSource": [{
                        "reportId": "169ddc07-b458-44d2-83fd-665deb915c57",
                        "querySourceId": "45a16d82-18be-4871-a530-783e09a6bac6",
                        "querySourceUniqueName": "[con;#0].[cat;#0].[actor]",
                        "querySourceCategoryId": "6ebca7b7-c8f3-4b10-85af-9db3f582c307",
                        "connectionId": "b75f5e99-18c3-48c2-b9b6-959034edcbfb",
                        "selected": false,
                        "id": null,
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "System5 Admin5",
                        "modified": null,
                        "modifiedBy": null
                     }],
                     "type": 1,
                     "previewRecord": 0,
                     "advancedMode": false,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
                     "tenantName": null,
                     "description": "",
                     "title": null,
                     "lastViewed": "2017-10-18T07:37:07.707",
                     "owner": "IzendaAdmin@system.com",
                     "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "excludedRelationships": null,
                     "numberOfView": 1,
                     "renderingTime": 306.0,
                     "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "modifiedById": null,
                     "snapToGrid": false,
                     "usingFields": null,
                     "hasDeletedObjects": false,
                     "header": null,
                     "footer": null,
                     "titleDescription": null,
                     "sourceId": "ba219814-45d3-452a-8542-cacdb85162e9",
                     "checked": true,
                     "copyDashboard": false,
                     "exportFormatSetting": null,
                     "deletable": false,
                     "editable": false,
                     "movable": false,
                     "copyable": false,
                     "accessPriority": 0,
                     "active": false,
                     "fullPath": null,
                     "computeNameSettings": null,
                     "isGlobal": false,
                     "isCheck": true,
                     "id": "169ddc07-b458-44d2-83fd-665deb915c57",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 1,
                     "created": "2017-10-18T07:34:32.803",
                     "createdBy": "System5 Admin5",
                     "modified": "2017-10-18T07:34:32.803",
                     "modifiedBy": "System5 Admin5"
                  }],
                  "dashboards": null,
                  "numOfChilds": 0,
                  "numOfCheckedChilds": 0,
                  "indeterminate": false,
                  "fullPath": null,
                  "computeNameSettings": null,
                  "isCheck": true,
                  "id": null,
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": null,
                  "modifiedBy": null
               }],
               "checked": true,
               "reports": [],
               "dashboards": null,
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": true,
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System5 Admin5",
               "modified": null,
               "modifiedBy": null
            }],
            "checked": true
         }]

POST copyManagement/workspace/detectConflictingDashboard
--------------------------------------------------------------

Detect conflicting tenant's dashboards.

**Request**

    Payload: a :doc:`models/WorkspaceDetail` object

**Response**

    An array of :doc:`models/ConflictReportDashboardItem` objects

**Samples**

   .. container:: toggle

      .. container:: header

         Sample payload:

      .. code-block:: json

         {
            "id": null,
            "name": "Workspace",
            "description": "",
            "tenantId": null,
            "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "created": null,
            "createdBy": null,
            "modified": null,
            "copyDataModel": false,
            "copyRoles": false,
            "copyRolePermission": false,
            "copyAdvancedSettings": false,
            "copyTenantPermissions": false,
            "copyDashboard": true,
            "copyReport": false,
            "mergeDuplicateMappings": false,
            "sourceId": "c1703d12-6f50-454a-82bc-16efc00bbedd",
            "sourceHashCode": "3b81ceb0de496d4f31d30619021",
            "state": 0,
            "selectAllTenants": false,
            "workspaceTenants": [{
               "isDirty": true,
               "tenantName": "Wonka - Wonka",
               "name": "Wonka",
               "tenantUniqueName": "Wonka",
               "workspaceId": null,
               "tenantId": "6a3c2dc8-b915-44f7-aa2a-bb5d2764dfc2",
               "status": 1,
               "state": 0,
               "inserted": false,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null,
               "destinationHashCode": null,
               "dataMapping": [],
               "databaseSources": [],
               "querySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  },
                  "querySources": []
               },
               "destinationQuerySourceTree": {
                  "filter": {
                     "text": "",
                     "isFilterFields": true
                  }
               }
            }],
            "workspaceMappings": [],
            "copyOption": {
               
            },
            "copyAdvancedSettingOption": {
               
            },
            "copyDashboardOption": {
               
            },
            "copyReportOption": {
               
            },
            "copyTemplateOption": {
               
            },
            "copyTenantPermissionOption": {
               
            },
            "copyRolePermissionOption": {
               
            },
            "copiedRoles": [],
            "copiedRolePermission": [],
            "allHashcodes": {
               "advancedSettings": "",
               "tenantPermission": "",
               "roles": "ae94be3cd532ce4a025884819eb",
               "rolePermissions": "234f0b5092bbbab766f84371568",
               "dashboards": "825980920635e810a1465329872",
               "reports": "d41d8cd98f00b204e9800998ecf",
               "templates": "d41d8cd98f00b204e9800998ecf"
            },
            "sourceDashboards": [{
               "id": null,
               "type": 0,
               "name": null,
               "parentId": null,
               "state": 0,
               "modified": null,
               "canDelete": false,
               "subCategories": [{
                  "id": null,
                  "type": 0,
                  "name": null,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "state": 0,
                  "modified": null,
                  "canDelete": false,
                  "subCategories": [],
                  "dashboards": [{
                     "commonFilterFields": [],
                     "accesses": [],
                     "subscriptions": [],
                     "dashboardParts": [],
                     "name": "ExDashboard",
                     "description": null,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "c1703d12-6f50-454a-82bc-16efc00bbedd",
                     "backgroundColor": null,
                     "imageUrl": null,
                     "stretchImage": false,
                     "id": "5d5ecb92-54ed-48de-9e20-d7c2528600a8",
                     "state": 0,
                     "inserted": true,
                     "version": 1,
                     "created": "2017-10-18T08:54:21.213",
                     "createdBy": "System Admin",
                     "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "modified": "2017-10-18T08:54:21.213",
                     "modifiedBy": "System Admin",
                     "showFilterDescription": false,
                     "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "lastViewed": null,
                     "accessPriority": 1,
                     "checked": true
                  }],
                  "reports": [],
                  "checked": true,
                  "indeterminate": false,
                  "numOfCheckedChilds": 0,
                  "numOfChilds": 0,
                  "isGlobal": false,
                  "isEditing": false,
                  "editable": false,
                  "tenantId": null
               }],
               "dashboards": [],
               "reports": [],
               "checked": true,
               "indeterminate": false,
               "numOfCheckedChilds": 0,
               "numOfChilds": 0,
               "isGlobal": false,
               "isEditing": false,
               "editable": false,
               "tenantId": null
            }]
         }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "tenantId": "6a3c2dc8-b915-44f7-aa2a-bb5d2764dfc2",
            "tenantName": "Wonka - Wonka",
            "categories": [{
               "name": null,
               "type": 0,
               "parentId": null,
               "tenantId": null,
               "isGlobal": false,
               "canDelete": false,
               "editable": false,
               "savable": false,
               "subCategories": [{
                  "name": null,
                  "type": 0,
                  "parentId": "00000000-0000-0000-0000-000000000000",
                  "tenantId": null,
                  "isGlobal": false,
                  "canDelete": false,
                  "editable": false,
                  "savable": false,
                  "subCategories": [],
                  "checked": true,
                  "reports": [],
                  "dashboards": [{
                     "commonFilterFields": [],
                     "accesses": [],
                     "subscriptions": [],
                     "inaccessible": false,
                     "name": "ExDashboard",
                     "description": null,
                     "categoryId": null,
                     "categoryName": null,
                     "subCategoryId": null,
                     "subCategoryName": null,
                     "tenantId": "6a3c2dc8-b915-44f7-aa2a-bb5d2764dfc2",
                     "imageUrl": null,
                     "stretchImage": false,
                     "backgroundColor": null,
                     "showFilterDescription": false,
                     "lastViewed": "2017-10-18T09:00:43.36",
                     "owner": "System Admin",
                     "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "modifiedById": null,
                     "checked": true,
                     "numberOfView": 1,
                     "renderingTime": 252.0,
                     "sourceId": "5d5ecb92-54ed-48de-9e20-d7c2528600a8",
                     "isGlobal": false,
                     "deletable": false,
                     "editable": false,
                     "movable": false,
                     "copyable": false,
                     "accessPriority": 0,
                     "dashboardParts": [],
                     "indeterminate": false,
                     "fullPath": null,
                     "computeNameSettings": null,
                     "isCheck": true,
                     "id": "02dcc807-50ce-4daf-be7f-30c503326b3e",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": 2,
                     "created": "2017-10-18T09:00:17.67",
                     "createdBy": "System Admin",
                     "modified": "2017-10-18T09:01:03.183",
                     "modifiedBy": "System Admin"
                  }],
                  "numOfChilds": 0,
                  "numOfCheckedChilds": 0,
                  "indeterminate": false,
                  "fullPath": null,
                  "computeNameSettings": null,
                  "isCheck": true,
                  "id": null,
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System Admin",
                  "modified": null,
                  "modifiedBy": null
               }],
               "checked": true,
               "reports": [],
               "dashboards": [],
               "numOfChilds": 0,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": true,
               "id": null,
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System Admin",
               "modified": null,
               "modifiedBy": null
            }],
            "checked": true
         }]