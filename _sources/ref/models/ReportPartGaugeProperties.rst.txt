
=========================
ReportPartGaugeProperties
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **chartType** |br|
         string
      -
      -  The gauge type: either SolidGauge, LinearGauge or SimpleGauge
   *  -  **optionByType** |br|
         object
      -
      -  The options that are specific for each chart type
   *  -  .. container:: lpad2

               **izUseSeparator** |br|
               boolean
      -
      -  Whether to use separators
   *  -  .. container:: lpad2

               **izUsePagination** |br|
               boolean
      -
      -  Whether to use pagination
   *  -  .. container:: lpad2

               **izItemPerRow** |br|
               integer
      -
      -  The number of gauges per row, default 3
   *  -  **view** |br|
         object
      -
      -  
   *  -  .. container:: lpad2

               **showLabels** |br|
               boolean
      -
      -  Whether to show labels
   *  -  .. container:: lpad2
   
            **dataRefreshInterval** |br|
            object
      -
      -  An object with the following fields
   *  -  .. container:: lpad4
   
            **enable** |br|
            boolean
      -
      -  Is this feature turned on
   *  -  .. container:: lpad4
   
            **updateInteval** |br|
            integer
      -
      -  The refresh interval
   *  -  .. container:: lpad4
   
            **isAll** |br|
            boolean
      -
      -  View all data (or x latest records)
   *  -  .. container:: lpad4
   
            **latestRecord** |br|
            integer
      -
      -  How many latest records to retrieve

   *  -  **printing** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **izPageBreak** |br|
            **AfterSeparator** |br|
            boolean
      -
      -  Whether to insert page break after separator
