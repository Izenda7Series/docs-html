=========================================
ReportFilterField
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **connectionName** |br|
         string
      -
      -  The name of the connection
      -
   *  -  **querySourceCategoryName** |br|
         string
      -
      -  The name of the category of the data source
      -
   *  -  **sourceFieldName** |br|
         string
      -
      -  The name of the data source field
      -
   *  -  **sourceFieldVisible** |br|
         boolean
      -
      -  Is the data source field selected to be visible in Data Model
      -
   *  -  **sourceFieldFilterable** |br|
         boolean
      -
      -  Is the data source field selected to be filterable in Data Model
      -
   *  -  **sourceDataObjectName** |br|
         string
      -
      -  The name of the data source
      -
   *  -  **sourceDataObjectFullName** |br|
         string
      -
      -  The fully-qualified name of the data source
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type of the data source field
      -
   *  -  **isParameter** |br|
         boolean
      -
      -  Is the filter field a stored procedure parameter
      -
   *  -  **isCalculated** |br|
         boolean
      -
      -  Is this a calculated field
      -
   *  -  **calculatedTree** |br|
         string
      -
      -  The calculated tree
      -
   *  -  **compareFieldCalculatedTree** |br|
         string
      -
      -  The compare field calculated tree used for filter field comparison
      -
   *  -  **compareField** |br|
         string (GUID)
      -  Y
      -  The id of the compare field - used for filter field comparison
      -
   *  -  **selected** |br|
         boolean
      -
      -  Is the filter field selected
      -
   *  -  **dataFormat** |br|
         object
      -
      -  A :doc:`DataFormat` object
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report
      -
   *  -  **useMappedFieldAlias** |br|
         boolean
      -
      -  Internal use: whether filter uses mapped field alias, if yes, it will not be re-calculated to generate expression.
      -
   *  -  **uniqueId** |br|
         string (GUID)
      -
      -  The unique id for :term:`Front-end` to show specific error messages
      -
   *  -  **comparisonValue** |br|
         string
      -
      -  The comparison value
      -
   *  -  **inTimePeriodType** |br|
         string
      -
      -  The type of custom in time period
      -
   *  -  **valueInTimePeriod** |br|
         string
      -
      -  The value of custom in time period
      -
   *  -  **hasModifiedCalculatedTree** |br|
         boolean
      -
      -  Whether this instance has modified calculated tree
      -
   *  -  **isHiddenFilter** |br|
         boolean
      -
      -  Whether this instance is hidden filter
      -
   *  -  **isInheritableFilter** |br|
         boolean
      -
      -  Whether this filter is inherited from its master report
      -
   *  -  **operatorName** |br|
         string
      -
      -  The name of the operator
      -
   *  -  **filterLookupType** |br|
         int

         .. versionadded:: 2.15.0
      -
      -  Determine the type of lookup setting: |br|
      
            \- 0: No filter lookup |br|
            \- 1: Filter lookup key-value |br|
            \- 2: User defined user lookup |br|
      -
   *  -  **useLookup** |br|
         boolean

         .. versionadded:: 2.15.0
      -
      -  Whether use lookup key-value setting or not
      -
   *  -  **hasFilterLookup** |br|
         boolean

         Obsolete from version 2.15.0
      -
      -  Whether this field has filter lookup setting or not
      -
   *  -  **isOveridingInheritedFilter** |br|
         boolean

         .. versionadded:: 2.15.1
      -
      -  Whether the master filter value overrides the sub filter value
      -

Inherited fields:

.. include:: FilterField.rst



.. container:: toggle

   .. container:: header

      **ReportFilterField Sample**:

   .. code-block:: json

      {
         "connectionName" : "Northwind",
         "querySourceCategoryName" : "dbo",
         "sourceFieldName" : "ShipCountry",
         "sourceFieldVisible" : true,
         "sourceFieldFilterable" : true,
         "sourceDataObjectName" : "Orders",
         "dataType" : "Text",
         "filterId" : "00000000-0000-0000-0000-000000000000",
         "querySourceFieldId" : "d0f88020-8d3f-4f80-a1ac-0c187f87dfd3",
         "querySourceType" : "Table",
         "querySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
         "relationshipId" : null,
         "alias" : "ShipCountry",
         "position" : 1,
         "visible" : false,
         "required" : false,
         "cascading" : true,
         "operatorId" : "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
         "operatorSetting" : null,
         "value" : "'US'",
         "sortType" : "Unsorted",
         "fontFamily" : null,
         "fontSize" : 0,
         "textColor" : null,
         "backgroundColor" : null,
         "fontBold" : false,
         "fontItalic" : false,
         "fontUnderline" : false,
         "id" : "00000000-0000-0000-0000-000000000000",
         "status" : 0,
         "modified" : null,
         "dateTimeNow" : "2016-06-13T07:23:25.9138114Z",
         "isParameter" : false,
         "sourceDataObjectFullName" : "Northwind.dbo.Orders",
         "selected" : false
      }
