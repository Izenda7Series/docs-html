===========================
TenantGroupHierarchicalData
===========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 45 25

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantGroupId** |br|
         string (GUID)
      -
      -  The tenant group ID.
      -
   *  -  **tenantGroupName** |br|
         string
      -
      -  The tenant group name.
      -
   *  -  **tenantId** |br|
         string (GUID)
      -
      -  The tenant ID.
      -
   *  -  **tenantName** |br|
         string
      -
      -  The tenant name.
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "tenantGroupId": "095e50a7-11cf-47cf-a8a0-06125cc3f30b",
         "tenantGroupName": "TenantGroup1",
         "tenantId": "723f9b74-2cd7-4eff-8813-00dc86feea16",
         "tenantName": "Tenant1"
      }