

=========================================
ReportKey
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **key** |br|
         string (GUID)
      -  Y
      -  The id of the report
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **modified** |br|
         datetime
      -
      -  The modification date time
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "reportKey" : {
           "key" : "552d20ce-1269-4cb4-a679-0cd51d3e2058"
        }
      }
