

=========================================
PagedResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **result** |br|
         object
      -
      -  The search result
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

      **Sample**:

   .. code-block:: json

      {
        "result" : ["search result 1", "search result 2"],
        "pageIndex" : 1,
        "pageSize" : 10,
        "total" : 2
      }
