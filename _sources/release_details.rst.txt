.. _Release_Details:

==============
Release Details
==============

.. note::
    - In version v3.0.0 the IAdHocExtension implementation would only be picked up if the assembly name began with Izenda. This was resolved in the v3.1.0 release.
    - In addition, due to changes in our internal reference, please make the following changes to your references/implementation found `here <https://github.com/Izenda7Series/IAdHocExtensionSamples/commit/da47fd3780f3c07e00b0593f0dfbd268f400515a>`_.

v3.1.0 April 9, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
 
-  MongoDB Available as a Reporting Datasource
    - We've introduced MongoDB as a new datasource for reporting. This means that you are able to select Mongo from the Data Server Type dropdown when adding a new connection string. 
    - We support Mongo v2.6 or greater in this release. 

-  Key Joins Support Multiple Values
    - When creating key joins in the Data Sources page of the report designer, previously you were limited to only a singular value. This meant that for every unique value you wanted to join against, you would have to create an additional key join. Now you can hit enter once you've chosen or entered your value, and then continue to add them for the = and <> operators. 
   
-  Pie Charts Support Drilldown Aactions on the 'Other's slice
    - While designing a Pie Chart, you normally have the ability to set a value for 'Bottom X% Grouped to Other'. When enabled, a slice on your pie chart will be labeled 'Others' and it is the combined value of items that fall within your setting. Previously, if a drill down was set up on your chart, you could not see any underlying data for that slice. Now, if drilldowns are set for your pie chart, you will see a pop-up when clicking on the Others slice. This will let you choose any value within the Others slice to drill down on so you can see the lower level of data for that particular value.  
    
-  New Datetime Picker
    - Our goal for the immediate future was to help modernize and streamline our filer interactions. In order to do this, we needed to switch out our underlying library for DateTime interaction and replace it. Now that we've done this, the calendar picker for all DateTime values thorughout the application will change accordingly. Please note that while this change is in place now, some optimizations for filter space and presentation for these will be released in v3.2.0 now that the underlying libraries are in place. 

-  Update Results Button Relocated
    - To help streamline filter and report interactions, we've relocated the Update Results button to be within the filter contianer. This way, as your users are setting their filter values, the ability to immediate update the report to reflect that new data is located in the same vicinity so their attention stays with their workflow. 

-  Filter Panel - Space Consolidation
    - As a step towards responsive filter design, we've begun to consolidate the use of space within the filter panel. We've zbbreviated 'Show Filters Under Report Description' to save space and added a tooltip. Additionally we've changed the 'Add Filter' button to a '+' icon to make room for the Update Results button. 

-  Close Button in Viewer Methods
    - Previously, when use either the renderReportViewerPage or renderDashboardViewerPage endpoint, the 'Close' buton will still be present. When selected, it would bring the user back to the report or dashboard list. In order to respect the workflow of those pages, the Close button will not be rendered when using either of those rener methods. 

-  Bottom Row of Dashboard Tiles is Situationally Removed 
    - When a user would view a dashboard, there would always be a row of empty tiles at the bottom, where a report designer could add new content. Now, if a user is unable to edit a dashboard and is viewing one, that bottom row of empty cells we be gone to improve dashboard quality. 

-  Additional IntegrationStyle Flags for our Front-end Integration APIs
    - We've added some additional integrationStyle flages to the renderReportViewerPage and renderDashboardViewerPage to give users more control over what is disaplayed. 
    - For renderReportViewerPage, the two additional variables are hideReportName and hidePreviewRecords. When set to false these will hide the name of the report and the preview records dropdown respectively. 
    - For renderDashboardViewerPage, the additional variable is hideDashboardName. When set to false the name of the dashboard and the global checkbox will not be displayed. 

-  New Dashboard Tile Header Permission
    - For end users who are only viewing the report, the dropdown header on dashboard tiles may not be necessary. Because of this, we've introduce a new permission, 'Display tile header in uneditable dashboard' in the role permissions setup. If this permission is not enabled, then when a user opens a dashboard that they cannot edit, the blue tile headers will not display. This mirrors the behavior seen in the report viewer and simplifies a user's interaction with dashboards.     
