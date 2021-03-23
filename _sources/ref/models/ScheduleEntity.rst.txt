

=========================================
ScheduleEntity
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **schedule** |br|
         string
      -
      -  The schedule for display
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
   *  -  **isStartDateAdjusted** |br|
         boolean
      -
      -  Has the start date been updated
      -


Inherited fields:

.. include:: Entity.rst
