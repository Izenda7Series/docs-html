

=========================================
ConnectionResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **connection** |br|
         object
      -
      -  A :doc:`Connection` object
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "connection" : {
           "id" : "2f7e216b-8637-49e2-8391-cea682e4c32f",
           "name" : "AdventureWorks",
           "serverType" : "d968e96f-91dc-414d-9fd8-aef2926c9a18",
           "serverTypeName" : null,
           "connectionString" : "1a2B+=",
           "visible" : true,
           "deleted" : false,
           "relateToConnectionId" : null,
           "tenantId" : null,
           "dbSource" : {
              "querySources" : [{
                    "id" : "588d7aa8-6ba0-4629-ab68-56b8e1009fc7",
                    "name" : "dbo",
                    "parentCategoryId" : null,
                    "connectionId" : "2f7e216b-8637-49e2-8391-cea682e4c32f",
                    "querySources" : [{
                          "id" : "38804b44-bf23-41c0-b498-6d4199b8e34d",
                          "name" : "AWBuildVersion",
                          "type" : "Table",
                          "parentQuerySourceId" : null,
                          "categoryId" : "588d7aa8-6ba0-4629-ab68-56b8e1009fc7",
                          "selected" : false,
                          "connectionName" : null,
                          "childs" : null,
                          "dataSourceCategoryId" : null,
                          "dataSourceCategoryName" : null,
                          "alias" : null,
                          "querySourceFields" : [],
                          "querySourceCategory" : null,
                          "modified" : "2016-03-21T05:27:59.553",
                          "extendedProperties" : null,
                          "physicalChange" : 0,
                          "approval" : 0
                       }
                    ],
                    "childs" : null,
                    "connection" : null,
                    "physicalChange" : 0
                 }
              ]
           },
           "relationships" : null,
           "physicalChange" : 0
        },
        "success" : true,
        "messages" : null
      }
