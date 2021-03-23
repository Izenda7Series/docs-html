
=====================
ReportPartMap
=====================

.. comment: this is the Object Model in Front-end

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **type** |br|
         integer
      -
      -  The type of the report part (4 = Map)
   *  -  **title** |br|
         object
      -
      -  To be updated
   *  -  **description** |br|
         object
      -
      -  To be updated
   *  -  **properties** |br|
         object
      -
      -  A :doc:`ReportPartMapProperties` object
   *  -  **pointOptions** |br|
         object
      -
      -  Data for Point Options boxes |br|
         A :doc:`ReportPartContainer` object containing "pointOptions" in **name** and the list of selected data source fields (:doc:`ReportPartElement` objects) in **elements**. |br|
         The field ``properties.pointOptionType`` of each :doc:`ReportPartElement` object should be either "country", "state", "county", "city", "postalCode", "latitude" or "longtitude".
   *  -  **shadingMetric** |br|
         object
      -
      -  Data for the Values > Shading Metric box |br|
         A :doc:`ReportPartContainer` object containing "shadingMetric" in **name** and the list of selected data source fields in **elements**
   *  -  **bubbleMetrics** |br|
         object
      -
      -  Data for the Values > Bubble Metric box |br|
         A :doc:`ReportPartContainer` object containing "bubbleMetrics" in **name** and the list of selected data source fields in **elements**
