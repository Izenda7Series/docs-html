==========================
Front-end Integration APIs
==========================

This list documents the JavaScript APIs used for Front-end Integration.

.. _Frontend_Integration_API:

.. note::
      See `front end considerations <https://www.izenda.com/docs/dev/dev_front_end_considerations.html>`_ for common troubleshooting tips for embedding Izenda's front end.

List of APIs
------------

.. list-table::
   :widths: 63 37
   :header-rows: 1

   * - Class and Method
     - Purpose
   * - **IzendaSynergy**
     -
   * - .. container:: lpad2
   
          `config(configJson)`_
     - Configure Izenda
   * - .. container:: lpad2
   
          `render(element)`_
     - Render all Izenda web page inside hosting web
   * - .. container:: lpad2
   
          `renderSettingPage(element)`_
     - Render Izenda Setting page only inside hosting web
   * - .. container:: lpad2
   
          `renderReportPage(element)`_
     - Render Izenda Report page only inside hosting web
   * - .. container:: lpad2
   
          `renderReportDesignerPage(element)`_
     - Render Izenda Report Designer Page (New/Edit Report) inside hosting web
   * - .. container:: lpad2
   
          `renderReportViewerPage(element,report_id, filter,integrationStyle)`_
     - Render Izenda Report Viewer page only inside hosting web
   * - .. container:: lpad2
   
          `renderReportPart(element,params)`_
     - Render specific :term:`Report Part` inside hosting web
   * - .. container:: lpad2
   
          `renderDashboardPage(element)`_
     - Render Izenda Dashboard page only inside hosing web
   * - .. container:: lpad2
   
          `renderNewDashboardPage(element)`_
     - Render Izenda New Dashboard page
   * - .. container:: lpad2
   
          `setCurrentUserContext({"token":access_token})`_
     - Authentication and authorization between hosting web and Izenda
   * - .. container:: lpad2
   
          `renderDashboardViewerPage(element, dashboard_id, filter, integrationStyle)`_
     - Render Izenda Dashboard Viewer page
   * - .. container:: lpad2
   
          `addJsFormat(formatName, formatFunction)`_
     - Register a JsFormatString with format function |br|

       .. versionadded:: 2.6.20
   * - .. container:: lpad2
   
          `getClass(name)`_
     - Get the class by name |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `registerVisualizationEngine(name, vizEngineClazz)`_
     - Register a visualization engine with a name |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `registerPropertyEditor(type, factory)`_
     - Register property editor with its factory function to create a custom property editor inside Report Designer's property panel. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createDropDownPropertySchema`_
     - Create a dropdown editor schema in Properties editor panel. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createPopupSettingPropertySchema`_
     - Create a popup editor schema in Properties editor panel. It appears as a label and a gear button which opens the popup dialog. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createCheckBoxPropertySchema`_
     - Create a checkbox editor schema in Properties editor panel. It appears as a label and a checkbox. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createSelectPropertySchema`_
     - Create a select editor schema in Properties editor panel. It appears as a label and select control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createNumberPropertySchema`_
     - Create a number editor schema in Properties editor panel. It appears as a label and number input control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createColorPaletteSettingPropertySchema`_
     - Create a color palette editor schema in Properties editor panel. It appears as a label and color palette input control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `registerFieldContainer`_
     - Register field container with its factory function in order to create a custom field container in Report Designer's report part configuration. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createStaticLabelFieldContainerSchema`_
     - Create a static label only without input box. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `createConditionalFieldContainerSchema`_
     - Create a conditional label and a input box of fields which allows to add/remove or drag/drop a field into. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `setReportPartConfiguration`_
     - Set configuration of a report part type. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `getReportPartConfiguration`_
     - Get configuration of a report part type. |br|

       .. versionadded:: 2.11.0
   * - .. container:: lpad2
   
          `extendReportPartStyleConfiguration`_
     - Extends report part with a new style configuration. |br|

       .. versionadded:: 2.11.0

config(configJson)
----------------------------------------------------------------------------------------------

Configure Izenda


