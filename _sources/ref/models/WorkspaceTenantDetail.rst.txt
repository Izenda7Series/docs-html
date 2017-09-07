

=======================
WorkspaceTenantDetail
=======================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **destinationConnections** |br|
         array of objects
      -
      -  An array of :doc:`Connection` objects.
      -
   *  -  **sourceConnections** |br|
         array of objects
      -
      -  An array of :doc:`Connection` objects.
      -
   *  -  **tenantName** |br|
         string
      -
      -  The name of the tenant
      -
   *  -  **tenantUniqueName** |br|
         string
      -
      -  The tenant unique name
      -



Inherited fields:

.. include:: WorkspaceTenant.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "destinationConnections" : [],
         "sourceConnections" : [],
         "tenantName" : "Tenant 1",
         "tenantUniqueName" : "T1",
         "workspaceId" : "49d886bc-45be-4acf-8ebe-4de775546f8c",
         "tenantId" : "9ef4b0af-2485-4050-91b9-cf149d999afd",
         "status" : 0,
         "id" : null,
         "state" : 0,
         "inserted" : true,
         "version" : null,
         "created" : null,
         "createdBy" : null,
         "modified" : null,
         "modifiedBy" : null
      }
