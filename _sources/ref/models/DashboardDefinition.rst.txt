

=========================================
DashboardDefinition
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **commonFilterFields** |br|
         array of objects
      -
      -  An array of :doc:`CommonFilterField` objects
      -
   *  -  **accesses** |br|
         array of objects
      -
      -  An array of :doc:`UserPermission` objects
      -
   *  -  **subscriptions** |br|
         array of objects
      -
      -  An array of :doc:`Subscription` objects
      -
   *  -  **inaccessible** |br|
         boolean
      -
      -  True if dashboard is inaccessible for user
      -
      

Inherited fields:

.. include:: Dashboard.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "commonFilterFields" : [],
         "accesses" : [],
         "subscriptions" : [],
         "dashboardParts" : [{
               "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f",
               "type" : null,
               "title" : null,
               "reportId" : null,
               "reportPartId" : null,
               "filterDescription" : null,
               "numberOfRecord" : -1,
               "positionX" : 0,
               "positionY" : 4,
               "width" : 6,
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
                  "bodyContent" : {
                     "text" : "",
                     "config" : {
                        "fontFamily" : "Roboto",
                        "fontSize" : 14,
                        "bold" : false,
                        "italic" : false,
                        "underline" : false,
                        "strikethrough" : false,
                        "textColor" : "",
                        "backgroundColor" : "",
                        "alignleft" : false,
                        "aligncenter" : false,
                        "alignright" : false,
                        "alignjustify" : false,
                        "bullet" : "",
                        "numbered" : "",
                        "alignTop" : false,
                        "alignMiddle" : false,
                        "alignBottom" : false
                     }
                  }
               },
               "id" : "6b8a0f81-b0ba-4320-bd84-0cd6f61b2842",
               "state" : 0,
               "inserted" : true,
               "version" : 1,
               "created" : "2016-08-11T03:20:08.793",
               "createdBy" : null,
               "modified" : "2016-08-11T03:20:08.793",
               "modifiedBy" : null
            }, {
               "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f",
               "type" : "text",
               "title" : "text",
               "reportId" : null,
               "reportPartId" : null,
               "filterDescription" : null,
               "numberOfRecord" : -1,
               "positionX" : 0,
               "positionY" : 0,
               "width" : 12,
               "height" : 4,
               "filters" : [],
               "dashboardPartContent" : {
                  "contentTitle" : {
                     "text" : "A Title",
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
                     "text" : "desc",
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
                  "bodyContent" : {
                     "text" : "",
                     "config" : {
                        "fontFamily" : "Roboto",
                        "fontSize" : 14,
                        "bold" : false,
                        "italic" : false,
                        "underline" : false,
                        "strikethrough" : false,
                        "textColor" : "",
                        "backgroundColor" : "",
                        "alignleft" : false,
                        "aligncenter" : false,
                        "alignright" : false,
                        "alignjustify" : false,
                        "bullet" : "",
                        "numbered" : "",
                        "alignTop" : false,
                        "alignMiddle" : false,
                        "alignBottom" : false
                     }
                  }
               },
               "id" : "0cd06216-ee6f-4dee-9a8a-23d12f845e34",
               "state" : 0,
               "inserted" : true,
               "version" : 1,
               "created" : "2016-08-11T03:20:08.777",
               "createdBy" : null,
               "modified" : "2016-08-11T03:20:08.777",
               "modifiedBy" : null
            }, {
               "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f",
               "type" : null,
               "title" : null,
               "reportId" : null,
               "reportPartId" : null,
               "filterDescription" : null,
               "numberOfRecord" : -1,
               "positionX" : 6,
               "positionY" : 4,
               "width" : 6,
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
                  "bodyContent" : {
                     "text" : "",
                     "config" : {
                        "fontFamily" : "Roboto",
                        "fontSize" : 14,
                        "bold" : false,
                        "italic" : false,
                        "underline" : false,
                        "strikethrough" : false,
                        "textColor" : "",
                        "backgroundColor" : "",
                        "alignleft" : false,
                        "aligncenter" : false,
                        "alignright" : false,
                        "alignjustify" : false,
                        "bullet" : "",
                        "numbered" : "",
                        "alignTop" : false,
                        "alignMiddle" : false,
                        "alignBottom" : false
                     }
                  }
               },
               "id" : "042035e9-77e7-4102-baa7-e37eb5ed00d5",
               "state" : 0,
               "inserted" : true,
               "version" : 1,
               "created" : "2016-08-11T03:20:08.793",
               "createdBy" : null,
               "modified" : "2016-08-11T03:20:08.793",
               "modifiedBy" : null
            }
         ],
         "name" : "TestDashboard01",
         "description" : null,
         "categoryId" : "e443f282-eba4-422d-a7c3-32560a268373",
         "categoryName" : null,
         "subCategoryId" : null,
         "subCategoryName" : null,
         "tenantId" : null,
         "imageUrl" : null,
         "stretchImage" : false,
         "backgroundColor" : null,
         "showFilterDescription" : true,
         "lastViewed" : null,
         "id" : "a496ad94-fe92-48d5-a285-e45be738921f",
         "state" : 0,
         "inserted" : true,
         "version" : 2,
         "created" : "2016-08-11T03:20:08.777",
         "createdBy" : null,
         "modified" : "2016-08-11T03:44:01.27",
         "modifiedBy" : null
      }
