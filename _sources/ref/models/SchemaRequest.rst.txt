

=========================================
SchemaRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **serverTypeId** |br|
         string (GUID)
      -
      -  The id of the server type
      -
   *  -  **connectionString** |br|
         string
      -
      -  The connection string
      -
   *  -  **connectionId** |br|
         string (GUID)
      -  Y
      -  The id of the connection
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "connectionId" : "d91ee45e-f168-441d-81eb-7878cb2fa2ce",
        "connectionString" : "1aBcD+=",
        "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813"
      }
