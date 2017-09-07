
=========================
ReportPartGridProperties
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **generalInfo** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **gridStyle** |br|
            string
      -
      -  Either "Vertical", "Horizontal", "Pivot" or "Drill Down"
   *  -  .. container:: lpad2
   
            **separatorStyle** |br|
            string
      -
      -  Either "Comma", "Comma With Label", "Line", "Line With Label", "Multi Level" or "Multi Level With Label"
   *  -  **table** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **border** |br|
            object
      -
      -  An object with the following fields
   *  -  .. container:: lpad4
   
            **top** |br|
            object
      -
      -  An object with 3 fields: dashStyle, color and thickness |br|
         Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad4
   
            **right** |br|
            object
      -
      -  An object with 3 fields: dashStyle, color and thickness |br|
         Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad4
   
            **bottom** |br|
            object
      -
      -  An object with 3 fields: dashStyle, color and thickness |br|
         Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad4
   
            **midVer** |br|
            object
      -
      -  An object with 3 fields: dashStyle, color and thickness |br|
         Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad4
   
            **left** |br|
            object
      -
      -  An object with 3 fields: dashStyle, color and thickness |br|
         Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad4
   
            **midHor** |br|
      -
      -     An object with 3 fields: dashStyle, color and thickness |br|
            Example: {"dashStyle":"dotted","color":"#000","thickness":1}
   *  -  .. container:: lpad2
   
            **backgroundColor** |br|
            string
      -
      -  The background color value
   *  -  **columns** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **width** |br|
            object
      -
      -  An object with the following fields
   *  -  .. container:: lpad4

            **value** |br|
            integer
      -
      -  The width
   *  -  .. container:: lpad2
   
            **alterBackgroundColor** |br|
            boolean
      -
      -  Use Alternating Background Color or not
   *  -  **rows** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **alterBackgroundColor** |br|
            boolean
      -
      -  Use Alternating Background Color or not
   *  -  **headers** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **font** |br|
            object
      -
      -  An object with the following fields
   *  -  .. container:: lpad4
   
            **family** |br|
            string
      -
      -  The font family
   *  -  .. container:: lpad4
   
            **size** |br|
            integer
      -
      -  The font size
   *  -  .. container:: lpad4
   
            **bold** |br|
            boolean
      -
      -  Is the text in bold
   *  -  .. container:: lpad4
   
            **italic** |br|
            boolean
      -
      -  Is the text italic
   *  -  .. container:: lpad4
   
            **underline** |br|
            boolean
      -
      -  Is the text underlined
   *  -  .. container:: lpad4
   
            **backgroundColor** |br|
            string
      -
      -  The background color
   *  -  .. container:: lpad2
   
            **alignment** |br|
            string
      -
      -  The text alignment
   *  -  .. container:: lpad2
   
            **wordWrap** |br|
            boolean
      -
      -  Turns on word wrap or not
   *  -  .. container:: lpad2
   
            **removeHeaderForExport** |br|
            boolean
      -
      -  Remove header when exporting or not
   *  -  **grouping** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **useSeparator** |br|
            boolean
      -
      -  Turns on Separator or not
   *  -  **view** |br|
         object
      -
      -  An object with the following fields
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
   *  -  .. container:: lpad2
   
            **usePagination** |br|
            boolean
      -
      -  Whether to use pagination
   *  -  .. container:: lpad2
   
            **pivotColumns** |br|
            **PerExportedPage** |br|
            integer
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **pageSize** |br|
            integer
      -
      -  The page size
   *  -  **printing** |br|
         object
      -
      -  An object with the following fields
   *  -  .. container:: lpad2
   
            **usePageBreak** |br|
            **AfterSeparator** |br|
            boolean
      -
      -  Whether to insert page break after separator
