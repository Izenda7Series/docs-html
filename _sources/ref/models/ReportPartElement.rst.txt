
=========================
ReportPartElement
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **name** |br|
         string
      -
      -  The name of the selected data source field
   *  -  **properties** |br|
         object
      -
      -  The properties for the selected data source field |br|
         A :doc:`ReportPartElementProperties` object
   *  -  **position** |br|
         integer
      -
      -  The position in the list of selected items, starting from 0
   *  -  **field** |br|
         object
      -
      -  The data of the selected data source field
   *  -  .. container:: lpad2

            **fieldId** |br|
            string (GUID)
      -
      -  The id of the field
   *  -  .. container:: lpad2

            **fieldName** |br|
            string
      -
      -  The name of the field
   *  -  .. container:: lpad2

            **fieldNameAlias** |br|
            string
      -
      -  The alias of the field
   *  -  .. container:: lpad2

            **dataFieldType** |br|
            string
      -
      -  The Izenda data type
   *  -  .. container:: lpad2

            **querySourceId** |br|
            string (GUID)
      -
      -  The id of the data source
   *  -  .. container:: lpad2

            **querySourceType** |br|
            string
      -
      -  The type of the data source (Table, View or Stored Procedure) or null if it is an alias
   *  -  .. container:: lpad2

            **sourceAlias** |br|
            string
      -
      -  The alias of the data source
   *  -  .. container:: lpad2

            **relationshipId** |br|
            string (GUID)
      -
      -  The id of the alias data source, null if data source is not an alias
   *  -  .. container:: lpad2

            **visible** |br|
            boolean
      -
      -  Is the field visible
   *  -  .. container:: lpad2

            **calculatedTree** |br|
            object
      -
      -  Place-holder
   *  -  .. container:: lpad2

            **schemaName** |br|
            string
      -
      -  The name of the schema of the query source
   *  -  .. container:: lpad2

            **querySourceName** |br|
            string
      -
      -  The name of the query source
   *  -  .. container:: lpad2

            **databaseName** |br|
            string
      -
      -  The name of the connection
   *  -  .. container:: lpad2

            **isCalculated** |br|
            boolean
      -
      -  Is this a calculated field
   *  -  .. container:: lpad2

            **hasAggregatedFunction** |br|
            boolean
      -
      -  In case of calculated field, does it use an aggregated function
