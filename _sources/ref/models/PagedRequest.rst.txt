


PagedRequest
-----------------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **criteria** |br|
         array of objects
      -
      -  An array of :doc:`SearchCriteria` objects
      -
   *  -  **sortOrders** |br|
         array of objects
      -
      -  An array of :doc:`SortOrder` objects
      -
   *  -  **parentIds** |br|
         array of strings (GUIDs)
      -
      -  Ids of the parents
      -
   *  -  **pageIndex** |br|
         integer
      -
      -  The index of the page
      -  Inherited from :doc:`PagingInfo`
   *  -  **pageSize** |br|
         integer
      -
      -  The size of the page
      -  Inherited from :doc:`PagingInfo`
   *  -  **total** |br|
         integer
      -
      -  The total number of rows
      -  Inherited from :doc:`PagingInfo`
   *  -  **skipItems** |br|
         integer
      -
      -  Skip items
      -  Inherited from :doc:`PagingInfo`
   *  -  **isLastPage** |br|
         boolean
      -
      -  Whether this is the last page
      -  Inherited from :doc:`PagingInfo`

.. container:: toggle

   .. container:: header

      **PagedRequest Sample**:

   .. code-block:: json

      {
        "criteria": [
          {
            "key": "All",
            "value": "",
            "operation": 1
          }
        ],
        "pageIndex": 1,
        "pageSize": 10,
        "sortOrders": [
          {
            "key": "shareWith",
            "descending": true
          }
        ]
      }
