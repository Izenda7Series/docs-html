.. _Release_Details:

==============
Release Details
==============

v3.4.0 August 16, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
- Machine Learning Infrastructure Addition
    - The Prediction, Classification, and Forecasting model infrastructures are included. 
- System Cache Beta Implementation
    - A detailed description of caching setup and configuration can be found on our :ref:`Caching_Overview` page.
    - The system cache is enabled by default.
    - There is no ability to disable the system cache with this release. 
- Drilldown Grids can be Exported at the Current Expansion Level
    - When using drilldown grids, you will receive a new pop-up when choosing to export your report if you have modified the grid. 
    - This pop-up will let you designate if we're exporting all records in your drilldown grid, or the records as you've configured them (expanded vs collapsed)
    - Users will be able to leverage this functionality to create more fidelity between drilldown grids in the platform and in their exports.
- Join Logic can be Toggled Between Behavior before 2.18.1 and after 2.18.1
    - Defect 22764 was resolved in v2.18.1 of Izenda which required adjustments to our query engine. 
    - Reports that leverage order-specific join structures or LEFT/RIGHT joins may have seen their data change.
    - To toggle this you will need to edit a value in the web.config (.NET) or appsettings.json (.NET Core)
        - This is the following value: <add key="izendaJoinStructure" value="true" />
        - This is a boolean value, which should be set to true/false and is true by default. 
        - To leverage the older join logic you should set this value to false.
    - Note that this is an APPLICATION-WIDE setting, meaning that it is not configured per-tenant. 

DEFECTS
^^^^^
- For Defect 22502, there is an additional behavior where conditional formatting isn't applied when Custom Formats and Repeaters are in use (Defect 24687)
- For Defect 23976, there is an additional behavior where no alert is provided when a user naviagtes to the Report Viewer from the Report Designer after editing the report if they have not saved. 

v3.3.1 July 23, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^

- InTimePeriod filters reflect more accurate timezones
    - When opened in the application, these filters will be offset by a user's Data Offset value instead of using the API server's UTC time.
    - When sending an embedded or attached report, senders will be able to leverage the Time Zone setting for the schedule/subscription for InTimePeriod filters. 

- Multiple Selection filters now support delimited lists.
    - You can provide Comma and New Line delimited lists as valid inputs
    - Select 'None' in the delimiter selection dialogue if you want to leverage historical behavior.

- Izenda can load on pages with pre-existing Highcarts references. 
    - Izenda will make a backup of the customer Highcharts reference, reset the Highcharts global variable, and then load our resources. 
    - After Izenda's Highchart resources are loaded, we will restore the customer resources.  

v3.3.0 July 15, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::
	- The System Cache portion of this behavior will be released in a future version of Izenda.

The **System Configuration > Cache** page allows an administrator to manage users.

FEATURES
^^^^^^^^^

- Data Caching Beta is now Implemented
    - A detailed description of caching setup and configuration can be found on our :ref:`Caching_Overview` page.
    - We will be adding system-level caching (roles, validation, etc.) in a later release. 
    - No caching will be enabled by default, so you must set this up via the configuration page in the application.

v3.2.0 June 4, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^

- Report Headers Scale to Reduce Whitespace
    - Any unused rows in the report header will be removed, decreasing the overall whitespace seen in the report viewer and exports. 
    - Adding new objects into the report header will allow you to add new rows of content, up to the original height, if required. 
- New Filter Properties Interactions
    - The Filter Properties Panel now resides within a pop-up dialogue. 
    - Clicking on a filter object will open a pop-up that lets you select the operator and the value(s).
    - Right-clicking on a filter object and selecting 'Edit', or clicking on the gear icon will open the Filter Properties pop-up that used to be among the right-hand panels. 
- New Filter Interactions
    - The 'Between' operators are reworked to consume less space.
    - The 'Between Date' operator is more streamlined and will allow both dates to be selected from a singular dialogue.
- GetAccessToken is expanded for Grid and Form Exports
    - For integrated scenarios, grid and form exports will now set the user context in the same manner as chart exports, allowing for the same approach to security and token management.
- Subreports Allow Users to Pass Field Values into Input Parameters of a Report 
    - When setting up field mappings for subreports, you can now pass field values into the input parameters of stored procedures. 

