

=========================================
SchemaResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dbSource** |br|
         object
      -
      -  A :doc:`DBSource` object
      -
   *  -  **differentConnectionAndSchema** |br|
         boolean
      -
      -  True if different connection **and** schema; otherwise, false
      -


Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "dBSource" : {
           "querySources" : [ {
                 "id" : "6ca15f34-b4cb-4fd7-8d55-77ee26ba6abe",
                 "name" : "dbo",
                 "parentCategoryId" : null,
                 "connectionId" : "00000000-0000-0000-0000-000000000000",
                 "querySources" : [{
                       "id" : "bcf124c4-c5df-434a-bc4c-1638161d7949",
                       "name" : "AWBuildVersion",
                       "type" : "Table",
                       "parentQuerySourceId" : null,
                       "categoryId" : null,
                       "selected" : false,
                       "connectionName" : null,
                       "childs" : null,
                       "dataSourceCategoryId" : null,
                       "dataSourceCategoryName" : null,
                       "alias" : null,
                       "querySourceFields" : [],
                       "querySourceCategory" : null,
                       "modified" : null,
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
        "differentConnectionAndSchema" : false,
        "success" : true,
        "messages" : null
      }
