

=========================================
AdvancedSetting
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id
      -
   *  -  **name** |br|
         string
      -
      -  The name of the setting
      -
   *  -  **value** |br|
         string
      -
      -  The value of the setting
      -
   *  -  **defaultValue** |br|
         string
      -
      -  The default value of the setting
      -
   *  -  **type** |br|
         string
      -
      -  Either Performance, Security, Others, or null (e.g. Default Header Image)
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **deleted** |br|
         boolean
      -
      -  Is this deleted
      -
   *  -  **modified** |br|
         datetime
      -  Y
      -  The date of modification
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "id": "c8ecf9fd-196d-44a3-90ec-97f393ebfc0c",
         "name": "DefaultImageUrl",
         "value": "http://localhost/img/default.png",
         "defaultValue": null,
         "type": null,
         "tenantId": null,
         "deleted": false,
         "modified": "2017-04-12T16:55:11.4900000+07:00"
      }
