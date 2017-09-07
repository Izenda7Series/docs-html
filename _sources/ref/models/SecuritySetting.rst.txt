

===================
SecuritySetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantFieldValue** |br|
         string
      -
      -  Names of tenant fields, separated by semi-colon |br| |br|
         Example: ``TenantID;UserID``
      -
   *  -  **tenantFieldDefaultValue** |br|
         string
      -
      -  The default value for tenantFieldValue
      -
   *  -  **showTenantFieldValue** |br|
         boolean
      -
      -  Show Tenant Field - when false, this hides the fields identified in the TenantField property from being selected or viewed by users. Any filters based on the tenant fields will still affect the results.
      -
   *  -  **showTenantFieldDefaultValue** |br|
         boolean
      -
      -  The default value for Show Tenant Field (``true``)
      -
   *  -  **setAdditiveFieldAutoVisibleValue** |br|
         boolean
      -
      -  Additive Fields Auto Visible - if checked then additive fields when physical data model changes will be set as Visible automatically.
      -
   *  -  **setAdditiveFieldAutoVisibleDefaultValue** |br|
         boolean
      -
      -  The default value for Additive Fields Auto Visible (``false``)
      -
   *  -  **setAdditiveFieldAutoFilterableValue** |br|
         boolean
      -
      -  Additive Fields Auto Filterable - if checked then additive fields when physical data model changes will be set as Filterable automatically.
      -
   *  -  **setAdditiveFieldAutoFilterableDefaultValue** |br|
         boolean
      -
      -  The default value for Additive Fields Auto Filterable (``false``)
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant |br|
         null if the setting belongs to system
      -
   *  -  **tenantFields** |br|
         array of objects
      -
      -  An array of :doc:`TenantField` objects
      -
   *  -  **allowShowTenant** |br|
         boolean
      -
      -  Is Show Tenant Field disabled
      -
   *  -  **modified** |br|
         datetime
      -  Y
      -  The modification date time
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "tenantFieldValue": "TenantID;UserID",
         "tenantFieldDefaultValue": "",
         "showTenantFieldValue": true,
         "showTenantFieldDefaultValue": true,
         "setAdditiveFieldAutoVisibleValue": false,
         "setAdditiveFieldAutoVisibleDefaultValue": false,
         "setAdditiveFieldAutoFilterableValue": false,
         "setAdditiveFieldAutoFilterableDefaultValue": false,
         "tenantId": null,
         "tenantFields": [
            {
               "name": "TenantID",
               "isSystem": true
            },
            {
               "name": "UserID",
               "isSystem": true
            }
         ],
         "allowShowTenant": true,
         "modified": "2017-02-15T06:31:15"
      }
