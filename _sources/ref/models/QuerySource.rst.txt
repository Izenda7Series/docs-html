

=======================
QuerySource
=======================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id
      -
   *  -  **name** |br|
         string
      -
      -  The query source name qualified with schema name |br|
         Example: ``dbo.Table1``
      -
   *  -  **realName** |br|
         string
      -
      -  The name of the query source
      -
   *  -  **type** |br|
         string
      -
      -  Either "Table", "View", "Stored Procedure" or "Function"
      -
   *  -  **parentQuerySourceId** |br|
         string (GUID)
      -  Y
      -  Place-holder
      -
   *  -  **categoryId** |br|
         string (GUID)
      -  Y
      -  The id of the category (user schema)
      -
   *  -  **selected** |br|
         boolean
      -
      -  Is this query source selected in data model
      -
   *  -  **deleted** |br|
         boolean
      -
      -  Is this query source removed from data model
      -
   *  -  **connectionId** |br|
         string (GUID)
      -
      -  The id of the connection containing the query source
      -
   *  -  **connectionName** |br|
         string
      -
      -  The name of the connection containing the query source
      -
   *  -  **childs** |br|
         array of objects
      -  Y
      -  An array of children QuerySource objects if available
      -
   *  -  **dataSourceCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the :term:`data source category` containing the query source
      -
   *  -  **dataSourceCategoryName** |br|
         string
      -
      -  The name of the :term:`data source category` containing the query source
      -
   *  -  **alias** |br|
         string
      -
      -  The alias entered by user
      -
   *  -  **originalAlias** |br|
         string
      -
      -  The original alias
      -
   *  -  **querySourceFields** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceField` objects
      -
   *  -  **querySourceCategoryName** |br|
         string
      -
      -  The schema name
      -
   *  -  **querySourceCategory** |br|
         object
      -
      -  A :doc:`QuerySourceCategory` object (schema)
      -
   *  -  **modified** |br|
         datetime in ISO 8601 format
      -  Y
      -  The modification time
      -
   *  -  **extendedProperties** |br|
         string
      -
      -  The extended properties if available  (for stored procedures)
      -
   *  -  **physicalChange** |br|
         integer
      -
      -  Has the query source changed

         -  0 = None
         -  1 = Added
         -  2 = Modified
         -  3 = Deleted
      -
   *  -  **approval** |br|
         boolean
      -
      -  Is the change approved
      -
   *  -  **existed** |br|
         boolean
      -
      -  Exist flag
      -
   *  -  **checked** |br|
         boolean
      -
      -  Is selected for copy in Copy Management
      -
   *  -  **belongToCopiedReport** |br|
         boolean
      -
      -  Whether this query source belongs to a copied report
      -
   *  -  **customDefinition** |br|
         string
      -
      -  Definition of the view in case this is a custom query source
      -
   *  -  **isCustomQuerySource** |br|
         boolean
      -
      -  Whether this is a custom query source
      -
   *  -  **disable** |br|
         boolean
      -
      -  Whether this query source is a real query source and has a custom query source which has the same name
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
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
