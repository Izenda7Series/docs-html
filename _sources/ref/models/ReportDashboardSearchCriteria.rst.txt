

=========================================
ReportDashboardSearchCriteria
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **criterias** |br|
         array of objects
      -
      -  An array of :doc:`SearchCriteria` objects
      -
   *  -  **sortCriteria** |br|
         object
      -
      -  A :doc:`SortOrder` object
      -
   *  -  **copyGlobal** |br|
         boolean
      -
      -  Searches copy global report or not
      -
   *  -  **type** |br|
         integer
      -
      -  The type

         - 0 = Report
         - 1 = Template
         - 2 = Dashboard
      -
   *  -  **isUncategorized** |br|
         boolean
      -
      -  Searches uncategorized rows or not
      -
   *  -  **visibleCategoryIds** |br|
         array of strings (GUID)
      -
      -  List of visible category ids
      -
   *  -  **visibleSubCategoryIds** |br|
         array of strings (GUID)
      -
      -  List of visible sub-category ids
      -
   *  -  **visibleLocalUncategorized** |br|
         boolean
      -
      -  Whether local Uncategorized is visible
      -
   *  -  **visibleGlobalUncategorized** |br|
         boolean
      -
      -  Whether global Uncategorized is visible
      -
   *  -  **defaultChecked** |br|
         boolean
      -
      -  Default checked setting
      -
   *  -  **includeHascode** |br|
         boolean
      -
      -  Whether to compute hashcode
      -
   *  -  **timestampOffset** |br|
         real number
      -
      -  The timestamp offset
      -
   *  -  **includeGlobalCategory** |br|
         boolean
      -
      -  Whether to include global category
      -
   *  -  **isGlobal** |br|
         boolean
      -  Y
      -  Whether this instance is global
      -
   *  -  **includeUncategory** |br|
         boolean
      -
      -  Whether to include Uncategorized
      -

.. deprecated:: 2.0.0
   tenantId field is removed

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "tenantId" : null,
        "isUncategorized" : false,
        "criterias" : [{
              "key" : "CategoryId"
           }
        ]
      }
