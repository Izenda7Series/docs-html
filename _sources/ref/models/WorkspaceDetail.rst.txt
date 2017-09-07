

=================
WorkspaceDetail
=================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **workspaceTenants** |br|
         array of objects
      -
      -  An array of :doc:`WorkspaceTenantDetail` objects.
      -
   *  -  **workspaceMappings** |br|
         array of objects
      -
      -  An array of :doc:`WorkspaceMappingDetail` objects.
      -
   *  -  **copyOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyAdvancedSettingOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyTenantPermissionOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyRolePermissionOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyReportOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyDashboardOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **copyTemplateOption** |br|
         object
      -
      -  A dynamic object
      -
   *  -  **sourceConnections** |br|
         array of objects
      -
      -  An array of :doc:`Connection` objects.
      -
   *  -  **sourceReports** |br|
         array of objects
      -
      -  An array of :doc:`Category` objects.
      -
   *  -  **sourceTemplates** |br|
         array of objects
      -
      -  An array of :doc:`Category` objects.
      -
   *  -  **sourceDashboards** |br|
         array of objects
      -
      -  An array of :doc:`Category` objects.
      -
   *  -  **copiedRoles** |br|
         array of strings (GUIDs)
      -
      -  The list of ids of copied roles
      -
   *  -  **copiedRolePermissions** |br|
         array of strings (GUIDs)
      -
      -  The list of ids of copied roles
      -
   *  -  **allHashcodes** |br|
         dynamic object
      -
      -  Each field contains the hashcode for each copied section, e.g. advancedSettings, tenantPermission, etc.
      -




Inherited fields:

.. include:: Workspace.rst

.. container:: toggle

   .. container:: header

      **Sample**:

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