**Parameters**

    configJson

    .. code-block:: javascript

       {
          "WebApiUrl": hostApi,
          "BaseUrl": "/izenda",
          "RootPath": "/Scripts/izenda",
          "CssFile": "izenda-ui.css",
          "Routes": {
            "Settings": "settings",
            "New": "new",
            "Dashboard": "dashboard",
            "Report": "report",
            "ReportViewer": "reportviewer",
            "ReportViewerPopup": "reportviewerpopup",
            "Viewer": "viewer"
          },
          "TimeOut": 3600,
          "UIPreferences": { 
                "ReportFilterSectionExpanded": true 
            },
          "NeedToEncodeUrl" : true
       }

.. versionadded:: 2.0

   |br| The optional ``NeedToEncodeUrl`` parameter (defaults to ``true`` if not specified). |br|
   Set it to ``false`` if host framework expects unencoded urls (such as Angular 2).

**Samples**

    .. code-block:: javascript

       var hostApi = location.protocol + '//' + location.host + "/api/";
       
       var configJson = {
          "WebApiUrl": hostApi,
          "BaseUrl": "/izenda",
          "RootPath": "/Scripts/izenda",
          "CssFile": "izenda-ui.css",
          "Routes": {
            "Settings": "settings",
            "New": "new",
            "Dashboard": "dashboard",
            "Report": "report",
            "ReportViewer": "reportviewer",
            "ReportViewerPopup": "reportviewerpopup",
            "Viewer": "viewer"
          },
          "TimeOut": 3600,
          "UIPreferences": { 
            "ReportFilterSectionExpanded": true 
          }
       };
       
       IzendaSynergy.config(configJson);

.. versionadded:: 2.10.0
.. _Set_WebApiUrl:

   |br| For version 2.10.0 and later, Izenda provides option to configure dynamic WebApiUrl. |br|
   **Samples**

   .. code-block:: javascript

      var configJson = {
         "WebApiUrl": () => {
            const currentHour = new Date().getHours();
            return currentHour < 6 || currentHour >= 22 ? 'http://localhost:14809/api/' : 'http://localhost:65469/api';
         },
         "BaseUrl": "/izenda",
         "RootPath": "/Scripts/izenda",
         "CssFile": "izenda-ui.css",
         "Routes": {
         "Settings": "settings",
         "New": "new",
         "Dashboard": "dashboard",
         "Report": "report",
         "ReportViewer": "reportviewer",
         "ReportViewerPopup": "reportviewerpopup",
         "Viewer": "viewer"
         },
         "TimeOut": 3600,
         "UIPreferences": { 
               "ReportFilterSectionExpanded": true 
         },
         "NeedToEncodeUrl" : true
      };

      IzendaSynergy.config(configJson);



render(element)
----------------------------------------------------------------------------------------------

Render all Izenda web page inside hosting web


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.render(document.getElementById('izenda-root'));

    .. figure:: /_static/images/All_Izenda_Inside.png

       Izenda Inside

renderSettingPage(element)
----------------------------------------------------------------------------------------------

Render Izenda Setting page only inside hosting web


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderSettingPage(document.getElementById('izenda-root'));

    .. figure:: /_static/images/Izenda_Settings.png

       Izenda Settings

renderReportPage(element)
----------------------------------------------------------------------------------------------

Render Izenda Report page only inside hosting web


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderReportPage(document.getElementById('izenda-root'));

    .. figure:: /_static/images/Izenda_Report_only.png

       Izenda Report only

renderReportDesignerPage(element)
----------------------------------------------------------------------------------------------

Render Izenda Report Designer Page (New/Edit Report) inside hosting web


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderReportDesignerPage(document.getElementById('izenda-root'));v

    .. figure:: /_static/images/Izenda_Report_Designer_only.png

       Izenda Report Designer only

renderReportViewerPage(element,report_id, filter,integrationStyle)
----------------------------------------------------------------------------------------------

Render Izenda Report Viewer page only inside hosting web


