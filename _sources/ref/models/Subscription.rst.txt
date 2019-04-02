

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
   *  -  **schedule** |br|
         string
      -
      -  The schedule for display
      -
   *  -  **type** |br|
         string
      -
      -  The subscription type, either "Subscription Report" or "Subscription Alert"
      -
   *  -  **timeZoneName** |br|
         string
      -
      -  The display name of the timezone. |br|
         Example: ``(UTC-08:00) Pacific Time (US & Canada)``
      -
   *  -  **timeZoneValue** |br|
         string
      -
      -  The internal value of the timezone. |br|
         Example: ``Pacific Standard Time``
      -
   *  -  **startDate** |br|
         datetime
      -
      -  The start date
      -
   *  -  **startDateUtc** |br|
         datetime
      -
      -  The start date in UTC timezone
      -
   *  -  **startTime** |br|
         datetime
      -
      -  The start time
      -
   *  -  **recurrenceType** |br|
         int
      -
      -  The recurrence type

         -   0 = AlertHourly
         -   1 = AlertDaily
         -   2 = EveryDay
         -   3 = EveryWeekday
         -   4 = EveryWeek
         -   5 = EveryTwoWeeks
         -   6 = EveryMonth
         -   7 = EveryQuarter
         -   8 = CustomRecurrence
      -
   *  -  **recurrencePattern** |br|
         int
      -
      -  The recurrence pattern

         -   0 = Daily
         -   1 = Weekly
         -   2 = Monthly
         -   3 = Yearly
      -
   *  -  **recurrencePatternValue** |br|
         string
      -
      -  The selected recurrence pattern value, in json format. |br|
         For example: ``{"recurrenceWeek":1,"selectedDayValue":"2"}``
      -
   *  -  **recurrencePatternSetting** |br|
         object
      -
      -  A dynamic object to store the recurrence pattern value
      -
   *  -  **isEndless** |br|
         boolean
      -
      -  Does the recurrence have no end date
      -
   *  -  **isScheduled** |br|
         boolean
      -
      -  Is it scheduled to run
      -
   *  -  **occurence** |br|
         integer
      -
      -  The number of occurences to end after
      -
   *  -  **endDate** |br|
         datetime
      -  Y
      -  The end date
      -
   *  -  **endDateUtc** |br|
         datetime
      -  Y
      -  The end date in UTC timezone
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
   *  -  **lastSuccessfulRun** |br|
         string
      -
      -  The last successful run date and time for display
      -
   *  -  **lastSuccessfulRunDate** |br|
         datetime
      -
      -  The last successful run date and time
      -
   *  -  **nextScheduleRun** |br|
         string
      -
      -  The next scheduled run date and time for display
      -
   *  -  **nextScheduleRunDate** |br|
         datetime
      -  Y
      -  The next scheduled run date and time
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
   *  -  **isStartDateAdjusted** |br|
         boolean
      -
      -  Has the start date been updated
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
