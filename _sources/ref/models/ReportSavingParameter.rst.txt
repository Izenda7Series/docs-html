

=========================================
ReportSavingParameter
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
      -  Is this saved as new report
      -
   *  -  **report** |br|
         object
      -
      -  A :doc:`ReportDefinition` object
      -
   *  -  **section** |br|
         integer
      -
      -  The report section

         -  0 = All
         -  1 = DataSource
         -  2 = Fields
         -  3 = CalculatedField
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **ignoreCheckChange** |br|
         boolean
      -
      -  Is the check for report changes ignored
      -
   *  -  **ignoreCheckName** |br|
         boolean
      -
      -  Is the check for report name ignored
      -
   *  -  **insertWithAssignedId** |br|
         boolean
      -
      -  Whether to use the populated report id in **report** object to insert
      -
   *  -  **overrideCalculatedFields** |br|
         boolean
      -
      -  Whether to override calculated fields
      -
   *  -  **reportState** |br|
         integer
      -
      -  +  0 = Posted - Report is posted from client
         +  1 = Saved  - Get report from database
         +  2 = Draft  - Get report from draft
      -

Inherited fields:

.. include:: ReportParameter.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
       "reportKey" : {
          "key" : null,
          "modified" : null
       },
       "section" : 0,
       "saveAs" : false,
       "ignoreCheckChange" : false,
       "report" : {
          "name" : "",
          "type" : "Templates",
          "previewRecord" : 10,
          "advancedMode" : true,
          "allowNulls" : false,
          "isDistinct" : false,
          "reportDataSource" : [{
                "aliasId" : "479be129-338d-45f1-b216-1d95957fe2c8_Order Details",
                "querySourceId" : "479be129-338d-45f1-b216-1d95957fe2c8",
                "querySourceName" : "Order Details",
                "selected" : true
             }, {
                "aliasId" : "54852be4-5584-4c23-ae5d-4197724059e1_Orders",
                "querySourceId" : "54852be4-5584-4c23-ae5d-4197724059e1",
                "querySourceName" : "Orders",
                "selected" : true
             }
          ],
          "reportRelationship" : [{
                "tempId" : "16d3b9bf-86cb-45fa-b33d-53e3e2a8a042",
                "joinConnectionId" : "db19bb46-ffa3-45fd-b205-0dad305fdf98",
                "foreignConnectionId" : "db19bb46-ffa3-45fd-b205-0dad305fdf98",
                "joinQuerySourceId" : "479be129-338d-45f1-b216-1d95957fe2c8",
                "joinQuerySourceName" : "Order Details",
                "joinDataSourceCategoryName" : "",
                "foreignDataSourceCategoryName" : "",
                "foreignQuerySourceId" : "54852be4-5584-4c23-ae5d-4197724059e1",
                "foreignQuerySourceName" : "Orders",
                "joinFieldId" : "a0011b48-ef08-45fe-b044-abc68442cd17",
                "joinFieldName" : "OrderID",
                "foreignFieldId" : "3caf9c17-abd7-4119-809d-2c3debb8eb37",
                "foreignFieldName" : "OrderID",
                "alias" : "",
                "systemRelationship" : true,
                "joinType" : "Inner",
                "parentRelationshipId" : "c55d696b-f25d-4a6f-a951-7a4e6e532c98",
                "position" : null,
                "relationshipKeyJoins" : [],
                "selectedForeignAlias" : "54852be4-5584-4c23-ae5d-4197724059e1_Orders",
                "id" : "16d3b9bf-86cb-45fa-b33d-53e3e2a8a052",
                "state" : 1,
                "validationKey" : "c55d696b-f25d-4a6f-a951-7a4e6e532c98",
                "relationshipPosition" : 0,
                "invalidAlias" : null,
                "hidden" : false,
                "level" : 1
             }
          ],
          "reportPart" : []
       },
       "expandedLevel" : 0,
       "filters" : []
      }
