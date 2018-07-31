=============
Relationship
=============


.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **joinConnectionId** |br|
         string (GUID)
      -  Y
      -  The id of the connection containing the relationship
      -
   *  -  **foreignConnectionId** |br|
         string (GUID)
      -  Y
      -  The id of the connection of the query source referenced by the relationship
      -
   *  -  **joinQuerySourceAlias** |br|
         string
      -
      -  The alias of the query source containing the relationship
      -
   *  -  **foreignQuerySourceAlias** |br|
         string
      -
      -  The alias of the query source referenced by the relationship
      -
   *  -  **joinFieldAlias** |br|
         string
      -
      -  The alias of the join field
      -
   *  -  **specifictJoinFieldAlias** |br|
         string
      -
      -  The alias to be used in query without generating a new one
      -
   *  -  **foreignFieldAlias** |br|
         string
      -
      -  The alias of the foreign field
      -
   *  -  **specifictForeignFieldAlias** |br|
         string
      -
      -  The alias to be used in query without generating a new one
      -
   *  -  **alias** |br|
         string
      -
      -  The alias of the join query soure in relationship
      -
   *  -  **systemRelationship** |br|
         boolean
      -
      -  Is this relationship from physical database (cannot be deleted)
      -
   *  -  **joinType** |br|
         string
      -
      -  Either 'Inner', 'Left', 'Right', 'Full' or 'Cross'
      -
   *  -  **parentRelationshipId** |br|
         string (GUID)
      -  Y
      -  The id of the parent relationship - in case this is cloned from a physical relationship
      -
   *  -  **position** |br|
         string
      -
      -  Place-holder
      -
   *  -  **relationshipPosition** |br|
         integer
      -
      -  The ordinal position of this relationship inside a list of relationships
      -
   *  -  **relationshipKeyJoins** |br|
         array of objects
      -
      -  An array of :doc:`RelationshipKeyJoin` objects
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the parent report, in case this is a relationship in a report
      -
   *  -  **foreignAlias** |br|
         string
      -
      -  The foreign alias
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
   *  -  **tempId** |br|
         string
      -
      -  The temporary id
      -
   *  -  **aliasTempId** |br|
         string
      -
      -  Place-holder
      -
   *  -  **originalId** |br|
         string (GUID)
      -
      -  The original id of the relationship - in case this is cloned from a physical relationship
      -
   *  -  **isForeignDataObjectAlias** |br|
         boolean
      -
      -  Whether this instance is foreign data object alias
      -
   *  -  **selectedForeignAlias** |br|
         string
      -
      -  ``<foreignQuerySourceId>_[<foreignAlias>|<foreignQuerySourceName>]``
      -
   *  -  **hasBeenModified** |br|
         boolean

         .. versionadded:: 2.11.0
      -
      -  Whether the relationship has been modified or not
      -

Inherited fields:

.. include:: RelationshipBase.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "joinConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
         "foreignConnectionId" : "ca24a47e-ffdd-4391-a82a-254f48b451e5",
         "joinQuerySourceId" : "e03b8805-60ae-41df-b69a-f3bece9721c5",
         "joinQuerySourceName" : "EmployeeDepartmentHistory",
         "joinDataSourceCategoryName" : null,
         "joinDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
         "foreignDataSourceCategoryName" : null,
         "foreignDataSourceCategoryId" : "00000000-0000-0000-0000-000000000000",
         "foreignQuerySourceId" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92",
         "foreignQuerySourceName" : "Employee",
         "joinFieldId" : "322d9f3d-1f65-4d60-9cac-933a2c40db9d",
         "joinFieldName" : "BusinessEntityID",
         "foreignFieldId" : "484817ea-f130-417b-a096-32c13249b7d0",
         "foreignFieldName" : "BusinessEntityID",
         "alias" : "abc",
         "systemRelationship" : true,
         "joinType" : "Inner",
         "parentRelationshipId" : "00000000-0000-0000-0000-000000000000",
         "deleted" : false,
         "position" : null,
         "relationshipKeyJoins" : null,
         "reportId" : "00000000-0000-0000-0000-000000000000",
         "foreignAlias" : null,
         "selectedForeignAlias" : "9fb719f8-8a70-4f4e-91d5-4e8372413d92_Employee",
         "id" : "48ab1f19-db84-4d8b-9c18-02312d16c282",
         "state" : 0,
         "modified" : "2016-04-15T06:27:16.023"
      }
