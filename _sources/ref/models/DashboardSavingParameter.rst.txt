

=========================================
DashboardSavingParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **saveAs** |br|
         boolean
      -
      -  Is this saved as new dashboard
      -
   *  -  **dashboard** |br|
         object
      -
      -  A :doc:`DashboardDefinition` object
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "saveAs" : false,
        "dashboard" : {
           "accesses" : [],
           "name" : "TestDashboard01",
           "description" : null,
           "categoryName" : "Category01",
           "subCategoryName" : "Category01",
           "tenantId" : null,
           "imageUrl" : null,
           "stretchImage" : false,
           "id" : null,
           "state" : 0,
           "inserted" : false,
           "version" : null,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null,
           "showFilterDescription" : true,
           "categoryId" : null,
           "subCategoryId" : null,
           "dashboardParts" : [{
                 "isDirty" : false,
                 "dashboardId" : null,
                 "positionX" : 0,
                 "positionY" : 0,
                 "width" : 12,
                 "height" : 4,
                 "title" : "text",
                 "isBackSide" : false,
                 "isFullScreenMode" : false,
                 "state" : 1,
                 "type" : "text",
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
                 },
                 "id" : null,
                 "numberOfRecord" : -1,
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
                 "filters" : []
              }, {
                 "isDirty" : false,
                 "dashboardId" : null,
                 "positionX" : 0,
                 "positionY" : 4,
                 "width" : 6,
                 "height" : 4,
                 "isBackSide" : false,
                 "isFullScreenMode" : false,
                 "state" : 1,
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
                 },
                 "id" : null,
                 "numberOfRecord" : -1,
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
                 "filters" : []
              }, {
                 "isDirty" : false,
                 "dashboardId" : null,
                 "positionX" : 6,
                 "positionY" : 4,
                 "width" : 6,
                 "height" : 4,
                 "isBackSide" : false,
                 "isFullScreenMode" : false,
                 "state" : 1,
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
                 },
                 "id" : null,
                 "numberOfRecord" : -1,
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
                 "filters" : []
              }
           ],
           "commonFilterFields" : [],
           "subscriptions" : []
        }
      }
