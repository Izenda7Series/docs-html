

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
   * - `POST dataModel/basicQuerySourceCategoriesInfo`_
     - Returns an array of the :term:`query source categories <query source category>` with paging in the specified connection.
     
       .. versionadded:: 2.4.0
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
   * - `POST dataModel/functionOperators/`_
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
         "querySourceType": "Table",
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "criteria": [{
            "key": "DataSourceName",
            "value": "order",
            "operation": 1
         }],
         "pageIndex": 1,
         "pageSize": 10,
         "sortOrders": [{
            "key": "Category",
            "descending": true
         }]
      }

   Sample response::

      {
         "result": [        
            {
                  "realName": "orders_new",
                  "id": "18f55edc-b521-4614-9c06-817dac726284",
                  "name": "northwind.orders_new",
                  "type": "Table",
                  "parentQuerySourceId": null,
                  "categoryId": "94454a0a-17a2-49e5-bebf-9c0d07d95587",
                  "selected": false,
                  "deleted": false,
                  "connectionId": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
                  "connectionName": "northwind",
                  "childs": null,
                  "dataSourceCategoryId": null,
                  "dataSourceCategoryName": null,
                  "alias": null,
                  "originalAlias": null,
                  "querySourceFields": [],
                  "querySourceCategoryName": "northwind",
                  "querySourceCategory": null,
                  "modified": "2017-09-14T03:37:29.653",
                  "extendedProperties": null,
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "checked": false,
                  "belongToCopiedReport": false,
                  "customDefinition": null,
                  "isCustomQuerySource": false,
                  "isCheck": false,
                  "disabled": false,
                  "fullPath": null,
                  "indeterminate": false,
                  "numOfChilds": 0,
                  "numOfCheckedChilds": 0
            }
         ],
         "pageIndex": 1,
         "pageSize": 10,
         "total": 1,
         "skipItems": 0,
         "isLastPage": false
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
         "result": [
            {
                  "name": "ShipVia",
                  "alias": "",
                  "dataType": "int",
                  "izendaDataType": "Numeric",
                  "allowDistinct": true,
                  "visible": true,
                  "filterable": true,
                  "querySourceId": "18f55edc-b521-4614-9c06-817dac726284",
                  "parentId": null,
                  "expressionFields": [],
                  "filteredValue": "",
                  "type": 0,
                  "groupPosition": 0,
                  "position": 7,
                  "extendedProperties": "{\"PrimaryKey\":true}",
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "matchedTenant": false,
                  "functionName": null,
                  "expression": null,
                  "fullName": null,
                  "calculatedTree": null,
                  "reportId": null,
                  "originalName": null,
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isParameter": false,
                  "isCalculated": false,
                  "hasAggregatedFunction": false,
                  "querySource": null,
                  "querySourceName": null,
                  "categoryName": null,
                  "inaccessible": false,
                  "originalAlias": null,
                  "fullPath": null,
                  "isCheck": false,
                  "id": "0b0645cc-c401-4574-a868-aacaada4cb16",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "acme",
                  "modified": "2017-09-14T03:35:32.33",
                  "modifiedBy": null
            }
         ],
         "pageIndex": 1,
         "pageSize": 1,
         "total": 14,
         "skipItems": 0,
         "isLastPage": true
      }


GET dataModel/basicConnectionsInfo/(tenant_id)
--------------------------------------------------------------

Returns an array of id and name of connections (filtered by tenant_id if given).

.. note::

   The same as :ref:`GET_connection/basicInfo/(tenant_id)`

**Request**

    No payload

**Response**

   An array of :doc:`models/Item` objects with:

      \- **key** is the id of the connection |br|
      \- **value** is the name of the connection

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicConnectionsInfo HTTP/1.1

   Sample response::

      [
         {
            "key": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
            "value": "northwind",
            "originalValue": null,
            "dataFormat": null,
            "intimePeriodType": null,
            "valueInTimePeriod": 0,
            "function": null
         }
      ]

POST dataModel/basicConnectionsInfo
--------------------------------------------------------------

Returns an array of connections infor with paging.

.. versionadded:: 2.4.0

