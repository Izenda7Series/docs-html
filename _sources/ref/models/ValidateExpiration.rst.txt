

=========================================
ValidateExpiration
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -


Inherited fields:

.. include:: Expiration.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "tenantId" : null,
         "isExpired" : false,
         "notifyDuringDay" : null
      }
