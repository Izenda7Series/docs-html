

==================
ReportHistory
==================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportId** |br|
         string (GUID)
      -
      -  The id of the report
      -
   *  -  **reportName** |br|
         string
      -
      -  The name of the report
      -
   *  -  **description** |br|
         string
      -
      -  The description of the report
      -
   *  -  **definition** |br|
         string
      -
      -  The report definition in json format
      -
   *  -  **status** |br|
         string
      -
      -  The status
      -
   *  -  **inaccessible** |br|
         boolean
      -
      -  Whether user can access this version
      -
   *  -  **accessPriority** |br|
         integer
      -
      -  The access priority
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "reportId" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
         "reportName" : "TestReport02",
         "description" : null,
         "definition" : null,
         "status" : "Active",
         "id" : "41023c5b-3fe5-4a62-8ecf-7aae8974f63f",
         "state" : 0,
         "inserted" : true,
         "version" : 2,
         "created" : "2016-07-13T08:05:25.587",
         "createdBy" : null,
         "modified" : "2016-07-14T03:51:38",
         "modifiedBy" : null
      }
