

=========================================
WorkspaceSchedule
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **workspaceId** |br|
         string (GUID)
      -
      -  The id of the workspace
      -
   *  -  **createdById** |br|
         string (GUID)
      -  Y
      -  The id of the user creating this subscription
      -


Inherited fields:

.. include:: ScheduleEntity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "workspaceId": "4e854ea4-c803-4ca8-af07-53f3c05f848d",
         "createdById": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
         "schedule": "Occurs every day effective 05/01/2020 until 05/01/2020 at 02:00 PM (UTC-06:00) Central Time (US & Canada)",
         "timeZoneName": "(UTC-06:00) Central Time (US & Canada)",
         "timeZoneValue": "Central Standard Time",
         "startDate": "2020-05-01T00:00:00",
         "startDateUtc": "2020-05-01T19:00:00",
         "startTime": "2020-05-20T14:00:00",
         "recurrenceType": 8,
         "recurrencePattern": 0,
         "recurrencePatternSetting": {
            "isEveryWeekday": false,
            "recurrenceDay": 1
         },
         "isEndless": false,
         "isScheduled": false,
         "occurrence": 1,
         "endDate": "2020-05-01T14:00:00",
         "endDateUtc": "2020-05-01T19:00:00",
         "lastSuccessfulRun": "The schedule has not started.",
         "lastSuccessfulRunDate": null,
         "nextScheduledRun": "05/20/2020 02:00 PM (UTC-06:00) Central Time (US & Canada)",
         "nextScheduledRunDate": "2020-05-20T14:00:00",
         "isStartDateAdjusted": false,
         "id": "e2ed0d48-c8c3-4394-ab55-5d9367a09e42",
         "state": 0,
         "deleted": false,
         "inserted": true,
         "version": null,
         "created": null,
         "createdBy": "",
         "modified": null,
         "modifiedBy": null
      }
