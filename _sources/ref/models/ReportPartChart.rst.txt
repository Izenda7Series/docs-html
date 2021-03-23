
=====================
ReportPartChart
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
      -  The type of the report part (0 = Chart)
   *  -  **title** |br|
         object
      -
      -  The title object
   *  -  **description** |br|
         object
      -
      -  The description object
   *  -  **properties** |br|
         object
      -
      -  A :doc:`ReportPartChartProperties` object
   *  -  **settings** |br|
         object
      -
      -  A dynamic object to keep the settings in Report Part Configuration, can be user-defined.
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
   *  -  **valuesLabels** |br|
         object
      -
      -  Data for the Values Labels box |br|
         A :doc:`ReportPartContainer` object containing "valuesLabels" in **name** and the list of selected data source fields in **elements**
   *  -  **separators** |br|
         object
      -
      -  Data for the Separators box |br|
         A :doc:`ReportPartContainer` object containing "separators" in **name** and the list of selected data source fields in **elements**
   *  -  **bubbleSize** |br|
         object
      -
      -  Data for the Bubble Size box |br|
         A :doc:`ReportPartContainer` object containing "bubbleSize" in **name** and the list of selected data source fields in **elements**
