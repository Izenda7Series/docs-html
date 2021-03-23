

=========================================
SystemSchedulingPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **systemLevel** |br|
         boolean
      -
      -  Is the search at System level.
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **System SchedulingPagedRequest Sample**:

   .. code-block:: json

      {
        "systemLevel" : true,
        "tenantId" : null,
        "pageIndex" : 1,
        "pageSize" : 10,
        "sortOrders" : [{
              "key" : "name",
              "descending" : true
           }
        ],
        "criteria" : [{
              "key" : "ReportingType",
              "value" : ""
           }, {
              "key" : "ReportDashboardName",
              "value" : ""
           }, {
              "key" : "DeliveryType",
              "value" : ""
           }, {
              "key" : "DeliveryMethod",
              "value" : ""
           }, {
              "key" : "Recipients",
              "value" : ""
           }, {
              "key" : "Type",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRun",
              "value" : ""
           }, {
              "key" : "NextScheduledRun",
              "value" : ""
           }, {
              "key" : "NextScheduledRunFrom",
              "value" : ""
           }, {
              "key" : "NextScheduledRunTo",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRunFrom",
              "value" : ""
           }, {
              "key" : "LastSuccessfulRunTo",
              "value" : ""
           }, {
              "key" : "RecurrenceType",
              "value" : ""
           }, {
              "key" : "ExportFileType",
              "value" : ""
           }, {
              "key" : "CreatedBy",
              "value" : ""
           }
        ]
      }
