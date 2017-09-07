

============================
System Configuration APIs
============================

System Configuration APIs allow user to:

*  view and edit report settings
*  view and edit security policies
*  search for schedule instances
*  view, edit and delete schedule instances

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 35 40
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `POST systemSetting/reportSetting`_
     - Saves report setting.
     - Settings > System Configuration > Report > Save
   * - `GET systemSetting/reportSetting`_
     - Gets report setting.
     - Settings > System Configuration > Report
   * - `GET systemSetting/securityPolicy`_
     - Returns the security policies.
     - Settings > System Configuration > Sercurity Policies
   * - `POST systemSetting/securityPolicy`_
     - Updates the security policies.
     - Settings > System Configuration > Sercurity Policies > Save
   * - `POST systemSetting/loadSchedules`_
     - Searches for schedule instances.
     - Settings > System Configuration > Scheduling > Search
   * - `GET systemSetting/schedules/reportDashboardName/{reportingType}/(tenant_id)`_
     - Returns an array of possible report names (reportingType=1), dashboard names (reportingType=2), or both (reportingType=0) for schedule search screen.
     - 
       -\ Settings > System Configuration > Scheduling |br|
       -\ Settings > System Configuration > Scheduling > Choose Dashboard report type > Search
   * - `GET systemSetting/schedules/recipients/(tenant_id)`_
     - Returns an array of possible recipients for schedule search screen.
     - Settings > System Configuration > Scheduling
   * - `GET systemSetting/schedules/creators/(tenant_id)`_
     - Returns an array of possible owners for schedule search screen.
     - Settings > System Configuration > Scheduling
   * - `POST systemSetting/deleteSchedules`_
     - Deletes schedules from an array of ids.
     - Settings > System Configuration > Scheduling > Pick reports > Delete > OK
   * - `GET systemSetting/categorySetting`_
     - Returns the global category and local category.
     - Not used, replaced by `GET systemSetting/reportSetting`_



POST systemSetting/reportSetting
--------------------------------------------------------------

Saves report setting.

**Request**

    Payload: a :doc:`models/ReportSetting` object

**Response**

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **success** |br|
             boolean
          -  Is the save successful
          -
       *  -  **reportSetting** |br|
             object
          -  The saved :doc:`models/ReportSetting` object
          -

**Samples**

   .. code-block:: http

      POST /api/systemSetting/reportSetting HTTP/1.1

   Request payload::

      {
       "numOfArchivedVersionToKeepDefault": 5,
       "enforceVersionHistory": true,
       "numOfArchivedVersionToKeep": 5,
       "removeArchivedVersions": true,
       "recurrentReportSetting": {
         "once": false,
         "recurrence": true,
         "startDate": "2017-01-06T06:53:44.5249129",
         "startTime": "2017-01-06T06:53:44.5249129",
         "recurrenceType": 0,
         "occurValue": 0
       },
       "id": null,
       "state": 0,
       "deleted": false,
       "inserted": true,
       "version": null,
       "created": null,
       "createdBy": "John Doe",
       "modified": null,
       "modifiedBy": null
      }


GET systemSetting/reportSetting
--------------------------------------------------------------

Gets report setting.

**Request**

    No payload

**Response**

    A :doc:`models/ReportSetting` object

**Samples**

   .. code-block:: http

      GET /api/systemSetting/reportSetting HTTP/1.1

   Sample response::

      {
       "numOfArchivedVersionToKeepDefault": 5,
       "enforceVersionHistory": true,
       "numOfArchivedVersionToKeep": 5,
       "removeArchivedVersions": true,
       "recurrentReportSetting": {
         "once": false,
         "recurrence": true,
         "startDate": "2017-01-06T06:53:44.5249129",
         "startTime": "2017-01-06T06:53:44.5249129",
         "recurrenceType": 0,
         "occurValue": 0
       },
       "id": null,
       "state": 0,
       "deleted": false,
       "inserted": true,
       "version": null,
       "created": null,
       "createdBy": "John Doe",
       "modified": null,
       "modifiedBy": null
      }


GET systemSetting/securityPolicy
--------------------------------------------------------------

Returns the security policies.

**Request**

    No payload

**Response**

    A :doc:`models/SecurityPolicy` object

