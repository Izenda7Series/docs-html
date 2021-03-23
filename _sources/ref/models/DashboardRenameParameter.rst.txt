

=========================================
DashboardRenameParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **name** |br|
         string
      -
      -  The new name of the dashboard
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "tenantId" : null,
        "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f",
        "name" : "TestDashboard02"
      }
