

=========================================
UserPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **searchByRole** |br|
         arrray of objects
      -
      -  An array of :doc:`RoleDetail` objects
      -
   *  -  **visibleUserIds** |br|
         array of string (GUID)
      -
      -  The list of visible users' ids that the current user can view, search, sort
      -
   *  -  **userModeType** |br|
         integer
      -
      -  |br|

         *  0 = All
         *  1 = Access
         *  2 = Schedule
      -
   *  -  **includeRootAdminIfMatch** |br|
         boolean
      -
      -  Whether to include root admin if matching
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **UserPagedRequest Sample**:

   .. code-block:: json

      {
        "tenantId" : null,
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "userName",
              "descending" : true
           }
        ]
      }
