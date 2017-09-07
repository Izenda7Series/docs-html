

============================
Data Model APIs
============================

The '''Data Model''' section allows user to

.. hlist::
   :columns: 2
   
   * manage data sources and data source fields
   * add computed columns
   * delete columns
   * manage relationships

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `POST dataModel/loadQuerySources`_
     - Returns an array of visible query sources, paged and sorted, filtered by type and other search criteria.
   * - `POST dataModel/loadQuerySourceFields`_
     - Returns an array of query source fields in a query source. |br| |br|
       Will load from remote connection if they are not yet populated in system.
   * - `GET dataModel/basicConnectionsInfo/(tenant_id)`_
     - Returns an array of id and name of connections (filtered by tenant_id if given).
     
       .. note::
          
          The same as :ref:`GET_connection/basicInfo/(tenant_id)`
   * - `POST dataModel/basicConnectionsInfo`_
     - Returns an array of connections infor with paging.
   * - `GET dataModel/basicQuerySourceCategoriesInfo/{connection_id}`_
     - Returns an array of the :term:`query source categories <query source category>` in the specified connection.
     
       .. versionadded:: 2.0.3
   * - `GET dataModel/basicQuerySourcesInfo/{connection_id}/(type)`_
     - Returns an array of id and name of the query sources in the specified connection, filtered by type (Table, View or Stored Procedure).
   * - `GET dataModel/querySourcesInfo/{connection_id}/(type)`_
     - Returns an array of the query sources in the specified connection, filtered by type (Table, View or Stored Procedure).
   * - `DELETE dataModel/querySourceField/{query_source_field_id}`_
     - Removes a query source field from data model.
   * - `GET dataModel/basicQuerySourceFieldsInfo/{query_source_id}`_
     - Returns an array of id and name of the query source fields in the query source specified by the {query_source_id} value.
   * - `POST dataModel`_
     - Saves a list of query sources.
   * - `GET dataModel/indicator/(tenant_id)`_
     - Returns the number of physical changes in Data Model for each type Table, View, Stored procedure and Function, filtered by tenant_id if provided.
   * - `POST dataModel/reloadQuerySourceFields`_
     - Returns the schema of stored procedures after using user-supplied parameters to try running them.
   * - `POST dataModel/validateCalculatedField`_
     - Validates a calculated field for duplicated name before saving.
   * - `GET dataModel/functionOperators/(tenant_id)`_
     - Returns an array of functions/operators that support calculated fields, filtered by tenant_id if provided.
   * - `POST dataModel/loadRelationships`_
     - Returns an array of relationships of visible data sources, paged and sorted, filtered by search criteria.
   * - `POST dataModel/relationships`_
     - Saves an array of relationships. |br| |br|
       After adding a new relationship, `POST DataModel/loadRelationships`_ should be called to retrieve the new id value.
   * - `DELETE dataModel/relationship/{relationship_id}`_
     - Deletes the relationship specified by the {relationship_id} value.
   * - `GET dataModel/schema/(tenant_id)`_
     - Returns an array of query sources and an array of relationships with color properties (filtered by tenant_id if given).
   * - `POST dataModel/schema/updateConnectionColor`_
     - Updates the connection color.
   * - `GET dataModel/relationship/joinTypes`_
     - Returns an array of join types currently supported.
   * - `GET dataModel/databaseMapping`_
     - Returns an array of database mappings.
   * - `POST dataModel/databaseMapping`_
     - Saves an array of database mappings.
   * - `POST dataModel/loadDatabaseNames`_
     - Returns a paged array of database servers and database names.
   * - `POST dataModel/loadDatabaseObjects`_
     - Returns a paged array of connection names or schema names in the specified database.
   * - `POST dataModel/customQuerySource`_
     - Executes and saves a custom query source.
   * - `POST dataModel/validateCustomQuerySource`_
     - Validates that name of custom query source is unique.
   * - `POST dataModel/deleteCustomQuerySource`_
     - Deletes a custom query source.
   * - `GET dataModel/querySource/{query_source_id}`_
     - Returns the query source specified by query_source_id.

.. _POST_dataModel/loadQuerySources:

POST dataModel/loadQuerySources
--------------------------------------------------------------

Returns an array of visible query sources, paged and sorted, filtered by type and other search criteria.

**Request**

    Payload: a :doc:`models/QuerySourcePagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/QuerySource` objects

**Samples**

   .. code-block:: http

      POST /api/dataModel/loadQuerySources HTTP/1.1

   Request payload::

      {
        "querySourceType" : "Table",
        "tenantId" : null,
        "criteria" : [{
              "key" : "DataSourceName",
              "value" : "demo",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "Category",
              "descending" : true
           }
        ]
      }

   Sample response::

      {
        "result" : [{
              "id" : "24fa8fec-afe0-489d-b036-aaca514a7a0b",
              "name" : "dbo.CustomerDemographics",
              "type" : "Table",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "48733501-c57d-48ca-aded-501d5ebdaad9",
              "connectionName" : "Northwind",
              "childs" : null,
              "dataSourceCategoryId" : "feb74cd9-bc6d-4933-bf72-296b394d0f77",
              "dataSourceCategoryName" : "Cat_Customer",
              "alias" : "Cus_D",
              "querySourceFields" : [],
              "querySourceCategory" : null,
              "modified" : null,
              "extendedProperties" : null,
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }
        ],
        "total" : 2,
        "pageIndex" : 1,
        "pageSize" : 1
      }