**Parameters**

        .. list-table::
           :class: apitable
           :widths: 25 75
           :header-rows: 1


           * - Field
             - Description
           * - **element** |br|
               A DOM element to render in
             - Element to render in
           * - **report_id** |br|
               String (GUID)
             - The report Id
           * - **overridingFilterValue** |br|
               A filter object
             - The values for the filters, in this format ``{ p1value: a_value, p2value: another_value, .. }``
           * - **integrationStyle** |br|
                
             - The options for toolbar and filter section, in this format ``{ "hideToolbar": true/false, "hideFilter": true/false }``

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderReportViewerPage(document.getElementById('izenda-root'), "C2946606-7159-4FB3-82B7-E7D4ED3162A0",{overridingFilterValue: { p1value: "test123" }},{ "hideFilter" : true});

    .. figure:: /_static/images/Izenda_Report_Viewer.png

       Izenda Report Viewer Only

renderReportPart(element,params)
----------------------------------------------------------------------------------------------

Render specific :term:`Report Part` inside hosting web


**Parameters**

        element : a DOM element |br|
        params : an object contains fields below:

        .. list-table::
           :class: apitable
           :widths: 35 40 25
           :header-rows: 1

           * - Field
             - Description
             - Note
           * - **id** |br|
               String (GUID)
             - The report part Id
             - Required
           * - **filter** |br|
               An array of Object with **key** and **value** 
             - Filters on sub report
             - Optional
           * - **crosssfilters** |br|
               An array of Object with **key** and **value** 
             - Cross filtering's filter on report
             - Optional
           * - **overridingFilterValue** |br|
                
             - Override all or specified default fillter values by using **pvalue**
             - Optional
           * - **onPublishDrillInfo** |br|
               A function
             - This function which will be invoked when drilldown
             - Optional
           * - **useQueryParam** |br|
               A boolean
             - A flag to use parameters specified in a query string of a URL
             - Optional, required for exports
           * - **useHash** |br|
               A boolean
             - A flag to use hashing in a URL
             - Optional, required for exports
             
**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderReportPart(document.getElementById('izenda-part1'), {
          "id": "804B35C8-44A4-4535-A484-F27E8ABA410D",
          "filters": [
            {
               "key": "[northwind].[dbo].[Order].[ShipCountry]",
               "value": "Australia"
            }
          ],
          "overridingFilterValue": {
             p1value : 10,
           },
          "crosssfilters": [
            {
               key: "[northwind].[dbo].[Order].[ProductID]",
               value: 23
            }
          ],
          onPublishDrillInfo: function (drillInfo) {
                console.log("drillInfo", drillInfo);
            }
       });

    .. figure:: /_static/images/Render_Specific_report_part.png

       Izenda Specific Report Part
       
    The following example demonstrates the use of useQueryParam and useHash for exports. The sample is derived from our `Sample MVC 5 Application <https://github.com/Izenda7Series/Mvc5StarterKit/blob/9f5133b9eadb713dee85e9cdaed21b1b21e22efd/Mvc5StarterKit/Scripts/izenda.integrate.js#L261>`_

      .. code-block:: javascript

         IzendaSynergy.renderReportPart(document.getElementById('izenda-root'), {
            id: reportPartId,
            useQueryParam: true,
            useHash: false
         });


renderDashboardPage(element)
----------------------------------------------------------------------------------------------

Render Izenda Dashboard page only inside hosing web


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderDashboardPage(document.getElementById('izenda-root'));

    .. figure:: /_static/images/Izenda_Dashboard.png

       Izenda Dashboard Only

renderNewDashboardPage(element)
----------------------------------------------------------------------------------------------

Render Izenda New Dashboard page


**Parameters**

    element

**Samples**

    .. code-block:: javascript

       IzendaSynergy.renderNewDashboardPage(document.getElementById('izenda-root'));

    .. figure:: /_static/images/Izenda_New_Dashboard.png

       Izenda Dashboard Designer Only

setCurrentUserContext({"token":access_token})
----------------------------------------------------------------------------------------------

Authentication and authorization between hosting web and Izenda


**Parameters**

    element |br|
    access_token

