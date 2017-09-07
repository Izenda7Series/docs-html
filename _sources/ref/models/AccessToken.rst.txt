
==============
AccessToken
==============

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **token** |br|
         string
      -
      -  The access token
      -
   *  -  **tenant** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **cultureName** |br|
         string
      -
      -  The language
      -
   *  -  **dateFormat** |br|
         string
      -
      -  User-selectable date format
      -
   *  -  **systemAdmin** |br|
         boolean
      -
      -  Whether user is system admin
      -

Inherited fields:

.. include:: Expiration.rst


.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "token" : "UWmQLI13sORSrN5VLodTxqO9e/yElV4RwRb2K6PzW6l4tYtw7kkbHH2Im9oQNxToVBHCihEIophicrWyCf6J7w==",
         "tenant" : null,
         "isExpired" : false,
         "notifyDuringDay" : null
      }
