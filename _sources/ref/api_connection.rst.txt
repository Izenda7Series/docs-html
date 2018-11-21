

============================
Connection APIs
============================

The **Connection String** page allows user to

* manage the list of connections
* select individual items from these connections to be visible in reports

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 35 40
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET systemSetting/databaseSetup`_
     - Returns whether the system database has been set up.
     - On Front-end load
   * - `GET dataAdaptor`_
     - Returns an array of database server types currently supported for queries. |br|
       See also: :ref:`GET_databaseSetup/supportedDatabaseType`
     - Settings > Data Setup > Connection String > populate Data Server Type box
   * - `POST connection/verify`_
     - Validates a connection string. |br|
       See also: :ref:`POST_databaseSetup/testConnection`
     - Settings > Data Setup > Connection String > Test
   * - `POST connection/loadRemoteSchema`_
     - Returns an enumeration of all supported objects (query sources) from a connection string.
     - Settings > Data Setup > Connection String > Test > Connect
   * - `POST connection`_
     - Adds a new connection or updates an existing one. |br|
       Only visible query sources should be saved.
     - Settings > Data Setup > Connection String > Save
   * - `GET connection/(tenant_id)`_
     - Returns an array of connections (filtered by tenant_id if given).
     - Settings > Data Setup > Connection String, for a specific tenant
   * - `GET connection/detail/{connection_id}`_
     - Returns the details of the connection specified by the {connection_id} value.
     - Settings > Data Setup > Connection String > select an existing connection
   * - `GET connection/basicInfo/(tenant_id)`_
     - Returns an array of id and name of connections (filtered by tenant_id if given).
     - To be updated
   * - `GET connection/detailInfo/(tenant_id)/{loadField}`_
     - Returns an array of connection details.
     - To be updated
   * - `POST connection/detailInfo`_
     - Returns an array of connection details with paging.
     - To be updated
   * - `POST connection/invisible/{connection_id}`_
     - Hides from Data Model and Reports all query sources in the connection specified by the {connection_id} value.
     - Settings > Data Setup > Connection String > click Visibility icon of a visible connection
   * - `POST connection/visible/{connection_id}`_
     - Restores the visibility of all query sources in the connection specified by the {connection_id} value.
     - Settings > Data Setup > Connection String > click Visibility icon of a hidden connection
   * - `DELETE connection/{connection_id}`_
     - Deletes the connection specified by the {connection_id} value.
     - Settings > Data Setup > Connection String > click Delete icon of a connection
   * - `POST connection/reloadRemoteSchema`_
     - Returns an enumeration of all supported objects (query sources) from an existing connection with detected changes.
     - Settings > Data Setup > Connection String > Reconnect an existing connection
   * - `POST connection/databaseName`_
     - Returns the database name from a connection string.
     - Settings > Data Setup > Connection String > Test
   * - `POST connection/validateSchema`_
     - Returns true if remote schema has not changed, otherwise returns false.
     - To be updated
   * - GET connection/systemIndicator/(tenantId)
     - Returns the number of changes in Connection String and Data Model (filtered by tenant_id if provided). |br|
     
       .. warning::
          
          Obsolete, use :ref:`GET_systemSetting/systemIndicator/(tenant_id)` instead
     - Not used
   * - `GET connection/visible/(tenant_id)/count`_
     - Returns the count of visible connections, filtered by tenant_id if available.
     - Settings > Data Setup > Connection String
   * - `POST connection/loadDistinctConnections`_
     - Returns an array of distinct connections (by server type and database name) from a list of tenant ids.
     - Settings > Data Setup > Copy Management

GET systemSetting/databaseSetup
--------------------------------------------------------------

Returns whether the system database has been set up.

**Request**

    No payload

**Response**

    * true if the system database has been set up.
    * false if not.

**Samples**

   .. code-block:: http

      GET /api/systemSetting/databaseSetup HTTP/1.1

   Response when system database has been setup::

      true

.. _GET_dataAdaptor:

GET dataAdaptor
--------------------------------------------------------------

Returns an array of database server types currently supported for queries. |br|
See also: ``GET databaseSetup/SupportedDatabaseType``

**Request**

    No payload

**Response**

    An array of objects

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **id** |br|
             string (GUID)
          -  The id of the connection
          -  Example: ``572bd576-8c92-4901-ab2a-b16e38144813``
       *  -  **shortName** |br|
             string
          -  The short name of the database server type
          -
       *  -  **name** |br|
             string
          -  The display name of the database server type
          -

**Samples**

   .. code-block:: http

      GET /api/dataAdaptor HTTP/1.1

   Sample response::

      [
        {
           "name" : "[AZSQL] AzureSQL",
           "shortName" : "AZSQL",
           "id" : "d968e96f-91dc-414d-9fd8-aef2926c9a18"
        }, {
           "name" : "[MYSQL] MySQL",
           "shortName" : "MYSQL",
           "id" : "3d4916d1-5a41-4b94-874f-5bedacb89656"
        }, {
           "name" : "[ORACL] Oracle",
           "shortName" : "ORACL",
           "id" : "93942448-c715-4f98-85e2-9292ed7ca4bc"
        }, {
           "name" : "[PGSQL] PostgreSQL",
           "shortName" : "PGSQL",
           "id" : "f2638ed5-70e5-47da-a052-4da0c1888fcf"
        }, {
           "name" : "[MSSQL] SQLServer",
           "shortName" : "MSSQL",
           "id" : "572bd576-8c92-4901-ab2a-b16e38144813"
        }
      ]

.. _POST_connection/verify:

POST connection/verify
--------------------------------------------------------------

Validates a connection string. |br|
See also: :ref:`POST_databaseSetup/testConnection`

**Request**

    Payload: a :doc:`models/DBSetupInfo` object

**Response**

    A :doc:`models/ConnectionVerificationResult` object

**Samples**

   .. code-block:: http

      POST /api/connection/verify HTTP/1.1

   Request payload::

      {
        "ServerTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
        "ConnectionString" : "server=host01\instance01;database=db01;User Id=user01;Password=secret;"
      }

   Successful response::

      {
        "serverNotValid" : false,
        "databaseNotValid" : false,
        "loginFail" : false,
        "hasValidLicense" : false,
        "success" : true,
        "messages" : []
      }

.. _POST_connection/loadRemoteSchema:

POST connection/loadRemoteSchema
--------------------------------------------------------------

Returns an enumeration of all supported objects (query sources) from a connection string.

**Request**

    Payload: a :doc:`models/SchemaRequest` object

**Response**

    A :doc:`models/SchemaResult` object

**Samples**

   .. code-block:: http

      POST /api/connection/loadRemoteSchema HTTP/1.1

   Request payload::

      {
        "connectionString" : "1aBcD+=",
        "serverType" : "d968e96f-91dc-414d-9fd8-aef2926c9a18"
      }

   Successful response::

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

.. _POST_connection:

POST connection
--------------------------------------------------------------

Adds a new connection or updates an existing one. |br|
Only visible query sources should be saved. |br| |br|

The connection string will be validated before saving.

**Request**

    Payload: a :doc:`models/Connection` object

**Response**

    A :doc:`models/SaveConnectionStatus` object

**Samples**

   .. code-block:: http

      POST /api/connection HTTP/1.1

   Request payload for a new connection::

      {
        "id" : null,
        "name" : "db01",
        "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
        "connectionString" : "server=izenda01\\DB_INSTANCE;database=db01;User Id=user01;Password=secret;",
        "visible" : true,
        "dBSource" : {
           "querySources" : []
        }
      }

   Sample response (in case user has System Admin Permission)::

      {
        "success" : true,
        "connectionId" : "f5180bc0-7c07-48db-b672-e66a5adde027",
        "connectionErrors" : []
      }

   Response in case user does not have System Admin Permission::

      {
         "message" : "You don't have permission to perform this action",
         "detail" : "NoPermission"
      }

GET connection/(tenant_id)
--------------------------------------------------------------

Returns an array of connections (filtered by tenant_id if given).

**Request**

    No payload

**Response**

    An array of :doc:`models/Connection` objects

    .. note::
      
      **dBSource** field is not populated in this API, use `GET connection/detail/{connection_id}`_ instead.

**Samples**

   .. code-block:: http

      GET /api/connection HTTP/1.1

   Sample response::

      [{
           "id" : "89e91284-6546-44d0-8de0-f8f666a590ea",
           "name" : "Northwind",
           "serverType" : "d968e96f-91dc-414d-9fd8-aef2926c9a18",
           "serverTypeName" : "AZSQL",
           "connectionString" : "1aBcD+==",
           "visible" : true,
           "deleted" : false,
           "relateToConnectionId" : null,
           "tenantId" : null,
           "dBSource" : null,
           "relationships" : null,
           "physicalChange" : 0
        }, {
           "id" : "2f7e216b-8637-49e2-8391-cea682e4c32f",
           "name" : "oAdventure",
           "serverType" : "d968e96f-91dc-414d-9fd8-aef2926c9a18",
           "serverTypeName" : "AZSQL",
           "connectionString" : "1aBcD+==",
           "visible" : true,
           "deleted" : false,
           "relateToConnectionId" : null,
           "tenantId" : null,
           "dBSource" : null,
           "relationships" : null,
           "physicalChange" : 0
        }
      ]

GET connection/detail/{connection_id}
--------------------------------------------------------------

Returns the details of the connection specified by the {connection_id} value.

These include the connection fields and the query sources inside.

**Request**

    No payload

**Response**

    A :doc:`models/ConnectionResult` object

**Samples**

   .. code-block:: http

      POST /api/connection/detail/2f7e216b-8637-49e2-8391-cea682e4c32f HTTP/1.1

   Sample response::

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

.. _GET_connection/basicInfo/(tenant_id):

GET connection/basicInfo/(tenant_id)
--------------------------------------------------------------

Returns an array of id and name of connections (filtered by tenant_id if given).

**Request**

    No payload

**Response**

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

      GET /api/connection/basicInfo HTTP/1.1

   Sample response::

      [{
         "key": "1a65445b-2779-4825-8c0b-2491eaa87a46",
         "value": "AdventureWorks2008R2"
      }, {
         "key": "dda3633e-659f-4e88-9955-4e20bded686c",
         "value": "Northwind"
      }]

GET connection/detailInfo/(tenant_id)/{loadField}
--------------------------------------------------------------

Returns an array of connection details.

**Request**

    No payload
    
    **loadField**:

    * true: return query source field data
    * false: do not return query source field data
    
    **Query String**:

    loadStoreProcSchema=boolean&loadInactiveConnections=boolean |br| &removeEmptyParent=boolean&defaultChecked=boolean

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **hashCode** |br|
             string
          -  The hash code of the connections
          -
       *  -  **connections** |br|
             string
          -  An array of :doc:`models/Connection` objects
          -

**Samples**

   .. code-block:: http

      GET /api/connection/detailInfo/f6d1638a-df71-4f33-b2a8-a2510a7dbb40/true&loadStoreProcSchema=false HTTP/1.1

   Sample response::

      {
        "hashCode": "8d7b2626230999de7f6edb5c7ca",
        "connections": [
          {
            "id": "b6cff8c7-fd41-47a3-9a55-7b332344792c",
            "name": "Northwind",
            "serverTypeId": "572bd576-8c92-4901-ab2a-b16e38144813",
            "serverTypeName": "MSSQL",
            "connectionString": "123abc=",
            "visible": true,
            "deleted": false,
            "relateToConnectionId": null,
            "tenantId": "f6d1638a-df71-4f33-b2a8-a2510a7dbb40",
            "dbSource": {
              "querySources": [
                {
                 "id": "cc61e681-f6d1-4784-97c7-c387af2d8ff1",
                 "name": "dbo",
                 "parentCategoryId": null,
                 "connectionId": "b6cff8c7-fd41-47a3-9a55-7b332344792c",
                 "querySources": [
                    {
                      "realName": null,
                      "id": "0ad3e706-b775-411d-bcc5-acf615d9f4ce",
                      "name": "CustOrderHist",
                      "type": "Stored Procedure",
                      "parentQuerySourceId": null,
                      "categoryId": "cc61e681-f6d1-4784-97c7-c387af2d8ff1",
                      "selected": false,
                      "deleted": false,
                      "connectionId": "00000000-0000-0000-0000-000000000000",
                      "connectionName": null,
                      "childs": null,
                      "dataSourceCategoryId": null,
                      "dataSourceCategoryName": null,
                      "alias": null,
                      "querySourceFields": [
                        {
                          "name": "@CustomerID",
                          "alias": "",
                          "dataType": "nchar",
                          "izendaDataType": "Text",
                          "allowDistinct": false,
                          "visible": true,
                          "filterable": true,
                          "querySourceId": "0ad3e706-b775-411d-bcc5-acf615d9f4ce",
                          "parentId": null,
                          "expressionFields": [],
                          "filteredValue": "",
                          "type": 1,
                          "groupPosition": 0,
                          "position": 1,
                          "extendedProperties": null,
                          "physicalChange": -1,
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
                          "isParameter": true,
                          "isCalculated": false,
                          "hasAggregatedFunction": false,
                          "querySource": null,
                          "querySourceName": null,
                          "categoryName": null,
                          "inaccessible": false,
                          "fullPath": null,
                          "id": "f8e8651b-64c7-454f-81c2-ca7a5866d4e5",
                          "state": 0,
                          "deleted": false,
                          "inserted": true,
                          "version": null,
                          "created": null,
                          "createdBy": "4e9fd487-56b6-4ee7-856a-1428ea4d0739",
                          "modified": "2016-11-02T10:52:05.723",
                          "modifiedBy": null
                        }
                      ],
                      "querySourceCategoryName": "dbo",
                      "querySourceCategory": null,
                      "modified": "2016-11-02T10:52:05.707",
                      "extendedProperties": "{\"Dynamic\":false,\"Static\":false}",
                      "physicalChange": -1,
                      "approval": 0,
                      "existed": false,
                      "checked": true,
                      "fullPath": null
                    }
                 ]
                }
              ]
            }
          }
        ]
      }

POST connection/detailInfo
--------------------------------------------------------------

Returns an array of connection details with paging.

**Request**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  NULL
          -  Description
          -  Note
       *  -  **tenantId** |br|
             string (GUID)
          -  Y
          -  The id of the tenant
          -
       *  -  **loadStoreProcSchema** |br|
             boolean
          -  Y
          -  Whether to load schema of stored procedures
          -
       *  -  **loadInactiveConnections** |br|
             boolean
          -  Y
          -  Whether to load data of inactive connections
          -
       *  -  **removeEmptyParent** |br|
             boolean
          -  Y
          -  Whether to remove empty parents
          -
       *  -  **defaultChecked** |br|
             boolean
          -  Y
          -  Whether to tick the copy check-box by default, to be used in Copy Management
          -
       *  -  **loadField** |br|
             boolean
          -  Y
          -  Whether to load data of query source fields
          -
       *  -  **pagedIndex** |br|
             integer
          -  Y
          -  The index of the page
          -
       *  -  **pagedSize** |br|
             integer
          -  Y
          -  The size of the page
          -

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **hashCode** |br|
             string
          -  The hash code of the connections
          -
       *  -  **connections** |br|
             string
          -  An array of :doc:`models/Connection` objects
          -
       *  -  **maxNumberOfRecords** |br|
             integer
          -  The total number of records returned
          -

**Samples**

   .. code-block:: http

      POST /api/connection/detailInfo HTTP/1.1

   Request payload::

      {
        "tenantId": "45c747c5-a11a-48f4-b966-14819a07450f"
      }

   Sample response::

      {
       "hashCode": "27ab6cfbfec1bc319cde19a907a",
       "connections": [],
       "maxNumberOfRecords": 0
      }

POST connection/invisible/{connection_id}
--------------------------------------------------------------

Hides from Data Model and Reports all query sources in the connection specified by the {connection_id} value.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field populated

**Samples**

   .. code-block:: http

      POST /api/connection/invisible/866d8a41-3bd8-48d5-bc1e-9e4488c171c3 HTTP/1.1

   Successful response (in case user has System Admin Permission)::

      {
         "success": true,
         "messages": null
      }

   Response in case user does not have System Admin Permission::

      {
         "message" : "You don't have permission to perform this action",
         "detail" : "NoPermission"
      }


POST connection/visible/{connection_id}
--------------------------------------------------------------

Restores the visibility of all query sources in the connection specified by the {connection_id} value.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field populated

**Samples**

   .. code-block:: http

      POST /api/connection/visible/866d8a41-3bd8-48d5-bc1e-9e4488c171c3 HTTP/1.1

   Sample response::

      {
         "success": true,
         "messages": null
      }

DELETE connection/{connection_id}
--------------------------------------------------------------

Deletes the connection specified by the {connection_id} value.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field populated

**Samples**

   .. code-block:: http

      DELETE /api/connection/f5180bc0-7c07-48db-b672-e66a5adde027 HTTP/1.1

   Successful response (in case user has System Admin Permission)::

      {
        "success" : true,
        "messages" : null
      }

   Response in case user does not have System Asmin Permission)::

      {
         "message" : "You don't have permission to perform this action",
         "detail" : "NoPermission"
      }

POST connection/reloadRemoteSchema
--------------------------------------------------------------

Returns an enumeration of all supported objects (query sources) from an existing connection with detected changes.

**Request**

    Payload: a :doc:`models/SchemaRequest` object

**Response**

    A :doc:`models/SchemaResult` object

**Samples**

   .. code-block:: http

      POST /api/connection/reloadRemoteSchema HTTP/1.1

   Request payload::

      {
        "connectionId" : "d91ee45e-f168-441d-81eb-7878cb2fa2ce",
        "connectionString" : "1aBcD+=",
        "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813"
      }

   Successful response::

      {
        "dBSource" : {
           "querySources" : [{
                 "id" : "024248ec-0058-49d3-a07c-f987bd300cae",
                 "name" : "dbo",
                 "parentCategoryId" : null,
                 "connectionId" : "d91ee45e-f168-441d-81eb-7878cb2fa2ce",
                 "querySources" : [{
                       "id" : "bf21830d-bb38-4b17-853b-26df0cb56549",
                       "name" : "Table01",
                       "type" : "Table",
                       "parentQuerySourceId" : null,
                       "categoryId" : "024248ec-0058-49d3-a07c-f987bd300cae",
                       "selected" : true,
                       "connectionId" : "00000000-0000-0000-0000-000000000000",
                       "connectionName" : null,
                       "childs" : null,
                       "dataSourceCategoryId" : null,
                       "dataSourceCategoryName" : null,
                       "alias" : null,
                       "querySourceFields" : [{
                             "id" : "69460143-6fd3-496c-8ddf-32e955801007",
                             "name" : "TableId",
                             "alias" : "",
                             "dataType" : "nvarchar",
                             "visible" : false,
                             "filterable" : false,
                             "deleted" : false,
                             "querySourceId" : "bf21830d-bb38-4b17-853b-26df0cb56549",
                             "parentId" : null,
                             "children" : null,
                             "modified" : "2016-04-04T08:47:32.0000000+07:00",
                             "filteredValue" : "",
                             "type" : 0,
                             "position" : 0,
                             "extendedProperties" : "",
                             "physicalChange" : 0,
                             "approval" : 0,
                             "existed" : true,
                             "matchedTenant" : false
                          }
                       ],
                       "querySourceCategory" : null,
                       "modified" : null,
                       "extendedProperties" : null,
                       "physicalChange" : 0,
                       "approval" : 0,
                       "existed" : true
                    }
                 ],
                 "childs" : null,
                 "connection" : null,
                 "physicalChange" : 0,
                 "existed" : true
              }
           ]
        },
        "differentConnectionAndSchema" : false,
        "success" : true,
        "messages" : null
      }

POST connection/databaseName
--------------------------------------------------------------

Returns the database name from a connection string.

**Request**

    Payload: a :doc:`models/DBSetupInfo` object

**Response**

    * The database name if success
    * An empty string in case of error

**Samples**

   .. code-block:: http

      POST /api/connection/databaseName HTTP/1.1

   Request payload::

      {
        "ServerTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
        "ConnectionString" : "server=host01\instance01;database=db01;User Id=user01;Password=secret;"
      }

   Successful response::

      "db01"

POST connection/validateSchema
--------------------------------------------------------------

Returns true if remote schema has not changed, otherwise returns false.

**Request**

    Payload: a :doc:`models/Connection` object

**Response**

    A boolean value

**Samples**

   .. code-block:: http

      POST /api/connection/validateSchema HTTP/1.1

   Request payload::

      {
        "id" : "dda3633e-659f-4e88-9955-4e20bded686c",
        "serverType" : "572bd576-8c92-4901-ab2a-b16e38144813",
        "connectionString" : "1aBcD+="
      }

   Sample response::

      true

GET connection/visible/(tenant_id)/count
--------------------------------------------------------------

Returns the count of visible connections, filtered by tenant_id if available.

**Request**

    No payload

**Response**

    The number of connections

**Samples**

   .. code-block:: http

      GET /api/connection/visible/count HTTP/1.1

   Sample response (in case user has System Asmin Permission)::

      2

   Reponse in case user does not have System Admin Permission::

      {
         "message" : "You don't have permission to perform this action",
         "detail" : "NoPermission"
      }


.. _POST_connection/loadDistinctConnections:

POST connection/loadDistinctConnections
--------------------------------------------------------------

Returns an array of distinct connections (by server type and database name) from a list of tenant ids.

**Request**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **tenantIds** |br|
             array of strings
          -  An array of string (GUID) values.
          -

**Response**

    An array of :doc:`models/Connection` objects

**Samples**

   .. code-block:: http

      POST /api/connection/loadDistinctConnections HTTP/1.1

   Request payload::

      {
        "tenantIds" : ["e9e54aaf-64d8-4dbd-88c4-642f51ba16ec"]
      }

   Sample response::

      [{
           "id" : "3cd79317-5d1b-4842-93d7-47abae6e0273",
           "name" : "Northwind",
           "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
           "serverTypeName" : "MSSQL",
           "connectionString" : "4d8jRon2cmwd8K1blELZB7RtRYUM76oW5ZOYxEcE4eCRy19pnCeeyM4ZFpAxX+dwIsv+p+3JKbZbJCdDyj6XXOlS88wnw9pNBuLfk3SxFJM=",
           "visible" : true,
           "deleted" : false,
           "relateToConnectionId" : null,
           "tenantId" : "e9e54aaf-64d8-4dbd-88c4-642f51ba16ec",
           "dbSource" : {
              "querySources" : []
           },
           "relationships" : null,
           "physicalChange" : 0,
           "checked" : false,
           "databaseName" : "Northwind",
           "fullPath" : null
        }
      ]
