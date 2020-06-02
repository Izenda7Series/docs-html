

==========================
Connection
==========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id of the connection
      -
   *  -  **name** |br|
         string
      -
      -  The name of the connection
      -
   *  -  **originalName** |br|
         string
      -
      -  The original name of the connection
      -
   *  -  **serverTypeId** |br|
         string (GUID)
      -
      -  The id of the server type
      -
   *  -  **databaseServer** |br|
         string
      -
      -  The database address
      -
   *  -  **serverTypeName** |br|
         string
      -
      -  The type of the server
      -
   *  -  **connectionString** |br|
         string
      -
      -  The connection string
      -
   *  -  **visible** |br|
         boolean
      -
      -  Whether this is visible in Data Model
      -
   *  -  **deleted** |br|
         boolean
      -
      -  Whether this is deleted
      -
   *  -  **relateToConnectionId** |br|
         string (GUID)
      -  Y
      -  The id of the related connection
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **dBSource** |br|
         object
      -
      -  A :doc:`DBSource` object
      -
   *  -  **relationships** |br|
         array of objects
      -
      -  An array of :doc:`Relationship` objects
      -
   *  -  **physicalChange** |br|
         integer
      -
      -  The change status
      -
   *  -  **copyDataConnector** |br|
         boolean
      -
      -  Is selected for copy in Copy Management (only data connector mode)
      -  .. versionadded:: 3.9.3
   *  -  **checked** |br|
         boolean
      -
      -  Is selected for copy in Copy Management
      -
   *  -  **databaseName** |br|
         string
      -
      -  The name of the database
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
           "id" : "89e91284-6546-44d0-8de0-f8f666a590ea",
           "name" : "Northwind",
           "serverType" : "d968e96f-91dc-414d-9fd8-aef2926c9a18",
           "serverTypeName" : "AZSQL",
           "connectionString" : "1aBcD+==",
           "visible" : true,
           "deleted" : false,
           "relateToConnectionId" : null,
           "tenantId" : null,
           "dBSource" : null,
           "relationships" : null,
           "physicalChange" : 0
      }
