===================
GoogleAPISetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **useSystemConfiguration** |br|
         boolean
      -
      -  Whether inherit the setting from System or not
      -
   *  -  **googleAPIKey** |br|
         string
      -
      -  The Google Map API key
      -
   *  -  **useGEOCodingService** |br|
         boolean
      -
      -  Whether tenant can allowed to use GEOCoding Service or not
      -
   *  -  **tenantId** |br|
         string (GUID)
      -
      -  The id of the tenant
      -


Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
      "useSystemConfiguration": false,
      "googleAPIKey": "The google api key",
      "useGEOCodingService": true,
      "tenantId": null,
      "id": "e7798b61-3192-42dc-b0cd-7f7726cbfa69",
      "state": 0,
      "deleted": false,
      "inserted": true,
      "version": 1,
      "created": "2019-09-03T07:45:33.0134920+07:00",
      "createdBy": "System Admin",
      "modified": "2019-09-03T07:45:33.0134920+07:00",
      "modifiedBy": "System Admin"
      }
