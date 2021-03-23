

=================
RelationshipOrder
=================


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
      -  The alias
      -
   *  -  **joinQuerySourceId** |br|
         string (GUID)
      -  Y
      -  The id of the query source containing the relationship
      -
   *  -  **selectedForeignAlias** |br|
         string
      -
      -  The foreign alias of the selected relationship
      -
   *  -  **relationshipPosition** |br|
         integer
      -
      -  The ordinal position of this relationship inside a list of relationships
      -
   *  -  **convertedKeyJoinIds** |br|
         an array of string(GUID)

         .. versionadded:: 2.11.0
      -
      -  The relationship ids that converted to key join
      -
   *  -  **hasBeenModified** |br|
         boolean

         .. versionadded:: 2.11.0
      -
      -  Whether the relationship has been modified or not
      -
