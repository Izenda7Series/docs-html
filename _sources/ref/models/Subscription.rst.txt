

=========================================
Subscription
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **name** |br|
         string
      -
      -  The name of the subscription
      -
   *  -  **type** |br|
         string
      -
      -  The subscription type, either "Subscription Report" or "Subscription Alert"
      -
   *  -  **deliveryType** |br|
         string
      -
      -  The delivery type (Email or File Location)
      -
   *  -  **deliveryMethod** |br|
         string
      -
      -  The delivery method (Link, Attachment, Embedded HTML, Send to disk)
      -
   *  -  **exportFileType** |br|
         string
      -
      -  The export file type (PDF, Word Doc, Excel, CSV)
      -
   *  -  **exportAttachmentType** |br|
         string
      -
      -  The export attachment type (PDF, Word Doc, Excel, CSV)
      -
   *  -  **emailSubject** |br|
         string
      -
      -  The email subject template
      -
   *  -  **emailBody** |br|
         string
      -
      -  The email body template
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report
      -
   *  -  **draftId** |br|
         string (GUID)
      -  Y
      -  The id of the draft report
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **filterValueSelection** |br|
         string
      -
      -  The filter value selection
      -
   *  -  **recipients** |br|
         string
      -
      -  The recipients
      -
   *  -  **isSubscription** |br|
         boolean
      -
      -  Is this a subscription (or scheduling)
      -
   *  -  **createdById** |br|
         string (GUID)
      -  Y
      -  The id of the user creating this subscription
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **subscriptionFilterFields** |br|
         array of objects
      -  Y
      -  An array of :doc:`SubscriptionFilterField` objects. |br| |br|
         *When emailing a report with selected filter(s).*
      -
   *  -  **subscriptionCommonFilterFields** |br|
         array of objects
      -  Y
      -  An array of :doc:`SubscriptionCommonFilterField` objects. |br| |br|
         *When emailing a dashboard with selected common filter(s).*
      -
   *  -  **tempId** |br|
         string (GUID)
      -
      -  The temporary id
      -
   *  -  **reportingType** |br|
         string
      -
      -  The reporting type
      -
   *  -  **additionalRecipients** |br|
         string
      -
      -  Additional recipients
      -
   *  -  **reportDashboardName** |br|
         string
      -
      -  The name of the report or dashboard
      -
   *  -  **isSubscriptionTimeZoneUsed** |br|
         string
      -
      -  Is subscription timezone used for reports and dashboards
      -

Inherited fields:

.. include:: ScheduleEntity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "isDirty" : false,
         "name" : "Everyday at 2 PM",
         "type" : "Subscription Report",
         "timeZoneName" : "(UTC-06:00) Central Time (US & Canada)",
         "timeZoneValue" : "Central Standard Time",
         "startDate" : "08/11/2016",
         "startTime" : "8/11/2016 2:00 PM",
         "recurrenceType" : "2",
         "recurrencePattern" : 1,
         "recurrencePatternSetting" : {
            "recurrenceWeek" : 1,
            "selectedDayValue" : "5"
         },
         "isEndless" : true,
         "endDate" : "11/11/2016",
         "deliveryType" : "Email",
         "deliveryMethod" : "Link",
         "emailSubject" : "{reportName}",
         "subscriptionFilterFields" : [],
         "subscriptionCommonFilterFields" : [],
         "reportId" : null,
         "createdBy" : "",
         "id" : null,
         "state" : 1,
         "isSubscription" : true,
         "isEndAfter" : false,
         "isEndBy" : false,
         "isEdit" : false
      }
