
==============
DBSetupInfo
==============

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **serverTypeId** |br|
         string (GUID)
      -
      -  The id of the server type
      -
   *  -  **serverTypeName** |br|
         string
      -
      -  The name of the server type
      -
   *  -  **connectionString** |br|
         string
      -
      -  The connection string
      -
   *  -  **connectionId** |br|
         string (GUID)
      -
      -  The id of the connection
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "ServerTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813",
        "ConnectionString" : "server=host01\\instance01;database=db01;User Id=user01;Password=secret;"
      }
