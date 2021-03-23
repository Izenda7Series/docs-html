

=========================================
SharingRoleUserParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The tenant id
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The report id
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The dashboard id
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Whether to set roles for global reports
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "reportId": "63d50ed1-5323-47a1-bc11-3a03a070ec34",
        "tenantId": null
      }
