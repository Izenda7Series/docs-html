

=========================================
DataModel
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySources** |br|
         array of objects
      -
      -  An array of :doc:`QuerySource` objects
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "tenantId" : null,
        "querySources" : [{
              "id" : "c3330d53-cd8d-411c-9e7d-05849c7f2cc3",
              "name" : "dbo.AWBuildVersion",
              "type" : "Table",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "828e10df-dedb-42f6-8adf-b0785810837e",
              "connectionName" : "AdventureWorks2008R2",
              "childs" : null,
              "dataSourceCategoryId" : null,
              "dataSourceCategoryName" : null,
              "alias" : null,
              "querySourceFields" : [{
                    "id" : "dc4eca5c-ec25-4721-9f72-f98813f9b116",
                    "name" : "VersionDate",
                    "alias" : "",
                    "dataType" : "datetime",
                    "visible" : true,
                    "filterable" : true,
                    "deleted" : false,
                    "querySourceId" : "c3330d53-cd8d-411c-9e7d-05849c7f2cc3",
                    "parentId" : null,
                    "children" : null,
                    "modified" : "2016-04-06T04:20:37",
                    "filteredValue" : "{}",
                    "type" : 0,
                    "position" : 0,
                    "extendedProperties" : "",
                    "physicalChange" : 0,
                    "approval" : 0,
                    "existed" : false,
                    "matchedTenant" : false
                 }, {
                    "id" : "a3466647-d30b-4b21-868d-c05d074cba66",
                    "name" : "Database Version",
                    "alias" : "dbversion",
                    "dataType" : "nvarchar",
                    "visible" : true,
                    "filterable" : true,
                    "deleted" : false,
                    "querySourceId" : "c3330d53-cd8d-411c-9e7d-05849c7f2cc3",
                    "parentId" : null,
                    "children" : null,
                    "modified" : "2016-04-06T04:20:37",
                    "filteredValue" : "{}",
                    "type" : 0,
                    "position" : 0,
                    "extendedProperties" : "",
                    "physicalChange" : 0,
                    "approval" : 0,
                    "existed" : false,
                    "matchedTenant" : false
                 }
              ],
              "querySourceCategory" : null,
              "modified" : null,
              "extendedProperties" : "{}",
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }, {
              "id" : "f5e3450b-2b5b-4388-bce3-05efba5b8311",
              "name" : "dbo.Categories",
              "type" : "Table",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "8143ad74-fa73-4224-9299-b115252e1cc7",
              "connectionName" : "Northwind2014",
              "childs" : null,
              "dataSourceCategoryId" : "014e42b4-979a-4a7f-80cf-492142572d10",
              "dataSourceCategoryName" : "test",
              "alias" : "Cats",
              "querySourceFields" : [],
              "querySourceCategory" : null,
              "modified" : null,
              "extendedProperties" : "{}",
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }
        ]
      }
