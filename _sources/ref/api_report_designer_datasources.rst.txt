

==================================
Report Designer Data Sources APIs
==================================

The **Report Designer** page allows user to

-  create a report
-  select report data sources
-  create report filters
-  design report layout
-  set up report schedule

This page documents the APIs related to data sources, relationships and fields.

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 35 40
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET report/dataSourceCategory/(tenant_id)`_
     - Returns data sources and data source fields grouped by data source categories (filtered by tenant_id if provided). |br| |br|
       See also: :ref:`POST_advancedSetting/category` and :ref:`POST_dataModel` for APIs that create these data source categories.
     - Not used
   * - `POST report/loadDataSourceCategory`_
     - For a report, returns both selected, visible data sources and other available data sources, all grouped by data source categories. |br| |br|
       Compared with `GET report/dataSourceCategory/(tenant_id)`_, this API sets the "selected" and "visible" flags.
     - Report Designer > Data Source
   * - `POST report/loadQuerySources`_
     - Returns details for a list of query sources and a list of related query sources.
     - 
       \- Switch to Simple mode |br|
       \- Create a new report OR open an existing report |br|
       \- In Data Source tab, choose a data source |br|
       \- OR switch from the others to Data Source tab
   * - `POST report/loadRelatedQuerySources`_
     - Returns list of related query source categories.

       .. versionadded:: 2.5.0
     - 
   * - `POST report/loadJoinQuerySourceByRelationship`_
     - Get join query source by relationship

       .. versionadded:: 2.6.0
     - To be updated
   * - `POST report/loadRelationships`_
     - Returns an updated list of relationships from an existing report together with an updated list of data sources.
     - Report Designer for an existing report
   * - `POST report/validateRelationshipSyntax`_
     - Validates relationship syntax.
     - Report Designer > Data Source > Validate Syntax
   * - `POST report/validateCycleRelationships`_
     - Validates cycle relationships

       .. versionadded:: 2.6.0
     - In Report Designer, switch from Data Source tab to the others.
       Report Designer > Data Source > Validate Syntax
   * - `POST report/detectRelationshipsChange`_
     - Detects if any relationship should be removed because of changes in data sources.
     - Not used
   * - `POST report/availableQuerySourceFields`_
     - Returns a list of data source fields in selected query sources of a report.
     - Report Designer > Data Source > select a data source
   * - `GET report/availableReportMappingFields/{report_id}`_
     - Returns a list of data source fields, alias fields, and calculated fields in selected query sources of a report.
     - To be updated
   * - `GET report/fieldProperties/{query_source_field_id}`_
     - Returns the properties of query source field specified by query_source_field_id.
     - 
   * - `POST report/loadDataSourceFields`_
     - Returns the list fields of selected query source.
       
       .. versionadded:: 2.5.0
     - To be updated
   * - `POST report/calculatedField`_
     - Saves a calculated field after validating name duplication (does not validate the expression).
     - Report Designer > Fields > Add Calculated Field > OK
   * - `GET report/calculatedField/{calculated_field_id}`_
     - Returns the calculated field specified by calculated_field_id.
     - To be updated
   * - `GET report/hasReportUseCalculatedField/{calculated_field_id}`_
     - Returns true if the calculated field is being used in any report part or report filter.
     - To be updated
   * - `GET report/hasReportUseRelationship/{relationship_id}`_
     - Returns true if the relationship is being used in report.
     - To be updated
   * - `POST report/deleteReportCalculatedField`_
     - Removes a calculated field from report.
     - Report Designer > Fields > Delete icon on a calculated field
   * - `POST report/loadDynamicDataSourceCategory`_
     - Returns list of dynamic report data source category.

       .. versionadded:: 2.5.0
     - To be updated
   * - `POST report/loadPartialDataSourceCategory`_
     - Returns list of report data source category with paging.

       .. versionadded:: 2.5.0
     - In Report Designer when switching from the others to Data Source tab.

GET report/dataSourceCategory/(tenant_id)
------------------------------------------------

Returns data sources and data source fields grouped by data source categories (filtered by tenant_id if provided).

See also: :ref:`POST_advancedSetting/category` and :ref:`POST_dataModel` for APIs that create these data source categories.

**Request**

    No payload

**Response**

    An array of :doc:`models/ReportDataSourceCategory` objects

**Samples**

   .. code-block:: http

      POST /api/report/dataSourceCategory HTTP/1.1

   Sample response::

      [{
         "id": "f28d7175-4cef-478e-b914-ae075c3c33b8",
         "name": "Data Source Category 1",
         "querySource": [{
            "id": "ffd40590-aa27-4a14-8ebf-f32a0567bc08",
            "name": "Department",
            "type": "Table",
            "selected": false,
            "visible": true,
            "querySourceCategoryName": "HumanResources",
            "connectionName": "AdventureWorks2008R2",
            "isAlias": false,
            "fields": [{
                 "id": "5da4090d-9b31-433c-b9bb-e9e82fcc92a8",
                 "name": "DepartmentID",
                 "alias": null,
                 "dataType": "smallint",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "{\"PrimaryKey\":true}",
                 "isParameter": false,
                 "allowDistinct": false
            }, {
                 "id": "2636eeb4-cb65-48f4-9da6-2bfe5cd0659a",
                 "name": "Name",
                 "alias": null,
                 "dataType": "nvarchar",
                 "unitDataType": "Text",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }]
         }]
      }, {
         "id": "00000000-0000-0000-0000-000000000000",
         "name": null,
         "querySource": [{
            "id": "06cc2448-5a09-44db-99b5-5fb7c8863be6",
            "name": "vEmployee",
            "type": "View",
            "selected": false,
            "visible": true,
            "querySourceCategoryName": "HumanResources",
            "connectionName": "AdventureWorks2008R2",
            "isAlias": false,
            "fields": [{
                 "id": "c8840bd0-572f-4243-a840-2d1d20402a43",
                 "name": "BusinessEntityID",
                 "alias": null,
                 "dataType": "int",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }, {
                 "id": "0284b8a5-f97e-4496-9f2e-dd2a6766153a",
                 "name": "EmailAddress",
                 "alias": null,
                 "dataType": "nvarchar",
                 "unitDataType": "Text",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }]
         }]
      }]

.. _POST_report/loadDataSourceCategory:

POST report/loadDataSourceCategory
------------------------------------------------

For a report, returns both selected, visible data sources and other available data sources, all grouped by data source categories.

Compared with `GET report/dataSourceCategory/(tenant_id)`_, this API sets the "selected" and "visible" flags.

**Request**

    Payload: a :doc:`models/ReportDataSourceParameter` object

**Response**

    An array of :doc:`models/ReportDataSourceCategory` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadDataSourceCategory HTTP/1.1

   Request payload::

      {
        "tenantId" : null,
        "reportKey" : {
           "key" : "f53b65ba-4d27-45c9-930e-156538f30531",
           "tenantId" : null
        }
      }

   Response::

      [{
         "id": "f28d7175-4cef-478e-b914-ae075c3c33b8",
         "name": "Data Source Category 1",
         "querySource": [{
            "id": "ffd40590-aa27-4a14-8ebf-f32a0567bc08",
            "name": "Department",
            "type": "Table",
            "selected": true,
            "visible": false,
            "querySourceCategoryName": "HumanResources",
            "connectionName": "AdventureWorks2008R2",
            "isAlias": false,
            "fields": [{
                 "id": "5da4090d-9b31-433c-b9bb-e9e82fcc92a8",
                 "name": "DepartmentID",
                 "alias": null,
                 "dataType": "smallint",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "{\"PrimaryKey\":true}",
                 "isParameter": false,
                 "allowDistinct": false
            }, {
                 "id": "2636eeb4-cb65-48f4-9da6-2bfe5cd0659a",
                 "name": "Name",
                 "alias": null,
                 "dataType": "nvarchar",
                 "unitDataType": "Text",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }]
         }]
      }, {
         "id": "00000000-0000-0000-0000-000000000000",
         "name": null,
         "querySource": [{
            "id": "06cc2448-5a09-44db-99b5-5fb7c8863be6",
            "name": "vEmployee",
            "type": "View",
            "selected": false,
            "visible": true,
            "querySourceCategoryName": "HumanResources",
            "connectionName": "AdventureWorks2008R2",
            "isAlias": false,
            "fields": [{
                 "id": "c8840bd0-572f-4243-a840-2d1d20402a43",
                 "name": "BusinessEntityID",
                 "alias": null,
                 "dataType": "int",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }, {
                 "id": "0284b8a5-f97e-4496-9f2e-dd2a6766153a",
                 "name": "EmailAddress",
                 "alias": null,
                 "dataType": "nvarchar",
                 "unitDataType": "Text",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": "",
                 "isParameter": false,
                 "allowDistinct": false
            }]
         }]
      }]

POST report/loadQuerySources
------------------------------------------------

Returns details for a list of query sources and a list of related query sources.

**Request**

    Payload: a :doc:`models/ReportSelectedPagedRequest` object

    .. note::
       
       The keys for :doc:`models/SearchCriteria` that this API support: |br|
       - All |br|
       - Category |br|
       - DatabaseName |br|
       - DataSourceName |br|
       - DataSourceAlias |br|
       - ColumnName |br|
       - DataType |br|
       - ColumnAlias |br|
       - SchemaName |br|
       - DataObject |br|
       - DataObjectType

**Response**

    A :doc:`models/ReportSelectedQuerySourceResult` object

**Samples**

   .. code-block:: http

      POST /api/report/loadQuerySources HTTP/1.1

   Request payload::

      {
         "querySources": [{
            "querySourceId": "126c58e7-e061-4f27-83c8-47c9135dde2c",
            "selected": true,
            "physicalChange": 0,
            "state": 2
         }],
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "criteria": [{
            "key": "All",
            "value": "",
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
         "relatedQuerySources": [{
            "querySourceId": "126c58e7-e061-4f27-83c8-47c9135dde2c",
            "selected": false,
            "physicalChange": 0,
            "isNew": false
         },
         {
            "querySourceId": "735f70b1-8e33-4b02-bf62-53d2c57b9498",
            "selected": false,
            "physicalChange": 0,
            "isNew": false
         }],
         "relatedDataSourceCategories": null,
         "result": [{
            "id": "126c58e7-e061-4f27-83c8-47c9135dde2c",
            "category": "MySQL-Northwind",
            "databaseName": "northwind",
            "schemaName": "northwind",
            "dataObject": "order details",
            "dataObjectType": "Table"
         }],
         "pageIndex": 1,
         "pageSize": 10,
         "total": 1,
         "skipItems": 0,
         "isLastPage": false
      }

POST report/loadRelatedQuerySources
-----------------------------------------

Returns list of related query source categories.


**Request**

    Payload: a :doc:`models/ReportSelectedPagedRequest` object

**Response**

    The following object:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **data** |br|
             an array of :doc:`ReportDataSourceCategory`
          -  The list of report data source category
          -
       *  -  **totalItems** |br|
             integer
          -  The number of all items
          -
       *  -  **numOfChilds** |br|
             integer
          -  The number of children
          -
       *  -  **numOfCheckedChilds** |br|
             integer
          -  The number of selected children
          -
       *  -  **indeterminate** |br|
             boolean
          -  * true if 0 < numOfCheckedChilds < numOfChilds
             * false if not
          -
       *  -  **isLastPage** |br|
             boolean
          -  Whether this is the last page
          -

**Samples**

   .. code-block:: http

      POST /api/report/loadRelatedQuerySources HTTP/1.1

   Sample Request Payload::

      {
         "querySources": [{
            "querySourceId": "67a0d2f7-3171-412f-8e44-3ab17c134700",
            "selected": true,
            "physicalChange": 0,
            "state": 2
         }],
         "tenantId": "f09289c1-3f43-4da3-85c8-249e474dd074",
         "criteria": [{
            "key": "All",
            "value": "",
            "operation": 1
         }],
         "pageIndex": 1,
         "pageSize": 10,
         "sortOrders": [{
            "key": "Category",
            "descending": true
         }]
      }

   .. container:: toggle

      .. container:: header

         Sample response

      .. code-block:: json

         {
            "data": [
               {
                     "id": "63cff017-70de-4e6a-9318-97c42116a29e",
                     "name": "MSSQL",
                     "querySource": [
                        {
                           "id": "9a014d06-6c3a-46f5-813f-2cbbd0eee7f0",
                           "name": "Order Details",
                           "originalName": "Order Details",
                           "type": "Table",
                           "selected": true,
                           "visible": true,
                           "querySourceCategoryName": "dbo",
                           "dataSourceCategoryName": "MSSQL",
                           "dataSourceCategoryId": "63cff017-70de-4e6a-9318-97c42116a29e",
                           "connectionName": "MSSQL_Northwind",
                           "isAlias": false,
                           "isDynamic": false,
                           "fields": [
                                 {
                                    "name": "OrderID",
                                    "alias": "",
                                    "dataType": "int",
                                    "izendaDataType": "Numeric",
                                    "allowDistinct": false,
                                    "visible": true,
                                    "filterable": true,
                                    "querySourceId": "00000000-0000-0000-0000-000000000000",
                                    "parentId": null,
                                    "expressionFields": [],
                                    "filteredValue": "",
                                    "type": 0,
                                    "groupPosition": 0,
                                    "position": 0,
                                    "extendedProperties": null,
                                    "physicalChange": 0,
                                    "approval": 0,
                                    "existed": false,
                                    "matchedTenant": false,
                                    "functionName": null,
                                    "expression": null,
                                    "isRunningField": false,
                                    "supportDefaultTotal": null,
                                    "fullName": null,
                                    "calculatedTree": null,
                                    "reportId": null,
                                    "originalName": "OrderID",
                                    "originalId": "00000000-0000-0000-0000-000000000000",
                                    "isParameter": false,
                                    "isCalculated": false,
                                    "hasAggregatedFunction": false,
                                    "hasSupportDefaultTotal": true,
                                    "querySource": null,
                                    "querySourceName": null,
                                    "categoryName": null,
                                    "inaccessible": false,
                                    "originalAlias": null,
                                    "allowToSave": false,
                                    "fullPath": null,
                                    "isCheck": false,
                                    "id": "9aa1a6ed-5bc9-4152-8f0d-c7ab6e7d9d1d",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": null,
                                    "created": null,
                                    "createdBy": "System Admin",
                                    "modified": "0001-01-01T00:00:00",
                                    "modifiedBy": null
                                 },
                                 {
                                    "name": "ProductID",
                                    "alias": "",
                                    "dataType": "int",
                                    "izendaDataType": "Numeric",
                                    "allowDistinct": false,
                                    "visible": true,
                                    "filterable": true,
                                    "querySourceId": "00000000-0000-0000-0000-000000000000",
                                    "parentId": null,
                                    "expressionFields": [],
                                    "filteredValue": "",
                                    "type": 0,
                                    "groupPosition": 0,
                                    "position": 0,
                                    "extendedProperties": null,
                                    "physicalChange": 0,
                                    "approval": 0,
                                    "existed": false,
                                    "matchedTenant": false,
                                    "functionName": null,
                                    "expression": null,
                                    "isRunningField": false,
                                    "supportDefaultTotal": null,
                                    "fullName": null,
                                    "calculatedTree": null,
                                    "reportId": null,
                                    "originalName": "ProductID",
                                    "originalId": "00000000-0000-0000-0000-000000000000",
                                    "isParameter": false,
                                    "isCalculated": false,
                                    "hasAggregatedFunction": false,
                                    "hasSupportDefaultTotal": true,
                                    "querySource": null,
                                    "querySourceName": null,
                                    "categoryName": null,
                                    "inaccessible": false,
                                    "originalAlias": null,
                                    "allowToSave": false,
                                    "fullPath": null,
                                    "isCheck": false,
                                    "id": "316d1a12-9252-41c8-85e3-95c65b3da396",
                                    "state": 0,
                                    "deleted": false,
                                    "inserted": true,
                                    "version": null,
                                    "created": null,
                                    "createdBy": "System Admin",
                                    "modified": "0001-01-01T00:00:00",
                                    "modifiedBy": null
                                 }
                           ],
                           "numOfChilds": 2,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        }
                     ],
                     "numOfChilds": 1,
                     "numOfCheckedChilds": 0,
                     "indeterminate": false,
                     "fullPath": null,
                     "computeNameSettings": null,
                     "isCheck": false
               }],
            "totalItems": 0,
            "numOfChilds": 1,
            "numOfCheckedChilds": 0,
            "indeterminate": false,
            "isLastPage": true
         }

POST report/loadJoinQuerySourceByRelationship
----------------------------------------------

Return a list of join query source.

**Request**

    Payload: a :doc:`models/ReportParameter` object

**Response**

    An array of :doc:`models/RelationshipQuerySource` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadJoinQuerySourceByRelationship HTTP/1.1

   Sample Request Payload::

      {
         "reportKey":{"key":"c0091e01-22f9-44a5-99e3-eb656a1fcebd"},
         "relationshipIds": ["f03fcf35-5994-4cc4-ac5f-c4ae5f4bd26a"]
      }

   Sample Response::

      [
         {
            "relationshipId": "f03fcf35-5994-4cc4-ac5f-c4ae5f4bd26a",
            "querySourceId": "7f9cd714-9b06-4aaf-9a8b-5475ea0cdefc",
            "querySourceName": "Order Details",
            "dataSourceCategoryId": "00000000-0000-0000-0000-000000000000",
            "dataSourceCategoryName": ""
         }
      ]

POST report/loadRelationships
------------------------------------------------

Returns an updated list of relationships from an existing report together with an updated list of data sources.

**Request**

    Payload: a :doc:`models/RelationshipPagedRequest` object

**Response**

    A :doc:`models/ReportRelationshipResult` object

**Samples**

   .. code-block:: http

      POST /api/report/loadRelationships HTTP/1.1

   Request payload (query source id = "65d587e2-71f9-4565-8ad8-e6f532398455" has been selected by user)::

      {
        "objectId" : null,
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "querySources" : [{
              "querySourceId" : "65d587e2-71f9-4565-8ad8-e6f532398455",
              "selected" : true,
              "physicalChange" : 2,
              "state" : 1
           }, {
              "querySourceId" : "7d4d81a0-4813-4e77-912d-934333c607e1",
              "selected" : false,
              "physicalChange" : 0,
              "state" : 1
           }
        ]
      }

   Response:

      .. code-block:: json
         :emphasize-lines: 6,7,15,17,19

         {
           "hasRemovedRelationship" : false,
           "result" : [{
                 "joinConnectionId" : "11d2c31c-e726-4f80-8621-2b4856fae1a5",
                 "foreignConnectionId" : "11d2c31c-e726-4f80-8621-2b4856fae1a5",
                 "joinQuerySourceId" : "65d587e2-71f9-4565-8ad8-e6f532398455",
                 "joinQuerySourceName" : "Employees",
                 "joinDataSourceCategoryName" : null,
                 "joinDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
                 "foreignDataSourceCategoryName" : null,
                 "foreignDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
                 "foreignQuerySourceId" : "65d587e2-71f9-4565-8ad8-e6f532398455",
                 "foreignQuerySourceName" : "Employees",
                 "joinFieldId" : "d198eb03-6dee-4e3d-bc08-4ab11f08d3bd",
                 "joinFieldName" : "ReportsTo",
                 "foreignFieldId" : "f661a585-b463-426c-8849-dc6921139f7c",
                 "foreignFieldName" : "EmployeeID",
                 "alias" : null,
                 "systemRelationship" : true,
                 "joinType" : "Inner",
                 "parentRelationshipId" : "00000000-0000-0000-0000-000000000000",
                 "deleted" : false,
                 "position" : null,
                 "relationshipPosition" : 0,
                 "relationshipKeyJoins" : null,
                 "reportId" : "00000000-0000-0000-0000-000000000000",
                 "foreignAlias" : null,
                 "selectedForeignAlias" : "65d587e2-71f9-4565-8ad8-e6f532398455_Employees",
                 "id" : "65fe4ced-577c-4da5-97a0-5e2903a0a7ab",
                 "state" : 0,
                 "modified" : "2016-04-28T03:33:48.4200000+07:00",
                 "dateTimeNow" : "2016-04-28T04:04:09.0399962Z"
              }
           ],
           "total" : 1,
           "pageIndex" : 1,
           "pageSize" : 10
         }

      The response says that: There is one relationship involving query source id = "65d587e2-71f9-4565-8ad8-e6f532398455" (Employees). That is a system relationship (foreign key) with Employees.ReportsTo self-references Employees.EmployeeID.


POST report/validateRelationshipSyntax
------------------------------------------------

Validates relationship syntax, as following:

In Report Simple mode, validates that selected data sources have relationships.

In Report Advanced mode, validates that specified relationships correctly joins selected data sources. Also validates:

*  Alias is required for the same selected object
*  Aliases in relationships are not duplicated
*  Aliases between relationships and data sources are not duplicated 
*  Relationship key joins have correct syntax
*  Data types between join fields and foreign fields are compatible (same Izenda data type)
*  Relationships are not duplicated
*  Relationship key joins are not duplicated

.. note::

   Ignores data sources, relationships and relationship key joins with **state** = 2 (deleted)

**Request**

   Payload: a :doc:`models/ReportSavingParameter` object, with **reportKey**, **report.reportDataSource** and **report.reportRelationship** fields populated.

   Required fields for **report.reportDataSource**:

   *  querySourceId
   *  state

   Required fields for **report.reportRelationship** in Report Advanced mode:

   *  state
   *  joinType
   *  joinQuerySourceId
   *  foreignQuerySourceId
   *  joinFieldId (nullable when joinType is "Cross")
   *  foreignFieldId (nullable when joinType is "Cross")
   *  alias (nullable)
   *  relationshipKeyJoins

   **report.reportRelationship** should be empty in Report Simple mode.

**Response**

    An :doc:`models/OperationResult` object, with **success** field true if syntax is valid

**Samples**

   .. code-block:: http

      POST /api/report/validateRelationshipSyntax HTTP/1.1

   Request payload::

      {
        "reportKey" : {
           "key" : null,
           "modified" : null
        },
        "section" : 0,
        "saveAs" : false,
        "ignoreCheckChange" : false,
        "report" : {
           "name" : "",
           "type" : "Templates",
           "previewRecord" : 10,
           "advancedMode" : true,
           "allowNulls" : false,
           "isDistinct" : false,
           "reportDataSource" : [{
                 "aliasId" : "479be129-338d-45f1-b216-1d95957fe2c8_Order Details",
                 "querySourceId" : "479be129-338d-45f1-b216-1d95957fe2c8",
                 "querySourceName" : "Order Details",
                 "selected" : true,
                 "state" : 1
              }, {
                 "aliasId" : "54852be4-5584-4c23-ae5d-4197724059e1_Orders",
                 "querySourceId" : "54852be4-5584-4c23-ae5d-4197724059e1",
                 "querySourceName" : "Orders",
                 "selected" : true,
                 "state" : 1
              }
           ],
           "reportRelationship" : [{
                 "tempId" : "16d3b9bf-86cb-45fa-b33d-53e3e2a8a042",
                 "joinConnectionId" : "db19bb46-ffa3-45fd-b205-0dad305fdf98",
                 "foreignConnectionId" : "db19bb46-ffa3-45fd-b205-0dad305fdf98",
                 "joinQuerySourceId" : "479be129-338d-45f1-b216-1d95957fe2c8",
                 "joinQuerySourceName" : "Order Details",
                 "joinDataSourceCategoryName" : "",
                 "foreignDataSourceCategoryName" : "",
                 "foreignQuerySourceId" : "54852be4-5584-4c23-ae5d-4197724059e1",
                 "foreignQuerySourceName" : "Orders",
                 "joinFieldId" : "a0011b48-ef08-45fe-b044-abc68442cd17",
                 "joinFieldName" : "OrderID",
                 "foreignFieldId" : "3caf9c17-abd7-4119-809d-2c3debb8eb37",
                 "foreignFieldName" : "OrderID",
                 "alias" : "",
                 "systemRelationship" : true,
                 "joinType" : "Inner",
                 "parentRelationshipId" : "c55d696b-f25d-4a6f-a951-7a4e6e532c98",
                 "position" : null,
                 "relationshipKeyJoins" : [],
                 "selectedForeignAlias" : "54852be4-5584-4c23-ae5d-4197724059e1_Orders",
                 "id" : "16d3b9bf-86cb-45fa-b33d-53e3e2a8a052",
                 "state" : 1,
                 "validationKey" : "c55d696b-f25d-4a6f-a951-7a4e6e532c98",
                 "relationshipPosition" : 0,
                 "invalidAlias" : null,
                 "hidden" : false,
                 "level" : 1
              }
           ],
           "reportPart" : []
        },
        "expandedLevel" : 0,
        "filters" : []
      }

   Successful response::

      {
         "success": true,
         "messages": [{
            "key": "",
            "messages": ["A valid SQL statement can be constructed from the given relationships."]
         }]
      }

POST report/validateCycleRelationships
----------------------------------------
Validate if cycle relationships error occurs.

**Request**

    Payload: a :doc:`models/Relationship` object

**Response**

    A :doc:`models/OperationResult` object

    * success = true when there is no cycle relationship
    * success = false and error message when cycle relationship occurs

**Samples**

   .. code-block:: http

      POST /api/report/validateCycleRelationships HTTP/1.1

   Request payload do not contain cycle relationship::

      [{
         "previousAlias": "",
         "tempId": "relationship_65",
         "joinConnectionId": null,
         "foreignConnectionId": null,
         "joinQuerySourceId": "5eec76ff-4de9-403a-a7dd-66a9db4e6eba",
         "joinQuerySourceName": "orders",
         "joinDataSourceCategoryName": "MySQL-Northwind",
         "joinDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
         "foreignDataSourceCategoryName": "",
         "foreignDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
         "foreignQuerySourceId": null,
         "foreignQuerySourceName": "order details",
         "joinFieldId": "b5ea4297-8fe1-47d2-bfde-13b2eef6c36d",
         "joinFieldName": "OrderID",
         "foreignFieldId": "368088ba-5e24-4bf8-b709-1c44fe3e80e5",
         "foreignFieldName": "OrderID",
         "alias": "",
         "aliasTempId": "alias_66",
         "systemRelationship": false,
         "joinType": "Inner",
         "parentRelationshipId": null,
         "position": null,
         "relationshipKeyJoins": [],
         "reportId": null,
         "selectedForeignAlias": "126c58e7-e061-4f27-83c8-47c9135dde2c_order details",
         "isForeignDataObjectAlias": false,
         "id": null,
         "state": 1,
         "validationKey": "relationship_65",
         "relationshipPosition": 0,
         "needAlias": false,
         "level": 1,
         "comparisonOperator": "= (Field)",
         "comparisonValue": null,
         "hidden": false,
         "isDirty": true
      }]

   Success Response::

      {"success" : true, "message" : null, "data" : null}

   .. container:: toggle

      .. container:: header

         Sample Payload contains cycle relationship:

      .. code-block:: json

         [{
            "previousAlias": "",
            "tempId": "d9260bf3-c979-4969-9f9f-55d42c76bd64",
            "joinConnectionId": "00000000-0000-0000-0000-000000000000",
            "foreignConnectionId": "00000000-0000-0000-0000-000000000000",
            "joinQuerySourceId": "5eec76ff-4de9-403a-a7dd-66a9db4e6eba",
            "joinQuerySourceName": "orders",
            "joinDataSourceCategoryName": "MySQL-Northwind",
            "joinDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignDataSourceCategoryName": "",
            "foreignDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignQuerySourceId": "126c58e7-e061-4f27-83c8-47c9135dde2c",
            "foreignQuerySourceName": "order details",
            "joinFieldId": "b5ea4297-8fe1-47d2-bfde-13b2eef6c36d",
            "joinFieldName": "OrderID",
            "foreignFieldId": "368088ba-5e24-4bf8-b709-1c44fe3e80e5",
            "foreignFieldName": "OrderID",
            "alias": "",
            "aliasTempId": "alias_93",
            "systemRelationship": false,
            "joinType": "Inner",
            "parentRelationshipId": null,
            "position": null,
            "relationshipKeyJoins": [],
            "reportId": "85df9d52-f992-4be4-a58f-bd6c6c6b79fa",
            "selectedForeignAlias": "126c58e7-e061-4f27-83c8-47c9135dde2c_order details",
            "isForeignDataObjectAlias": false,
            "id": "d9260bf3-c979-4969-9f9f-55d42c76bd64",
            "state": 1,
            "validationKey": "d9260bf3-c979-4969-9f9f-55d42c76bd64",
            "relationshipPosition": 0,
            "needAlias": false,
            "level": 1,
            "comparisonOperator": "= (Field)",
            "comparisonValue": null,
            "hidden": false,
            "isDirty": false
         },
         {
            "previousAlias": "",
            "tempId": "54c64a53-1c91-4415-b812-dae4a5062cdf",
            "joinConnectionId": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
            "foreignConnectionId": "6cc06e5b-0627-432c-bc33-708b0843c7c7",
            "joinQuerySourceId": "126c58e7-e061-4f27-83c8-47c9135dde2c",
            "joinQuerySourceName": "order details",
            "joinDataSourceCategoryName": "MySQL-Northwind",
            "joinDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignDataSourceCategoryName": "MySQL-Northwind",
            "foreignDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignQuerySourceId": "735f70b1-8e33-4b02-bf62-53d2c57b9498",
            "foreignQuerySourceName": "products",
            "joinFieldId": "61066219-3ab6-405a-ba80-770cb1aad8b0",
            "joinFieldName": "ProductID",
            "foreignFieldId": "989242ea-6671-419d-b6f4-6bfb450b9500",
            "foreignFieldName": "ProductID",
            "alias": "",
            "aliasTempId": "alias_144",
            "systemRelationship": true,
            "joinType": "Inner",
            "parentRelationshipId": null,
            "position": null,
            "relationshipKeyJoins": [],
            "reportId": null,
            "selectedForeignAlias": "735f70b1-8e33-4b02-bf62-53d2c57b9498_products",
            "isForeignDataObjectAlias": false,
            "id": "54c64a53-1c91-4415-b812-dae4a5062cdf",
            "state": 0,
            "validationKey": "54c64a53-1c91-4415-b812-dae4a5062cdf",
            "relationshipPosition": 1,
            "needAlias": false,
            "level": 2,
            "comparisonOperator": "= (Field)",
            "comparisonValue": null,
            "hidden": false,
            "isDirty": false
         },
         {
            "previousAlias": "",
            "tempId": "relationship_146",
            "joinConnectionId": null,
            "foreignConnectionId": null,
            "joinQuerySourceId": "735f70b1-8e33-4b02-bf62-53d2c57b9498",
            "joinQuerySourceName": "products",
            "joinDataSourceCategoryName": "MySQL-Northwind",
            "joinDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignDataSourceCategoryName": "",
            "foreignDataSourceCategoryId": "42d34867-a67c-4423-a846-08f2d7e49f8f",
            "foreignQuerySourceId": null,
            "foreignQuerySourceName": "orders",
            "joinFieldId": "989242ea-6671-419d-b6f4-6bfb450b9500",
            "joinFieldName": "ProductID",
            "foreignFieldId": "b5ea4297-8fe1-47d2-bfde-13b2eef6c36d",
            "foreignFieldName": "OrderID",
            "alias": "",
            "aliasTempId": "alias_147",
            "systemRelationship": false,
            "joinType": "Inner",
            "parentRelationshipId": null,
            "position": null,
            "relationshipKeyJoins": [],
            "reportId": null,
            "selectedForeignAlias": "5eec76ff-4de9-403a-a7dd-66a9db4e6eba_orders",
            "isForeignDataObjectAlias": false,
            "id": null,
            "state": 1,
            "validationKey": "relationship_146",
            "relationshipPosition": 2,
            "needAlias": false,
            "level": 3,
            "comparisonOperator": "= (Field)",
            "comparisonValue": null,
            "hidden": false,
            "isDirty": true
         }]

   Sample Response::

      {
         "success": false,
         "messages": [{
            "key": "",
            "detail": null,
            "messages": ["Relationships are invalid. Please update the relationships before navigating to another screen in Report Designer."]
         }],
         "data": null
      }

POST report/detectRelationshipsChange
------------------------------------------------

Detects if any relationship should be removed because of changes in data sources.

**Request**

    Payload: a :doc:`models/RelationshipPagedRequest` object

**Response**

    * true if any relationship needs to be removed
    * false if none

**Samples**

   .. code-block:: http

      POST /api/report/detectRelationshipsChange HTTP/1.1

   Request payload::

      {
         "objectId": "9197f210-766a-45d3-a1f9-5c4f4a4aa8ba",
         "criteria": [
            {
               "key": "All",
               "value": "",
               "operation": 1
            }
         ],
         "pageIndex": 1,
         "pageSize": 1000,
         "querySources": [
            {
               "querySourceId": "d38e8059-6b7e-49a7-be68-ec02d2b42168",
               "selected": true,
               "physicalChange": 0,
               "state": 1
            },
            {
               "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
               "selected": true,
               "physicalChange": 0,
               "state": 1
            },
            {
               "querySourceId": "ec580d6d-709a-41fd-b71e-489795e7428f",
               "selected": true,
               "physicalChange": 2,
               "state": 1
            }
         ],
         "relationshipOrders": [],
         "tenantId": null,
         "selectedDataSourceChanged": true
      }

   Response::

      false

.. _POST_report/availableQuerySourceFields:

POST report/availableQuerySourceFields
------------------------------------------------

Returns a list of data source fields in selected query sources of a report.

**Request**

    Payload: a :doc:`models/ReportSavingParameter` object, with either:

   *  **reportKey** field populated - for an existing/draft report.
   *  **reportKey** empty and **reportDataSource**.\ **querySourceId** populated - for a new report.

**Response**

    An array containing exactly one :doc:`models/ReportDataSourceCategory` object

**Samples**

   .. code-block:: http

      POST /api/report/availableQuerySourceFields HTTP/1.1

   Request payload for a draft report::

      {
        "reportKey" : {
           "key" : "024b91d3-4896-4191-8d8e-384997746178",
           "tenantId" : null
        }
      }

   Sample response::

      [{
         "id": null,
         "name": "Selected Data Source",
         "querySource": [{
            "id": "58ea6138-2980-46d7-b19a-4b102c359865",
            "name": "Employees",
            "type": "Table",
            "selected": false,
            "visible": true,
            "querySourceCategoryName": "Category_1",
            "connectionName": "Northwind",
            "isAlias": false,
            "fields": [{
                 "id": "343945c3-fbb9-43bb-8d57-f548b5566c35",
                 "name": "EmployeeID",
                 "alias": null,
                 "dataType": "int",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": null,
                 "isParameter": false,
                 "allowDistinct": true
            }]
         },  {
            "id": "5f39b800-47c9-4fca-970b-20e81cb2dbd9",
            "name": "Products",
            "type": "Table",
            "selected": false,
            "visible": true,
            "querySourceCategoryName": "Category_2",
            "connectionName": "Northwind",
            "isAlias": false,
            "fields": [{
                 "id": "bc8c7b39-53c2-49fc-8a4a-20782ad3369d",
                 "name": "ProductID",
                 "alias": null,
                 "dataType": "int",
                 "unitDataType": "Number",
                 "visible": true,
                 "filterable": true,
                 "extendedProperties": null,
                 "isParameter": false,
                 "allowDistinct": true
            }]
         }]
      }]

   Request payload for a new report::

      {
         "reportKey": {
            "key": null,
            "modified": null,
            "tenantId": null
         },
         "report": {
            "reportDataSource": [
               {
                  "querySourceId": "ab5b596a-6d35-45a0-ad9b-d3188326bafb",
                  "querySourceName": "Orders",
               }
            ],
            "reportRelationship": [],
            "dynamicQuerySourceFields": [],
            "calculatedFields": []
         }
      }

   Sample response is similar to above.

GET report/availableReportMappingFields/{report_id}
-----------------------------------------------------------

Returns a list of data source fields, alias fields, and calculated fields in selected query sources of a report.

**Request**

    No payload

**Response**

    An array of :doc:`models/ReportField` objects

**Samples**

   .. code-block:: http

      GET /api/report/availableReportMappingFields/45f17b8a-3708-4f36-80ef-9178b7124841 HTTP/1.1

   Response::

      [{
          "fieldId": "1524ea5e-2111-4fd9-b749-f0f9150691a1",
          "originalName": null,
          "fieldName": "CalendarYear",
          "fieldNameAlias": "",
          "dataFieldType": "Numeric",
          "querySourceId": "f56e717c-d45b-4af9-9e98-968c259ee858",
          "querySourceType": "Table",
          "sourceAlias": "DueDate",
          "relationshipId": "78fb49b8-de6f-491b-aab2-fc01a509093e",
          "visible": true,
          "filterable": false,
          "reportId": null,
          "fieldFunctionExpression": "[DueDate].[CalendarYear]",
          "expression": null,
          "grandTotalExpression": null,
          "subTotalExpression": null,
          "sort": "Unsorted",
          "function": null,
          "format": null,
          "functionDataType": null,
          "calculatedTree": null,
          "grandTotalTree": null,
          "isCalculated": false
        }
      ]

GET report/fieldProperties/{query_source_field_id}
---------------------------------------------------------

Returns the properties of query source field specified by query_source_field_id.

**Request**

    No payload

**Response**

    A :doc:`models/ReportQuerySource` object

**Samples**

   .. code-block:: http

      GET /api/report/fieldProperties/bd207050-e2a4-4128-9b5a-89409bee0377 HTTP/1.1

   Sample response::

      {
         "id": "d9728d5f-b6f6-462b-b988-8180bc733972",
         "name": "HumanResources.Employee",
         "type": "Table",
         "selected": false,
         "visible": true,
         "querySourceCategoryName": null,
         "connectionName": null,
         "isAlias": false,
         "fields": [{
            "id": "bd207050-e2a4-4128-9b5a-89409bee0377",
            "name": "Gender",
            "alias": "",
            "dataType": "nchar",
            "izendaDataType": "Text",
            "visible": true,
            "filterable": true,
            "extendedProperties": null,
            "isParameter": false,
            "allowDistinct": false
         }]
      }

POST report/loadDataSourceFields
-------------------------------------

Returns the list fields of selected query source.

**Request**

    Payload: a :doc:`models/ReportDataSourceParameter` object

**Response**

    An array of :doc:`models/QuerySourceField` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadDataSourceFields HTTP/1.1

POST report/calculatedField
------------------------------------------------

Saves a calculated field after validating name duplication (does not validate the expression).

**Request**

    Payload: a :doc:`models/ReportCalculatedFieldParameter` object

**Response**

    An array containing exactly one :doc:`models/ReportDataSourceCategory` object

**Samples**

   .. code-block:: http

      POST /api/report/calculatedField HTTP/1.1

   Request payload to add a calculated field [MoneyInStock] from [UnitPrice] * [UnitsInStock]::

      {
        "reportKey" : {
           "key" : "681dc08e-4355-441f-a438-370d5c1a7a99"
        },
        "calculatedField" : {
           "id" : null,
           "name" : "MoneyInStock",
           "functionName" : "[None]",
           "expression" : "[Northwind].[dbo].[Products].[UnitPrice] * [Northwind].[dbo].[Products].[UnitsInStock]",
           "izendaDataType" : "Money"
        }
      }

   Sample response::

      {
        "id" : null,
        "name" : "Calculated Fields",
        "querySource" : [{
              "id" : "00000000-0000-0000-0000-000000000000",
              "name" : "Calculated Fields",
              "originalName" : null,
              "type" : null,
              "selected" : false,
              "visible" : true,
              "querySourceCategoryName" : null,
              "connectionName" : null,
              "isAlias" : false,
              "fields" : [{
                    "name" : "MoneyInStock",
                    "alias" : "",
                    "dataType" : "",
                    "izendaDataType" : "Money",
                    "allowDistinct" : true,
                    "visible" : true,
                    "filterable" : true,
                    "deleted" : false,
                    "querySourceId" : "00000000-0000-0000-0000-000000000000",
                    "parentId" : null,
                    "expressionFields" : [{
                          "fieldId" : "3f79de74-1152-4896-b966-ea82849efece",
                          "fieldName" : "UnitPrice",
                          "fieldNameAlias" : "",
                          "dataFieldType" : "Money",
                          "querySourceId" : "e1bc2021-3874-4e5a-b51e-d799cef5e29a",
                          "querySourceType" : "Table",
                          "sourceAlias" : "Products",
                          "relationshipId" : "00000000-0000-0000-0000-000000000000",
                          "visible" : true,
                          "reportId" : null,
                          "fieldFunctionExpression" : null,
                          "expression" : "[Northwind].[dbo].[Products].[UnitPrice]",
                          "grandTotalExpression" : null,
                          "subTotalExpression" : null,
                          "sort" : "Unsorted",
                          "function" : null,
                          "calculatedTree" : null,
                          "grandTotalTree" : null
                       }, {
                          "fieldId" : "54c13d3b-d8fe-4e78-a710-230d3d794039",
                          "fieldName" : "UnitsInStock",
                          "fieldNameAlias" : "",
                          "dataFieldType" : "Numeric",
                          "querySourceId" : "e1bc2021-3874-4e5a-b51e-d799cef5e29a",
                          "querySourceType" : "Table",
                          "sourceAlias" : "Products",
                          "relationshipId" : "00000000-0000-0000-0000-000000000000",
                          "visible" : true,
                          "reportId" : null,
                          "fieldFunctionExpression" : null,
                          "expression" : "[Northwind].[dbo].[Products].[UnitsInStock]",
                          "grandTotalExpression" : null,
                          "subTotalExpression" : null,
                          "sort" : "Unsorted",
                          "function" : null,
                          "calculatedTree" : null,
                          "grandTotalTree" : null
                       }
                    ],
                    "filteredValue" : "",
                    "type" : 0,
                    "groupPosition" : 0,
                    "position" : 0,
                    "extendedProperties" : "[{" FieldId ":" 3f79de74 - 1152 - 4896 - b966 - ea82849efece "," FieldName ":" UnitPrice "," FieldNameAlias ":" "," DataFieldType ":" Money "," QuerySourceId ":" e1bc2021 - 3874 - 4e5a - b51e - d799cef5e29a "," QuerySourceType ":" Table "," SourceAlias ":" Products "," RelationshipId ":" 00000000 - 0000 - 0000 - 0000 - 000000000000 "," Visible ":true," ReportId ":null," FieldFunctionExpression ":null," Expression ":"[Northwind].[dbo].[Products].[UnitPrice]"," GrandTotalExpression ":null," SubTotalExpression ":null," Sort ":" Unsorted "," Function ":null," CalculatedTree ":null," GrandTotalTree ":null},{" FieldId ":" 54c13d3b - d8fe - 4e78 - a710 - 230d3d794039 "," FieldName ":" UnitsInStock "," FieldNameAlias ":" "," DataFieldType ":" Numeric "," QuerySourceId ":" e1bc2021 - 3874 - 4e5a - b51e - d799cef5e29a "," QuerySourceType ":" Table "," SourceAlias ":" Products "," RelationshipId ":" 00000000 - 0000 - 0000 - 0000 - 000000000000 "," Visible ":true," ReportId ":null," FieldFunctionExpression ":null," Expression ":"[Northwind].[dbo].[Products].[UnitsInStock]"," GrandTotalExpression ":null," SubTotalExpression ":null," Sort ":" Unsorted "," Function ":null," CalculatedTree ":null," GrandTotalTree ":null}]",
                    "physicalChange" : 0,
                    "approval" : 0,
                    "existed" : false,
                    "matchedTenant" : false,
                    "functionName" : "[None]",
                    "expression" : "[Northwind].[dbo].[Products].[UnitPrice] * [Northwind].[dbo].[Products].[UnitsInStock]",
                    "fullName" : null,
                    "calculatedTree" : null,
                    "reportId" : "00000000-0000-0000-0000-000000000000",
                    "originalName" : null,
                    "isParameter" : false,
                    "isCalculated" : true,
                    "querySource" : null,
                    "id" : "fc6ea2e3-8a30-4f2a-b2ba-6f33dd2fdb07",
                    "state" : 0,
                    "modified" : "2016-06-24T00:46:25.63744"
                 }
              ]
           }
        ]
      }

GET report/calculatedField/{calculated_field_id}
------------------------------------------------

Returns the calculated field specified by calculated_field_id.

**Request**

    No payload

**Response**

    A :doc:`models/QuerySourceField` object

**Samples**

   .. code-block:: http

      GET /api/report/calculatedField/52c55f01-b347-4a23-b089-32f8e1db05fe HTTP/1.1

   Sample response::

      {
         "name": "MoneyInStock",
         "alias": "",
         "dataType": "",
         "izendaDataType": "Money",
         "allowDistinct": true,
         "visible": true,
         "filterable": true,
         "deleted": false,
         "querySourceId": "00000000-0000-0000-0000-000000000000",
         "parentId": null,
         "expressionFields": [{
            "fieldId": "3f79de74-1152-4896-b966-ea82849efece",
            "fieldName": "UnitPrice",
            "fieldNameAlias": "",
            "dataFieldType": "Money",
            "querySourceId": "e1bc2021-3874-4e5a-b51e-d799cef5e29a",
            "querySourceType": "Table",
            "sourceAlias": "Products",
            "relationshipId": "00000000-0000-0000-0000-000000000000",
            "visible": true,
            "reportId": null,
            "fieldFunctionExpression": null,
            "expression": "[Northwind].[dbo].[Products].[UnitPrice]",
            "grandTotalExpression": null,
            "subTotalExpression": null,
            "sort": "Unsorted",
            "function": null,
            "calculatedTree": null,
            "grandTotalTree": null
         }, {
            "fieldId": "54c13d3b-d8fe-4e78-a710-230d3d794039",
            "fieldName": "UnitsInStock",
            "fieldNameAlias": "",
            "dataFieldType": "Numeric",
            "querySourceId": "e1bc2021-3874-4e5a-b51e-d799cef5e29a",
            "querySourceType": "Table",
            "sourceAlias": "Products",
            "relationshipId": "00000000-0000-0000-0000-000000000000",
            "visible": true,
            "reportId": null,
            "fieldFunctionExpression": null,
            "expression": "[Northwind].[dbo].[Products].[UnitsInStock]",
            "grandTotalExpression": null,
            "subTotalExpression": null,
            "sort": "Unsorted",
            "function": null,
            "calculatedTree": null,
            "grandTotalTree": null
         }],
         "filteredValue": "",
         "type": 0,
         "groupPosition": 0,
         "position": 0,
         "extendedProperties": "[{\"FieldId\":\"3f79de74-1152-4896-b966-ea82849efece\",\"FieldName\":\"UnitPrice\",\"FieldNameAlias\":\"\",\"DataFieldType\":\"Money\",\"QuerySourceId\":\"e1bc2021-3874-4e5a-b51e-d799cef5e29a\",\"QuerySourceType\":\"Table\",\"SourceAlias\":\"Products\",\"RelationshipId\":\"00000000-0000-0000-0000-000000000000\",\"Visible\":true,\"ReportId\":null,\"FieldFunctionExpression\":null,\"Expression\":\"[Northwind].[dbo].[Products].[UnitPrice]\",\"GrandTotalExpression\":null,\"SubTotalExpression\":null,\"Sort\":\"Unsorted\",\"Function\":null,\"CalculatedTree\":null,\"GrandTotalTree\":null},{\"FieldId\":\"54c13d3b-d8fe-4e78-a710-230d3d794039\",\"FieldName\":\"UnitsInStock\",\"FieldNameAlias\":\"\",\"DataFieldType\":\"Numeric\",\"QuerySourceId\":\"e1bc2021-3874-4e5a-b51e-d799cef5e29a\",\"QuerySourceType\":\"Table\",\"SourceAlias\":\"Products\",\"RelationshipId\":\"00000000-0000-0000-0000-000000000000\",\"Visible\":true,\"ReportId\":null,\"FieldFunctionExpression\":null,\"Expression\":\"[Northwind].[dbo].[Products].[UnitsInStock]\",\"GrandTotalExpression\":null,\"SubTotalExpression\":null,\"Sort\":\"Unsorted\",\"Function\":null,\"CalculatedTree\":null,\"GrandTotalTree\":null}]",
         "physicalChange": 0,
         "approval": 0,
         "existed": false,
         "matchedTenant": false,
         "functionName": "[None]",
         "expression": "[Northwind].[dbo].[Products].[UnitPrice] * [Northwind].[dbo].[Products].[UnitsInStock]",
         "fullName": null,
         "calculatedTree": null,
         "reportId": "ba7cc132-689c-43fd-8fc8-272c5162d263",
         "originalName": null,
         "isParameter": false,
         "isCalculated": true,
         "querySource": null,
         "id": "52c55f01-b347-4a23-b089-32f8e1db05fe",
         "state": 0,
         "modified": "2016-06-24T08:38:51.367"
      }

GET report/hasReportUseCalculatedField/{calculated_field_id}
-------------------------------------------------------------------

Returns true if the calculated field is being used in any report part or report filter.

**Request**

    No payload

**Response**

    * true if the calculated field is being used in any report part or report filter
    * false if none

**Samples**

   .. code-block:: http

      GET /api/report/hasReportUseCalculatedField/BC0E2AA2-8310-429E-8212-00FC4863A559 HTTP/1.1

   Response::

      false

GET report/hasReportUseRelationship/{relationship_id}
--------------------------------------------------------------

Returns true if the relationship is being used in report.

**Request**

    No payload

**Response**

    * true if the relationship is being used in report
    * false if none

**Samples**

   .. code-block:: http

      GET /api/report/hasReportUseRelationship/f7ee0950-f203-4c56-b2db-c04728edae36 HTTP/1.1

   Response::

      true

POST report/deleteReportCalculatedField
------------------------------------------------

Removes a calculated field from report.

**Request**

    Payload: a :doc:`models/ReportCalculatedFieldParameter` object

**Response**

    * true if the calculated field was removed successfully
    * an :doc:`models/OperationResult` object with **messages** field populated if not

**Samples**

   .. code-block:: http

      POST /api/report/deleteReportCalculatedField HTTP/1.1

   Request payload::

      {
        "reportKey" : {
           "key" : "aef4b8eb-1b4c-41e3-b1c5-d227970007c3"
        },
        "calculatedField" : {
           "id" : "fe94ab0d-2063-4d2d-8931-0d2a9185658b"
        }
      }

   Response if success::

      true

   Response in case of error::

      {
         "success": false,
         "messages": [{
            "key": "",
            "messages": ["There is an error while process request. Please contact administrator."]
         }]
      }

POST report/loadDynamicDataSourceCategory
-------------------------------------------

Returns list of dynamic report data source category.

**Request**

    Payload: a :doc:`models/ReportDataSourceParameter` object

**Response**

    An array of :doc:`models/ReportDataSourceCategory` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadDynamicDataSourceCategory HTTP/1.1

   Sample Request Payload ::

      {
         "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
         "reportKey": {
            "key": null
         },
         "criteria": [{
            "key": "Name",
            "value": ""
         }],
         "skipItems": 0,
         "pageSize": 50,
         "parentIds": []
      }

   Sample Response ::

      {
         "data": [],
         "totalItems": 0,
         "numOfChilds": 0,
         "numOfCheckedChilds": 0,
         "indeterminate": false,
         "isLastPage": true
      }



POST report/loadPartialDataSourceCategory
---------------------------------------------

Returns list of report data source category with paging.

**Request**

    Payload: a :doc:`models/ReportDataSourceParameter` object

**Response**

    The following object:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **data** |br|
             an array of :doc:`ReportDataSourceCategory`
          -  The list of report data source category
          -
       *  -  **totalItems** |br|
             integer
          -  The number of all items
          -
       *  -  **numOfChilds** |br|
             integer
          -  The number of children
          -
       *  -  **numOfCheckedChilds** |br|
             integer
          -  The number of selected children
          -
       *  -  **indeterminate** |br|
             boolean
          -  * true if 0 < numOfCheckedChilds < numOfChilds
             * false if not
          -
       *  -  **isLastPage** |br|
             boolean
          -  Whether this is the last page
          -

**Samples**

   .. code-block:: http

      POST /api/report/loadPartialDataSourceCategory HTTP/1.1

   Sample Request Payload ::

      {
         "tenantId": "0fc6bbfe-7066-4e1d-92f5-9c6d75558ead",
         "reportKey": {
            "key": null
         },
         "criteria": [{
            "key": "Name",
            "value": ""
         }],
         "skipItems": 0,
         "pageSize": 50,
         "parentIds": []
      }

   Sample Response ::

      {
         "data": [{
            "id": "00000000-0000-0000-0000-000000000000",
            "name": null,
            "querySource": [{
               "id": "45a16d82-18be-4871-a530-783e09a6bac6",
               "name": "actor",
               "originalName": "actor",
               "type": "Table",
               "selected": false,
               "visible": true,
               "querySourceCategoryName": "public",
               "dataSourceCategoryName": null,
               "dataSourceCategoryId": "00000000-0000-0000-0000-000000000000",
               "connectionName": "PG-DVDRental",
               "isAlias": false,
               "isDynamic": false,
               "fields": [
               {
                  "name": "actor_id",
                  "alias": "",
                  "dataType": "integer",
                  "izendaDataType": "Numeric",
                  "allowDistinct": false,
                  "visible": true,
                  "filterable": true,
                  "querySourceId": "00000000-0000-0000-0000-000000000000",
                  "parentId": null,
                  "expressionFields": [],
                  "filteredValue": "",
                  "type": 0,
                  "groupPosition": 0,
                  "position": 0,
                  "extendedProperties": "{\"PrimaryKey\":true}",
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "matchedTenant": false,
                  "functionName": null,
                  "expression": null,
                  "isRunningField": false,
                  "supportDefaultTotal": null,
                  "fullName": null,
                  "calculatedTree": null,
                  "reportId": null,
                  "originalName": "actor_id",
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isParameter": false,
                  "isCalculated": false,
                  "hasAggregatedFunction": false,
                  "hasSupportDefaultTotal": true,
                  "querySource": null,
                  "querySourceName": null,
                  "categoryName": null,
                  "inaccessible": false,
                  "originalAlias": null,
                  "allowToSave": false,
                  "fullPath": null,
                  "isCheck": false,
                  "id": "f95febd6-6a9e-4f43-afa9-cffba7435a3e",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": "0001-01-01T00:00:00",
                  "modifiedBy": null
               },
               {
                  "name": "first_name",
                  "alias": "",
                  "dataType": "character varying",
                  "izendaDataType": "Text",
                  "allowDistinct": false,
                  "visible": true,
                  "filterable": true,
                  "querySourceId": "00000000-0000-0000-0000-000000000000",
                  "parentId": null,
                  "expressionFields": [],
                  "filteredValue": "",
                  "type": 0,
                  "groupPosition": 0,
                  "position": 0,
                  "extendedProperties": "",
                  "physicalChange": 0,
                  "approval": 0,
                  "existed": false,
                  "matchedTenant": false,
                  "functionName": null,
                  "expression": null,
                  "isRunningField": false,
                  "supportDefaultTotal": null,
                  "fullName": null,
                  "calculatedTree": null,
                  "reportId": null,
                  "originalName": "first_name",
                  "originalId": "00000000-0000-0000-0000-000000000000",
                  "isParameter": false,
                  "isCalculated": false,
                  "hasAggregatedFunction": false,
                  "hasSupportDefaultTotal": true,
                  "querySource": null,
                  "querySourceName": null,
                  "categoryName": null,
                  "inaccessible": false,
                  "originalAlias": null,
                  "allowToSave": false,
                  "fullPath": null,
                  "isCheck": false,
                  "id": "b661eedd-f00c-45c8-a117-063ec3bf7ab4",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "System5 Admin5",
                  "modified": "0001-01-01T00:00:00",
                  "modifiedBy": null
               },
               "numOfChilds": 2,
               "numOfCheckedChilds": 0,
               "indeterminate": false,
               "fullPath": null,
               "computeNameSettings": null,
               "isCheck": false
            }],
            "numOfChilds": 1,
            "numOfCheckedChilds": 0,
            "indeterminate": false,
            "fullPath": null,
            "computeNameSettings": null,
            "isCheck": false
         }],
         "totalItems": 10,
         "numOfChilds": 1,
         "numOfCheckedChilds": 0,
         "indeterminate": false,
         "isLastPage": true
      }