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
   *  -  **allowShowTenant** |br|
         boolean
      -
      -  Is Show Tenant Field disabled.
      -
   *  -  **dataSecurityRuleSets** |br|
         array of objects

         .. versionadded:: 3.11.0
      -
      -  An array of :doc:`DataSecurityRuleSet` objects.
      -
   *  -  **modified** |br|
         datetime
      -  Y
      -  The modification date time.
      -
   *  -  **setAdditiveFieldAutoFilterableDefaultValue** |br|
         boolean
      -
      -  The default value for Additive Fields Auto Filterable (``false``).
      -
   *  -  **setAdditiveFieldAutoFilterableValue** |br|
         boolean
      -
      -  Additive Fields Auto Filterable - if checked then additive fields when physical data model changes will be set as Filterable automatically.
      -
   *  -  **setAdditiveFieldAutoVisibleDefaultValue** |br|
         boolean
      -
      -  The default value for Additive Fields Auto Visible (``false``).
      -
   *  -  **setAdditiveFieldAutoVisibleValue** |br|
         boolean
      -
      -  Additive Fields Auto Visible - if checked then additive fields when physical data model changes will be set as Visible automatically.
      -
   *  -  **showTenantFieldDefaultValue** |br|
         boolean
      -
      -  The default value for Show Tenant Field (``true``).
      -
   *  -  **showTenantFieldValue** |br|
         boolean
      -
      -  Show Tenant Field - when false, this hides the fields identified in the TenantField property from being selected or viewed by users. Any filters based on the tenant fields will still affect the results.
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant |br|
         (null if the setting belongs to system).
      -
   *  -  **tenantFields** |br|
         array of objects
      -
      -  An array of :doc:`TenantField` objects.
      -
   *  -  **tenantFieldDefaultValue** |br|
         string
      -
      -  The default value for tenantFieldValue.
      -
   *  -  **tenantFieldValue** |br|
         string
      -
      -  Names of tenant fields, separated by semi-colon. |br| |br|
         Example: ``TenantID;UserID``
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
         "dataSecurityRuleSets": [],
         "modified": "2017-02-15T06:31:15"
      }
