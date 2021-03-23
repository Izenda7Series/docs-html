Entity
^^^^^^^^

.. list-table::
   :header-rows: 1
   :widths: 25 5 45 25

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id of this object |br|
         Example: ``572bd576-8c92-4901-ab2a-b16e38144813``
      -  Allow null incase insert a new entity
   *  -  **state** |br|
         integer
      -
      -  The entity state of this object

         - 0 = None
         - 1 = Insert
         - 2 = Delete
         - 3 = Update
      -
   *  -  **deleted** |br|
         boolean
      -
      -  Is this object deleted
      -
   *  -  **inserted** |br|
         boolean
      -
      -  Is this object inserted
      -
   *  -  **version** |br|
         string
      -  Y
      -  The version
      -
   *  -  **created** |br|
         datetime in ISO 8601 format
      -  Y
      -  The created datetime
      -
   *  -  **createdBy** |br|
         string
      -
      -  The creator
      -
   *  -  **modified** |br|
         datetime in ISO 8601 format
      -  Y
      -  The modification datetime
      -
   *  -  **modifiedBy** |br|
         string
      -
      -  The user who last modified this object
      -