**Samples**

   .. code-block:: http

      GET /api/systemSetting/securityPolicy HTTP/1.1

   Sample response::

      {
        "minNumberOfPasswordLenght" : null,
        "maxNumberOfPasswordLenght" : null,
        "minNumberOfSpecialCharacter" : null,
        "maxNumberOfSpecialCharacter" : null,
        "minNumberOfUppercaseCharacter" : null,
        "maxNumberOfUppercaseCharacter" : null,
        "minNumberOfLowercaseCharacter" : null,
        "maxNumberOfLowercaseCharacter" : null,
        "minNumberOfNumericCharacter" : null,
        "maxNumberOfNumericCharacter" : null,
        "maxNumberOfRepeatSequentialCharacter" : null,
        "minNumberOfPasswordAge" : null,
        "maxNumberOfPasswordAge" : null,
        "notifyUseDuring" : null,
        "numberOfPasswordToKeep" : null,
        "passwordLinkValidity" : 1,
        "numberOfSecurityQuestionProfile" : null,
        "numberOfSecurityQuestionToResetPassword" : null,
        "numberOfFailedLogonAttemptsAllowed" : null,
        "numberOfFailedSecurityQuestionAlllowed" : null,
        "tenantId" : null,
        "lockoutPeriod" : null,
        "id" : "95aa269c-0d8c-4f68-8155-06429774d0f0",
        "state" : 0,
        "inserted" : true,
        "version" : null,
        "created" : null,
        "createdBy" : null,
        "modified" : null,
        "modifiedBy" : null
      }


POST systemSetting/securityPolicy
--------------------------------------------------------------

Updates the security policies.

**Request**

    Payload: a :doc:`models/SecurityPolicy` object

**Response**

    The updated :doc:`models/SecurityPolicy` object

**Samples**

   .. code-block:: http

      POST /api/systemSetting/securityPolicy HTTP/1.1

   Request payload::

      {
        "id": "00000000-0000-0000-0000-000000000000",
        "state": 0,
        "inserted": true,
        "version": null,
        "created": null,
        "createdBy": null,
        "modified": null,
        "minNumberOfPasswordLenght": 6,
        "maxNumberOfPasswordLenght": 10,
        "minNumberOfSpecialCharacter": null,
        "maxNumberOfSpecialCharacter": null,
        "minNumberOfUppercaseCharacter": null,
        "maxNumberOfUppercaseCharacter": null,
        "minNumberOfLowercaseCharacter": null,
        "maxNumberOfLowercaseCharacter": null,
        "minNumberOfNumericCharacter": null,
        "maxNumberOfNumericCharacter": null,
        "maxNumberOfRepeatSequential": null,
        "minNumberOfPasswordAge": null,
        "maxNumberOfPasswordAge": null,
        "notifyUseDuring": null,
        "numberOfPasswordToKeep": null,
        "passwordLinkValidity": null,
        "numberOfQuestionProfile": null,
        "numberOfQuestionResetPassword": null,
        "numberOfFailedLogonAllowed": null,
        "numberOfFailedAnswerAllowed": null,
        "lockoutPeriod": null
      }


POST systemSetting/loadSchedules
--------------------------------------------------------------

Searches for schedule instances.

**Request**

    Payload: a :doc:`models/SystemSchedulingPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/SystemSchedulingPagedResult`

