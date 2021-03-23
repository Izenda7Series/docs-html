
================
ReportSetting
================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **numOfArchivedVersionToKeepDefault** |br|
         integer
      -
      -  The default value for number of archived versions to keep
      -  Default value ``5``
   *  -  **enforceVersionHistory** |br|
         boolean
      -
      -  Whether to keep report version history
      -
   *  -  **numOfArchivedVersionToKeep** |br|
         integer
      -
      -  The number of archived versions to keep
      -
   *  -  **removeArchivedVersions** |br|
         boolean
      -
      -  Whether to remove achived versions
      -
   *  -  **isScheduled** |br|
         boolean
      -
      -  Whether to use the schedule to remove archived versions
      -
   *  -  **localCategoryName** |br|
         string
      -
      -  The local category name
      -
   *  -  **globalCategoryName** |br|
         string
      -
      -  The global category name
      -
   *  -  **recurrentReportSetting** |br|
         object
      -
      -  The Remove Archived Versions options
      -
   *  -  .. container:: lpad2

           **once** |br|
           boolean
      -
      -  True to run one time, opposite of **recurrence**
      -
   *  -  .. container:: lpad2

            **recurrence** |br|
            boolean
      -
      -  True to run multiple times, opposite of **once**
      -
   *  -  .. container:: lpad2

            **startDate** |br|
            datetime
      -  Y
      -  The start date
      -
   *  -  .. container:: lpad2

            **startTime** |br|
            datetime
      -  Y
      -  The start time
      -
   *  -  .. container:: lpad2

            **recurrenceType** |br|
            integer
      -
      -  *  0 = Day
            1 = Week
            2 = Month
            3 = Year
      -
   *  -  .. container:: lpad2

            **occurValue** |br|
            integer
      -  Y
      -  The numer of times it has run
      -


Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

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
