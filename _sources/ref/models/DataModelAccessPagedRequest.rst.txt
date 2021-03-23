

=============================
DataModelAccessPagedRequest
=============================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **roleId** |br|
         string (GUID)
      -
      -  The id of the role
      -
   *  -  **visibleQuerySourcesTree** |br|
         array of objects
      -
      -  An array of :doc:`DataSourceItem` objects
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **DataModelAccessPagedRequest Sample**:

   .. code-block:: json

      {  
         "tenantId":"c39a4500-b902-4e5b-ae86-901c09b71516",
         "roleId":"101991da-d576-488b-a0aa-4df03512fbbb",
         "skipItems":0,
         "pageSize":100,
         "parentIds":[],
         "visibleQuerySourcesTree":[],
         "criteria":[  
            {  
               "key":"DataSourceName",
               "value":""
            },
            {  
               "key":"ShowCheckedQuerySource",
               "value":false
            }
         ]
      }