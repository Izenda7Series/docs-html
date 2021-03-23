
=========================================
ReportFilterSetting
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **filterFields** |br|
         array of objects
      -
      -  An array of :doc:`ReportFilterField` objects
      -


Inherited fields:

.. include:: ReportFilter.rst

.. container:: toggle

   .. container:: header

      **ReportFilterSetting Sample**:

   .. code-block:: json

      {
        "status" : 0,
        "logic" : null,
        "visible" : false,
        "filterFields" : [{
            "connectionName" : "Northwind",
            "querySourceCategoryName" : "dbo",
            "sourceFieldName" : "ShipCountry",
            "sourceFieldVisible" : true,
            "sourceFieldFilterable" : true,
            "sourceDataObjectName" : "Orders",
            "dataType" : "Text",
            "filterId" : "00000000-0000-0000-0000-000000000000",
            "querySourceFieldId" : "d0f88020-8d3f-4f80-a1ac-0c187f87dfd3",
            "querySourceType" : "Table",
            "querySourceId" : "8fda0166-5f38-4ca1-ae20-9b6cab288f9d",
            "relationshipId" : null,
            "alias" : "ShipCountry",
            "position" : 1,
            "visible" : false,
            "required" : false,
            "cascading" : true,
            "operatorId" : "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
            "operatorSetting" : null,
            "value" : "'US'",
            "sortType" : "Unsorted",
            "fontFamily" : null,
            "fontSize" : 0,
            "textColor" : null,
            "backgroundColor" : null,
            "fontBold" : false,
            "fontItalic" : false,
            "fontUnderline" : false,
            "id" : "00000000-0000-0000-0000-000000000000",
            "status" : 0,
            "modified" : null,
            "dateTimeNow" : "2016-06-13T07:23:25.9138114Z",
            "isParameter" : false,
            "sourceDataObjectFullName" : "Northwind.dbo.Orders",
            "selected" : false
          }
        ],
        "id" : "00000000-0000-0000-0000-000000000000",
        "reportId" : "37e99389-fa8a-4f9f-9d03-f6362240c931"
      }
