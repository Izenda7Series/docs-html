

=========================================
ReportField
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **fieldId** |br|
         string (GUID)
      -
      -  The id of the field
      -
   *  -  **fieldUniqueName** |br|
         string
      -
      -  Unique name for the field
      -
   *  -  **originalName** |br|
         string
      -
      -  The original name of the field
      -
   *  -  **fieldName** |br|
         string
      -
      -  The name of the field
      -
   *  -  **fieldNameAlias** |br|
         string
      -
      -  The alias of the field
      -
   *  -  **dataFieldType** |br|
         string
      -
      -  The data type
      -
   *  -  **querySourceId** |br|
         string (GUID)
      -  Y
      -  The id of the query source
      -
   *  -  **querySourceUniqueName** |br|
         string
      -
      -  Unique name for the query source
      -
   *  -  **querySourceType** |br|
         string
      -
      -  Either "Table", "View", "Stored Procedure" or "Function"
      -
   *  -  **sourceAlias** |br|
         string
      -
      -  The source alias
      -
   *  -  **querySourceAlias** |br|
         string
      -
      -  The alias of the query source
      -
   *  -  **relationshipId** |br|
         string (GUID)
      -
      -  The id of the relationship if applicable
      -
   *  -  **visible** |br|
         boolean
      -
      -  Is the field visible
      -
   *  -  **filterable** |br|
         boolean
      -
      -  Is the field filterable
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report of applicable
      -
   *  -  **fieldFunctionExpression** |br|
         string
      -
      -  The expression for field function
      -
   *  -  **expression** |br|
         string
      -
      -  The calculated expression
      -
   *  -  **grandTotalExpression** |br|
         string
      -
      -  The grand total expression
      -
   *  -  **grandTotalFormat** |br|
         string
      -
      -  Format for the grand total
      -
   *  -  **subTotalExpression** |br|
         string
      -
      -  The sub total expression
      -
   *  -  **subtotalFormat** |br|
         string
      -
      -  Format for the sub total
      -
   *  -  **sort** |br|
         string
      -
      -  Either "Unsorted", "Ascending" or "Descending"
      -
   *  -  **autoSort** |br|
         boolean
      -
      -  Internal use: whether the field is automatically sorted
      -
   *  -  **function** |br|
         string
      -
      -  The function
      -
   *  -  **formatting** |br|
         object
      -
      -  A :doc:`DataFormating` object
      -
   *  -  **functionDataType** |br|
         string
      -
      -  The result data type of the function
      -
   *  -  **isCalculated** |br|
         boolean
      -
      -  Is this a calculated field
      -
   *  -  **hasAggregatedFunction** |br|
         boolean
      -
      -  Whether this field uses aggregated function
      -
   *  -  **invalidField** |br|
         integer
      -
      -  Invalid field setting
      -
   *  -  **isCrossFilter** |br|
         boolean
      -
      -  Whether this instance is cross filter
      -

.. container:: toggle

   .. container:: header

      **ReportField Sample**:

   .. code-block:: json

      {
         "fieldId" : "76139896-c2c3-432e-898a-2c2205bb2e35",
         "fieldName" : "Country",
         "fieldNameAlias" : "Country",
         "dataFieldType" : "Text",
         "querySourceId" : "1641cb37-b60c-42bc-b986-c51667e8037d",
         "querySourceType" : "Table",
         "sourceAlias" : "Suppliers",
         "relationshipId" : null,
         "visible" : true,
         "calculatedTree" : null,
         "schemaName" : "dbo",
         "querySourceName" : "Suppliers",
         "databaseName" : "Northwind",
         "isCalculated" : false
      }