**Samples**

    .. code-block:: javascript

       var currentUserContext = {
          token: data.token
       };
       
       IzendaSynergy.setCurrentUserContext(currentUserContext);

renderDashboardViewerPage(element, dashboard_id, filter, integrationStyle)
----------------------------------------------------------------------------------------------

Render Izenda Dashboard Viewer page


**Parameters**

   .. list-table::
      :widths: 20 80

      * - **element**
        - The element to render in
      * - **dashboard_id**
        - The id of the dashboard
      * - **filter**
        - The values for the filters, in this format ``{ p1: a_value, p2: another_value, .. }``
      * - **integrationStyle**
        - The options for toolbar and common filter section, in this format ``{ hideDashboardToolbar: true/false, hideCommonFilter: true/false }``

**Samples**

   .. code-block:: javascript

      IzendaSynergy.renderDashboardViewerPage(
         document.getElementById('izenda-root'),
         '9371375f-2fe7-43f1-b83a-e69340f6136d',
         {
            p1: "10366",
            p2: "Barcelona"
         }, {
            hideDashboardToolbar: true,
            hideCommonFilter: false
         });

.. _addJsFormat:

addJsFormat(formatName, formatFunction)
---------------------------------------------

Register a JsFormatString with format function

This function is used in the LoadCustomDataFormat (see more `here <https://www.izenda.com/docs/dev/ref_iadhocextension.html?highlight=iadhocextension#loadcustomdataformat>`_). To register this function, it must be declared in either your izenda.integrate.js (for embedded mode) or the index.html for (standalone mode). See example of both integrated and standalone below:  

.. versionadded:: 2.6.20


**Parameters**

   .. list-table::
      :widths: 20 80

      * - **name**
        - The JsFormatString name that used in :doc:`../ref/models/DataFormat`
      * - **formatFunction**
        - The js format function

**Sample Integrated (izenda.integrate.js)**

   .. code-block:: javascript

      IzendaSynergy.config(configJson);
      // Put the registration of JS format functions below. Please note: the format label is case sensitive.
      IzendaSynergy.addJSFormat("1k", function (value)
         { return "$ " + value/1000 + " k"; }
      );

      
**Sample Standalone (index.html)**

   .. code-block:: html

      <script type="text/javascript" src="/izenda_ui.js?c76cbb3f0591ba2de5a0"></script>
      <script>

         // Ensure this script is placed after Izenda UI library (izenda_ui.js as above)
         (function() {
         
            // Please note: the format label is case sensitive.
            IzendaSynergy.addJsFormat("1k", function (value) {
            return "$ " + value/1000 + " K"
               });
         })();
      </script>
      
getClass(name)
----------------------------------

Get the class by name. Following is the list of supported classes that can be retrieved via this API:

.. versionadded:: 2.11.0

