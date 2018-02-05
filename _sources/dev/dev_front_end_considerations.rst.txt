====================================================
Front End Rendering Considerations
====================================================

There are no errors in the API Logs or console but the component doesn't render
--------------------------------------------------------------------------------------

When an Izenda components is rendered, it will scale to fit its container's size. The following CSS class definition will scale an HTML element to the size of the window.
.. code-block:: css
   .container {
      width: 100%;
      height: 100vh;
      min-height: 100vh;
      }
      
            
The "Visual" Tab of Forms Editor in the Report and the "Text" Tile Editor in Dashboards Don't Render
----------------------------------------------------------------------------------------------------------

The plugin used for Forms and Dashboard Text Tiles utilizes the "RootPath" value defined in your Configuration JSON declared when the Izenda config function is called (e.g. *"RootPath": "/Scripts/izenda"* ). For more information about Izenda's config function, please refer to our list of `Front-end Integration APIs <https://www.izenda.com/docs/dev/api_frontend_integration.html#config-configjson>`_

* If you have deployed your front end application into a virtual directory, ensure that your virtual directory name is included in the root path name (e.g. If you have deployed your application to "FE", your Root Path value would be "/FE/Scripts/izenda")

* Ensure that the izenda_vendors.js file exists within your solution
