

=========================================
SystemSchedulingPagedResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **result** |br|
         array of objects
      -
      -  An array of :doc:`Subscription` objects
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantName** |br|
         string
      -
      -  The name of the tenant
      -
   *  -  **pageIndex** |br|
         integer
      -
      -  The index of the page
      -  Inherited from :doc:`PagedResult`
   *  -  **pageSize** |br|
         integer
      -
      -  The size of the page
      -  Inherited from :doc:`PagedResult`
   *  -  **total** |br|
         integer
      -
      -  The total number of rows
      -  Inherited from :doc:`PagedResult`
   *  -  **skipItems** |br|
         integer
      -
      -  Skip items
      -  Inherited from :doc:`PagedResult`
   *  -  **isLastPage** |br|
         boolean
      -
      -  Whether this is the last page
      -  Inherited from :doc:`PagedResult`

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
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
      }
