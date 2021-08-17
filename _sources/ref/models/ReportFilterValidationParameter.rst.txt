=========================================
ReportFilterValidationParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportId** |br|
         string (GUID)
      -
      -  The id of the report
      -
   *  -  **masterReportId** |br|
         string (GUID)
      -  Y
      -  The id of the master report
      -
   *  -  **reportWrapper** |br|
         object
      -  Y
      -  A special object that is a simplified representation :doc:`ReportDefinition` object (used in the Report Designer 2.0).
      -
   *  -  **inheritMasterReportFilter** |br|
         boolean
      -
      -  A flag that determines whether to inherit filters from master report
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "reportId": "90c5ee59-b816-4034-b927-e8f16b1c2759",
         "masterReportId": "ec7efb62-8a54-4803-bce6-5a2b10e6e3bd",
         "reportWrapper": null,
         "inheritMasterReportFilter": true,
      }
