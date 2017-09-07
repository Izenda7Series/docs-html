

=========================================
DataResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **data** |br|
         object
      -
      -  A dynamic object
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "data" : {
           "result" : [{
                 "id" : "00000000-0000-0000-0000-000000000000",
                 "name" : "ProductName",
                 "alias" : "",
                 "dataType" : "nvarchar",
                 "visible" : true,
                 "filterable" : true,
                 "deleted" : false,
                 "querySourceId" : "0cd0f186-48f1-47a9-9975-1f2bded3a5cc",
                 "parentId" : null,
                 "children" : null,
                 "modified" : "0001-01-01T00:00:00",
                 "filteredValue" : "",
                 "type" : 0,
                 "position" : 0,
                 "extendedProperties" : null,
                 "physicalChange" : 0,
                 "approval" : 0,
                 "existed" : false,
                 "matchedTenant" : false
              }, {
                 "id" : "8ccfac80-c883-446b-948d-18568dc4d173",
                 "name" : "@OrderID",
                 "alias" : "",
                 "dataType" : "int",
                 "visible" : true,
                 "filterable" : true,
                 "deleted" : false,
                 "querySourceId" : "0cd0f186-48f1-47a9-9975-1f2bded3a5cc",
                 "parentId" : null,
                 "children" : null,
                 "modified" : "2016-04-14T04:19:48",
                 "filteredValue" : "{}",
                 "type" : 1,
                 "position" : 1,
                 "extendedProperties" : null,
                 "physicalChange" : 0,
                 "approval" : 0,
                 "existed" : false,
                 "matchedTenant" : false
              }
           ],
           "total" : 2,
           "pageIndex" : 0,
           "pageSize" : 1000
        },
        "success" : true,
        "messages" : null
      }
