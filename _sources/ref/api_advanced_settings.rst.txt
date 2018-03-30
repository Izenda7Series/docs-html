

============================
Advanced Settings APIs
============================

The **Advanced Settings** page allows user to

* manage the list of data source categories
* update system settings in related groups

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 35 40
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `POST advancedSetting/category`_
     - Updates the list of :term:`categories <data source category>`.
     - Settings > Data Setup > Advanced Settings > Category > Save
   * - `GET advancedSetting/category/(tenant_id)`_
     - Returns an array of :term:`categories <data source category>` (filtered by tenant_id if provided).
     - Settings > Data Setup > Advanced Settings > Category
   * - `DELETE advancedSetting/category/{category_id}`_
     - Deletes the :term:`category <data source category>` specified by category_id.
     - Settings > Data Setup > Advanced Settings > Category > click Remove icon
   * - `GET advancedSetting/performance/(tenant_id)`_
     - Returns the settings in Performance group (filtered by tenant_id if provided).
     - \- On Front-end load |br|
       \- Settings > Data Setup > Advanced Settings > Performance
   * - `POST advancedSetting/performance`_
     - Updates the settings in Performance group.
     - Settings > Data Setup > Advanced Settings > Performance > Save
   * - `GET advancedSetting/security/(tenant_id)`_
     - Returns the settings in Security group (filtered by tenant_id if provided).
     - \- On Front-end load |br|
       \- Settings > Data Setup > Advanced Settings > Security
   * - `POST advancedSetting/security`_
     - Updates the settings in Security group.
     - Settings > Data Setup > Advanced Settings > Security > Save
   * - `GET advancedSetting/miscSetting/(tenant_id)`_
     - Returns the settings in Others group (filtered by tenant_id if provided).
     - Settings > Data Setup > Advanced Settings > Others
   * - `POST advancedSetting/miscSetting`_
     - Updates the settings in Others group.
     - Settings > Data Setup > Advanced Settings > Others > Save
   * - `POST advancedSetting/defaultImageUrl`_
     - Updates the default image url setting.
     - Not used
   * - `GET advancedSetting/defaultImageUrl(?tenantId=tenant_id)`_
     - Returns the default image url setting.
     - Setting Level Tenant is selected

.. _POST_advancedSetting/category:

POST advancedSetting/category
--------------------------------------------------------------

Updates the list of :term:`categories<data source category>`.

**Request**

    An array of :doc:`models/DataSourceCategory` objects

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/advancedSetting/category HTTP/1.1

   With an existing empty category list, this request payload will add two categories ABC and XYZ::

      [
        {
           "id" : null,
           "name" : "ABC",
           "tenantId" : null
        }, {
           "id" : null,
           "name" : "XYZ",
           "tenantId" : null
        }
      ]

   Sample response::

      {
        "success" : true,
        "messages" : []
      }

   User needs to reload the category list to have the server-generated ids by calling `GET advancedSetting/category/(tenant_id)`_. User will get::

      [
        {
           "id" : "0eac7266-4150-4b45-b6f7-6c40d95b6a37",
           "name" : "ABC",
           "tenantId" : null
        }, {
           "id" : "45c747c5-a11a-48f4-b966-14819a07450f",
           "name" : "XYZ",
           "tenantId" : null		
        }
      ]

   Right after that, assuming user have renamed ABC category to ABCDEF, removed XYZ and added QRS, the update request payload will be::

      [
        {
           "id" : "0eac7266-4150-4b45-b6f7-6c40d95b6a37",
           "name" : "ABCDEF",
           "tenantId" : null		
        }, {
           "id" : null,
           "name" : "QRS",
           "tenantId" : null		
        }
      ]

.. _GET_advancedSetting/category/(tenant_id):

GET advancedSetting/category/(tenant_id)
--------------------------------------------------------------

Returns an array of :term:`categories<data source category>` (filtered by tenant_id if provided).

**Request**

    No payload

**Response**

    An array of :doc:`models/DataSourceCategory` objects

**Samples**

   .. code-block:: http

      GET /api/advancedSetting/category HTTP/1.1

   Sample response::

      [{
           "id" : "45c747c5-a11a-48f4-b966-14819a07450f",
           "name" : "ABC",
           "tenantId" : null,
           "modified" : "2016-03-20T04:47:09.1170000+07:00",
           "deleted" : false
        }, {
           "id" : "cda0ef9a-7fc0-4f9b-96ed-b1c33ea624b1",
           "name" : "DEF",
           "tenantId" : null,
           "modified" : "2016-03-20T04:47:09.1330000+07:00",
           "deleted" : false
        }, {
           "id" : "868e6176-530f-4e8a-bef4-fb14d50e1882",
           "name" : "QRS",
           "tenantId" : null,
           "modified" : "2016-03-20T04:47:09.1330000+07:00",
           "deleted" : false
        }
      ]

.. _DELETE_advancedSetting/category/{category_id}:

DELETE advancedSetting/category/{category_id}
--------------------------------------------------------------

Deletes the :term:`category<data source category>` specified by category_id.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the deletion is successful

**Samples**

   .. code-block:: http

      DELETE /api/advancedSetting/category/cda0ef9a-7fc0-4f9b-96ed-b1c33ea624b1 HTTP/1.1

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

GET advancedSetting/performance/(tenant_id)
--------------------------------------------------------------

Returns the settings in Performance group (filtered by tenant_id if provided).

**Request**

    No payload

**Response**

    A :doc:`models/PerformanceSetting` object

