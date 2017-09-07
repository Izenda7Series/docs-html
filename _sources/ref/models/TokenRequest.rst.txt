

===================
TokenRequest
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **licenseKey** |br|
         string
      -
      -  The license key
      -
   *  -  **tokenKey** |br|
         string
      -  Y
      -  The token, in case :term:`offline mode` is used
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {"LicenseKey":"1aBcD+==","TokenKey":"1aBcD+="}