.. list-table::
   :widths: 45 55
   :header-rows: 1

   * - Class Name
     - Description
   * - VizEngine
     - The base class of Izenda visualization engine
   * - HighchartVizEngine
     - The visualization engine class of Highchart
   * - HighmapVizEngine
     - The visualization engine class of Highmap
   * - ChartOptionsBuilder
     - The base class of chart options builder. Extending ChartOptionsBuilder is to build a custom options builder for custom visualization engine.
   * - HighchartOptionsBuilder
     - The base class of Highchart chart options builder
   * - HighmapOptionsBuilder
     - The base class of Highmap map options builder
   * - ReportPartContent
     - The base class of report part content model
   * - ReportPartChartContent
     - The report part chart content model class
   * - ReportPartGaugeContent
     - The report part gauge content model class
   * - ReportPartMapContent
     - The report part map content model class
   * - AreaChartOptionsBuilder
     - The Area chart options builder class
   * - BarChartOptionsBuilder
     - The Bar chart options builder class
   * - BubbleChartOptionsBuilder
     - The Bubble chart options builder class
   * - ChartHasThresholdOptionBuilder
     - The base class of chart options builder that supports threshold settings
   * - ColumnChartOptionsBuilder
     - The Column chart options builder class
   * - CombinationChartOptionsBuilder
     - The Combination chart options builder class
   * - DefaultChartOptionsBuilder
     - The default chart options builder. All chart options builders inherit from this class. It consists of the common logic to handle a chart options
   * - DonutChartOptionsBuilder
     - The Donut chart options builder class
   * - FunnelChartOptionsBuilder
     - The Funnel chart options builder class
   * - HeatmapChartOptionsBuilder
     - The Heatmap chart options builder class
   * - LineChartOptionsBuilder
     - The Line chart options builder class
   * - PieChartOptionsBuilder
     - The Pie chart options builder class
   * - The Pie chart options builder class
     - The Scatter chart options builder class
   * - SparklineChartOptionsBuilder
     - The Sparkline chart options builder class
   * - TreemapChartOptionsBuilder
     - The Treemap chart options builder class
   * - WaterfallChartOptionsBuilder
     - The Waterfall chart options builder class
   * - LinearGaugeOptionsBuilder
     - The Linear gauge options builder class
   * - SimpleGaugeOptionsBuilder
     - The Simple gauge options builder class
   * - SolidGaugeOptionsBuilder
     - The Solid gauge options builder class
   * - ChartSettingsContainer
     - The ChartSettingsContainer React component. This component is used for building a custom popup content settings with supported configuration and preview panels.
   * - FieldContainer
     - The minimal field container React component. This component is used for building a custom field container with supported common behaviours (add/remove/drag/drop) of fields.

**Parameters**

   * **name**: Name of class

**Samples**

   Get *VizEngine* class

   .. code-block:: javascript

      getClass('VizEngine');


registerVisualizationEngine(name, vizEngineClazz)
-----------------------------------------------------------

Register a visualization engine with a name

.. versionadded:: 2.11.0

**VISUALIZATION_NAMES**

   Get the built-in visualization name constants

      *  `Highchart`: Name of Highchart visualization engine
      *  `Highmap`: Name of Highmap visualization engine


**Parameters**

   .. list-table::
      :widths: 20 80

      * - **name**
        - The name of visualization engine
      * - **vizEngineClazz**
        - The class or constructor function of visualization engine. This class must inherit from VizEngine class.

**Sample**

   .. code-block:: javascript

      class D3 extends VizEngine {
      draw(chartContainer, chartType, options, onCompleted) {
         //Implement the drawing logic into chartContainer here.
         }
      }

      registerVisualizationEngine('D3', D3);

registerPropertyEditor(type, factory)
-----------------------------------------------

Register property editor with its factory function to create a custom property editor inside Report Designer's property panel.

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **type**
        - Editor type key
      * - **factory**
        - Function to create editor component

**Sample**
   Register a text input property editor

   .. code-block:: javascript

      registerPropertyEditor('text', function(type, props) {
      return {
         component: Input,
         props: {
            className: 'form-control',
            onChange: props.onChange
         }
      };
      });

   Returns *void*

createDropDownPropertySchema
-----------------------------------------------------

Create a dropdown editor schema in Properties editor panel. This function is used as the factory property value of propertySchema of report part/style configuration.

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip of dropdown editor
      * - **props.value**
        - The value of selected item of dropdown editor
      * - **props.props**
        - The component properties
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   An example of how using the function to create a dropdown list field schema in report part property schema

   .. code-block:: javascript

      {
         factory: createDropDownSchema,
         title: 'Example Dropdown',
         value: 'getChartType',
         props: {
            defaultValue: 'value1',
            options: ['value1', 'value2']
         }
      }

createPopupSettingPropertySchema
---------------------------------------

Create a popup editor schema in Properties editor panel. It appears as a label and a gear button which opens the popup dialog. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip of editor
      * - **props.value**
        - The value of selected item of editor
      * - **props.props**
        - The component computational properties
      * - **props.staticProps**
        - The component's static properties
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   .. code-block:: javascript

      {
         factory: createPopupSettingSchema,
         title: 'Border',
         value: 'getBorder',
         props: {
            reportPartType: REPORT_PART_TYPE.Chart,
            title: 'Border Settings',
            // The Border settings dialog uses chart properties to render the preview
            allChartProps: 'getAllChartProps',
            // Getter function or property to determine whether the setting exists
            hadSetting: 'hadSettingBorder',
            // Function to reset the setting value
            fnResetDefaultValue: 'fnResetBorderDefaultValue',
            // Getter function to retrieve value
            loadValue: 'getBorder'
         },
         staticProps: {
            popupTitle: 'Border Settings',
            popupContent: ChartBorderSettings
         }
      }

