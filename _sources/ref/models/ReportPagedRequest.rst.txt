

=========================================
ReportPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **categoryId** |br|
         string (GUID)
      -  Y
      -  The id of the category if available
      -
   *  -  **subCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the sub-category if available
      -
   *  -  **isGlobal** |br|
         boolean
      -  Y
      -  Whether to load global reports
      -
   *  -  **timestampOffset** |br|
         real number
      -
      -  The timestamp offset. See :doc:`/ui/doc_user_setup`.
      -
   *  -  **excludeIds** |br|
         array of strings (GUIDs)
      -
      -  The list of report ids to exclude
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **ReportPagedRequest Sample**:

   .. code-block:: json

      {
        	"subcategoryid" : null,
        	"categoryId" : null,
        	"tenantId" : null,
        	"pageSize" : 10,
        	"pageIndex" : 1,
        	"sortOrders" : [{
        			"key" : "reportname",
        			"descending" : true
        		}
        	],
        	"criteria" : [{
        			"key" : "reportName",
        			"value" : "test",
        			"operation" : 1
        		}
        	]
      }
