

=======================
QuerySourceInfo
=======================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id of the query source
      -
   *  -  **name** |br|
         string
      -
      -  The query source name
      -
   *  -  **alias** |br|
         string
      -
      -  The alias of the query source
      -
   *  -  **category** |br|
         string
      -
      -  The category name
      -
   *  -  **serverTypeId** |br|
         string (GUID)
      -
      -  The id of the type of database server
      -
   *  -  **connectionStringId** |br|
         string (GUID)
      -
      -  The id of the connection
      -
   *  -  **connectionString** |br|
         string
      -
      -  The connection string
      -
   *  -  **connectionName** |br|
         string
      -
      -  The name of the connection containing the query source
      -
   *  -  **querySourceCategoryName** |br|
         string
      -
      -  The name of the :term:`query source category` containing the query source
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "id": "77882ea1-6d82-45c2-b762-6c8612682b91",
        "name": "Categories",
        "alias": null,
        "category": "dbo",
        "serverTypeId": "00000000-0000-0000-0000-000000000000",
        "connectionStringId": "00000000-0000-0000-0000-000000000000",
        "connectionString": null
      }
