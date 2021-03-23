


WorkspaceMapping
-------------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **workspaceId** |br|
         string (GUID)
      -  Y
      -  The id of the workspace tenant
      -
   *  -  **type** |br|
         integer
      -
      -  The type of the database in Source

         * 1 = Schema
         * 2 = Database
      -
   *  -  **fromServer** |br|
         string
      -
      -  The from server
      -
   *  -  **toServer** |br|
         string
      -
      -  The to server
      -
   *  -  **fromDatabaseName** |br|
         string
      -
      -  The name of the database in Source
      -
   *  -  **toDatabaseName** |br|
         string
      -
      -  The name of the database in Destination
      -
   *  -  **fromObject** |br|
         string
      -
      -  The name of the object in Source
      -
   *  -  **toObject** |br|
         string
      -
      -  The name of the object in Destination
      -
   *  -  **fromDatabaseUser** |br|
         string

         .. versionadded:: 3.10.0
      -
      -  The source (encrypted) database username
      -
   *  -  **toDatabaseUser** |br|
         string

         .. versionadded:: 3.10.0
      -
      -  The destination (encrypted) database username
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Is this a global mapping
      -


Inherited fields:

.. include:: Entity.rst
