
=====================
ReportPartGauge
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
      -  The type of the report part (2 = Gauge)
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
      -  A :doc:`ReportPartGaugeProperties` object
   *  -  **labels** |br|
         object
      -
      -  Data for the Labels box |br|
         A :doc:`ReportPartContainer` object containing "labels" in **name** and the list of selected data source fields in **elements**
   *  -  **values** |br|
         object
      -
      -  Data for the Values box |br|
         A :doc:`ReportPartContainer` object containing "values" in **name** and the list of selected data source fields in **elements**
   *  -  **separators** |br|
         object
      -
      -  Data for the Separators box |br|
         A :doc:`ReportPartContainer` object containing "separators" in **name** and the list of selected data source fields in **elements**
