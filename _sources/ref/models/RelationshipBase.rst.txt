


RelationshipBase
-------------------


.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **joinQuerySourceName** |br|
         string
      -
      -  The alias/name of the query source containing the relationship
      -
   *  -  **joinQuerySourceId** |br|
         string (GUID)
      -
      -  The id of the query source containing the relationship
      -
   *  -  **joinFieldId** |br|
         string (GUID)
      -  Y
      -  The id of the referencing field
      -
   *  -  **joinFieldType** |br|
         string
      -
      -  Place-holder
      -
   *  -  **foreignQuerySourceName** |br|
         string
      -
      -  The alias/name of the query source referenced by the relationship
      -
   *  -  **foreignQuerySourceId** |br|
         string (GUID)
      -
      -  The id of the query source referenced by the relationship
      -
   *  -  **foreignFieldId** |br|
         string (GUID)
      -  Y
      -  The id of the field referenced by the relationship
      -
   *  -  **foreignFieldType** |br|
         string
      -
      -  Place-holder
      -
   *  -  **joinFieldName** |br|
         string
      -
      -  The alias/name of the referencing field
      -
   *  -  **foreignFieldName** |br|
         string
      -
      -  The alias/name of the field referenced by the relationship
      -
   *  -  **joinDataSourceCategoryId** |br|
         string (GUID)
      -
      -  The id of the category of the query source containing the relationship
      -
   *  -  **joinDataSourceCategoryName** |br|
         string
      -
      -  The name of the category of the query source containing the relationship
      -
   *  -  **foreignDataSourceCategoryId** |br|
         string (GUID)
      -
      -  The id of the category of the query source referenced by the relationship
      -
   *  -  **foreignDataSourceCategoryName** |br|
         string
      -
      -  The name of the category of the query source referenced by the relationship
      -
   *  -  **comparisonOperator** |br|
         string
      -
      -  The comparison operator
      -




Inherited fields:

.. include:: Entity.rst
