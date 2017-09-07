

========================
WorkspaceMappingDetail
========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **workspaceMappingTenants** |br|
         array of objects
      -
      -  An array of :doc:`WorkspaceMappingTenant` objects.
      -
   *  -  **errorType** |br|
         integer
      -
      -  The type of the error
      -




Inherited fields:

.. include:: WorkspaceMapping.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "workspaceMappingTenants" : [],
         "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
         "fromDatabaseName" : "[MSSQL] Northwind",
         "type" : 2,
         "fromObject" : "",
         "toDatabaseName" : "",
         "toObject" : "",
         "isGlobal" : false,
         "id" : "b0cd65d5-762a-48be-afc8-5bc9678aebd0",
         "state" : 0,
         "inserted" : true,
         "version" : null,
         "created" : null,
         "createdBy" : null,
         "modified" : null,
         "modifiedBy" : null
      }