.. _POST_dataModel/loadQuerySourceFields:

POST dataModel/loadQuerySourceFields
--------------------------------------------------------------

Returns an array of query source fields in a query source. |br| |br|
Will load from remote connection if they are not yet populated in system.

**Request**

    Payload: a :doc:`models/QuerySourceFieldPagedRequest` object

**Response**

        A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/QuerySourceField` objects

**Samples**

   .. code-block:: http

      POST /api/dataModel/loadQuerySourceFields HTTP/1.1

   Request payload::

      {
        "querySource" : {
           "id" : "9fa90af2-5329-44ac-a753-50c27f9d6fd5",
           "type" : "Table"
        },
        "criteria" : [],
        "tenantId" : null,
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "Alias",
              "descending" : true
           }
        ]
      }


   Sample response::

      {
         "result": [{
            "id": "04ff2dc5-df20-48e3-bae8-443b400b0b89",
            "name": "CustomerTypeID",
            "alias": "CTypeID",
            "dataType": "nchar",
            "visible": true,
            "filterable": true,
            "deleted": false,
            "querySourceId": "9fa90af2-5329-44ac-a753-50c27f9d6fd5",
            "parentId": null,
            "children": null,
            "modified": "2016-04-07T04:51:17",
            "filteredValue": "{}",
            "type": 0,
            "position": 0,
            "extendedProperties": "{\"PrimaryKey\":true}",
            "physicalChange": 0,
            "approval": 0,
            "existed": false,
            "matchedTenant": false
         }],
         "total": 2,
         "pageIndex": 1,
         "pageSize": 1
      }


GET dataModel/basicConnectionsInfo/(tenant_id)
--------------------------------------------------------------

Returns an array of id and name of connections (filtered by tenant_id if given).

.. note::

   The same as :ref:`GET_connection/basicInfo/(tenant_id)`

**Request**

    No payload

**Response**

    An array of objects with two fields **key** and **value**
    
    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string (GUID)
          -  The id of the connection
          -
       *  -  **value** |br|
             string
          -  The name of the connection
          -

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicConnectionsInfo HTTP/1.1

   Sample response::

      [{
         "key": "48733501-c57d-48ca-aded-501d5ebdaad9",
         "value": "Northwind"
      }]

POST dataModel/basicConnectionsInfo
--------------------------------------------------------------

Returns an array of connections infor with paging.

.. versionadded:: 2.4.0

.. note::

   The same as :ref:`GET_connection/basicInfo/(tenant_id)`

**Request**

    Payload: a :doc:`models/PagedRequest` object.

**Response**

    - An array of objects with two fields **key** and **value** 
    
    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string (GUID)
          -  The id of the connection
          -
       *  -  **value** |br|
             string
          -  The name of the connection
          -

    - A :doc:`models/PagedRequest` object.

**Samples**

   .. code-block:: http

      POST /api/dataModel/basicConnectionsInfo HTTP/1.1

   Sample response::

      {
        [{
          "key": "48733501-c57d-48ca-aded-501d5ebdaad9",
          "value": "Northwind"
        },
        {
          "key": "ed13d1d0-cc0c-49bc-8925-3a11da65ef65",
          "value": "MVC5-ViTest",
        }],
        "pageIndex": 0,
        "pageSize": 1000,
        "total": 17,
        "skipItems": 0,
        "isLastPage": true
      }


GET dataModel/basicQuerySourceCategoriesInfo/{connection_id}
--------------------------------------------------------------

Returns an array of the :term:`query source categories <query source category>` in the specified connection.

.. versionadded:: 2.0.3

**Request**

    No payload

**Response**

    To be updated

**Samples**

   To be updated

POST dataModel/basicQuerySourceCategoriesInfo/
--------------------------------------------------------------

Returns an array of the :term:`query source categories <query source category>` with paging.

.. versionadded:: 2.4.0

**Request**

    Payload: a :doc:`models/QuerySourceCategoryPagedRequest` object.

**Response**

    To be updated

**Samples**

   To be updated

GET dataModel/basicQuerySourcesInfo/{connection_id}/(type)
--------------------------------------------------------------

Returns an array of id and name of the query sources in the specified connection, filtered by type (Table, View or Stored Procedure).

**Request**

    No payload

    **type** values:
    
    * Table
    * View
    * Stored%20Procedure

**Response**

    An array of objects with two fields **key** and **value**
    
    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string (GUID)
          -  The id of the query source
          -
       *  -  **value** |br|
             string
          -  The name of the query source, qualified with the schema name
          -


**Samples**

   .. code-block:: http

      GET /api/dataModel/basicQuerySourcesInfo/48733501-c57d-48ca-aded-501d5ebdaad9 HTTP/1.1

   Sample response::

      [{
         "key": "4e9aabda-9a95-4a00-8d80-0b8b1fbc7bc8",
         "value": "dbo.Suppliers"
      }, {
         "key": "42f7c4ff-f44e-4460-bd50-10540d99a276",
         "value": "dbo.Order Details"
      }]


GET dataModel/querySourcesInfo/{connection_id}/(type)
--------------------------------------------------------------

Returns an array of the query sources in the specified connection, filtered by type (Table, View or Stored Procedure).

**Request**

    No payload

    **type** values:

    * Table
    * View
    * Stored%20Procedure

**Response**

    An array of :doc:`models/QuerySourceInfo` objects

**Samples**

   .. code-block:: http

      GET /api/dataModel/querySourcesInfo/5e8e56ce-ac29-48cf-ae0d-56cb5d9a935e/Table HTTP/1.1

   Sample response::

      [
        {
          "id": "77882ea1-6d82-45c2-b762-6c8612682b91",
          "name": "Categories",
          "alias": null,
          "category": "dbo",
          "serverTypeId": "00000000-0000-0000-0000-000000000000",
          "connectionStringId": "00000000-0000-0000-0000-000000000000",
          "connectionString": null
        },
        {
          "id": "55329213-9db0-4835-b465-44b3ac9b19fa",
          "name": "CustomerCustomerDemo",
          "alias": null,
          "category": "dbo",
          "serverTypeId": "00000000-0000-0000-0000-000000000000",
          "connectionStringId": "00000000-0000-0000-0000-000000000000",
          "connectionString": null
        }]


DELETE dataModel/querySourceField/{query_source_field_id}
--------------------------------------------------------------

Removes a query source field from data model.

**Request**

    No payload

**Response**

    * true if the deletion is succesful
    * false if not

**Samples**

   .. code-block:: http

      DELETE /api/dataModel/querySourceField/da7be1b4-d4c0-43c4-a11b-5c87004c4837 HTTP/1.1

   Sample response::

      true


GET dataModel/basicQuerySourceFieldsInfo/{query_source_id}
--------------------------------------------------------------

Returns an array of id and name of the query source fields in the query source specified by the {query_source_id} value.

**Request**

    No payload

**Response**

    An array of objects with two fields **key** and **value**
    
    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string (GUID)
          -  The id of the query source field
          -
       *  -  **value** |br|
             string
          -  The name of the query source field
          -

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicQuerySourceFieldsInfo/4e9aabda-9a95-4a00-8d80-0b8b1fbc7bc8 HTTP/1.1

   Sample response::

      [{
         "key": "f8c2a34b-b304-4f1d-9d90-96c018ec3d2a",
         "value": "ContactName"
      }, {
         "key": "a895434e-a77b-452e-8ed1-9b5fa339f1a8",
         "value": "CompanyName"
      }, {
         "key": "3b266337-0142-4a4b-8351-ea0a74a7f234",
         "value": "SupplierID"
      }]

.. _POST_dataModel:

POST dataModel
--------------------------------------------------------------

Saves a list of query sources.

**Request**

    Payload: a :doc:`models/DataModel` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the save is successful

**Samples**

   .. code-block:: http

      POST /api/dataModel HTTP/1.1

   Request payload to save the aliases for column [dbo].[AWBuildVersion].[Database Version] and for table [dbo].[Categories]::

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

   Request Payload to set dynamic for stored procedure [dbo].[CustOrdersDetail]::

      {
        "tenantId" : null,
        "querySources" : [{
              "id" : "eabce774-10e4-4c9d-b0fd-7f8dc3b8a6be",
              "name" : "dbo.CustOrdersDetail",
              "type" : "Stored Procedure",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "38f89176-7113-4a20-aed0-9758cb65122a",
              "connectionName" : "AdventureWorks2008R2",
              "childs" : null,
              "dataSourceCategoryId" : null,
              "dataSourceCategoryName" : null,
              "alias" : null,
              "querySourceFields" : [{
                    "id" : "5d4c6339-1539-43ed-a1d4-fd6f423f6bd3",
                    "name" : "@OrderID",
                    "alias" : "",
                    "dataType" : "int",
                    "visible" : true,
                    "filterable" : true,
                    "deleted" : false,
                    "querySourceId" : "eabce774-10e4-4c9d-b0fd-7f8dc3b8a6be",
                    "parentId" : null,
                    "children" : null,
                    "modified" : "2016-04-13T08:55:15.803",
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
              "querySourceCategory" : null,
              "modified" : "2016-12-13T08:55:15.787",
              "extendedProperties" : "{\"Dynamic\":true,\"Static\":false}",
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }
        ]
      }

   Request Payload to set Field Level and Expression Level for functions::

      {
        "tenantId" : null,
        "querySources" : [{
              "id" : "b2972494-ca59-4904-9561-d4b609a6b806",
              "name" : "northwind.DateOnly",
              "type" : "Function",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "33244a6a-df64-46f8-8c5c-93eebe0f9c47",
              "connectionName" : "northwind",
              "childs" : null,
              "dataSourceCategoryId" : null,
              "dataSourceCategoryName" : null,
              "alias" : null,
              "querySourceFields" : [],
              "querySourceCategory" : null,
              "modified" : "2016-12-13T07:36:42.713",
              "extendedProperties" : "{\"ReturnedValue\":\"varchar\",\"InputParams\":\"InDateTime\",\"FieldLevel\":true,\"ExpressionLevel\":true}",
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }, {
              "id" : "2224f941-a4e1-4211-8c52-fcba3dc14dd8",
              "name" : "northwind.MyRound",
              "type" : "Function",
              "parentQuerySourceId" : null,
              "categoryId" : null,
              "selected" : false,
              "connectionId" : "33244a6a-df64-46f8-8c5c-93eebe0f9c47",
              "connectionName" : "northwind",
              "childs" : null,
              "dataSourceCategoryId" : null,
              "dataSourceCategoryName" : null,
              "alias" : null,
              "querySourceFields" : [],
              "querySourceCategory" : null,
              "modified" : "2016-12-13T07:36:42.713",
              "extendedProperties" : "{\"ReturnedValue\":\"double\",\"InputParams\":\"Operand,Places\",\"FieldLevel\":false,\"ExpressionLevel\":true}",
              "physicalChange" : 0,
              "approval" : 0,
              "existed" : false
           }
        ]
      }

   Successful response::

      {
        "success" : true,
        "messages" : []
      }

GET dataModel/indicator/(tenant_id)
--------------------------------------------------------------

Returns the number of physical changes in Data Model for each type Table, View, Stored procedure and Function, filtered by tenant_id if provided.

**Request**

    No payload

**Response**

    An array of objects with two fields **key** and **value**
    
    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **key** |br|
             string
          -  Either "Table", "View", "Stored procedure" or "Function"
          -
       *  -  **value** |br|
             integer
          -  The number of changes for each type
          -

**Samples**

   .. code-block:: http

      GET /api/dataModel/indicator HTTP/1.1

   Sample response::

      [{
        "key" : "Table",
        "value" : 2
      }, {
        "key" : "View",
        "value" : 1
      }]


POST dataModel/reloadQuerySourceFields
--------------------------------------------------------------

Returns the schema of stored procedures after using user-supplied parameters to try running them.

**Request**

    Payload: a :doc:`models/ReloadQuerySourceRequest` object

**Response**

    A :doc:`models/DataResult` object, with **data** field containing a :doc:`models/PagedResult` object whose **result** field containing a list of :doc:`models/QuerySourceField` objects

**Samples**

   .. code-block:: http

      POST /api/dataModel/reloadQuerySourceFields HTTP/1.1

   Request payload for Filter Lookup Key - Value::

      {
        "querySourceId" : "0cd0f186-48f1-47a9-9975-1f2bded3a5cc",
        "postedParameters" : [{
              "id" : "8ccfac80-c883-446b-948d-18568dc4d173",
              "name" : "@OrderID",
              "filteredValue" : {
                 "type":"1",
                 "databaseName":"Northwind",
                 "databaseId":"f7d00fd9-bfb4-40ae-b25a-61007781b196",
                 "querySourceName":"dbo.Order Details",
                 "querySourceId":"000e6c8a-89fd-4b38-8d6a-1b891c180daa",
                 "lookupKeyQuerySourceFieldName":"OrderID",
                 "lookupKeyQuerySourceFieldId":"a0acf5b0-4e47-49d6-af73-c953408df3ef",
                 "displayQuerySourceFieldName":"OrderID",
                 "displayQuerySourceFieldId":"a0acf5b0-4e47-49d6-af73-c953408df3ef",
                 "userDefinedValues": []
              }
           }
        ],
        "sortOrders" : [{
              "key" : "ColumnName",
              "descending" : true
           }
        ]
      }

   Request payload for User Defined Filter Value::

      {
        "querySourceId" : "0cd0f186-48f1-47a9-9975-1f2bded3a5cc",
        "postedParameters" : [{
              "id" : "8ccfac80-c883-446b-948d-18568dc4d173",
              "name" : "@OrderID",
              "filteredValue" : {
                 "type" : "2",
                 "userDefinedValues" : ["1", "2"]
              }
           }
        ],
        "sortOrders" : [{
              "key" : "ColumnName",
              "descending" : true
           }
        ]
      }

   Sample response::

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


POST dataModel/validateCalculatedField
--------------------------------------------------------------

Validates a calculated field for duplicated name before saving.

**Request**

    Payload: a :doc:`models/QuerySourceField` object

**Response**

    * true if the name is valid
    * false if not

**Samples**

   .. code-block:: http

      POST /api/dataModel/validateCalculatedField HTTP/1.1

   Request payload::

      {
              "name" : "UnitPrice",
              "querySourceId" : "9d18fa06-bf09-4908-9cc0-3ecb15c0e9e4"
      }

   Sample response::

      true


GET dataModel/functionOperators/(tenant_id)
--------------------------------------------------------------

Returns an array of functions/operators that support calculated fields, filtered by tenant_id if provided.

**Request**

    No payload

**Response**

    An array of :doc:`models/ReportFunction` objects

**Samples**

   .. code-block:: http

      GET /api/dataModel/functionOperators HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "id": null,
            "name": "-",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression - expression",
            "expressionSyntax": "-",
            "isOperator": false
         }, {
            "id": null,
            "name": "*",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression * expression",
            "expressionSyntax": "*",
            "isOperator": false
         }, {
            "id": null,
            "name": "/",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression / expression",
            "expressionSyntax": "/",
            "isOperator": false
         }, {
            "id": null,
            "name": "+",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression + expression",
            "expressionSyntax": "+",
            "isOperator": false
         }, {
            "id": null,
            "name": "<",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression < expression",
            "expressionSyntax": "<",
            "isOperator": false
         }, {
            "id": null,
            "name": "<=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression <= expression",
            "expressionSyntax": "<=",
            "isOperator": false
         }, {
            "id": null,
            "name": "<>",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression <> expression",
            "expressionSyntax": "<>",
            "isOperator": false
         }, {
            "id": null,
            "name": "=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression = expression",
            "expressionSyntax": "=",
            "isOperator": false
         }, {
            "id": null,
            "name": ">",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression > expression",
            "expressionSyntax": ">",
            "isOperator": false
         }, {
            "id": null,
            "name": ">=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression >= expression",
            "expressionSyntax": ">=",
            "isOperator": false
         }, {
            "id": null,
            "name": "AND",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "boolean_expression AND boolean_expression",
            "expressionSyntax": "AND",
            "isOperator": false
         }, {
            "id": null,
            "name": "AVG",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "AVG (expression)",
            "expressionSyntax": "AVG",
            "isOperator": false
         }, {
            "id": null,
            "name": "BETWEEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "BETWEEN (test_expression, begin_expression, end_expression)",
            "expressionSyntax": "BETWEEN",
            "isOperator": false
         }, {
            "id": null,
            "name": "CASE WHEN...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CASE WHEN (boolean_expression) THEN (result_expression) [...n] [ELSE (else_result_expression)] END",
            "expressionSyntax": "CASE...WHEN...THEN...ELSE...END",
            "isOperator": false
         }, {
            "id": null,
            "name": "CASE...WHEN...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CASE (input_expression) WHEN (when_expression) THEN (result_expression) [...n] [ELSE (else_result_expression)] END",
            "expressionSyntax": "CASE...WHEN...THEN...ELSE...END",
            "isOperator": false
         }, {
            "id": null,
            "name": "CAST...AS",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CAST (expression AS data_type)",
            "expressionSyntax": "CAST...AS",
            "isOperator": false
         }, {
            "id": null,
            "name": "CONVERT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CONVERT (data_type [( length)], expression[, style])",
            "expressionSyntax": "CONVERT",
            "isOperator": false
         }, {
            "id": null,
            "name": "COUNT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "COUNT (expression)",
            "expressionSyntax": "COUNT",
            "isOperator": false
         }, {
            "id": null,
            "name": "DATEADD",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEADD (datepart, number, expression)",
            "expressionSyntax": "DATEADD",
            "isOperator": false
         }, {
            "id": null,
            "name": "DATEDIFF",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEDIFF (datepart, startdate, enddate)",
            "expressionSyntax": "DATEDIFF",
            "isOperator": false
         }, {
            "id": null,
            "name": "DATEPART",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEPART (datepart, date)",
            "expressionSyntax": "DATEPART",
            "isOperator": false
         }, {
            "id": null,
            "name": "DISTINCT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DISTINCT (column) or DISTINCT column",
            "expressionSyntax": "DISTINCT",
            "isOperator": false
         }, {
            "id": null,
            "name": "GETDATE",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "GETDATE ()",
            "expressionSyntax": "GETDATE",
            "isOperator": false
         }, {
            "id": null,
            "name": "IF...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "IF (boolean_expression) THEN (true_expression) [ELSE (false_expression)] END",
            "expressionSyntax": "IF...THEN...ELSE...END",
            "isOperator": false
         }, {
            "id": null,
            "name": "IIF",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "IIF (boolean_expression, true_expression, [false_expression])",
            "expressionSyntax": "IIF",
            "isOperator": false
         }, {
            "id": null,
            "name": "ISNULL",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "ISNULL (check_expression, replacement_value)",
            "expressionSyntax": "ISNULL",
            "isOperator": false
         }, {
            "id": null,
            "name": "LEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "LEN (expression)",
            "expressionSyntax": "LEN",
            "isOperator": false
         }, {
            "id": null,
            "name": "MAX",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "MAX (expression)",
            "expressionSyntax": "MAX",
            "isOperator": false
         }, {
            "id": null,
            "name": "MIN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "MIN (expression)",
            "expressionSyntax": "MIN",
            "isOperator": false
         }, {
            "id": null,
            "name": "NOTBETWEEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "NOTBETWEEN (test_expression, begin_expression, end_expression)",
            "expressionSyntax": "NOTBETWEEN",
            "isOperator": false
         }, {
            "id": null,
            "name": "OR",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "boolean_expression OR boolean_expression",
            "expressionSyntax": "OR",
            "isOperator": false
         }, {
            "id": null,
            "name": "ROUND",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "ROUND (expression, length[, function])",
            "expressionSyntax": "ROUND",
            "isOperator": false
         }, {
            "id": null,
            "name": "RUNNING AVG",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGAVG (column)",
            "expressionSyntax": "RUNNINGAVG",
            "isOperator": false
         }, {
            "id": null,
            "name": "RUNNING COUNT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGCOUNT (column)",
            "expressionSyntax": "RUNNINGCOUNT",
            "isOperator": false
         }, {
            "id": null,
            "name": "RUNNING SUM",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGSUM (column)",
            "expressionSyntax": "RUNNINGSUM",
            "isOperator": false
         }, {
            "id": null,
            "name": "SUM",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "SUM (expression)",
            "expressionSyntax": "SUM",
            "isOperator": false
         }]


POST dataModel/loadRelationships
--------------------------------------------------------------

Returns an array of relationships of visible data sources, paged and sorted, filtered by search criteria.

**Request**

    Payload: a :doc:`models/RelationshipPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/Relationship` objects

**Samples**

   .. code-block:: http

      POST /api/dataModel/loadRelationships HTTP/1.1

   Request payload::

      {
        "querySourceId" : null,
        "tenentId" : "",
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "DatabaseName",
              "descending" : true
           }
        ]
      }

   Sample response::

      {
        "result" : [{
              "joinConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
              "foreignConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
              "joinQuerySourceId" : "e03b8805-60ae-41df-b69a-f3bece9721c5",
              "joinQuerySourceName" : "EmployeeDepartmentHistory",
              "joinDataSourceCategoryName" : null,
              "joinDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
              "foreignDataSourceCategoryName" : null,
              "foreignDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
              "foreignQuerySourceId" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92",
              "foreignQuerySourceName" : "Employee",
              "joinFieldId" : "322d9f3d-1f65-4d60-9cac-933a2c40db9d",
              "joinFieldName" : "BusinessEntityID",
              "foreignFieldId" : "484817ea-f130-417b-a096-32c13249b7d0",
              "foreignFieldName" : "BusinessEntityID",
              "alias" : "abc",
              "systemRelationship" : true,
              "joinType" : "Inner",
              "parentRelationshipId" : "00000000-0000-0000-0000-000000000000",
              "deleted" : false,
              "position" : null,
              "relationshipKeyJoins" : null,
              "reportId" : "00000000-0000-0000-0000-000000000000",
              "foreignAlias" : null,
              "selectedForeignAlias" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92_Employee",
              "id" : "48ab1f19-db84-4d8b-9c18-02312d16c282",
              "state" : 0,
              "modified" : "2016-04-15T06:27:16.023"
           }
        ],
        "total" : 60,
        "pageIndex" : 1,
        "pageSize" : 1
      }


POST dataModel/relationships
--------------------------------------------------------------

Saves an array of relationships. |br| |br|
After adding a new relationship, `POST DataModel/loadRelationships`_ should be called to retrieve the new id value.

**Request**

    Payload: an array of :doc:`models/Relationship` objects

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the save is successful

**Samples**

   .. code-block:: http

      POST /api/dataModel/relationships HTTP/1.1

   Request payload to insert one new relationship and update another::

      [{
           "id" : null,
           "joinConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
           "foreignConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
           "joinQuerySourceId" : "d310d0ec-06b3-409f-b48c-1f519d0a51d5",
           "foreignQuerySourceId" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92",
           "joinFieldId" : "79c398b3-bc5d-4c68-9329-111a7125ad0d",
           "foreignFieldId" : "aff13fd8-b7dc-439d-bfbf-1cd1a1728565",
           "alias" : "",
           "systemRelationship" : false,
           "joinType" : "Inner",
           "position" : "191"
        }, {
           "id" : "c7288fb3-1f9d-49c3-897e-1587d6ccda5f",
           "joinConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
           "foreignConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
           "joinQuerySourceId" : "e03b8805-60ae-41df-b69a-f3bece9721c5",
           "foreignQuerySourceId" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92",
           "joinFieldId" : "322d9f3d-1f65-4d60-9cac-933a2c40db9d",
           "foreignFieldId" : "484817ea-f130-417b-a096-32c13249b7d0",
           "alias" : "",
           "systemRelationship" : false,
           "joinType" : "Inner",
           "modified" : "2016-04-15T03:57:37.803",
           "position" : "185"
        }
      ]

   Sample response::

      {
        "success" : true,
        "messages" : []
      }


DELETE dataModel/relationship/{relationship_id}
--------------------------------------------------------------

Deletes the relationship specified by the {relationship_id} value.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if deletion is successful

**Samples**

   .. code-block:: http

      DELETE /api/dataModel/relationship/457dbf49-9b1d-42d0-9026-0e67ee86a912 HTTP/1.1

   Successful response::

      {
        "success" : true,
        "messages" : []
      }

   Response when trying to delete a system relationship::

      {
        "success": false,
        "messages": [
          {
            "key": "",
            "detail": null,
            "messages": [
              "System relationship cannot be deleted."
            ]
          }
        ],
        "data": null
      }

GET dataModel/schema/(tenant_id)
--------------------------------------------------------------

Returns an array of query sources and an array of relationships with color properties (filtered by tenant_id if given).

**Request**

    No payload

**Response**

    A :doc:`models/DataModelSchema` object

**Samples**

   .. code-block:: http

      GET /api/dataModel/schema HTTP/1.1

   Sample response for 2 relationships "Customer" Left joins with "Orders" and "Orders" Inner joins with "Order Details"::

      {
         "querySources": [{
            "id": "8aa52ba9-8324-4b8e-bf42-619a3f050aa5",
            "name": "dbo.Customers",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-04-19T03:08:56.091528",
            "fields": [{
                 "name": "ContactName",
                 "properties": ""
            }, {
                 "name": "CustomerID",
                 "properties": "{\"PrimaryKey\":true}"
            }]
         }, {
            "id": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "name": "dbo.Orders",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-12-19T03:08:56.091528",
            "fields": [{
                 "name": "CustomerID",
                 "properties": ""
            }, {
                 "name": "OrderDate",
                 "properties": ""
            }, {
                 "name": "OrderID",
                 "properties": "{\"PrimaryKey\":true}"
            }]
         }, {
            "id": "26efbdf4-c724-4824-bd9c-6ae1e2dc7435",
            "name": "dbo.Order Details",
            "type": "Table",
            "color": null,
            "connectionId": "8195a480-ddd8-4915-95a0-432e24fed0ad",
            "modified": "2016-12-19T03:08:56.091528",
            "fields": [{
                 "name": "OrderID",
                 "properties": "{\"PrimaryKey\":true}"
            }, {
                 "name": "ProductID",
                 "properties": "{\"PrimaryKey\":true}"
            }, {
                 "name": "Quantity",
                 "properties": ""
            }, {
                 "name": "UnitPrice",
                 "properties": ""
            }]
         }],
         "relationships": [{
            "joinQuerySourceId": "8aa52ba9-8324-4b8e-bf42-619a3f050aa5",
            "foreignQuerySourceId": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "twoWays": false
         }, {
            "joinQuerySourceId": "66dcf36e-e4b0-4c9b-9919-b9ba49377784",
            "foreignQuerySourceId": "26efbdf4-c724-4824-bd9c-6ae1e2dc7435",
            "twoWays": true
         }]
      }


POST dataModel/schema/updateConnectionColor
--------------------------------------------------------------

Updates the connection color.

To be updated

GET dataModel/relationship/joinTypes
--------------------------------------------------------------

Returns an array of join types currently supported.	

**Request**

    No payload

**Response**

    An array of string values. |br| |br|
    Currently supported are: "Inner", "Left", "Right", "Full" and "Cross".

**Samples**

   .. code-block:: http

      GET api/dataModel/relationship/joinTypes HTTP/1.1

   Sample response::

      ["Inner", "Left", "Right", "Full", "Cross"]

GET dataModel/databaseMapping
--------------------------------------------------------------

Returns an array of database mappings.

**Request**

    No payload

**Response**

    An array of :doc:`models/GlobalDatabaseMapping` objects

**Samples**

   .. code-block:: http

      GET api/dataModel/databaseMapping HTTP/1.1

   Sample response::

      [
         {
            "fromServer": "SERVER1",
            "toServer": "SERVER2",
            "fromDatabaseName": "[MSSQL] Northwind",
            "type": 2,
            "fromObject": "connection_name",
            "toDatabaseName": "[MSSQL] northwind",
            "toObject": "connection_name_2",
            "selectAllTenants": true,
            "tenantIds": "null",
            "tenants": null,
            "errorType": 0,
            "id": "258bbcf9-4bd1-49de-8728-1578bb4aefa7",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-04-14T04:18:50.4000000-07:00",
            "createdBy": "John Doe",
            "modified": "2017-04-14T04:18:50.4000000-07:00",
            "modifiedBy": "John Doe"
         }
      ]

POST dataModel/databaseMapping
--------------------------------------------------------------

Saves an array of database mappings.

**Request**

    An array of :doc:`models/GlobalDatabaseMapping` objects

**Response**

    An :doc:`models/OperationResult` object, with **success** field true if the save is successful

**Samples**

   .. code-block:: http

      POST api/dataModel/databaseMapping HTTP/1.1

   Request Payload::

      [
         {
            "id": null,
            "fromServer": "SERVER1",
            "fromDatabaseName": "[MSSQL] Northwind",
            "type": 2,
            "fromObject": "connection_name",
            "toServer": "SERVER2",
            "toDatabaseName": "[MSSQL] northwind",
            "toObject": "connection_name_2",
            "tenants": null,
            "state": 1,
            "selectAllTenants": true
         }
      ]

   Sample response::

      {
         "success":true
      }

POST dataModel/loadDatabaseNames
--------------------------------------------------------------

Returns a paged array of database servers and database names.

**Request**

    A :doc:`models/DatabaseMappingPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of the following object:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **serverTypeName** |br|
             string
          -  The type of the database server (MSSQL, Oracle, MySQL, etc.)
          -
       *  -  **databaseServer** |br|
             string
          -  The name of the server
          -
       *  -  **databaseName** |br|
             string
          -  The name of the database
          -

