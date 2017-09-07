
=========================
ReportPartChartProperties
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
      -  The chart type

         .. hlist::
            :columns: 3

            -  Line
            -  Column
            -  Bar
            -  Area
            -  Pie
            -  Funnel
            -  Donut
            -  Combination
            -  TreeMap
            -  HeatMap
            -  Bubble
            -  Scatter
            -  Waterfall
            -  Sparkline
   *  -  **commonOptions** |br|
         object
      -
      -  The options that are common for all chart types
   *  -  .. container:: lpad2

               **izHoverLabels** |br|
               boolean
      -
      -  Whether to show labels on hover
   *  -  .. container:: lpad2

               **izLegend.visibility** |br|
               boolean
      -
      -  Is the legend visible
   *  -  .. container:: lpad2

               **izLegend.horizontalAlign** |br|
               string
      -
      -  The alignment for horizontal axis, either izRight, izLeft or izCenter
   *  -  .. container:: lpad2

               **izLegend.verticalAlign** |br|
               string
      -
      -  The alignment for vertical axis, either izTop, izBottom or izMiddle
   *  -  .. container:: lpad2

               **izLegend.borderWidth** |br|
               integer
      -
      -  The border width for the legend
   *  -  .. container:: lpad2

               **izChartStyle** |br|
               object
      -
      -  To be updated
   *  -  .. container:: lpad2

               **izendaHiddenAllAxis** |br|
               boolean
      -
      -  Whether to hide all axis
   *  -  **optionByType** |br|
         object
      -
      -  The options that are specific for each chart type
   *  -  .. container:: lpad2

               **izTotalLabel** |br|
               string
      -
      -  To be updated
   *  -  .. container:: lpad2

               **izUseSeparator** |br|
               boolean
      -
      -  Whether to use separators
   *  -  .. container:: lpad2

               **izInverted** |br|
               boolean
      -
      -  Whether to invert X-axis and Y-axis
   *  -  .. container:: lpad2

               **izSpline** |br|
               boolean
      -
      -  Whether to use spline
   *  -  .. container:: lpad2

               **izValueLabel** |br|
               boolean
      -
      -  Whether to show labels for values
   *  -  .. container:: lpad2

               **legendSettings** |br|
               boolean
      -
      -  Whether to use settings for legends
   *  -  **view** |br|
         object
      -
      -  
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
   *  -  **commonXYAxis** |br|
         object
      -
      -  
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
