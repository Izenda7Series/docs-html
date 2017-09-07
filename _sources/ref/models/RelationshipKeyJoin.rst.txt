====================
RelationshipKeyJoin
====================


.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **relationshipId** |br|
         string (GUID)
      -
      -  The id of the relationship
      -
   *  -  **operator** |br|
         string
      -
      -  Either "And" or "Or"
      -
   *  -  **joinSourceAlias** |br|
         string
      -
      -  The alias of the join query source
      -
   *  -  **specifictJoinFieldAlias** |br|
         string
      -
      -  The alias to be used in query without generating a new one
      -
   *  -  **foreignSourceAlias** |br|
         string
      -
      -  The alias of the foregin query source
      -
   *  -  **specifictForeignFieldAlias** |br|
         string
      -
      -  The alias to be used in query without generating a new one
      -
   *  -  **position** |br|
         integer
      -
      -  The position of the key join in the relationship
      -
   *  -  **tempId** |br|
         string
      -
      -  The temporary id
      -
   *  -  **joinQuerySourceUniqueName** |br|
         string
      -
      -  Unique name for join query source
      -
   *  -  **joinFieldUniqueName** |br|
         string
      -
      -  Unique name for join field
      -
   *  -  **foreignQuerySourceUniqueName** |br|
         string
      -
      -  Unique name for foreign query source
      -
   *  -  **foreignFieldUniqueName** |br|
         string
      -
      -  Unique name for foreign field
      -
   *  -  **comparisonValue** |br|
         string
      -
      -  The comparison value
      -
   *  -  **selectedJoinSourceAlias** |br|
         string
      -
      -  ``<joinQuerySourceId>_[<joinSourceAlias>|<joinQuerySourceName>]``
      -
   *  -  **selectedForeignSourceAlias** |br|
         string
      -
      -  ``<foreignQuerySourceId>_[<foreignSourceAlias>|<foreignQuerySourceName>]``
      -

Inherited fields:

.. include:: RelationshipBase.rst