**Samples**

   .. code-block:: http

      POST /api/systemSetting/loadSchedules HTTP/1.1

   Request payload::

      {
        "systemLevel" : true,
        "tenantId" : null,
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "name",
              "descending" : true
           }
        ],
        "criteria" : [{
              "key" : "ReportingType",
              "value" : ""
           }, {
              "key" : "ReportDashboardName",
              "value" : ""
           }, {
              "key" : "DeliveryType",
              "value" : ""
           }, {
              "key" : "DeliveryMethod",
              "value" : ""
           }, {
              "key" : "Recipients",
              "value" : ""
           }, {
              "key" : "Type",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRun",
              "value" : ""
           }, {
              "key" : "NextScheduledRun",
              "value" : ""
           }, {
              "key" : "NextScheduledRunFrom",
              "value" : ""
           }, {
              "key" : "NextScheduledRunTo",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRunFrom",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRunTo",
              "value" : ""
           }, {
              "key" : "RecurrenceType",
              "value" : ""
           }, {
              "key" : "ExportFileType",
              "value" : ""
           }, {
              "key" : "CreatedBy",
              "value" : ""
           }
        ]
      }

   Sample response::

      {
        "result" : [{
              "tenantId" : null,
              "tenantName" : null,
              "result" : [{
                    "name" : "Weekly Email",
                    "schedule" : "Occurs every Thursday effective 10/06/2016 at 05:00 PM (UTC-06:00) Central Time (US & Canada)",
                    "type" : "Subscribed Reporting Item",
                    "timeZoneName" : "(UTC-06:00) Central Time (US & Canada)",
                    "timeZoneValue" : "Central Standard Time",
                    "startDate" : "2016-10-06T00:00:00",
                    "startDateUtc" : "0001-01-01T00:00:00",
                    "startTime" : "2016-10-06T17:00:00",
                    "recurrenceType" : 8,
                    "recurrencePattern" : 1,
                    "recurrencePatternSetting" : {
                       "recurrenceWeek" : 1,
                       "selectedDayValue" : "5"
                    },
                    "isEndless" : true,
                    "isScheduled" : false,
                    "occurrence" : 0,
                    "endDate" : null,
                    "endDateUtc" : null,
                    "deliveryType" : "Email",
                    "deliveryMethod" : "Link",
                    "exportFileType" : null,
                    "exportAttachmentType" : null,
                    "emailSubject" : "{reportName}",
                    "emailBody" : "Dear {currentUserName},    <br/>    <br/>        Please see dashboard in the following link.    <br/>    <br/>        {dashboardLink}    <br/>    <br/>        Regards,",
                    "reportId" : null,
                    "dashboardId" : "5a21db3b-82c6-4791-8380-41affe1f0dcd",
                    "filterValueSelection" : "",
                    "recipients" : null,
                    "lastSuccessfulRun" : "The schedule has not started.",
                    "lastSuccessfulRunDate" : null,
                    "nextScheduledRun" : "10/06/2016 05:00 PM (UTC-06:00) Central Time (US & Canada)",
                    "nextScheduledRunDate" : null,
                    "isSubscription" : true,
                    "createdById" : null,
                    "isStartDateAdjusted" : false,
                    "subscriptionFilterFields" : [],
                    "subscriptionCommonFilterFields" : [],
                    "tempId" : null,
                    "reportingType" : "Dashboard",
                    "additionalRecipients" : null,
                    "reportDashboardName" : "001*",
                    "id" : "17b78ebb-aece-41d1-a73d-6ffc965b00d6",
                    "state" : 0,
                    "deleted" : false,
                    "inserted" : true,
                    "version" : 1,
                    "created" : null,
                    "createdBy" : null,
                    "modified" : "2016-10-06T04:31:13.34",
                    "modifiedBy" : null
                 }, {
                    "name" : "Daily Email",
                    "schedule" : "Occurs every day effective 10/06/2016 at 05:00 PM (UTC-06:00) Central Time (US & Canada)",
                    "type" : "Subscribed Reporting Item",
                    "timeZoneName" : "(UTC-06:00) Central Time (US & Canada)",
                    "timeZoneValue" : "Central Standard Time",
                    "startDate" : "2016-10-06T00:00:00",
                    "startDateUtc" : "0001-01-01T00:00:00",
                    "startTime" : "2016-10-06T17:00:00",
                    "recurrenceType" : 1,
                    "recurrencePattern" : 1,
                    "recurrencePatternSetting" : {
                       "recurrenceWeek" : 1,
                       "selectedDayValue" : "5"
                    },
                    "isEndless" : true,
                    "isScheduled" : false,
                    "occurrence" : 0,
                    "endDate" : null,
                    "endDateUtc" : null,
                    "deliveryType" : "Email",
                    "deliveryMethod" : "Link",
                    "exportFileType" : null,
                    "exportAttachmentType" : null,
                    "emailSubject" : "{reportName}",
                    "emailBody" : "Dear {currentUserName},    <br/>    <br/>        Please see report in the following link.    <br/>    <br/>        {reportLink}    <br/>    <br/>        Regards,",
                    "reportId" : "aeb4258e-7e30-4018-af48-9d73c6a41dee",
                    "dashboardId" : null,
                    "filterValueSelection" : "",
                    "recipients" : null,
                    "lastSuccessfulRun" : "The schedule has not started.",
                    "lastSuccessfulRunDate" : null,
                    "nextScheduledRun" : "10/06/2016 05:00 PM (UTC-06:00) Central Time (US & Canada)",
                    "nextScheduledRunDate" : null,
                    "isSubscription" : true,
                    "createdById" : null,
                    "isStartDateAdjusted" : false,
                    "subscriptionFilterFields" : [],
                    "subscriptionCommonFilterFields" : [],
                    "tempId" : null,
                    "reportingType" : "Report",
                    "additionalRecipients" : null,
                    "reportDashboardName" : "grid1",
                    "id" : "4ff7a37f-b381-4869-bf9d-16b6a8e5349e",
                    "state" : 0,
                    "deleted" : false,
                    "inserted" : true,
                    "version" : 1,
                    "created" : null,
                    "createdBy" : null,
                    "modified" : "2016-10-06T04:31:49.153",
                    "modifiedBy" : null
                 }
              ],
              "pageIndex" : 1,
              "pageSize" : 10,
              "total" : 2
           }, {
              "tenantId" : "a246229f-d190-4445-9fe9-1cdb22a03461",
              "tenantName" : "001",
              "result" : [],
              "pageIndex" : 1,
              "pageSize" : 10,
              "total" : 0
           }
        ],
        "pageIndex" : 0,
        "pageSize" : 0,
        "total" : 0
      }