**Samples**

   .. code-block:: http

      GET /api/advancedSetting/performance HTTP/1.1

   Sample response::

      {
        "queryTimeoutValue" : 3600,
        "queryTimeoutDefaultValue" : 3600,
        "useNoLockValue" : true,
        "useNoLockDefaultValue" : true,
        "dataSourceLimitValue" : 1000,
        "dataSourceLimitDefaultValue" : 1000,
        "tenantId" : null
      }

POST advancedSetting/performance
--------------------------------------------------------------

Updates the settings in Performance group.

**Request**

    A :doc:`models/PerformanceSetting` object

**Response**

    An :doc:`models/OperationResult` object with **success** fied true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/advancedSetting/performance HTTP/1.1

   Request payload to update Query Timeout to 360::

      {
        "queryTimeoutValue" : 360,
        "useNoLockValue" : true,
        "dataSourceLimitValue" : 1000,
        "tenantId" : null
      }

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

GET advancedSetting/security/(tenant_id)
--------------------------------------------------------------

Returns the settings in Security group (filtered by tenant_id if provided).

**Request**

    No payload

**Response**

    A :doc:`models/SecuritySetting` object

**Samples**

   .. code-block:: http

      GET /api/advancedSetting/security HTTP/1.1

   Sample response::

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

POST advancedSetting/security
--------------------------------------------------------------

Updates the settings in Security group.

**Request**

    A :doc:`models/SecuritySetting` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/advancedSetting/security HTTP/1.1

   Request payload to set Additive Fields Auto Visible::

      {
        "showTenantFieldValue" : true,
        "setAdditiveFieldAutoVisibleValue" : true,
        "setAdditiveFieldAutoFilterableValue" : false,
        "tenantId" : null
      }

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

GET advancedSetting/miscSetting/(tenant_id)
--------------------------------------------------------------

Returns the settings in Others group (filtered by tenant_id if provided).

**Request**

    A :doc:`models/Entity` object

**Response**

    An :doc:`models/OtherSetting` object

**Samples**

   .. code-block:: http

      GET /api/advancedSetting/miscSetting HTTP/1.1

   Sample response::

      {
         "sortColumnNameValue": false,
         "sortColumnNameDefaultValue": false,
         "trimTimeInJoinsValue": true,
         "trimTimeInJoinsDefaultValue": true,
         "timezoneForDataOffsetValue": 0,
         "timezoneForDataOffsetDefaultValue": 0,
         "timezoneForTimestampOffsetValue": 0,
         "timezoneForTimestampOffsetDefaultValue": 0,
         "convertNullToEmptyStringValue": false,
         "convertNullToEmptyStringDefaultValue": false,
         "showSchemaNameValue": false,
         "showSchemaNameDefaultValue": false,
         "showIntroductionTextValue": false,
         "showIntroductionTextDefaultValue": false,
         "introductionTextValue": "",
         "introductionTextDefaultValue": "",
         "sendToDiskPathValue": "",
         "sendToDiskPathDefaultValue": "",
         "tenantId": null,
         "modified": "2017-02-15T07:29:25.3300651"
         "hideReportHeaderAndFooterValue": true,
         "hideReportHeaderAndFooterDefaultValue": false
      }

POST advancedSetting/miscSetting
--------------------------------------------------------------

Updates the settings in Others group.

**Request**

    An :doc:`models/OtherSetting` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the update is successful

**Samples**

   .. code-block:: http

      POST /api/advancedSetting/miscSetting HTTP/1.1

   Request payload to set Timezone Offset to -4::

      {
         "sortColumnNameValue": false,
         "trimTimeInJoinsValue": true,
         "timezoneForDataOffsetValue": "-4",
         "timezoneForTimestampOffsetValue": "0",
         "convertNullToEmptyStringValue": false,
         "showSchemaNameValue": false,
         "showIntroductionTextValue": false,
         "introductionTextValue": "",
         "sendToDiskPathValue": "",
         "sortColumnNameDefaultValue": false,
         "trimTimeInJoinsDefaultValue": true,
         "timezoneForDataOffsetDefaultValue": 0,
         "timezoneForTimestampOffsetDefaultValue": 0,
         "convertNullToEmptyStringDefaultValue": false,
         "showSchemaNameDefaultValue": false,
         "showIntroductionTextDefaultValue": false,
         "introductionTextDefaultValue": "",
         "sendToDiskPathDefaultValue": "",
         "tenantId": null,
         "modified": "2017-02-15T07:29:25.3300651",
         "hideReportHeaderAndFooterValue":true
      }

   Sample response::

      {
        "success" : true,
        "messages" : null
      }

POST advancedSetting/defaultImageUrl
-----------------------------------------------------------

Updates the default image url setting.

**Request**

   Payload: an :doc:`models/AdvancedSetting` object

**Response**

   The saved :doc:`models/AdvancedSetting` object with **name** field value "DefaultImageUrl"

**Samples**

   .. code-block:: http

      POST /api/advancedSetting/defaultImageUrl HTTP/1.1

   Payload::

      {
         "value": "http://localhost/img/default.png",
         "tenantId": null
      }

   Response::

      {
         "id": "c8ecf9fd-196d-44a3-90ec-97f393ebfc0c",
         "name": "DefaultImageUrl",
         "value": "http://localhost/img/default.png",
         "defaultValue": null,
         "type": null,
         "tenantId": null,
         "deleted": false,
         "modified": "2017-04-12T16:55:11.4884228Z"
      }

GET advancedSetting/defaultImageUrl(?tenantId=tenant_id)
-----------------------------------------------------------

Returns the default image url setting.

**Request**

   No payload

   Optional querystring: ?tenantId=<the id of the tenant>

**Response**

   An :doc:`models/AdvancedSetting` object

**Samples**

   .. code-block:: http

      GET /api/advancedSetting/defaultImageUrl HTTP/1.1

   Response::

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