**Samples**

   .. code-block:: http

      POST api/dataModel/loadDatabaseNames HTTP/1.1

   Request Payload::

      {
         "pageIndex": 1,
         "pageSize": 10,
         "loadFromDatabase": true
      }

   Sample response::

      {
         "result": [
            {
               "serverTypeName": "AZSQL",
               "databaseServer": "abc.database.windows.net",
               "databaseName": "Northwind"
            },
            {
               "serverTypeName": "MSSQL",
               "databaseServer": "localhost",
               "databaseName": "Northwind"
            },
            {
               "serverTypeName": "MYSQL",
               "databaseServer": "192.168.1.1",
               "databaseName": "northwind"
            },
            {
               "serverTypeName": "ORACL",
               "databaseServer": "192.168.1.1:1521/orcl",
               "databaseName": "orcl"
            },
            {
               "serverTypeName": "PGSQL",
               "databaseServer": "192.168.1.1",
               "databaseName": "DB"
            }
         ],
         "pageIndex": 1,
         "pageSize": 10,
         "total": 5,
         "skipItems": 0,
         "isLastPage": true
      }

POST dataModel/loadDatabaseObjects
--------------------------------------------------------------

Returns a paged array of connection names or schema names in the specified database.

**Request**

    A :doc:`models/DatabaseMappingPagedRequest` object

