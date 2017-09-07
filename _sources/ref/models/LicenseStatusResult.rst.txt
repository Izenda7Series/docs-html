

===================
LicenseStatusResult
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **licenseStatus** |br|
         object
      -
      -  A :doc:`LicenseStatus` object
      -


Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "licenseStatus": {
            "disabled": false,
            "meetExprireWarningPeriod": false,
            "numberOfDayToExpire": 88,
            "numberOfDayToValid": 0,
            "exceedLostConnectionAllowPeriod": false,
            "isAdminUser": false,
            "trialLicense": false
         },
         "success": true,
         "messages": null
      }
