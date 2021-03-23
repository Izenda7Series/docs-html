

=========================
QuerySourceField
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **alias** |br|
         string
      -
      -  The alias entered by user
      -
   *  -  **allowDistinct** |br|
         boolean
      -
      -  Does the data type allow distinct select or not
      -
   *  -  **approval** |br|
         boolean
      -
      -  Is the change approved
      -
   *  -  **calculatedTree** |br|
         object
      -
      -  The calculated tree
      -
   *  -  **categoryName** |br|
         string
      -
      -  The name of the :term:`query source category`
      -
   *  -  **checked** |br|
         boolean

         .. versionadded:: 3.11.0
      -
      -  Is the field checked for some operations or not (like for PII/Data Security)
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type of the field
      -
   *  -  **existed** |br|
         boolean
      -
      -  Exist flag
      -
   *  -  **expression** |br|
         string
      -
      -  The calculated expression in case this is a calculated field
      -
   *  -  **expressionFields** |br|
         array of objects
      -  Y
      -  An array of :doc:`ReportField` objects
      -
   *  -  **extendedProperties** |br|
         string
      -
      -  The extended properties (for stored procedures and functions)
      -
   *  -  **filterable** |br|
         boolean
      -
      -  Is the field selected to be filterable in report
      -
   *  -  **filteredValue** |br|
         string
      -
      -  The filter value in json format - when the field is a stored procedure parameter
      -
   *  -  **filterStatus** |br|
         integer

         .. versionadded:: 2.14.0
      -
      -  The status of filter lookup key-value

            *  0: valid lookup (default state)
            *  1: invalid query source
            *  2: invalid database connection
            *  4: lookup key is a Tenant Field
            *  8: lookup key is invisible
            *  16: display value is a Tenant Field
            *  32: display value is invisible
         
         **Note:** If multiple errors occur at the same time, system will return the sum of error code.
      -
   *  -  **fullName** |br|
         string
      -
      -  The fully-qualified name of the field
      -
   *  -  **functionName** |br|
         string
      -
      -  Place-holder
      -
   *  -  **groupPosition** |br|
         integer
      -
      -  The group position
      -
   *  -  **hasAggregatedFunction** |br|
         boolean
      -
      -  Whether this calculated field contains an aggregated function
      -
   *  -  **hasFilterLookup** |br|
         boolean

         .. versionadded:: 2.14.0
      -
      -  Whether this field has filter lookup setting or not
      -
   *  -  **inaccessible** |br|
         boolean
      -
      -  Whether this is inaccessible
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  *  true if 0 < numOfCheckedChilds < numOfChilds
         *  false if not
      -
   *  -  **isCalculated** |br|
         boolean
      -
      -  Is this a calculated field
      -
   *  -  **isCheck** |br|
         boolean
      -
      -  Whether this is selected in workspace for copying
      -
   *  -  **isParameter** |br|
         boolean
      -
      -  Is this a stored procedure parameter (or a normal field)
      -
   *  -  **izendaDataType** |br|
         string
      -
      -  The mapped data type of the field
      -
   *  -  **matchedTenant** |br|
         boolean
      -
      -  Is this query source field hidden from view because it is a tenant field (in Tenant Field setting), and current Show Tenant Field setting is false.

         .. seealso::

            :ref:`Update_settings_in_Security_Additive_Fields_group`
      -
   *  -  **name** |br|
         string
      -
      -  The name of the query source field
      -
   *  -  **numOfCheckedChilds** |br|
         integer
      -
      -  The number of selected children
      -
   *  -  **numOfChilds** |br|
         integer
      -
      -  The number of children
      -
   *  -  **originalAlias** |br|
         string
      -
      -  The original alias
      -
   *  -  **originalId** |br|
         string (GUID)
      -
      -  The original id of the field - in case this field is cloned from a physical field
      -
   *  -  **originalName** |br|
         string
      -
      -  The original name of the field - in case this field is cloned from a physical field
      -
   *  -  **parentId** |br|
         string (GUID)
      -  Y
      -  The id of the parent of the parent query source
      -
   *  -  **physicalChange** |br|
         integer
      -
      -  Has the field changed

         -  0 = None
         -  1 = Added
         -  2 = Modified
         -  3 = Deleted
      -
   *  -  **position** |br|
         integer
      -
      -  The ordinal position of the field inside the query source
      -
   *  -  **querySource** |br|
         object
      -
      -  The parent :doc:`QuerySource` object
      -
   *  -  **querySourceId** |br|
         string (GUID)
      -
      -  The id of the parent query source
      -
   *  -  **querySourceName** |br|
         string
      -
      -  The name of the parent query source
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the parent report - in case this is a calculated field
      -
   *  -  **type** |br|
         integer
      -
      -

         -  0 = Field
         -  1 = Parameter
      -
   *  -  **visible** |br|
         boolean
      -
      -  Is the field selected to be visible in report
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
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
      }
