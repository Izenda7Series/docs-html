

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
   *  -  **name** |br|
         string
      -
      -  The name of the query source field
      -
   *  -  **alias** |br|
         string
      -
      -  The alias entered by user
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type of the field
      -
   *  -  **izendaDataType** |br|
         string
      -
      -  The mapped data type of the field
      -
   *  -  **allowDistinct** |br|
         boolean
      -
      -  Does the data type allow distinct select or not
      -
   *  -  **visible** |br|
         boolean
      -
      -  Is the field selected to be visible in report
      -
   *  -  **filterable** |br|
         boolean
      -
      -  Is the field selected to be filterable in report
      -
   *  -  **querySourceId** |br|
         string (GUID)
      -
      -  The id of the parent query source
      -
   *  -  **parentId** |br|
         string (GUID)
      -  Y
      -  The id of the parent of the parent query source
      -
   *  -  **expressionFields** |br|
         array of objects
      -  Y
      -  An array of :doc:`ReportField` objects
      -
   *  -  **filteredValue** |br|
         string
      -
      -  The filter value in json format - when the field is a stored procedure parameter
      -
   *  -  **type** |br|
         integer
      -
      -

         -  0 = Field
         -  1 = Parameter
      -
   *  -  **groupPosition** |br|
         integer
      -
      -  The group position
      -
   *  -  **position** |br|
         integer
      -
      -  The ordinal position of the field inside the query source
      -
   *  -  **extendedProperties** |br|
         string
      -
      -  The extended properties (for stored procedures and functions)
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
   *  -  **matchedTenant** |br|
         boolean
      -
      -  Is this query source field hidden from view because it is a tenant field (in Tenant Field setting), and current Show Tenant Field setting is false.

         .. seealso::

            :ref:`Update_settings_in_Performance_Security_Additive_Fields_and_Others_group`
      -
   *  -  **functionName** |br|
         string
      -
      -  Place-holder
      -
   *  -  **expression** |br|
         string
      -
      -  The calculated expression in case this is a calculated field
      -
   *  -  **fullName** |br|
         string
      -
      -  The fully-qualified name of the field
      -
   *  -  **calculatedTree** |br|
         object
      -
      -  The calculated tree
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the parent report - in case this is a calculated field
      -
   *  -  **originalName** |br|
         string
      -
      -  The original name of the field - in case this field is cloned from a physical field
      -
   *  -  **originalId** |br|
         string (GUID)
      -
      -  The original id of the field - in case this field is cloned from a physical field
      -
   *  -  **isParameter** |br|
         boolean
      -
      -  Is this a stored procedure parameter (or a normal field)
      -
   *  -  **isCalculated** |br|
         boolean
      -
      -  Is this a calculated field
      -
   *  -  **hasAggregatedFunction** |br|
         boolean
      -
      -  Whether this calculated field contains an aggregated function
      -
   *  -  **querySource** |br|
         object
      -
      -  The parent :doc:`QuerySource` object
      -
   *  -  **querySourceName** |br|
         string
      -
      -  The name of the parent query source
      -
   *  -  **categoryName** |br|
         string
      -
      -  The name of the :term:`query source category`
      -
   *  -  **inaccessible** |br|
         boolean
      -
      -  Whether this is inaccessible
      -
   *  -  **originalAlias** |br|
         string
      -
      -  The original alias
      -
   *  -  **isCheck** |br|
         boolean
      -
      -  Whether this is selected in workspace for copying
      -
   *  -  **numOfChilds** |br|
         integer
      -
      -  The number of children
      -
   *  -  **numOfCheckedChilds** |br|
         integer
      -
      -  The number of selected children
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  *  true if 0 < numOfCheckedChilds < numOfChilds
         *  false if not
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