.. note::

   The same as :ref:`GET_connection/basicInfo/(tenant_id)`

**Request**

   Payload: a :doc:`models/PagedRequest` object.

**Response**

   A :doc:`models/PagedResult` object with **result** field containing a list of :doc:`models/Item` objects whose each **key** is the connectionsId and **value** is the connectionName.

**Samples**

   .. code-block:: http

      POST /api/dataModel/basicConnectionsInfo HTTP/1.1

   Sample response::

      {
         "result": [
            {
                  "key": "2046c03b-3830-4385-9ac0-bdc95e92ea49",
                  "value": "[MSSQL]My Test 1",
                  "originalValue": null,
                  "dataFormat": null,
                  "intimePeriodType": null,
                  "valueInTimePeriod": 0,
                  "function": null
            },
            {
                  "key": "7e682625-52c8-4524-a19d-4d8225aa9ea8",
                  "value": "[MSSQL]My Test 2",
                  "originalValue": null,
                  "dataFormat": null,
                  "intimePeriodType": null,
                  "valueInTimePeriod": 0,
                  "function": null
            }
         ],
         "pageIndex": 1,
         "pageSize": 2,
         "total": 19,
         "skipItems": 0,
         "isLastPage": false
      }

GET dataModel/basicQuerySourceCategoriesInfo/{connection_id}
--------------------------------------------------------------

Returns an array of the :term:`query source categories <query source category>` in the specified connection.

.. versionadded:: 2.0.3

**Request**

    No payload

**Response**

   An array of :doc:`models/Item` objects with:

      \- **key** is the id of the :doc:`models/QuerySourceCategory` |br|
      \- **value** is the name of the :doc:`models/QuerySourceCategory`

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicQuerySourceCategoriesInfo/2046c03b-3830-4385-9ac0-bdc95e92ea49 HTTP/1.1

   Sample response::

      [
        {
          "key": "34dc82ea-890d-4e3a-86a9-91ef171fd6f5",
          "value": "Application",
          "originalValue": null,
          "dataFormat": null,
          "intimePeriodType": null,
          "valueInTimePeriod": 0,
          "function": null
        },
        {
          "key": "e3354049-cffc-4b3d-1g25-e9f518d12d01",
          "value": "DataLoadSimulation",
          "originalValue": null,
          "dataFormat": null,
          "intimePeriodType": null,
          "valueInTimePeriod": 0,
          "function": null
        }
      ]

POST dataModel/basicQuerySourceCategoriesInfo/
--------------------------------------------------------------

Returns an array of the :term:`query source categories <query source category>` with paging.

.. versionadded:: 2.4.0

**Request**

    Payload: a :doc:`models/QuerySourceCategoryPagedRequest` object.

**Response**

       A :doc:`models/PagedResult` object with **result** field containing a list of :doc:`models/Item` objects whose each **key** is the id of the :doc:`models/QuerySourceCategory` and **value** is the name of the the :doc:`models/QuerySourceCategory`.

