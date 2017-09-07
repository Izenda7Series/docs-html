

=========================================
ReportValidation
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportName** |br|
         string
      -
      -  The name of the report
      -
   *  -  **categoryName** |br|
         string
      -
      -  The name of the category |br|
         Used in :ref:`POST_report/validateExistingReport`
      -
   *  -  **subCategoryName** |br|
         string
      -
      -  The name of the sub-category |br|
         Used in :ref:`POST_report/validateExistingReport`
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **columnFullReference** |br|
         array of strings
      -
      -  An array of column names to be validated |br|
         Used in :ref:`POST_report/validateExistingField`
      -