createCheckBoxPropertySchema
-------------------------------------

Create a checkbox editor schema in Properties editor panel. It appears as a label and a checkbox. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip of editor
      * - **props.value**
        - The value of selected item of editor
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   .. code-block:: javascript

      izSeparator: {
         factory: createCheckBoxSchema,
         title: 'Use Separator',
         // 'getValueByKey' is a default getter function of Chart that allows to get the value of a property of chart properties by its field name, ie. izSeparator
         value: 'getValueByKey'
      }

createSelectPropertySchema
------------------------------------

Create a select editor schema in Properties editor panel. It appears as a label and select control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip of editor
      * - **props.value**
        - The value of selected item of editor
      * - **props.props**
        - The component computational properties
      * - **props.staticProps**
        - The component's static properties
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   Create a selection list of state with default blank option is All

   .. code-block:: javascript

      {
         factory: createSelectSchema,
         title: 'State',
         value: 'getValueByKey',
         props: {
            options: 'getStateByCountry'
         },
         staticProps: {
            blankOption: true,
            blankOptionText: 'All'
         }
      }

createNumberPropertySchema
--------------------------------------------------
Create a number editor schema in Properties editor panel. It appears as a label and number input control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip editor
      * - **props.value**
        - The value of selected item editor
      * - **props.props**
        - The component properties
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   .. code-block:: javascript

      {
         factory: createNumberSchema,
         title: 'Item Per Row',
         value: 'getValueByKey',
         props: {
            min: 1,
            max: 20,
            isDecimal: false
         }
      }

createColorPaletteSettingPropertySchema
-----------------------------------------------------

Create a color palette editor schema in Properties editor panel. It appears as a label and color palette input control. This function is used as the factory property value of propertySchema of report part/style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   **props**: An object with the following properties.

   .. list-table::
      :widths: 20 80

      * - **props.title**
        - The title of label
      * - **props.info**
        - The information tooltip editor
      * - **props.value**
        - The value of selected item editor
      * - **props.props**
        - The component properties
      * - **props.isHidden**
        - Hide the editor or not. |br| 
          (It is optional with the default value is *false*)

**Sample**

   .. code-block:: javascript

      {
         factory: createColorPaletteSettingSchema,
         title: 'Color Theme',
         value: 'getColorTheme',
         props: {
            selectionPopupTitle:'Select Color Theme',
            defaultColorThemeLabel:'No Theme',
            displaySettingStatus: true,
            needMaskDefault: false,
            defaultColorPalette: null,
            hiddenByState: true
         }
      }

registerFieldContainer
-----------------------------------------------------
Register field container with its factory function in order to create a custom field container in Report Designer's report part configuration. Most of the time, using createFieldContainerSchema function to create labeled box of fields fits in the same way with current Values, Labels... field containers.|br|

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **type**
        - Field container type, i.e. chart_label, grid_rows...
      * - **factory**
        - Function to create field container

**Sample**

   Create an custom metric fields container using *CustomMetricReactComponent*

   .. code-block:: javascript

      // Note that it requires to create a React component to render the custom metric GUI
      registerFieldContainer('custom_metric', function(type, containerProps) {
         return {
            key: type,
            component: CustomMetricReactComponent,
            props: containerProps
         };
      });

   Returns *void*

createStaticLabelFieldContainerSchema
-------------------------------------------------------

Create a static label only without input box. |br|

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **type**
        - Field container type, i.e. chart_label, grid_rows...
      * - **label**
        - The label text value or a function return a text

**Sample**

   .. code-block:: javascript

      createStaticLabelSchema('LabelPoint', function() {
      return localizer.getText('LABEL_POINT_OPTIONS');
      })

