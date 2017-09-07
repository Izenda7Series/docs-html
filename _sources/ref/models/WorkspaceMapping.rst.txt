


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
   *  -  **type** |br|
         integer
      -
      -  The type of the database in Source

         * 1 = Schema
         * 2 = Database
      -
   *  -  **fromObject** |br|
         string
      -
      -  The name of the object in Source
      -
   *  -  **toDatabaseName** |br|
         string
      -
      -  The name of the database in Destination
      -
   *  -  **toObject** |br|
         string
      -
      -  The name of the object in Destination
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Is this a global mapping
      -


Inherited fields:

.. include:: Entity.rst
