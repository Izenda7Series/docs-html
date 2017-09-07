

=========================================
RelationshipPagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySourceId** |br|
         string (GUID)
      -  Y
      -  The id of the query source
      -
   *  -  **objectId** |br|
         string (GUID)
      -  Y
      -  The id of the object in draft to load from |br| |br|
         Put null here to load from the database
      -
   *  -  **relationshipOrders** |br|
         array of objects
      -
      -  An array of :doc:`RelationshipOrder` objects
      -
   *  -  **querySources** |br|
         array of objects
      -
      -  An array of :doc:`ReportSelectedQuerySource` objects
      -
   *  -  **selectedDataSourceChanged** |br|
         boolean
      -
      -  Whether selected data source has changed
      -

Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **RelationshipPagedRequest Sample**:

   .. code-block:: json

      {
        "querySourceId" : null,
        "tenentId" : "",
        "criteria" : [{
              "key" : "All",
              "value" : "",
              "operation" : 1
           }
        ],
        "pageIndex" : 1,
        "pageSize" : 1,
        "sortOrders" : [{
              "key" : "DatabaseName",
              "descending" : true
           }
        ]
      }