**Samples**

   .. code-block:: http

      POST /api/dataModel/basicQuerySourceCategoriesInfo HTTP/1.1

   Sample response::

      {
         "result": [
            {
                  "key": "34dc82ea-890d-4e3a-86a9-91ef171f4ca5",
                  "value": "Application",
                  "originalValue": null,
                  "dataFormat": null,
                  "intimePeriodType": null,
                  "valueInTimePeriod": 0,
                  "function": null
            }
         ],
         "pageIndex": 1,
         "pageSize": 1,
         "total": 11,
         "skipItems": 0,
         "isLastPage": false
      }

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

   An array of :doc:`models/Item` objects with:

      \- **key** is the id of the :doc:`models/QuerySource` |br|
      \- **value** is the name of the :doc:`models/QuerySource`

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicQuerySourcesInfo/48733501-c57d-48ca-aded-501d5ebdaad9 HTTP/1.1

   Sample response::

      [{
         "key": "4e9aabda-9a95-4a00-8d80-0b8b1fbc7bc8",
         "value": "dbo.Suppliers",
         "originalValue": null,
         "dataFormat": null,
         "intimePeriodType": null,
         "valueInTimePeriod": 0,
         "function": null
      }, {
         "key": "42f7c4ff-f44e-4460-bd50-10540d99a276",
         "value": "dbo.Order Details",
         "originalValue": null,
         "dataFormat": null,
         "intimePeriodType": null,
         "valueInTimePeriod": 0,
         "function": null
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
          "connectionString": null,
          "connectionName": null,
          "querySourceCategoryName": null
        },
        {
          "id": "55329213-9db0-4835-b465-44b3ac9b19fa",
          "name": "CustomerCustomerDemo",
          "alias": null,
          "category": "dbo",
          "serverTypeId": "00000000-0000-0000-0000-000000000000",
          "connectionStringId": "00000000-0000-0000-0000-000000000000",
          "connectionString": null,
          "connectionName": null,
          "querySourceCategoryName": null
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

   An array of :doc:`models/Item` objects with:

      \- **key** is the id of the :doc:`models/QuerySourceField` |br|
      \- **value** if the name of the :doc:`models/QuerySourceField`

**Samples**

   .. code-block:: http

      GET /api/dataModel/basicQuerySourceFieldsInfo/4e9aabda-9a95-4a00-8d80-0b8b1fbc7bc8 HTTP/1.1

   Sample response::

      [{
         "key": "f8c2a34b-b304-4f1d-9d90-96c018ec3d2a",
         "value": "ContactName",
         "originalValue": null,
         "dataFormat": null,
         "intimePeriodType": null,
         "valueInTimePeriod": 0,
         "function": null
      }, {
         "key": "a895434e-a77b-452e-8ed1-9b5fa339f1a8",
         "value": "CompanyName",
         "originalValue": null,
         "dataFormat": null,
         "intimePeriodType": null,
         "valueInTimePeriod": 0,
         "function": null
      }, {
         "key": "3b266337-0142-4a4b-8351-ea0a74a7f234",
         "value": "SupplierID",
         "originalValue": null,
         "dataFormat": null,
         "intimePeriodType": null,
         "valueInTimePeriod": 0,
         "function": null
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
        "messages" : [],
        "data" : null
      }

GET dataModel/indicator/(tenant_id)
--------------------------------------------------------------

Returns the number of physical changes in Data Model for each type Table, View, Stored procedure and Function, filtered by tenant_id if provided.

**Request**

    No payload

**Response**

   An array of :doc:`models/Item` objects with:

      \- **key** is Either "Table", "View", "Stored procedure" or "Function" |br|
      \- **value** is the number of changes for each type

**Samples**

   .. code-block:: http

      GET /api/dataModel/indicator HTTP/1.1

   Sample response::

      [{
        "key" : "Table",
        "value" : 2,
        "originalValue": null,
        "dataFormat": null,
        "intimePeriodType": null,
        "valueInTimePeriod": 0,
        "function": null
      }, {
        "key" : "View",
        "value" : 1,
        "originalValue": null,
        "dataFormat": null,
        "intimePeriodType": null,
        "valueInTimePeriod": 0,
        "function": null
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

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "data": {
               "result": [
                     {
                        "name": "ProductName",
                        "alias": "",
                        "dataType": "nvarchar",
                        "izendaDataType": "Text",
                        "allowDistinct": true,
                        "visible": true,
                        "filterable": true,
                        "querySourceId": "00000000-0000-0000-0000-000000000000",
                        "parentId": null,
                        "expressionFields": [],
                        "filteredValue": "{}",
                        "type": 0,
                        "groupPosition": 1,
                        "position": 3,
                        "extendedProperties": null,
                        "physicalChange": 0,
                        "approval": 0,
                        "existed": false,
                        "matchedTenant": false,
                        "functionName": null,
                        "expression": null,
                        "fullName": null,
                        "calculatedTree": null,
                        "reportId": null,
                        "originalName": null,
                        "originalId": "00000000-0000-0000-0000-000000000000",
                        "isParameter": false,
                        "isCalculated": false,
                        "hasAggregatedFunction": false,
                        "querySource": null,
                        "querySourceName": null,
                        "categoryName": null,
                        "inaccessible": false,
                        "originalAlias": null,
                        "fullPath": null,
                        "isCheck": false,
                        "id": "156f529f-af43-44b1-82b8-419e4a5ed086",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "acme",
                        "modified": "0001-01-01T00:00:00",
                        "modifiedBy": null
                     },
                     {
                        "name": "@OrderID",
                        "alias": "",
                        "dataType": "int",
                        "izendaDataType": "Int",
                        "allowDistinct": true,
                        "visible": true,
                        "filterable": true,
                        "querySourceId": "00000000-0000-0000-0000-000000000000",
                        "parentId": null,
                        "expressionFields": [],
                        "filteredValue": "{}",
                        "type": 0,
                        "groupPosition": 1,
                        "position": 2,
                        "extendedProperties": null,
                        "physicalChange": 0,
                        "approval": 0,
                        "existed": false,
                        "matchedTenant": false,
                        "functionName": null,
                        "expression": null,
                        "fullName": null,
                        "calculatedTree": null,
                        "reportId": null,
                        "originalName": null,
                        "originalId": "00000000-0000-0000-0000-000000000000",
                        "isParameter": false,
                        "isCalculated": false,
                        "hasAggregatedFunction": false,
                        "querySource": null,
                        "querySourceName": null,
                        "categoryName": null,
                        "inaccessible": false,
                        "originalAlias": null,
                        "fullPath": null,
                        "isCheck": false,
                        "id": "086d5f37-d6b4-4aa4-807e-f6edac2f05b2",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": null,
                        "created": null,
                        "createdBy": "acme",
                        "modified": "0001-01-01T00:00:00",
                        "modifiedBy": null
                     },
               ],
               "pageIndex": 0,
               "pageSize": 10,
               "total": 2,
               "skipItems": 0,
               "isLastPage": true
            },
            "success": true,
            "messages": null
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

      {
         "success": true,
         "messages": null,
         "data": null
      }


POST dataModel/functionOperators/
--------------------------------------------------------------

Returns an array of functions/operators that support calculated fields, filtered by tenant_id if provided.

**Request**

    A :doc:`models/CalculatedFieldFunctionParam` object.

**Response**

    An array of :doc:`models/ReportFunction` objects

**Samples**

   .. code-block:: http

      POST /api/dataModel/functionOperators HTTP/1.1

   Sample Payload::

      {
         "tenantId" : "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "querySourceIds" : [
            "273badf8-d210-494f-a458-25e8f462891f",
            "5cc9e1dd-239c-43ac-8098-6b1c4b9e4478",
            "25ac2696-cabb-41df-a9aa-1b46f46c42f1",
            "f7ae5b5d-628e-4eaf-b8b2-fd823a484a35"
         ],
         "includeCustomJsonFunction" : false
      }

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
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "*",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression * expression",
            "expressionSyntax": "*",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "/",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression / expression",
            "expressionSyntax": "/",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "+",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression + expression",
            "expressionSyntax": "+",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "<",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression < expression",
            "expressionSyntax": "<",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "<=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression <= expression",
            "expressionSyntax": "<=",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "<>",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression <> expression",
            "expressionSyntax": "<>",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression = expression",
            "expressionSyntax": "=",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": ">",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression > expression",
            "expressionSyntax": ">",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": ">=",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "expression >= expression",
            "expressionSyntax": ">=",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "AND",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "boolean_expression AND boolean_expression",
            "expressionSyntax": "AND",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "AVG",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "AVG (expression)",
            "expressionSyntax": "AVG",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "BETWEEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "BETWEEN (test_expression, begin_expression, end_expression)",
            "expressionSyntax": "BETWEEN",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "CASE WHEN...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CASE WHEN (boolean_expression) THEN (result_expression) [...n] [ELSE (else_result_expression)] END",
            "expressionSyntax": "CASE...WHEN...THEN...ELSE...END",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "CASE...WHEN...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CASE (input_expression) WHEN (when_expression) THEN (result_expression) [...n] [ELSE (else_result_expression)] END",
            "expressionSyntax": "CASE...WHEN...THEN...ELSE...END",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "CAST...AS",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CAST (expression AS data_type)",
            "expressionSyntax": "CAST...AS",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "CONVERT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "CONVERT (data_type [( length)], expression[, style])",
            "expressionSyntax": "CONVERT",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "COUNT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "COUNT (expression)",
            "expressionSyntax": "COUNT",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "DATEADD",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEADD (datepart, number, expression)",
            "expressionSyntax": "DATEADD",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "DATEDIFF",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEDIFF (datepart, startdate, enddate)",
            "expressionSyntax": "DATEDIFF",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "DATEPART",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DATEPART (datepart, date)",
            "expressionSyntax": "DATEPART",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "DISTINCT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "DISTINCT (column) or DISTINCT column",
            "expressionSyntax": "DISTINCT",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "GETDATE",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "GETDATE ()",
            "expressionSyntax": "GETDATE",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "IF...THEN...ELSE...END",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "IF (boolean_expression) THEN (true_expression) [ELSE (false_expression)] END",
            "expressionSyntax": "IF...THEN...ELSE...END",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "IIF",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "IIF (boolean_expression, true_expression, [false_expression])",
            "expressionSyntax": "IIF",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "ISNULL",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "ISNULL (check_expression, replacement_value)",
            "expressionSyntax": "ISNULL",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "LEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "LEN (expression)",
            "expressionSyntax": "LEN",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "MAX",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "MAX (expression)",
            "expressionSyntax": "MAX",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "MIN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "MIN (expression)",
            "expressionSyntax": "MIN",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "NOTBETWEEN",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "NOTBETWEEN (test_expression, begin_expression, end_expression)",
            "expressionSyntax": "NOTBETWEEN",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "OR",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "boolean_expression OR boolean_expression",
            "expressionSyntax": "OR",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "ROUND",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "ROUND (expression, length[, function])",
            "expressionSyntax": "ROUND",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "RUNNING AVG",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGAVG (column)",
            "expressionSyntax": "RUNNINGAVG",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "RUNNING COUNT",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGCOUNT (column)",
            "expressionSyntax": "RUNNINGCOUNT",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "RUNNING SUM",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "RUNNINGSUM (column)",
            "expressionSyntax": "RUNNINGSUM",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
         }, {
            "id": null,
            "name": "SUM",
            "expression": null,
            "dataType": null,
            "formatDataType": null,
            "syntax": "SUM (expression)",
            "expressionSyntax": "SUM",
            "isOperator": false,
            "userDefined": false,
            "extendedProperties": {}
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
         "querySourceId": null,
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "criteria": [{
            "key": "All",
            "value": "SQL-North",
            "operation": 1
         }],
         "pageIndex": 1,
         "pageSize": 1,
         "sortOrders": [{
            "key": "DatabaseName",
            "descending": true
         }]
      }

   Sample response::

      {
         "result": [
            {
                  "joinConnectionId": "5e97b5e4-bf85-4be8-8244-cf195bdf4739",
                  "foreignConnectionId": "5e97b5e4-bf85-4be8-8244-cf195bdf4739",
                  "joinQuerySourceAlias": null,
                  "foreignQuerySourceAlias": null,
                  "joinFieldAlias": "",
                  "specifictJoinFieldAlias": null,
                  "foreignFieldAlias": "",
                  "specifictForeignFieldAlias": null,
                  "alias": null,
                  "systemRelationship": true,
                  "joinType": "Inner",
                  "parentRelationshipId": null,
                  "position": null,
                  "relationshipPosition": 0,
                  "relationshipKeyJoins": [],
                  "reportId": null,
                  "foreignAlias": null,
                  "joinQuerySourceUniqueName": null,
                  "joinFieldUniqueName": null,
                  "forgeinQuerySourceUniqueName": null,
                  "forgeinFieldUniqueName": null,
                  "tempId": null,
                  "aliasTempId": null,
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isForeignDataObjectAlias": false,
                  "selectedForeignAlias": "c7341994-3506-4f4a-acd9-96f9b8936ec2_Orders",
                  "joinQuerySourceName": "Order Details",
                  "joinQuerySourceId": "7f9cd714-9b06-4aaf-9a8b-5475ea0cdefc",
                  "joinFieldId": "b577df4a-4419-4229-aefd-ad9caa0543ce",
                  "joinFieldType": null,
                  "foreignQuerySourceName": "Orders",
                  "foreignQuerySourceId": "c7341994-3506-4f4a-acd9-96f9b8936ec2",
                  "foreignFieldId": "da29f67c-6cc5-4aa8-b456-0b192ec07fa1",
                  "foreignFieldType": null,
                  "joinFieldName": "OrderID",
                  "foreignFieldName": "OrderID",
                  "joinDataSourceCategoryId": "31df942e-62be-4cda-8866-7ae7a65365f0",
                  "joinDataSourceCategoryName": "Northwind-MSSQL",
                  "foreignDataSourceCategoryId": "31df942e-62be-4cda-8866-7ae7a65365f0",
                  "foreignDataSourceCategoryName": "Northwind-MSSQL",
                  "comparisonOperator": null,
                  "id": "fb386813-a7f8-4033-862a-4a9cafbad38c",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "Pika Chu",
                  "modified": "2017-09-14T10:12:06.667",
                  "modifiedBy": null
            }
         ],
         "pageIndex": 1,
         "pageSize": 1,
         "total": 7,
         "skipItems": 0,
         "isLastPage": false
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
        "messages" : [],
        "data" : null
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
        "messages" : [],
        "data" : null
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

**Request**

    A :doc:`models/ConnectionColor` object.

**Response**

    An :doc:`models/OperationResult` object.

**Samples**

   .. code-block:: http

      POST api/dataModel/schema/updateConnectionColor HTTP/1.1

   Request Payload::

      {
         "connectionId" : "6cc06e5b-0627-432c-bc33-708b0843c7c7",
         "color": null,
         "modified": "2017-09-15T03:11:24"
      }

   Sample Response::

      {
         "success": true,
         "messages": null,
         "data": null
      }

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

   Sample response in case user has System Admin Permission::

      {
         "success":true
         "messages" : [],
         "data" : null
      }

   Sample response in case user does not have System Admin Permission::

    {
      "message" : "You don't have permission to perform this action",
      "detail" : "NoPermission"
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

   .. code-block:: http

      POST api/dataModel/customQuerySource HTTP/1.1

   Request Payload::

      {
         "name": "test",
         "connectionId": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
         "categoryId": "94454a0a-17a2-49e5-bebf-9c0d07d95587",
         "customDefinition": "Select OrderID\nfrom orders"
      }

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         {
            "realName": "test",
            "id": "193a0a94-decf-4217-9e0c-1956f0335f59",
            "name": "northwind.test",
            "type": "View",
            "parentQuerySourceId": null,
            "categoryId": "94454a0a-17a2-49e5-bebf-9c0d07d95587",
            "selected": true,
            "deleted": false,
            "connectionId": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
            "connectionName": null,
            "childs": null,
            "dataSourceCategoryId": null,
            "dataSourceCategoryName": null,
            "alias": "",
            "originalAlias": null,
            "querySourceFields": [
               {
                     "name": "OrderID",
                     "alias": "",
                     "dataType": "INT",
                     "izendaDataType": "Numeric",
                     "allowDistinct": true,
                     "visible": false,
                     "filterable": false,
                     "querySourceId": "193a0a94-decf-4217-9e0c-1956f0335f59",
                     "parentId": null,
                     "expressionFields": [],
                     "filteredValue": "",
                     "type": 0,
                     "groupPosition": 0,
                     "position": 1,
                     "extendedProperties": "",
                     "physicalChange": 0,
                     "approval": 0,
                     "existed": false,
                     "matchedTenant": false,
                     "functionName": null,
                     "expression": null,
                     "fullName": null,
                     "calculatedTree": null,
                     "reportId": null,
                     "originalName": null,
                     "originalId": "00000000-0000-0000-0000-000000000000",
                     "isParameter": false,
                     "isCalculated": false,
                     "hasAggregatedFunction": false,
                     "querySource": null,
                     "querySourceName": null,
                     "categoryName": null,
                     "inaccessible": false,
                     "originalAlias": null,
                     "fullPath": null,
                     "isCheck": false,
                     "id": "269987d3-7a92-4ba4-9e99-3829905f471b",
                     "state": 0,
                     "deleted": false,
                     "inserted": true,
                     "version": null,
                     "created": null,
                     "createdBy": "System5 Admin5",
                     "modified": "2017-09-15T04:52:03.0678276",
                     "modifiedBy": null
               }
            ],
            "querySourceCategoryName": null,
            "querySourceCategory": null,
            "modified": "2017-09-15T04:52:02.9811771",
            "extendedProperties": null,
            "physicalChange": 0,
            "approval": 0,
            "existed": false,
            "checked": false,
            "belongToCopiedReport": false,
            "customDefinition": "Select OrderID\nfrom orders",
            "isCustomQuerySource": true,
            "isCheck": false,
            "disabled": false,
            "fullPath": null,
            "indeterminate": false,
            "numOfChilds": 0,
            "numOfCheckedChilds": 0
         }

POST dataModel/validateCustomQuerySource
--------------------------------------------------------------

Validates that name of custom query source is unique.

**Request**

    A :doc:`models/QuerySource` object, with **name** and **categoryId** fields populated.

**Response**

   An :doc:`models/OperationResult` object, with **success** field true if View Name is unique and other custom view contents are valid.

**Samples**

   .. code-block:: http

      POST api/dataModel/validateCustomQuerySource HTTP/1.1

   Request Payload::

      {
        "name": "Test",
        "connectionId": "3562497d-07a1-4a0a-823d-811b8a098d73",
        "categoryId": "533f001b-88ef-46d5-b0c1-69b774c81aba",
        "customDefinition": "SELECT customerID,employeeID\nFROM  Orders "
      }

   Sample response::

      {
        "success": true,
        "confirmation": false,
        "messages": []
      }

POST dataModel/deleteCustomQuerySource
--------------------------------------------------------------

Deletes a custom query source.

**Request**

    A :doc:`models/QuerySource` object, with **id** field populated.

**Response**

   An :doc:`models/OperationResult` object, with **success** true if the deletion is successful.

**Samples**

   .. code-block:: http

      POST api/dataModel/deleteCustomQuerySource HTTP/1.1

   Request Payload::

      {"id":"e26a908a-5d76-473e-a364-91afe9147023"}

   Sample Response::

      {
         "success": true
      }

GET dataModel/querySource/{query_source_id}
--------------------------------------------------------------

Returns the query source specified by query_source_id.

**Request**

    No payload

**Response**

   A :doc:`models/QuerySource` object.

**Samples**

   .. code-block:: http

      GET api/dataModel/querySource/c7341994-3506-4f4a-acd9-96f9b8936ec2 HTTP/1.1

   Sample Response::

      {
         "realName": null,
         "id": "c7341994-3506-4f4a-acd9-96f9b8936ec2",
         "name": "Orders",
         "type": "Table",
         "parentQuerySourceId": null,
         "categoryId": "942c529a-38c7-4ffc-9e46-044c3f364130",
         "selected": true,
         "deleted": false,
         "connectionId": "00000000-0000-0000-0000-000000000000",
         "connectionName": null,
         "childs": null,
         "dataSourceCategoryId": "31df942e-62be-4cda-8866-7ae7a65365f0",
         "dataSourceCategoryName": null,
         "alias": null,
         "originalAlias": null,
         "querySourceFields": [],
         "querySourceCategoryName": null,
         "querySourceCategory": null,
         "modified": "2017-09-15T03:57:38",
         "extendedProperties": null,
         "physicalChange": 0,
         "approval": 0,
         "existed": false,
         "checked": false,
         "belongToCopiedReport": false,
         "customDefinition": null,
         "isCustomQuerySource": false,
         "isCheck": false,
         "disabled": false,
         "fullPath": null,
         "indeterminate": false,
         "numOfChilds": 0,
         "numOfCheckedChilds": 0
      }
