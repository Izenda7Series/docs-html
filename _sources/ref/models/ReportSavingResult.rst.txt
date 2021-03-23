

=========================================
ReportSavingResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportKey** |br|
         object
      -
      -  A :doc:`ReportKey` object
      -
   *  -  **report** |br|
         object
      -
      -  A :doc:`ReportDefinition` object
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "reportKey": {
            "key": null,
            "tenantId": null
        },
        "report": null
      }