createConditionalFieldContainerSchema
-------------------------------------------------------------

Create a conditional label and a input box of fields which allows to add/remove or drag/drop a field into. |br|

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **predicateFn**
        - A predicate to determine whether render the container or not. It receives report part detail object as a parameter.
      * - **containerKey**
        - The key of the container
      * - **label**
        - The label text value or a function return a text
      * - **dataKey**
        - Data key to access container information of report part content's property
      * - **height**
        - Pixel height of container. Leave it null or undefined to use default height
      * - **maximumField**
        - Maximum number of fields in the container. Leave it null or undefined to unlimit the number of fields
      * - **isHorizontal**
        - Whether horizontal alignment between label and input box or not |br|
          (It is optional with the default value is false)

**Sample**

   Create an example container with dataKey is exampleContainer, having default height and 1 field maximum

   .. code-block:: javascript

      createConditionalContainerSchema(
         function(reportPartDetail) {
            return true;
         },
         'exampleContainer',
         function() {
            return localizer.getText('ExampleContainer');
         },
         'exampleContainer',
         null,
         1,
         true
      );

setReportPartConfiguration
----------------------------------------------

Set configuration of a report part type.  It is typically using for customizing the existing report part type (i.e. Chart, Gauge or Map). Instead of setting a new configuration, it recommends getting the current configuration via :doc: `getReportPartConfiguration`, change appropreate property, then set it back using this function. By changing this configuration, it would impact to all report part styles of the particular report part type. For example, adding a new field container schema to the Chart configuration will result the new field container appears in all chart type configuration designer.|br|

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **reportPartType**
        - Report part type
      * - **configuration**
        - A report part type configuration object with the following properties:

            *  **configuration.visualEngine** |br|
               The name of default visualization engine. It will be used as default visualization engine if the report part style configuration doesn't specify explicitly
            *  **configuration.optionsBuilder** |br|
               The options builder class or constructor function to build visualization options
            *  **configuration.model** |br|
               The report part content model class or constructor function. This class/constructor is used to construct ReportPartContent object
            *  **configuration.fieldContainerSchema** |br|
               An array of field container schema
            *  **configuration.propertyWidgets** |br|
               An array of custom React components to create property editor.It would be useful in case of using a custom React component directly in the propertySchema property, instead of using registerPropertyEditor to register a custom property editor by type.
            *  **configuration.propertySchema** |br|
               The object contains defined schema of property editor of report part in designer
            *  **configuration.propertyMappingProps** |br|
               The function to create the mapping properties object
            *  **configuration.propertyMappingSource** |br|
               The function to create the mapping source object
            *  **configuration.propertyValueChange** |br|
               The function to create value change handler
            *  **configuration.optionsMapping** |br|
               Mapping to visualization options. This settings is optional as you can write code in options builder to populate visualization object

**Sample**

   .. code-block:: javascript

      setReportPartConfiguration(REPORT_PART_TYPES.Chart, {
      visualEngine: 'Highchart',
      // The builder class to build chart visualization options
      optionsBuilder: CustomHighchartOptionBuilder,
      // Report part content model class
      model: CustomReportPartChartContent,
      // Default field container schema
      fieldContainerSchema: null,
      // Array of custom React component to create property editor.
      // It would be useful in case of using a custom React component directly in the propertySchema property, instead of
      // using registerPropertyEditor to register a custom property editor by type.
      propertyWidgets: [],
      // The object contains defined schema of property editor of report part in designer
      propertySchema: {
         schemaKey: 'Example',
         groups: {
            example_group_name: {
            title: 'Example Group',
            fields: {
               example_field_name: {
                  factory: createDropDownSchema,
                  title: 'Title of example_field_name',
                  value: '<any property name or getter function of propertyMappingProps, propertyMappingSource object>',
                  props: {
                  defaultValue: 'value1',
                  options: ['value1', 'value2']
                  }
               }
            }
            }
         }
      },
      // The function to create the mapping properties
      propertyMappingProps: function(reportPartDetails, fieldStore) {
         return {
            otherProperty: 'Value1'
         };
      },
      // The function to create the mapping source
      propertyMappingSource: function(reportPartDetails, fieldStore) {
         return {
            example_field_name: 'Value1'
         };
      },
      // The function to create an value changed handler
      propertyValueChange: function(reportPartDetails, fieldStore) {
         return function(schemaData, changedKey, changedKeyPath, changedValue, changedOthersInfo, derivedChange) {
            // It must return a Promise with chartProperties object.
            return Promise.resolve({ needToUpdate: false, chartProperties: reportPartProperties });
         };
      },
      // Mapping to visualization options.
      // This settings is optional as you can write code in options builder to populate visualization object
      optionsMapping: null
      });