GET systemSetting/schedules/reportDashboardName/{reportingType}/(tenant_id)
---------------------------------------------------------------------------------

Returns an array of possible report names (reportingType=1), dashboard names (reportingType=2), or both (reportingType=0) for schedule search screen.

**Request**

    No payload

**Response**

    An array of strings

**Samples**

   .. code-block:: http

      GET /api/systemSetting/schedules/reportDashboardName/0 HTTP/1.1

   Sample response::

      ["Orders Report", "Products Report", "Sales Dashboard"]


GET systemSetting/schedules/recipients/(tenant_id)
--------------------------------------------------------------

Returns an array of possible recipients for schedule search screen.

**Request**

    No payload

**Response**

    An array of strings

**Samples**

   .. code-block:: http

      GET /api/systemSetting/schedules/recipients HTTP/1.1

   Sample response::

      ["jdoe@acme.com","jbourne@treadstone.com","Admin","jdoe","jbourne","HR_Role","Reviewer_Role"]


GET systemSetting/schedules/creators/(tenant_id)
--------------------------------------------------------------

Returns an array of possible owners for schedule search screen.

**Request**

    No payload

**Response**

    An array of strings

**Samples**

   .. code-block:: http

      GET /api/systemSetting/schedules/creators HTTP/1.1

   Sample response::

      ["Admin","jdoe"]


POST systemSetting/deleteSchedules
--------------------------------------------------------------

Deletes schedules from an array of ids.

**Request**

    Payload: an array of strings (GUIDs)

**Response**

    * true if the deletion was successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/systemSetting/deleteSchedules HTTP/1.1

   Request payload::

      ["083ad7a3-f0ec-427d-ba3e-7f5327720eb2","22072491-1714-43dd-ae82-a07397390fab","d7c75b0f-bd05-4d82-ae1d-dd8904429115"]

   Sample response::

      true

GET systemSetting/categorySetting
--------------------------------------------------------------

Returns the global category and local category.

**Request**

    No payload

**Response**

    An array of exactly two objects with the following fields:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **id** |br|
             string (GUI)
          -  The id of the setting
          -
       *  -  **name** |br|
             string
          -  Either "Global Category" or "Local Category"
          -
       *  -  **isGlobal** |br|
             boolean
          -  *  true if Global
             *  false if Local

          -

**Samples**

   .. code-block:: http

      GET /api/systemSetting/categorySetting HTTP/1.1

   Sample response::

      [
         {
            "id": "2a83e3ce-f91b-4f14-910d-76cadf42d0fe",
            "name": "Global Category",
            "isGlobal": true
         },
         {
            "id": "09f8c4ab-0fe8-4e03-82d1-7949e3738f87",
            "name": "Local Category",
            "isGlobal": false
         }
      ]