v3.1.1 May 16, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. warning::
    - (5/16) If you are using the ADOJobStore, you will need to explicity state if you are using binary or json serialization.  
    - (5/16) For an existing ADOJobStore setup please use the binary serializer type, but please note that this is not supported when targeting .NET Core.
    - (5/16) For new configurations and .NET Core instances, the serializer type should be set to json. 
    - (5/16) For Quartz, ADO.NET provider names have been simplified and are without version. e.g. SqlServer-20 => SqlServer
    - (5/16) For these Quartz migration changes please see their migration guide `here <https://www.quartz-scheduler.net/documentation/quartz-3.x/migration-guide.html>`_.


v3.1.0 May 9, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. warning::
    - (5/9) In version v3.0.0 the IAdHocExtension implementation would only be picked up if the assembly name began with Izenda. This was resolved in the v3.1.0 release.
    - (5/9) In addition, due to changes in our internal reference, please make the following changes to your references/implementation found `here <https://github.com/Izenda7Series/IAdHocExtensionSamples/commit/da47fd3780f3c07e00b0593f0dfbd268f400515a>`_.
    - (5/14) A user in a load-balanced environment has reported inconsistencies with scheduling. We are investigating and will provide a fix, if necessary, as soon as possible. 

FEATURES
^^^^^^^^^
 
-  MongoDB Available as a Reporting Datasource
    - We've introduced MongoDB as a new datasource for reporting. This means that you are able to select Mongo from the Data Server Type dropdown when adding a new connection string. 
    - We support Mongo v2.6 or greater in this release. 

-  Key Joins Support Multiple Values
    - When creating key joins in the Data Sources page of the report designer, previously you were limited to only a singular value. This meant that for every unique value you wanted to join against, you would have to create an additional key join. Now you can hit enter once you've chosen or entered your value, and then continue to add them for the = and <> operators. 
   
-  Pie Charts Support Drilldown Actions on the 'Others' slice
    - While designing a Pie Chart, you normally have the ability to set a value for 'Bottom X% Grouped to Other'. When enabled, a slice on your pie chart will be labeled 'Others' and it is the combined value of items that fall within your setting. Previously, if a drill down was set up on your chart, you could not see any underlying data for that slice. Now, if drilldowns are set for your pie chart, you will see a pop-up when clicking on the Others slice. This will let you choose any value within the Others slice to drill down on so you can see the lower level of data for that particular value.  
    
-  New Datetime Picker
    - Our goal for the immediate future was to help modernize and streamline our filter interactions. In order to do this, we needed to switch out our underlying library for DateTime interaction and replace it. Now that we've done this, the calendar picker for all DateTime values throughout the application will change accordingly. Please note that while this change is in place now, some optimizations for filter space and presentation for these will be released in v3.2.0 now that the underlying libraries are in place. 

-  Update Results Button Relocated
    - To help streamline filter and report interactions, we've relocated the Update Results button to be within the filter container. This way, as your users are setting their filter values, the ability to immediate update the report to reflect that new data is located in the same vicinity so their attention stays with their workflow. 

-  Filter Panel - Space Consolidation
    - As a step towards responsive filter design, we've begun to consolidate the use of space within the filter panel. We've abbreviated 'Show Filters Under Report Description' to save space and added a tooltip. Additionally we've changed the 'Add Filter' button to a '+' icon to make room for the Update Results button. 

-  Close Button in Viewer Methods
    - Previously, when use either the renderReportViewerPage or renderDashboardViewerPage endpoint, the 'Close' button will still be present. When selected, it would bring the user back to the report or dashboard list. In order to respect the workflow of those pages, the Close button will not be rendered when using either of those rener methods. 

-  Bottom Row of Dashboard Tiles is Situationally Removed 
    - When a user would view a dashboard, there would always be a row of empty tiles at the bottom, where a report designer could add new content. Now, if a user is unable to edit a dashboard and is viewing one, that bottom row of empty cells we be gone to improve dashboard quality. 

-  Additional IntegrationStyle Flags for our Front-end Integration APIs
    - We've added some additional integrationStyle flages to the renderReportViewerPage and renderDashboardViewerPage to give users more control over what is displayed. 
    - For renderReportViewerPage, the two additional variables are hideReportName and hidePreviewRecords. When set to false these will hide the name of the report and the preview records dropdown respectively. 
    - For renderDashboardViewerPage, the additional variable is hideDashboardName. When set to false the name of the dashboard and the global checkbox will not be displayed. 

-  New Dashboard Tile Header Permission
    - For end users who are only viewing the report, the dropdown header on dashboard tiles may not be necessary. Because of this, we've introduce a new permission, 'Display tile header in uneditable dashboard' in the role permissions setup. If this permission is not enabled, then when a user opens a dashboard that they cannot edit, the blue tile headers will not display. This mirrors the behavior seen in the report viewer and simplifies a user's interaction with dashboards.     