getReportPartConfiguration
----------------------------------------------

Get configuration of a report part type.|br|

.. versionadded:: 2.11.0

**Parameters**

   *   **reportPartType**: Report part type

**Sample**

   Gets the report part configuration object of Chart

   .. code-block:: javascript

      getReportPartConfiguration(REPORT_PART_TYPES.Chart);

   Returns [Object][14]

extendReportPartStyleConfiguration
------------------------------------------

Extends report part with a new style configuration. |br|

.. versionadded:: 2.11.0

**Parameters**

   .. list-table::
      :widths: 20 80

      * - **reportPartType**
        - Report part type
      * - **reportPartStyle**
        - The new report part style
      * - **baseStyle**
        - A chart type that new chart derives on
      * - **configuration**
        - The new chart type configuration with the following properties

            *  **configuration.visualEngine** |br|
               The name of visualization engine.x |br| 
               This settings is optional.The default visualization engine which is defined in report part configuration.
            *  **configuration.visualType** |br|
               Visual type to identify which visualization type to be rendered. For example, it would be "type" property of Highchart options.
            *  **configuration.visualLabel** |br|
               The label text of this report part style showing in the chart type dropdown of report designer.
            *  **configuration.optionsBuilder** |br|
               The options builder class or constructor function to build visualization options.
            *  **configuration.fieldContainerSchema** |br|
               An array of field container schema. |br| 
               *This settings is optional.*
            *  **configuration.propertyWidgets** |br|
               An array of custom React components to create property editor. |br|
               It would be useful in case of using a custom React component directly in the propertySchema property, instead of using `registerPropertyEditor(type, factory)`_ to register a custom property editor by type.
            *  **configuration.propertySchema** |br|
               The object contains defined schema of property editor of report part in designer
            *  **configuration.propertyMappingProps** |br|
               The function to create the mapping properties object
            *  **configuration.propertyMappingSource** |br|
               The function to create the mapping source object
            *  **configuration.propertyValueChange** |br|
               The function to create value change handler
            *  **configuration.optionsMapping** |br|
               Mapping to visualization options. |br| 
               This settings is optional.
**Sample**

   Extend Chart with an additional 3D Column chart type

   .. code-block:: javascript

      extendReportPartStyleConfiguration(REPORT_PART_TYPES.Chart, '3DColumn', CHART_STYLES.Column, {
      visualType: 'column',
      visualLabel: '3D Column',
      propertySchema: {
         groups: {
            chart: {
            fields: {
               '3d': {
                  factory: createCheckBoxSchema,
                  title: 'Enable 3D',
                  value: 'getValueByKey',
                  props: {
                  title: 'Enable 3D'
                  }
               }
            }
            }
         }
      },
      propertyValueChange: (reportPartDetails, fieldStore) => (
         chartProperties,
         schemaData,
         changedKey,
         changedKeyPath,
         changedValue,
         changedOthersInfo
      ) => {
         const threeDOptions = schemaData.chart['3d'];
         chartProperties.optionByType['3d'] = threeDOptions ? threeDOptions.value : false;
      },
      optionsBuilder: ThreeDColumnChartOptionsBuilder,
      optionsMapping: {
         optionsByType: {
            '3d': { propKey: 'chart.options3d.enabled', defaultValue: true }
         }
      }
      });

**Tags**

Embed, Embedding, Fully Embeddable. 
