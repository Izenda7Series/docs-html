
============================
ReportPartElementProperties
============================

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **fieldItemVisible** |br|
         boolean
      -
      -  Is the field visible
   *  -  **dataFormattings** |br|
         object
      -
      -  The properties of the data source field, in Data Formatting group
   *  -  .. container:: lpad2

            **function** |br|
            string (GUID)
      -
      -  The id of the Izenda function
   *  -  .. container:: lpad2

            **functionInfo** |br|
            object
      -
      -  The properties for the function
   *  -  .. container:: lpad4

            **id** |br|
            string (GUID)
      -
      -  The id of the Izenda function
   *  -  .. container:: lpad4

            **name** |br|
            string
      -
      -  The name of the Izenda function
   *  -  .. container:: lpad4

            **expression** |br|
            string
      -
      -  The expression
   *  -  .. container:: lpad4

            **dataType** |br|
            string
      -
      -  The data type
   *  -  .. container:: lpad4

            **formatDataType** |br|
            string
      -
      -  The output data type
   *  -  .. container:: lpad4

            **syntax** |br|
            string
      -
      -  The syntax displayed to user
   *  -  .. container:: lpad4

            **expressionSyntax** |br|
            string
      -
      -  The syntax of the function/operator
   *  -  .. container:: lpad4

            **isOperator** |br|
            boolean
      -
      -  Is this an operator (or a function)
   *  -  .. container:: lpad4

            **userDefined** |br|
            boolean
      -
      -  Is this a user-defined function
   *  -  .. container:: lpad4

            **extendedProperties** |br|
            object
      -
      -  A dynamic object to store the extended properties
   *  -  .. container:: lpad2

            **format** |br|
            object
      -
      -  
   *  -  .. container:: lpad4

            **createNewHiddenPercenOfGroupField** |br|
            string
      -
      -  Whether to create a new hidden "PercentOfGroup" field
   *  -  .. container:: lpad2

            **font** |br|
            string
      -
      -  The font properties
   *  -  .. container:: lpad4

            **family** |br|
            string
      -
      -  The font family, e.g. "Roboto"
   *  -  .. container:: lpad4

            **size** |br|
            integer
      -
      -  The font size
   *  -  .. container:: lpad4

            **bold** |br|
            boolean
      -
      -  Whether text is in bold
   *  -  .. container:: lpad4

            **italic** |br|
            boolean
      -
      -  Whether text is in italic
   *  -  .. container:: lpad4

            **underline** |br|
            boolean
      -
      -  Whether text is underlined
   *  -  .. container:: lpad4

            **color** |br|
            string
      -
      -  The text color
   *  -  .. container:: lpad4

            **backgroundColor** |br|
            string
      -
      -  The background color
   *  -  .. container:: lpad2

            **width** |br|
            string (GUID)
      -
      -  The width properties
   *  -  .. container:: lpad2

            **alignment** |br|
            string
      -
      -  The text alignment for the data source field, either "alignLeft", "alignCenter" or "alignRight"
   *  -  .. container:: lpad2

            **sort** |br|
            string
      -
      -  The sorting option, either "ASC" or "DESC"
   *  -  .. container:: lpad2

            **color** |br|
            object
      -
      -  The color properties for the data source field
   *  -  .. container:: lpad4

            **textColor** |br|
            object
      -
      -  The text color properties
   *  -  .. container:: lpad6

            **rangePercent** |br|
            string
      -
      -  The range percent color option if available
   *  -  .. container:: lpad6

            **rangeValue** |br|
            string
      -
      -  The range value color option if available
   *  -  .. container:: lpad6

            **value** |br|
            string
      -
      -  The color value if available
   *  -  .. container:: lpad4

            **cellColor** |br|
            object
      -
      -  The cell color properties
   *  -  .. container:: lpad6

            **rangePercent** |br|
            string
      -
      -  The range percent color option if available
   *  -  .. container:: lpad6

            **rangeValue** |br|
            string
      -
      -  The range value color option if available
   *  -  .. container:: lpad6

            **value** |br|
            string
      -
      -  The color value if available
   *  -  .. container:: lpad2

            **alternativeText** |br|
            object
      -
      -  The alternative text property for the data source field
   *  -  .. container:: lpad4

            **rangePercent** |br|
            string
      -
      -  The range percent color option if available
   *  -  .. container:: lpad4

            **rangeValue** |br|
            string
      -
      -  The range value color option if available
   *  -  .. container:: lpad4

            **value** |br|
            string
      -
      -  The color value if available
   *  -  .. container:: lpad2

            **customURL** |br|
            object
      -
      -  The custom url property for the data source field
   *  -  .. container:: lpad4

            **url** |br|
            string
      -
      -  The url
   *  -  .. container:: lpad4

            **option** |br|
            string
      -
      -  Either "LINK_NEW_WINDOW", "LINK_NEW_TAB" or "LINK_CURRENT_WINDOW"
   *  -  .. container:: lpad2

            **embeddedJavascript** |br|
            string
      -
      -  The Embedded Javascript property for the data source field
   *  -  .. container:: lpad4

            **script** |br|
            string
      -
      -  The script
   *  -  .. container:: lpad2

            **subTotal** |br|
            string
      -
      -  The Sub Total property for the data source field
   *  -  .. container:: lpad4

            **label** |br|
            string
      -
      -  The Subtotal label
   *  -  .. container:: lpad4

            **function** |br|
            string
      -
      -  The Subtotal function
   *  -  .. container:: lpad4

            **expression** |br|
            string
      -
      -  The Subtotal expression if available
   *  -  .. container:: lpad4

            **dataType** |br|
            string
      -
      -  The target data type
   *  -  .. container:: lpad4

            **format** |br|
            object
      -
      -  Format options
   *  -  .. container:: lpad4

            **previewResult** |br|
            string
      -
      -  The cached preview result
   *  -  .. container:: lpad4

            **levels** |br|
            string
      -
      -  The level of subtotal |br|
         For Form report part only 

         .. versionadded:: 2.12.0
   *  -  .. container:: lpad2

            **grandTotal** |br|
            string
      -
      -  The Grand Total property for the data source field
   *  -  .. container:: lpad4

            **label** |br|
            string
      -
      -  The Subtotal label
   *  -  .. container:: lpad4

            **function** |br|
            string
      -
      -  The Grandtotal function
   *  -  .. container:: lpad4

            **expression** |br|
            string
      -
      -  The Grandtotal expression if available
   *  -  .. container:: lpad4

            **dataType** |br|
            string
      -
      -  The target data type
   *  -  .. container:: lpad4

            **format** |br|
            object
      -
      -  Format options
   *  -  .. container:: lpad4

            **previewResult** |br|
            string
      -
      -  The cached preview result
   *  -  **headerFormating** |br|
         object
      -
      -  The formatting of the header
   *  -  .. container:: lpad2

            **font** |br|
            object
      -
      -  The font properties of the header
   *  -  .. container:: lpad4

            **family** |br|
            string
      -
      -  The font family, e.g. "Roboto"
   *  -  .. container:: lpad4

            **size** |br|
            integer
      -
      -  The font size
   *  -  .. container:: lpad4

            **bold** |br|
            boolean
      -
      -  Whether text is in bold
   *  -  .. container:: lpad4

            **italic** |br|
            boolean
      -
      -  Whether text is in italic
   *  -  .. container:: lpad4

            **underline** |br|
            boolean
      -
      -  Whether text is underlined
   *  -  .. container:: lpad4

            **color** |br|
            string
      -
      -  The text color
   *  -  .. container:: lpad4

            **backgroundColor** |br|
            string
      -
      -  The background color
   *  -  .. container:: lpad2

            **alignment** |br|
            string
      -
      -  The header alignment
   *  -  .. container:: lpad2

            **wordWrap** |br|
            object
      -
      -  The header word wrap setting
   *  -  .. container:: lpad2

            **columnGroup** |br|
            string
      -
      -  The column group setting
   *  -  **drillDown** |br|
         object
      -
      -  The drill down properties
   *  -  **otherProps** |br|
         object
      -
      -  Other properties |br|
         A dynamic object
   *  -  **metric** |br|
         object
      -  Y
      -  Properties for Gauge metrics
   *  -  .. container:: lpad2
   
            **scale** |br|
            object
      -
      -  The scale settings
   *  -  .. container:: lpad6
   
            **from** |br|
            integer
      -
      -  The minimum value of the scale
   *  -  .. container:: lpad6
   
            **to** |br|
            integer
      -
      -  The maximum value of the scale
   *  -  .. container:: lpad2
   
            **unitLabel** |br|
            string
      -
      -  The display unit label beneath the gauge
   *  -  .. container:: lpad2
   
            **thresholds** |br|
            object
      -
      - 
   *  -  .. container:: lpad4
   
            **setting** |br|
            string
      -
      -  "static" or "dynamic"
   *  -  .. container:: lpad4
   
            **levels** |br|
            array of objects
      -
      -  An array of objects with the following fields
   *  -  .. container:: lpad6
   
            **name** |br|
            string
      -
      -  Either "low", "target" or "high"
   *  -  .. container:: lpad6
   
            **color** |br|
            string
      -
      -  The color for the threshold level
   *  -  .. container:: lpad6
   
            **operator** |br|
            string
      -
      -  Either "less than", "between" or "greater than"
   *  -  .. container:: lpad6
   
            **value** |br|
            integer
      -
      -  The value for "greater than" operator, or the minimum value for "between than" operator
   *  -  .. container:: lpad6
   
            **valueUpper** |br|
            integer
      -
      -  The value for "less than" operator, or the maximum value for "between than" operator
   *  -  .. container:: lpad6
   
            **element** |br|
            object
      -
      -  The element value for "greater than" operator, or the minimum element value for "between than" operator
   *  -  .. container:: lpad6
   
            **elementUpper** |br|
            object
      -
      -  The element value for "less than" operator, or the maximum element value for "between than" operator