**Response**

   A :doc:`models/PagedResult` object, with **result** field containing an array of strings.

   If :doc:`models/DatabaseMappingPagedRequest`.``type`` is ``2`` (Database), return connection names, else return schema names.

**Samples**

   .. code-block:: http

      POST api/dataModel/loadDatabaseObjects HTTP/1.1

   Request Payload for Database::

      {
         "pageIndex": 1,
         "pageSize": 10,
         "databaseServer": "SERVER1",
         "databaseName": "[MSSQL] Northwind",
         "type": 2
      }

   Sample response for Database::

      {
         "result": [
            "connection_name"
         ],
         "pageIndex": 1,
         "pageSize": 10,
         "total": 1,
         "skipItems": 0,
         "isLastPage": true
      }

   Request Payload for Schema::

      {
         "pageIndex": 1,
         "pageSize": 10,
         "databaseServer": "SERVER1",
         "databaseName": "[MSSQL] Northwind",
         "type": 1
      }

   Sample response for Schema::

      {
         "result": [
            "dbo"
         ],
         "pageIndex": 1,
         "pageSize": 10,
         "total": 1,
         "skipItems": 0,
         "isLastPage": true
      }

POST dataModel/customQuerySource
--------------------------------------------------------------

Executes and saves a custom query source.

**Request**

    A :doc:`models/QuerySource` object

**Response**

   The saved :doc:`models/QuerySource` object.

**Samples**

   To be updated

POST dataModel/validateCustomQuerySource
--------------------------------------------------------------

Validates that name of custom query source is unique.

**Request**

    A :doc:`models/QuerySource` object, with **name** and **categoryId** fields populated.

**Response**

   An :doc:`models/OperationResult` object, with **success** field true if name of custom query source is unique.

**Samples**

   To be updated

POST dataModel/deleteCustomQuerySource
--------------------------------------------------------------

Deletes a custom query source.

**Request**

    A :doc:`models/QuerySource` object, with **id** field populated.

**Response**

   An :doc:`models/OperationResult` object, with **success** true if the deletion is successful.

**Samples**

   To be updated

GET dataModel/querySource/{query_source_id}
--------------------------------------------------------------

Returns the query source specified by query_source_id.

**Request**

    No payload

**Response**

   A :doc:`models/QuerySource` object.

**Samples**

   To be updated
