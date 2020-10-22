

=========================================
GlobalDatabaseMapping
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **type** |br|
         integer
      -
      -  *  1 = Schema
         *  2 = Database

      -
   *  -  **fromServer** |br|
         string
      -
      -  The source server
      -
   *  -  **toServer** |br|
         string
      -
      -  The destination server
      -
   *  -  **fromDatabaseName** |br|
         string
      -
      -  The source database name
      -
   *  -  **toDatabaseName** |br|
         string
      -
      -  The destination database name
      -
   *  -  **fromObject** |br|
         string
      -
      -  The source schema (N/A in case of type 2 Database)
      -
   *  -  **toObject** |br|
         string
      -
      -  The destination
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
   *  -  **selectAllTenants** |br|
         boolean
      -
      -  Is option All Tenants selected
      -
   *  -  **tenants** |br|
         array of strings
      -
      -  An array of tenant ids
      -
   *  -  **errorType** |br|
         integer
      -
      -  *  0 = None
         *  1 = Required
         *  2 = Duplicate
         *  3 = MultipleMapping

      -



Inherited fields:

.. include:: Entity.rst
