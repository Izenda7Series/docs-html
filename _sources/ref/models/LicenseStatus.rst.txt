

===================
LicenseStatus
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **disabled** |br|
         boolean
      -
      -  Is the license disabled
      -
   *  -  **meetExprireWarningPeriod** |br|
         boolean
      -
      -  Is the license near expiration
      -
   *  -  **numberOfDayToExpire** |br|
         integer
      -
      -  The number of days until license expiration
      -
   *  -  **numberOfDayToValid** |br|
         integer
      -
      -  The number of days until the token starts |br| |br|
         0 if the token has already started
      -
   *  -  **exceedLostConnectionAllowPeriod** |br|
         boolean
      -
      -  Has the token exceeded LostConnectionAllowPeriod threshold |br| |br|
         See ``LostConnectionAllowPeriod`` system setting in :doc:`/ref/spec_izendasystemsetting_table`
      -
   *  -  **isAdminUser** |br|
         boolean
      -
      -  True if user is admin user
      -
   *  -  **trialLicense** |br|
         boolean
      -
      -  Is this a trial license
      -
   *  -  **connected** |br|
         boolean
      -
      -  True if this is connected to license server
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "disabled": false,
         "meetExprireWarningPeriod": false,
         "numberOfDayToExpire": 88,
         "numberOfDayToValid": 0,
         "exceedLostConnectionAllowPeriod": false,
         "isAdminUser": false,
         "trialLicense": false
      }
