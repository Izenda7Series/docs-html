

=========================================
DashboardPart
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **reportName** |br|
         string
      -
      -  The name of the parent report of the report part
      -
   *  -  **type** |br|
         string
      -
      -  The type of the dashboard part
      -
   *  -  **title** |br|
         string
      -
      -  The title of the dashboard part
      -
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report containing the report part
      -
   *  -  **reportPartId** |br|
         string (GUID)
      -  Y
      -  The id of the report part being used
      -
   *  -  **content** |br|
         string
      -
      -  The content of the report part
      -
   *  -  **filterDescription** |br|
         string
      -
      -  The filter description for display
      -
   *  -  **numberOfRecord** |br|
         integer
      -  Y
      -  The number of records
      -
   *  -  **positionX** |br|
         integer
      -
      -  The row number position
      -
   *  -  **positionY** |br|
         integer
      -
      -  The column number position
      -
   *  -  **width** |br|
         integer
      -
      -  The width of dashboard part
      -
   *  -  **height** |br|
         integer
      -
      -  The height of dashboard part
      -
   *  -  **filters** |br|
         array of objects
      -
      -  An array of :doc:`DashboardPartFilterField` objects
      -
   *  -  **reportDataSource** |br|
         array of objects
      -
      -  An array of :doc:`ReportDataSource` objects
      -


Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "dashboardId" : "827f1a53-8afc-4f7c-b384-dd3a7cbe7b45",
        "type" : "reportPart",
        "title" : "002/002/test/Chart",
        "reportId" : "46af03c2-a740-46e0-bb15-49f97e66ff49",
        "reportPartId" : "7e76a8cb-d584-4f3e-9494-2c937d49dde6",
        "filterDescription" : "",
        "numberOfRecord" : -1,
        "positionX" : 0,
        "positionY" : 0,
        "width" : 12,
        "height" : 4,
        "filters" : [],
        "dashboardPartContent" : {
           "contentTitle" : {
              "text" : "",
              "settings" : {
                 "fontFamily" : "",
                 "fontSize" : 14,
                 "fontBold" : true,
                 "fontItalic" : false,
                 "fontUnderline" : false,
                 "fontColor" : "",
                 "fontHighlightColor" : "",
                 "alignment" : ""
              }
           },
           "contentDescription" : {
              "text" : "",
              "settings" : {
                 "fontFamily" : "",
                 "fontSize" : 14,
                 "fontBold" : true,
                 "fontItalic" : false,
                 "fontUnderline" : false,
                 "fontColor" : "",
                 "fontHighlightColor" : "",
                 "alignment" : ""
              }
           },
           "contentFromPreset" : true,
           "textTypeContent" : ""
        },
        "id" : "75950fe5-fb5b-4f99-a3a1-0ef0f6a26aed",
        "state" : 0,
        "deleted" : false,
        "inserted" : true,
        "version" : 1,
        "created" : "2016-10-06T09:03:30.313",
        "createdBy" : null,
        "modified" : "2016-10-06T09:03:30.313",
        "modifiedBy" : null
      }
