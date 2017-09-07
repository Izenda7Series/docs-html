

=========================================
SubscriptionPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report if available
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard if available
      -
   *  -  **isSubscription** |br|
         boolean
      -
      -  Used internally: is this a subscription request
      -
   *  -  **isReportingOwner** |br|
         boolean
      -
      -  Used internally: is current user the report/dashboard owner
      -
   *  -  **createdById** |br|
         string (GUID)
      -  Y
      -  Used internally
      -
   *  -  **subscriptions** |br|
         array of objects
      -
      -  An array of subscriptions, should be populated in case modifications are not yet saved to database
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **SubscriptionPagedRequest Sample**:

   .. code-block:: json

      {
        "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f",
        "isSubscription" : true,
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
              "key" : "name",
              "descending" : true
           }
        ]
      }
