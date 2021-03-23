

FilterField
------------------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **filterId** |br|
         string (GUID)
      -
      -  The id of the filter
      -
   *  -  **reportFieldAlias** |br|
         string
      -
      -  The alias of the field
      -
   *  -  **reportPartTitle** |br|
         string
      -
      -  The report part title
      -
   *  -  **querySourceFieldId** |br|
         string (GUID)
      -  
      -  The id of the query source field
      -
   *  -  **querySourceType** |br|
         string
      -
      -  Either "Table", "View", "Stored Procedure" or "Function"
      -
   *  -  **querySourceId** |br|
         string (GUID)
      -  Y
      -  The id of the query source
      -
   *  -  **relationshipId** |br|
         string (GUID)
      -  Y
      -  The id of the relationship if this field is in a relationship
      -
   *  -  **alias** |br|
         string
      -
      -  The alias of the field
      -
   *  -  **position** |br|
         integer
      -
      -  The position in the list of filters
      -
   *  -  **visible** |br|
         boolean
      -
      -  Is the filter field visible
      -
   *  -  **required** |br|
         boolean
      -
      -  Is the filter field required
      -
   *  -  **cascading** |br|
         boolean
      -
      -  Whether common filter field will be cascaded
      -
   *  -  **operatorId** |br|
         string (GUID)
      -  Y
      -  The id of the operator
      -
   *  -  **operatorSetting** |br|
         string
      -
      -  The operator setting
      -
   *  -  **value** |br|
         string
      -
      -  The value for the filter field and the selected operator
      -
   *  -  **dataFormatId** |br|
         string (GUID)
      -  Y
      -  The id of the display format for the filter field
      -
   *  -  **sortType** |br|
         string
      -
      -  Either "Unsorted", "Ascending" or "Descending"
      -
   *  -  **fontFamily** |br|
         string
      -
      -  The font family
      -
   *  -  **fontSize** |br|
         integer
      -
      -  The font size
      -
   *  -  **textColor** |br|
         string
      -
      -  The text color
      -
   *  -  **backgroundColor** |br|
         string
      -
      -  The background color
      -
   *  -  **fontBold** |br|
         boolean
      -
      -  Is the text in bold
      -
   *  -  **fontItalic** |br|
         boolean
      -
      -  Is the text in italic
      -
   *  -  **fontUnderline** |br|
         boolean
      -
      -  Is the text underlined
      -
   *  -  **querySourceUniqueName** |br|
         string
      -
      -  A unique name for query source
      -
   *  -  **querySourceFieldName** |br|
         string
      -
      -  The name of query source field
      -
   *  -  **comparisonFieldUniqueName** |br|
         string
      -
      -  The unique name for comparison field
      -
   *  -  **isNegative** |br|
         boolean
      -
      -  Whether this filter field is indeterminate
      -

Inherited fields:

.. include:: Entity.rst
