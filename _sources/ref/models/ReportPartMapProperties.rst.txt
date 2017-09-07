
=========================
ReportPartMapProperties
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **chartType** |br|
         string
      -  No
      -  The map type: either SolidGauge, LinearGauge or SimpleGauge
   *  -  **reportPartState** |br|
         object
      -
      -
   *  -  .. container:: lpad2

               **drilldownInfo** |br|
               array of objects
      -
      -  The drill down information
   *  -  .. container:: lpad2

               **activeSerie** |br|
               object
      -  Y
      -  To be updated
   *  -  .. container:: lpad2

               **pointOptionsList** |br|
               array of objects
      -  **No**
      -  Selected data source fields in Point Options boxes |br|
         Cannot be empty
   *  -  .. container:: lpad4

               **label** |br|
               string
      -
      -  Name of the data source field
   *  -  .. container:: lpad4

               **value** |br|
               string
      -
      -  Name of the data source field
   *  -  .. container:: lpad4

               **field** |br|
               object
      -
      -  The data of the selected data source field |br|
         An exact copy of content of **field** in :doc:`ReportPartElement`
   *  -  .. container:: lpad4

               **pointType** |br|
               string
      -
      -  Type of the point, either "country", "state", "county", "city", "postalCode", "latitude" or "longtitude"
   *  -  .. container:: lpad4

               **pointTypeName** |br|
               string
      -
      -  Same value as **pointType**
   *  -  .. container:: lpad2

               **activePointOption** |br|
               object
      -  **No**
      -  The active point in the above **pointOptionsList** |br|
         Cannot be empty
   *  -  **continentInfo** |br|
         object
      -
      -  To be updated
   *  -  **countryInfo** |br|
         object
      -
      -  To be updated
   *  -  **stateInfo** |br|
         object
      -
      -  To be updated
   *  -  **commonOptions** |br|
         object
      -
      -  The options that are common for all map types
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
      -  The options that are specific for each map type
   *  -  .. container:: lpad2

               **izValueLabel** |br|
               boolean
      -
      -  Whether to show value labels
   *  -  .. container:: lpad2

               **izShowTooltip** |br|
               boolean
      -
      -  Whether to show tooltips
   *  -  .. container:: lpad2

               **izMapLabel** |br|
               boolean
      -
      -  Whether to show labels for map
   *  -  .. container:: lpad2

               **izMapNavigation.enabled** |br|
               boolean
      -
      -  Whether map navigation is enabled
   *  -  .. container:: lpad2

               **legendSettings** |br|
               boolean
      -
      -  Whether legend settings are set
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
