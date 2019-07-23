
==============
Release Notes
==============

.. note::
	- Weekly Release - Defect Fixes, Patch release x.x.1
	- Monthly Release - Enhancements and Defect Fixes, Minor release x.1.x
	- Major Release - Larger Features, Major release 1.x.x

For more information and details on our releases, please see our :ref:`Release_Details`.

v3.3.1 July 23, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
- InTimePeriod filters reflect more accurate timezones
- Multiple Selection filters now support delimited lists.
- Izenda can load on pages with pre-existing Highcarts references. 

FIXES
^^^^^
- Defect 23242 Preview Dashboard Triggered Query when Required Filters were Set
- Defect 23975 Unhandled Exception in Pivot Grids with Non-sum Aggregations in Rows
- Defect 24077 Report Imports Fail with a Postgres Configuration Database
- Defect 24326 Passing Multiple Date Filter Values to renderDashboardViewerPage caused Front-end Error with Date Pickers
- Defect 23842 General Info Values Failed to Populate for Logo Images
- Defect 24427 System Job Implementation Polled System Inefficiently

v3.3.0 July 15, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
- Data Caching Beta is now Implemented
    - Caching can be leveraged through a Disk Cache or a Memory Cache.
    - Data for Reports and Dashboards will be cached after the initial load.
    - A new UI button, 'Refresh' will be present which will allow users to update the cache.
    - 'Update Results' has been renamed 'Apply Filters' and will always prioritize pulling from the cached data.  
- Sorting can now be changed on fields with subtotals. 

FIXES
^^^^^
- Defect 17160 System/Tenant Dropdown on Mobile Resolutions Isn't Responsive
- Defect 19005 Export and print actions do not work on mobile devices
- Defect 19040 Dashboard Background Color Picker Is Cut Off in a Portrait Layout on Mobile Devices
- Defect 20253 Mobile Dashboard Map Point Options Selector Not Scaling
- Defect 20254 Mobile Dashboard Map Navigation for Drilldowns Covered
- Defect 21139 Integration and external endpoint for save/update user does not change Active property
- Defect 22368 Non-visible fields are being displayed in exports.
- Defect 22683 Days Old function in chart values
- Defect 22811 Filter error when using tinyint(1) data type with mysql database
- Defect 22866 Scatter chart Y-axis labels overlapping on small chart sizes
- Defect 22916 Word Wrap Not Being Carried Over to Excel Export
- Defect 23124 Join relationship using aliased join gets reordered when not listed at the bottom
- Defect 23241 When a user creates a Chart type report using Range only Option from Report Part properties Error is displayed
- Defect 23272 Issue Rendering Embedded Report Part when trying to drill-down into a report
- Defect 23315 Add field button doesn't respond
- Defect 23398 Alternative Text Value Displays as Blank When Using Separators
- Defect 23513 Responsiveness with dashboard and report tiles in mobile design
- Defect 23546 Whitelisted functions not recognized in calculated field IF or CASE statements
- Defect 23552 Quality Issue for Exporting Chart/Gauge/Map using Syncfusion on .NET Core
- Defect 23556 Tenant User with Full Report and Dashboard Access gets logged out when saving a dashboard
- Defect 23717 When moving an existing report to a new category, the category is put under Available Categories
- Defect 23730 Value displayed incorrectly for forms in Microsoft Edge and Internet Explorer
- Defect 23731 Access rights drop-down does not populate and locks the report designer
- Defect 23739 Wrong colors in maps when using dynamic High and Low values
- Defect 23777 Incorrect tooltip is displayed when using pivots and Custom URL
- Defect 23801 Unexpected behaviors when using the OnPreLoadFilterDataTree IAdHocExtension method
- Defect 23833 Cannot view a Gauge report in Dashboard on Mobile
- Defect 23924 Fields with null values in forms displays incorrectly
- Defect 24076 Scheduling limit not being set by default
- Defect 24251 Map background is cut off in report designer
- Defect 24298 Can not navigate to report when setup Email link in Dashboard/Report

v3.2.1 June 21, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
- Defect 21677 Subtotals resulting in 0 were displayed as null in Horizontal Grids.
- Defect 23691 Values on Map Legends would not Display.

v3.2.0 June 4, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
- Report Headers Scale to Reduce Whitespace
- New Filter Interactions
    - Filters properties are now managed through a pop-up
    - 'Between' filter operators have a new interface
- GetAccessToken is expanded for Grid and Form Exports
- Subreports Allow Users to Pass Field Values into Input Parameters of a Report 

FIXES
^^^^^
- Defect 22976 The 'To' value of a Between Date operator is not committed when saving a dashboard.
- Defect 23239 OnPostLoadFilterData is no longer called for stored procedure parameters.
- Defect 23578 API-STRONGNAME resources were not available for v3.0.0
- Defect 23637 Connecting to an existing Postgres configuration database through the Standalone UI throws a duplicate key error.
- Defect 23685 Filters would fail to load their values after saving a report. 
- Defect 23689 Report visibility is cached when creating a report within a new category.
- Defect 23701 Visible data sources are moved back to available after updating the data model tab. 
- Defect 23713 The same aggregate field in a separate report part would not be displayed within the 'Add new filter' popup. 
- Defect 23735 RenderReportViewerPage function with AngularJS 1.x front-end causes infinite URL reloading.
- Defect 23847 Report body grid lines would not display after adding a new report part.  


v3.1.1 May 16, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~


FIXES
^^^^^
- Defect 23378 Right clicking on report sends user to incorrect route in integrated applications.
- Defect 23654 Quartz ADOJobStore required additional configuration for schedules to run.
- Defect 23680 Unable to export forms to Excel in 3.1.0.

v3.1.0 May 9, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
 
FEATURES
^^^^^^^^^

-  MongoDB Available as a Reporting Datasource
-  Key Joins Support Multiple Values
    -  = and <> operators now support multiple input values
-  Pie Charts Support Drilldown Actions on the 'Others' slice
    - If you are using the 'Bottom X%' function on pie charts, you can drill down on the 'Others' slice.
    - When drilling down, a pop-up will let you select which underlying value you wish to drill down to.
-  New DateTime Picker
    - Implemented Blueprint.js to leverage a new DateTime picker for filters
    - Further enhancements for this will be released alongside v3.2.0
-  Update Results Button Relocated
    - The Update Results button is now located alongside the filter panel
-  Filter Panel - Space Consolidation
    - To prepare for further updates in v3.2.0, the filter box has been adjusted to save space in the report designer. 
-  Close Button in Viewer Methods is Removed
-  Bottom Row of Dashboard Tiles is Situationally Removed 
    - When viewing a dashboard that a user cannot edit, the bottom row of empty dashboard tiles will be removed. 
-  Additional IntegrationStyle Flags for Front-End Render Functions
    - renderReportViewerPage allows you to hide the report name and the preview records dropdown.
    - renderDashboardViewerPage allows you to hide the dashboard name and global dashboard checkbox.
-  New Dashboard Tile Header Permission
    - Added a new dashboard permission titled 'Display tile header in uneditable dashboard'
    - When unselected, the blue dropdown tile header will not be presented in dashboards. Please note this is intended for roles that only view, and not design, dashboard. 

FIXES
^^^^^
- Defect 22210 Cannot use Equals-No Auto Complete on Stored Procedures if the lookup field's data type is different than the parameter.
- Defect 22211 Invalid datatype fields should not be shown in the dropdown lists for setting lookups.
- Defect 22285 System displays an error message when a user uses the "Between Date & Time" filter on Oracle datasources.
- Defect 22488 QuerySourceId payload is missing when the field is added to report for the first time after the designer page loads.
- Defect 22543 Link Location Being Adjusted Upon Altering Form Contents.
- Defect 22650 Tenant Users are unable to view Global Gauge Reports when there is a Dynamic Threshold.
- Defect 22732 Potential erroneous hashing increases chance of collision.
- Defect 22767 User-defined aggregate functions could not be grouped at the field level.
- Defect 22835 Number of Records does not work for charts and gauges when exporting from dashboards.
- Defect 22838 Username field in header is inconsistent between report viewer and exports.
- Defect 22841 Category values are not filled automatically when trying to use Save As.
- Defect 22843 Focus on Report Name when saving a report.
- Defect 22844 Focus on Report Name input in Subreport Settings when selecting reports.
- Defect 22850 Filter values were re-requested each time the dropdown was expanded.
- Defect 22937 Executing SPs in the Data Model resets field properties.
- Defect 22947 Using [BLANK] for stored procedure parameter value passes NULL instead of empty string.
- Defect 22962 Gauge Metrics could not be deleted in IE.
- Defect 22969 'No. of Columns Per Exported Page' setting is not impacting Excel exports. 
- Defect 22979 Report Part Name could not be easily set when using IE.
- Defect 23094 Column widths would reset in the Data Model after making changes. 
- Defect 23188 Gauge previews are not impacted by removing metrics from the gauge. 
- Defect 23205 Dashboards Initially Load a Blank Dashboard with 'Example Dashboard Name'.
- Defect 23248 Pagination of embedded subreports is not scaled properly when extending the Grid's width.
- Defect 23249 Cannot create report from Oracle data sources if a Date field is used as a key join.
- Defect 23281 Failed to load Default landing page in a .Net 4.6.1 site.
- Defect 23283 Quality Issue for Exporting Chart/Gauge/Map using Syncfusion on Framework 4.6.1
- Defect 23301 Timestamp without time zone date/time type in PostgreSQL shows incorrect time with data offset setting
- Defect 23314 Invisible UTF symbols removed from class/variable names. 
- Defect 23443 Updated unit tests for current dev branch.
- Defect 23476 Unable to Provision Map Data on 3.0.0.
- Defect 23477 User API duplicates database call to get the user's roles.
- Defect 23478 Tenant users cannot export dashboard tiles made from grids/forms.
- Defect 23516 IAdHocExtension Methods Not Hit in 3.0.0.

v3.0.0 April 2, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  UI Re-skin 
    -  The v3.0.0 release features a new themed application that is easier to whitelabel.
-  .NET Core Compliance
    -  Our libraries have been updated to support .NET Core
    -  Izenda can now be deployed in Linux environments
-  Export Provider Change
    -  We have changed our export provider from EvoPDF to Syncfusion
-  Default API Route
    -  Navigating to http://[YourIP]/api/ will now provide a default Izenda landing page. 
    -  If you make an application/json request to this endpoint it will return 'The system is online' upon a successful response. 
-  Improved Import/Export Error Messaging
    -  While importing report/dashboard definitions, the pop-up will now contain file names, field names, and data types of all conflicting objects.
    -  The content of this pop-up is now copyable so it can be viewed outside of the application.
-  Improved Export Error Messaging
    -  Log messages will show if the system ran out of memory while exports, or if a navigation timeout occurred. 
    -  If a navigation timeout caused the export to fail, it will mention the values for export configuration currently set in the IzendaSystemSetting table.
-  Improved Emailed Report URLs
    -  When emailing the report URL, the filter values are now included so the opened report is filtered appropriately.
-  Improved Install Error Messages
    -  An error message is thrown during installation if the IIS users don't have sufficient permissions to the application files. 

.. warning::

   If you currently have additional Azure resources configured for an EvoPDF exporting provider, this is no longer necessary. Syncfusion works in Azure environments without the need of a specific service. You will need to adjust your exporting configurations accordingly.

FIXES
^^^^^
-  Defect  21853  Month In Time Period filters do not return the expected results using Oracle reporting database.   
-  Defect  21862  Sorting the x-axis did not work when a separator was in use. 
-  Defect  22258  Map drilldowns would break when using the % of Group format.  
-  Defect  22284  Using lookups with special characters would return all data.
-  Defect  22339  Labels on a static threshold would not display.
-  Defect  22687  Using AngularJS front end causes infinite URL redirecting.
-  Defect  22816  Unable to edit Report Name on Report Viewer in Multi-Tenant mode.
-  Defect  22821  Embedded subreports would not show data when field mappings were used.
-  Defect  22832  Top y-axis label on Heat Maps would be null without enough height.
-  Defect  22851  Some dropdowns did not have triange animation.
-  Defect  22859  Maps would not render when using the City field.
-  Defect  22918  Filter values would not updated when scheduling a Dashboard.
-  Defect  22919  Filter values would not update when scheduling a chart, gauge, or map.
-  Defect  22920  Filter values in report schedules would not display properly if one or more filters were not marked as visible.


v2.18.1 March 19, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Right-click Menu Options
    - Users can now right click on the following elements to open in a new tab or window: Reports/Report Menu, Report Categories, Dashboards/Dashboard Menu, Settings 

FIXES
^^^^^
-  Defect  22645  Calculated Fields were not properly sorted if other fields had sorting applied.   
-  Defect  22764  Query Generation would not accurately support LEFT/RIGHT joins in Star Schemas.   
-  Defect  22777  Users would receive a connection error when connecting to an Oracle configuration database.   
-  Defect  23012  Oracle migration scripts would not properly execute.   

.. warning::

   If you are currently leveraging LEFT or RIGHT joins in your reports, you should ensure that the changes in IZ-22764 have not impacted your reporting data. 




v2.18.0 March 6, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Elasticsearch Driver
    - Elasticsearch can now be used as a reporting database 
    - This driver is built to support Elasticsearch v2.2+

- Updated 3rd Party Libraries
    - Upgraded Jquery to v3.3.1
    - Upgraded Lodash to v4.17.5
    - Upgraded Moment to v2.19.3
    - Upgraded Quartz to v2.6.2

.. warning::

   If you are leveraging the Quartz ADOJobStore database you will need to run an upgrade script on your Quartz database that can be found `here <https://github.com/quartznet/quartznet/blob/2.x/database/schema_25_to_26_upgrade.sql>`_.


FIXES
^^^^^
-  Defect  18966  Relationships Grid should expand to take up entire panel in Settings> Data Setup> Data Model > Relationship.   
-  Defect  19196  CASE statement help text had incorrect text in the Expression Builder.   
-  Defect  21456  The "All changes will be lost" prompt doesn't show when creating new report and navigating away.
-  Defect  21458  Updating the PageSetting  value in the IzendaSystemSetting table (for formats like A4, A3, etc.) would not update the system to export in the newly selected format.   
-  Defect  21639  Map Color Value Range would not sorting in the chart legend.   
-  Defect  22204  Alternative Text values would incorrectly apply conditional formatting.   
-  Defect  22218  Dashboard filterse would display incorrectly if a self-join was used for an underlying report.   
-  Defect  22276  Stacked Percentage features on charts were not updating properly to the percentage format.   
-  Defect  22289  Embedded subreports in forms are not rendered during secondary load if a field mapping is not present.   
-  Defect  22292  No alert is thrown when trying to save a data model with duplicate column aliases.   
-  Defect  22549  The 3D Column Chart visualization would not draw a chart preview.   
-  Defect  22648  Database selection dropdowns would load indefinitely and inconsistently.   
-  Defect  22652  Scheduled/Subscribed reports that used a different timezone than the API server would send incorrectly when using the Quartz Scheduler.   
-  Defect  22666  Cache was not consistently cleared during the CopyManagement process.   
-  Defect  22667  Splines were not being applied to area charts.   
-  Defect  22709  Global reports do not show in tenant if reports listed before fail database mapping validation.   
-  Defect  22715  Formatting changes were not applied to the subtotal label.   
-  Defect  22729  End users could adjust their own UserID in their profile page.        
-  Defect  22755  Chart drilldowns were not working in Internet Explorer.   
-  Defect  22776  Subreports were not accurately filtered by field mappings.   
-  Defect  22809  Alternative text did not handle null values.        
-  Defect  22828  Top-left tile of the dashboard body could not be selected.   
-  Defect  22829  Report parts could not be removed once added to a report's Cross Filtering setup.   
-  Defect  22831  Axis labels would not match actual chart values.   
-  Defect  22842  Heatmap default colors would not be applied correctly.        



v2.17.1 February 19, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  21997  Mulit-level drilldowns with hidden fields breaks beyond two levels of depth.   
-  Defect  22194  Unable to Save Fields with Altered Capitalization in the Data Model.
-  Defect  22205  [Chart - Waterfall] The format for Threshold on Y-Axis is not applied as defined.
-  Defect  22334  Date field being used as a Comparison Filter provides text box instead of date picker.
-  Defect  22523  Simple Gauges would not render in the report designer.
-  Defect  22634  Subreports set on Map report parts will drilldown instead of opening the new report.
-  Defect  22739  Editing reports using IE and Edge caused a slowdown in performance on Form report parts.


v2.17.0 February 4, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Improved Error Messaging
    - Dashboard tiles will show error messages from their underlying reports.
    - System logs will provide more information on failed login attempts.
    - The report viewer will list any data sources and fields that are causing an error.
    - Email actions will throw more descriptive errors if an email server is not set up at the system level or for a tenant.
    - Errors on the data sources page of the report designer are reworked for more clarity. 

FIXES
^^^^^
-  Defect  16040  The message displays "The template....." Instead of "The report...." When a user Copies/Moves a report.   
-  Defect  17029  In Settings, Schedule, Created By should be <First Name> <Last Name> instead of userId.   
-  Defect  18351  When creating a role, the Permissions page shows 'Configure Password Options' under the User Setup > Actions area. In the Permission Summary page it shows that same area as 'Configure Security Options'.   
-  Defect  20351  In Time Period Fiscal Year filter operator includes both edge-case dates.   
-  Defect  20621  Resolved subscription-based security issue on API.   
-  Defect  21762  Report Category and Name change are not reflected in the dashboard report part link.   
-  Defect  21916  Alternative Text Not Applying to Subtotal NULL Value in Drill Down Grid.   
-  Defect  21917  Alternative Text Not Updating Chart Drill Down Labels for NULL Values.   
-  Defect  21995  Subtotal Creates Additional Border Cell in Pivot Grids.   
-  Defect  22167  Boolean Filter pValue Not Dynamically Updating.   
-  Defect  22209  Global subreports were not correctly filtered by field mappings.   
-  Defect  22277  Simple Gauge with Separator Not Exporting Values.   
-  Defect  22395  Side Totals were displayed if the % of Side Total function was used without enabling side totals.   
-  Defect  22522  Update Results button would be overlapped and unavailable in smaller resolutions.   
-  Defect  22541  Bar Chart axis were inverted.   
-  Defect  22591  Fields with a dot in the name could not be used in custom views.   
-  Defect  22592  Field dropdown in the Relationships page of the data model does not display non-visible fields.   
-  Defect  22649  Fixed JavaScript issues revealed in Karma testing.        



v2.16.0 January 7, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  "PositionID" is added to the Relationships page of the Data Model.
    - This is an additional column that accepts numerical values to represent the priority of each join when being loaded into a report.
    - When these relationships are loaded into a report, they are from top to bottom from the lowest number to highest.
    - If any data sources have multiple relationships that must be loaded, the relationship with the earliest position is loaded first and all other relationships become subkey joins.     
    - The settings of PositionID can be copied out using Copy Management to allow all tenants to leverage the same join priorities. 

-  Multi-Level Functionality for Tree Maps
    - Tree Maps now have a new Report Part Property 'Multi-Level'
    - If checked, drilldowns will be disabled and all x-axis groups are displayed on the same level.
     
FIXES
^^^^^
	
-  Defect  19640  Dashboard save dialog displaying Local Categories with Global Categories box checked.   
-  Defect  21419  Regression lines were not displayed on charts when the Multi-Color was enabled.
-  Defect  21455  Exporting report from report list with empty filter values results in incorrectly filtered export.
-  Defect  22332  Color and Alternative Text are not properly applied when using custom data formats.
-  Defect  22333  Tenant Field plus Filter Lookup causes report to not filter correctly.
-  Defect  22346  The Chart can't draw when apply Custom Format function for the Thresholds.
-  Defect  22359  [Chart/Gauge] The Color setting for Separators works incorrectly when having 0 or false value.
-  Defect  22370  Tenant Field setting does not work at the system level.
-  Defect  22397  Changing grid pagination after drilldowns would result in 'No record found'.


v2.15.1 December 17, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  16597  In Quick Edit mode filters Inherited from a Parent Report to a Sub Report are not retained after pressing "Update Result".   
-  Defect  17609  Security questions are enabled when not selected when you create or reset your password with username which has Backslash.
-  Defect  17615  When using a Bit data type as separator on chart legend shows series 1 not false.
-  Defect  18142  Dashboard tiles do not properly resize when user resizes browser to responsive mode in screen.
-  Defect  18534  Grid Type Report Part always display top 10 records when rendering it by integration API, it is not respecting the saved records per page limit in the report part.
-  Defect  18995  When a report that is used in a dashboard becomes incomplete, the URL to the report is not shown in the dashboard tile for ease of finding the report.
-  Defect  20916  Subtotal and Grandtotal not equal in drilldown grid when All is collapsed.
-  Defect  21181  Exporting a form to Word/PDF with a field returning no records exports the field alias name.
-  Defect  22039  Required Report Filter Behavior Not Translating to Dashboard Common Filter Behavior.
-  Defect  22340  Pivot grid side total shows incorrectly when a Row field has a null value.
-  Defect  22350  Improvements to Dashboard Performance.


v2.15.0 December 3, 2018
~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  "Use Lookup" Checkbox Added for Filters
    - If you have lookups set on a field (utilizing the v2.14 lookup functionality) there will be a "Use Lookup" option on those filter fields.
    - This option is a checkbox that determines if you want to leverage the lookup for the filter dropdown or have filter use the historic functionality.
    - This option will be visible in the Filter Properties Panel only if a lookup is set on that particular field in the data model.

FIXES
^^^^^

-  Defect  21200  Pivot grid side total shows incorrectly when a Row field has a null value.


v2.14.3 November 26, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  18246  When creating new calculated field in data model and adding alias prior to saving the calculated field is missing. User must save the calculated field prior to adding the alias.   
-  Defect  20173  Clickable labels are lost on Pie Charts when changing the Pie Chart type.
-  Defect  21232  PDF exports would shrink report content when compared to the size of the report content when printing.
-  Defect  21502  Subreports display Today's date in "Between Date" filters when set to inherit filters from main report.
-  Defect  21563  Conditional formatting would fail if a custom data format was in use.
-  Defect  21609  Some users may experience browser console errors when clicking the 'Cancel' button under 'My Profile'.
-  Defect  22195  Charts intermittently failed to export in standalone.
-  Defect  22198  Using the browser's back button would not load the last page in Izenda.
-  Defect  22217  Subreport only available when first filter value is present in separator.
-  Defect  22260  Report List would load when no initial License Key was set.
-  Defect  22278  Embedded chart reloads in form report part when scrolling.


v2.14.2 November 12, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  17829  Print always wait for 60 seconds timeout to open Printing dialogue after page rendered. 
-  Defect  20159  Columns do not sort when choosing recipient from list for emailing.
-  Defect  21898  ReportFilterField.SourceFieldName returns field alias.



v2.14.1 November 5, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  18990  Copyright was not updating automatically. 
-  Defect  21773  Report parts in print and exports overlap in some cases.
-  Defect  21899  Image data type fields that contain null fail when exporting to Excel or Word.
-  Defect  22098  Heat Map Hover Label Displaying NULL instead of x-axis value.


v2.14.0 November 1, 2018
~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Lookups for Fields in Tables and Views
	- You can now set lookups against any field in your tables and views similar to stored procedure input parameters.
	- You can define a lookup to pull values from any other table, or create a user defined list of values to leverage.

FIXES
^^^^^

-  Defect  22026  Stored Procedures return no records when using aggregated filters when lookup key is not equal to display value.
-  Defect  22028  Opening a subreport shows display values instead of lookup keys.
-  Defect  22092  Incorrect display values are shown for aggregated fields with a lookup setting.


v2.13.4 October 29, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  17942  Unnecessary spacing for subreports in Forms that don't return data.
-  Defect  21488  Forms were not consistently loading subreport contennt when updating filter values.
-  Defect  21939  Forms with embedded subreports would export slowly and with a blank visualization.
-  Defect  21940  Drilldown performance was slow accross chart types.
-  Defect  22029  Improved reliability in exports.


v2.13.3 October 22, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  18944  Users without User Role Association could assign roles to other users via the Role Setup pages.
-  Defect  21772  Reports utilizing Custom Views with calculated fields would break if the database name used in the view changes.

v2.13.2 October 15, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
	
-  Defect  21657  Optimized bubble chart query performance
-  Defect  21764  Cross database relationships were not being copied using copy management.
-  Defect  21851  Query for getting connection details in MySQL took too long to complete.

v2.13.1 October 8, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21649  Scheduled reports would send with inconsistent timing for each delivery.
-  Defect  21656  Sorting numeric fields with subtotals would cause other values to sort incorrectly. 
-  Defect  21760  Custom 3D charts would not print or export consistently. 
-  Defect  21765  Adding filters to a report based on a stored procedure would return no results.
-  Defect  21771  Global reports that leveraged calculated fields would export/print no records at the tenant level in Deployment Mode 1.
-  Defect  21838  The cursor position resets after leaving the Form HTML editor.
-  Defect  21839  Resolved a security issue within the dashboard APIs.
-  Defect  21840  Forms with both a style and table tag would fail to export/print.

v2.13.0 September 28, 2018
~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Highchart Version Update 
	- Upgraded Highcharts from v4.2.7 to v6.1.0
	- Customers leveraging custom charts now have the ability to implement custom charts up through v6.1.0
 	- Please reference https://github.com/Izenda7Series/IzendaCustomVisualizations for documentation on implementation of custom charts	

FIXES
^^^^^

-  Defect  21341  Izenda's UI would error when running inside of a MaterializeCSS application.
-  Defect  21497  Grid preview data would not render values in a 3D Column Chart.
-  Defect  21498  Regression lines would not render on 3D Column Charts.
-  Defect  21616  Scheduled/Subscribed reports would still run after the base report was deleted.
-  Defect  21749  Opening the print dialogue would redirect to an empty page in IE11.
-  Defect  21750  Gauge images would be cut off in the print dialogues.

v2.12.5 September 24, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21720  External Import API does not allow to import dashboard using different schemas from the same connection.
-  Defect  21730  After saving a custom chart, fields in z-axis containers may disappear in some cases.
-  Defect  19236  Search keys and values not respected for the (POST) user/load endpoint.

v2.12.4 September 17, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21259  In some cases, exporting to Excel will cause high memory consumption.
-  Defect  21648  When extending a default Map or Gauge configuration, all Map Type/Gauge Style specific field containers are shown. The default Map/Gauge configuration level should only have Title and Description.

v2.12.3 September 13, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21617  Tenant field is not properly applied to lookup value to select key for stored procedure input parameters.
-  Defect  21612  Some charts may randomly fail to export.
-  Defect  21564  Performance of load report slows when report contains several subreports linked.

v2.12.2 September 10, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21415  Valid calculated fields fail to add to the field list in the report designer.
-  Defect  21489  When exporting charts from the MVC starter kit, the x-axis is cut off.
-  Defect  21611  Removal of a filter in the report designer persists if the report isn't saved but opened in new tab. 
-  Defect  18984  Izenda configuration tables fail to create when using a case sensitive database on MSSQL.
-  Defect  20837  Titles and/or descriptions in text dashboard tiles are being duplicated in exports.

.. note::
	Defect 21489 has been resolved via CSS in the MVC5 Starterkit on our GitHub repository.


v2.12.1 September 5, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21607  Subtotal is not calculated properly for Pivot/Dripdown Grids.
-  Defect  21411  Clicking 'Update Results' in the data sources tab of the designer would remove foreign fields from aliased joins. 
-  Defect  21366  When 'Snap to Grid' is disabled, some reports would be re-positioned when rendering the report. 
-  Defect  21251  Pivot Grid Subreport Not Restricting Row Count Based on Field Mappings.
-  Defect  21223  Altered PDF and Print process to use SVG for chart, gauge, map render to improve quality of image. This process cannot be used for Excel, Word, or HTML Email as these export types cannot accept SVG.


v2.12.0 August 31, 2018
~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	

-  Combination Chart Enhancements  
	- Single Y Axis Option on combination chart property panel allows users to display multiple metrics on a single axis. See documentation on :ref:`Single Y Axis <Report_Designer_Single_Yaxis>`
	- The combination chart now supports the area chart style for metrics. See documentation on :ref:`Combination Chart <NW_Order_Details_Combination_Sales_and_DiscountSales>`

-  Regression Lines for Charts 
	- Regression lines are now available for chart types Line, Column, Bar, Area, Combination, Scatter, and Bubble.
	- The regression types supported are Linear, Polynomial, Logarithmic, or Exponential
	- See documentation on :ref:`Regression Lines <Chart_Regression_Line>`

-  Required Values for Stored Procedures
	- Prior to 2.12.0 values for all stored procedure input parameters were required. With the 2.12.0 release, by default the values will be required with the "Required" flag set in the filter's property panel. If the user deselects the required option, the value is not required and NULL will be passed to the stored procedure. See documentation on :ref:`Required Filters <Report_Designer_Required_Filter>`

-  Form Report Parts Support Subtotal In Repeater
	- Prior to the 2.12.0 release subtotals were only supported outside of repeater structures. Now users can add subtotal tags inside nested repeaters to obtain multiple subtotal levels.
	- Please note subtotals are not supported in parallel repeater structures
	- See documentation on :ref:`Form Subtotal Inside Repeaters <Form_Subtotal_Inside_Repeater>`

-  Upgrade to tinyMCE form builder	
	- Upgraded tinyMCE to v4.5.5
	

FIXES
^^^^^

-  Defect  20969  Tables in form report parts using Microsoft Edge are not functioning correctly  
	
	
v2.11.4 August 27, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21518  Cannot add a field into the field container of new custom chart.
-  Defect  21487  Filters built from calculated fields would not render in the report designer. 
-  Defect  21440  Drilldown grid containing a non-visible field fails to Print or Export.
-  Defect  21401  Applying subtotals to calculated fields would throw an invalid query exception.
-  Defect  21318  Charts using the Linear setting for the XY-Plane would not display properly if the x-axis was built from a time field.
-  Defect  18865  Cell Color setting for Bubble or Shading in Map report part, validation for values works incorrectly because it treats values as characters.


v2.11.3 August 20, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18947  Typing text on any select box on IE11, the first character of tying text is lost.
-  Defect  21416  When using Forms in Dashboard some content that exists outside of Viewport still seen in export.  

v2.11.2 August 13, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18938  Relative positioning of grids is not respected when the user changes the number of records or adds filters, causing unnecessary gaps between grids in the report 
-  Defect  21242  Subreport returns 'No Results' with "Convert NULL to Empty String" and NULL as Field Mapped value
-  Defect  21327  Izenda UI fails to render second time on Aurelia js framework
-  Defect  21340  Sort Column Name setting is inverted/reversed
-  Defect  21406  Custom Report Part Framework: registerVisualizationEngine, cannot register new frameworks
-  Defect  19061  Report actions disabled at the tenant level may still be visible under Role Setup in some scenarios

v2.11.1 August 6, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  21326  When using RUNNING functions, conditional statements are not supported (IF, CASE, etc), when using division if the RUNNING field is 0 error will be shown to user. System should handle divide by 0 and return 0.
-  Defect  21322  Stored procedure parameter defaults to filter position 1 after saving
-  Defect  21253  Threshold Popup Settings keeps expanding to the right at certain zoom levels
-  Defect  21222  When creating grid with separator and changing sort on grid columns, some times a null row appears and the subtotals are then incorrect.
-  Defect  21221  UI becomes unresponsive when editing some form report parts
-  Defect  18532  Settings of SubTotal is lost in form report part after setting it the first time

v2.11.0 July 31, 2018
~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^

-  Custom Visualization Framework  
	- New JavaScript APIs allow for the extension and customization of Izenda's current visualizations and the ability to use other charting and map libraries as well.
	- :ref:`Front-end Integration APIs <Frontend_Integration_API>`
	- Code examples can be found on our `GitHub repository <https://github.com/Izenda7Series/IzendaCustomVisualizations>`_ 

-  Dynamic threshold options for charts 
	- Threshold lines can now be set using a field to show a dynamic line for chart thresholds
	- More information on the new threshold option can be found :ref:`here <NW_Orders_Chart_Data_Thresholds_Settings>`
	
-  Relationship / Join enhancement 
	- Enhanced the way relationships display when more than one relationship for the same data sources are set up in the data model. These types of multiple joins will now be displayed as key joins in the UI for users with Advanced Data Source access.
	

v2.10.5 July 30, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  21180  Removed cast on datetime fields when no offset is used for system or user
-  Defect  21011  Filter Value Displays "No Results Found" While Loading Data
-  Defect  20839  Deleted relationships cause copy management validation to fail
-  Defect  19967  Having a period in database name causes errors when using forms
-  Defect  19502  In Single Tenant Mode Copy Management should not be shown in settings
-  Defect  18423  Subreport link in grid on datetime field to chart is failing with system error


v2.10.4 July 23, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect 20383 Report with multiple report parts shows report parts re-positioned when rendering report
-  Defect 21005 Reports containing a form with a table may produce a corrupted file when exported to WORD
-  Defect 21182 When using Save As or Copy from Report List, the new report should not contain the sourceid of the original report
-  Defect 17038 In Report Viewer, close button is not enabled in Report Subscription page


v2.10.3 July 19, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect 21224 When using Custom In Time Period filter values, Schedules and Subscriptions fail to save
-  Defect 21142 Angled labels on charts will not render when using an Azure Web Service
-  Defect 21074 Performance issues found for some joining options using rtrim in text fields, removing this option and using in memory option for join.

v2.10.2 July 16, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18655  When a user's email address is changed, existing subscriptions are not updated with the new email address.
-  Defect  20818  Cross-filtering not applied to report parts with a record limit.
-  Defect  20930  Using a pivot grid with a side total and a date filter throws an error when querying data.
-  Defect  21065  Subtotals display when a field is non-visible in drill-down grids.
-  Defect  21090  Drill-down grid with subtotal and null value shows extra null when expanded.
-  Defect  19370  Alert message about unsaved changes appears when user has already saved a new report



v2.10.1 July 9, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18176  Hamburger for category shows in report/dashboard view mode for mobile screens
-  Defect  20797  Exporting dashboards to excel would prompt a recovery message when opening the worksheets when tile name is duplicated
-  Defect  21119  Sort Column Name setting is not applied to Query Source Fields in Design tab of Report Designer


v2.10.0 June 29, 2018
~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^

-  Freeze Headers for Grid report part types

	- Vertical and Drilldown grids support Vertical header freeze
	- Horizontal grids support Horizontal header freeze
	- Pivot grids support Vertical or Horizontal header freeze
	- The freeze option can be selected in the report designer or Quick Edit on the report part property panel
	-  :ref:`Set Freeze Headers <Freeze_Headers1>`

-  Word wrap on field data in grid report part types

	- User can select to word wrap individual fields at the field level or all fields at the report part level using the report part properties menu
	
	-  :ref:`Set Field Format <Report_Designer_Field_Format>`
	
-  Vertical Alignment for data in grid report part types

	- This new option is available on the grid report part property panel for all fields or at the field level on the field property panel
	- This can be set for both headers and grid data
	-  :ref:`Set Field Format <Report_Designer_Field_Format>`
	-  :ref:`Set Grid Format <Report_Designer_Columns_Width_Setting>`
		
-  Bubble and Scatter charts now support the mulit-color option

	-  :ref:`Map Grid View <MultiColor>`

-  Pop up grid view for chart, gauge and map

	- This new option will show on all charts, gauges and maps allowing the user to open a popup window to see a grid view of the data from the visualization
	-  :ref:`Chart Grid View <Report_Chart_Grid_View>`	
	-  :ref:`Gauge Grid View <Report_Gauge_Grid_View>`
	-  :ref:`Map Grid View <Report_Map_Grid_View>`

-  New JavaScript API to resolve the WebApiUrl from custom logic

	-  :ref:`Set WebApiUrl <Set_WebApiUrl>`

FIXES
^^^^^^^^^

-  Defect  18952  When using Oracle/Postgres/MySQL reporting databases data is not properly filtered when using pperator DateTime - Equals Days Old
-  Defect  20160  In some cases when printing dashboards containing forms, the tiles overlap
-  Defect  20787  Users could not save copies of reports when given Quick Edit access
-  Defect  20970  For dashboard when scheduling / subscribing using links, the p values are showing p1value not p1 and not properly filtering the dashboard
-  Defect  21004  Resolved security issue in API
-  Defect  21063  Modifying or deleting a user using an Oracle config DB throws an error



v2.9.5 June 25, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20968  Tenant level users may encounter errors when attempting to change their password.
-  Defect  20915  Country Name "United States of America" works for World and Continent Map but does not work for Country maps.
-  Defect  20832  Visible checkbox in stored procedure parameter is auto checked after saving report although it is unchecked before
-  Defect  20823  Access Limits permission inconsistent when adding new user to role
-  Defect  20809  Performance improvement in the save report process
-  Defect  20775  Resolved inconsistency error for /api/user/all/ : ""UserName"", ""EmailAddress"", ""Role"", ""All"" Search Criteria return list of all users instead of filtered results.
-  Defect  20768  Map performance improvements
-  Defect  20441  Data Offset fields do not allow decimal values.
-  Defect  20193  Added caching for the license status endpoint to improve client-side performance.
-  Defect  19932  Grid Grand Total Table Not Summarizing Upon Printing or Exporting

v2.9.4 June 18, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  20962  When setting conditional color value for chart on datetime field formatted to month, using value range 1 - 12, month 12 does not show the proper color
-  Defect  20917  Failed to import report which has subreport when Izenda DB Config is Oracle and using External API to import report definitions.
-  Defect  20808  Using Oracle and conditional statements in a Calculated Field throws and error and returns no records
-  Defect  20455  Cross Filtering Not Applying to Multi-level Drill Downs
-  Defect  19631  In chart, field's custom color format Doesn't Apply When Filtered Report Returns only 1 Result
-  Defect  19252  Timestamp offset not changing time in report header/footer or email body
-  Defect  18389  Resolved security issue on API

v2.9.3 June 14, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  20914  Common Filter order does not adjust after changes to underlying report's filters
-  Defect  20845  Data Model Aliases impact Report Visibility for Role-based Users.

v2.9.2 June 11, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20836  Casing issue in method causing role data model access page to fail in loading.
-  Defect  20833  Lazy loading on Report and Dashboard list fail in some systems.
-  Defect  20814  In Role set up page system failed to load the next items after expanding the table again when "Show selected items only" is enable.
-  Defect  20806  Console error received and cannot open Configuration Mode of Dashboard Tile when editing filter in dashboard
-  Defect  20796  Expand drop down on parameter filter value lookup for stored procedure filter values.
-  Defect  20786  FilteredValue field of IzendaQuerySourceField is referenced when nothing is set
-  Defect  20754  Fields in joins defined in the model and not available to user should show as ..... but field name is present in some drop down lists
-  Defect  20623  ANSI_PADDING OFF inhibiting creation of some Izenda configuration database tables.
-  Defect  20595  In pop up subreport rendering multiple report parts on a page, loading bar persists on screen after clicking to open subreport and closing it
-  Defect  20562  Exporting a report definition fails when required filters are present and there is no default value for the filter.
-  Defect  18999  New parameters added to a stored-procedure are not added as filters in the reports.

v2.9.1 June 4, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20644  Load-balanced API sends schedule at start time and then four hours later
-  Defect  20622  Print permission required to render charts in email PDF attachment regardless of export permission
-  Defect  20454  Foreign Data Objects and Fields being obscured in the Data Model when multiple relationships reference a defined Join Alias
-  Defect  20387  US map drills down to World map instead of state map
-  Defect  20265  Reports with required filter on stored procedure parameter are executing report query before values are added
-  Defect  20237  RUNNING type calculated fields error when used in a report part

v2.9.0 May 31, 2018
~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^

-  Color Themes for charts, gauges, and maps provides color themes that can be selected when creating reports. These themes can also be set as the default for system or tenant levels which sets all existing and new reports containing charts, gauges and maps to this new theme default. New custom themes can be created using a JSON file to declare the theme name and color palette. These theme files are stored in a new folder, Themes, in the API. Please find the documentation links below for setting up, using and creating these themes:

	-  :ref:`Set Default Color Theme <Set_Default_Color_Theme>`
	-  :ref:`API get And Post Default Themes <Advanced_Settings>`
	-  :ref:`IAdHoc C# API for Color Themes <IAdHocExtension>`
	-  :ref:`Selecting Theme In Chart Report Part <Color_Theme_Selection>`
	-  :ref:`Selecting Theme In Gauge Report Part <Gauge_Color_Theme_Selection>`
	-  :ref:`Selecting Theme In Map Report Part <Map_Color_Theme_Selection>`
	-  :ref:`Create Custom Themes <Color_Theme_File>`

-  New Multi-Color Options allows user to select a check box which shows each value in selected charts as a different color from the selected color theme. Bubble, Scatter, Heat Map and Sparkline chart types do not support Multi-Color option. The option is only available for single metric charts because in charts containing multiple metrics, each metric is a unique color. 

	-  :ref:`Set Multi-Color Option for Chart <MultiColor>`


-  Report Designer Alternative Background Color for Grid allows user to set both the background color and the alternative background color for grid report parts.

	-  :ref:`Set Alternative Background Color <Report_Designer_Background_Color>`

-  Role Data Model Access is now a single tree to improve performance when loading the role set up. The available and visible options are shown in a single tree with checkbox to show which items are available to the role. There is a new filter option avaialble on the tree to show only selected items. 

	-  :ref:`Role Set up and Details <Role_Setup_List_and_Details>`
	-  :ref:`New API role loadPartialDataModelAccess <loadpartialdatamodelaccess>`

-  Import/Export Report & Dashboard Definitions keep source Category / Subcategory option allows users to import the same Category / Subcategory the file was exported from in the source system. If the Category or Subcategory does not exist in the destination it will be created.

	-  :ref:`Import Source Category and Subcategory <Import_Definitions>`
	-  :ref:`External API Updates importSourceCat <ImportExportExternal>`


FIXES
^^^^^

-  Defect  20636  Dashboard filters change order after navigation.

v2.8.5 May 29, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20634  Fields used in join when set to not visible/filterable cause join error for simple mode users
-  Defect  20592  Out of memory exception received on JSON response
-  Defect  20580  When scheduling a report, the recipients list takes a long time to load with a large number of users in the system.
-  Defect  20579  IzendaCity table not mapping to all MSSQL datatypes
-  Defect  20475  Some data types of Oracle stored procedures are not showing in the stored procedure schema when loaded into the data model.
-  Defect  20247  Starting Point on the y axis has no effect on the chart, this should set the absolute starting point
-  Defect  20238  Join fields not available to role should be obfuscated in the join and in the field dropdown of the join. The field is obfuscated but present in the field list of the join dropdown. 

v2.8.4 May 21, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20571  Drill-In functionality is not rendering second level of charts when using individual report parts.
-  Defect  20484  Decimal column width causes PDF export to fail
-  Defect  20483  Setting menu in Settings page is not refreshed when switching tenant via custom code.
-  Defect  20406  Report List Performance slows when Tenant Level Report List has over 140+ Global Reports
-  Defect  20405  Connection string replaced with Saved Password in Chrome version 66.0.3359.139
-  Defect  20397  Switching the tenant's value in the UserContext shows error 
-  Defect  20362  Users with multiple roles that do not have Full Report and Dashboard Access could not load their list of data sources in the report designer.
-  Defect  20215  When user updates a MySQL Store procedure and then updates connection of a MySQL database, the fields visible status will be set to false.
-  Defect  20191  In some instances user cannot open dashboard which was shared from other user
-  Defect  19939  Some roles permissions send user back user to Homepage when doing assigned actions
-  Defect  19714  In Oracle reporting database when report contains separator and preview records are set to more than 100 records, application error displays when setting Average/Sum Distinct for SubTotal of a grouped field.
-  Defect  19650  When tenant has a large data model the report list will not load for user when using Oracle configuration database.

v2.8.3 May 14, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  20469  Report definitions created with a custom data adapter cannot be imported via the external API.
-  Defect  20453  Custom JavaScript referencing field name returns [object Undefined]
-  Defect  20233  Special characters in field name throws error in report designer
-  Defect  20195  Endpoint to Create/Modify tenants in integrated modes does not allow for updates to permission and data setup
-  Defect  20115  Report list is empty after deleting schema at the Tenant level when mapping type is database
-  Defect  19891  Dashboard fails to load the global embedded subreport at the Tenant level
-  Defect  16576  Grand Total columns are out of alignment with the field columns when user changes field width


v2.8.2 May 9, 2018
~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  20444  First Page of load filter always shows isLastPage as true after first 100 items are loaded

v2.8.1 May 7, 2018
~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  20388  Improved memory utilization in the UI
-  Defect  20358  Change to remove grouping sets for subtotal calculations caused issues with smaller grids and should only be implemented when grids (horizontal and vertical) use more than 32 columns. When 33 columns are used and subtotals are enabled a sort must be enforced on the columns using the subtotal. 
-  Defect  20256  In Time period filter for previous Calendar Quarter is missing last day in Quarter
-  Defect  20255  In MYSQL the InTimePeriod filters are incorrect when using TIMESTAMPDIFF
-  Defect  20236  Exporting a subreport with applied field mappings returns all records instead of subset of data
-  Defect  20190  Resolved an issue where users and/or roles may not be applied when saving access rights.
-  Defect  19925  Gauge/Chart jsformatString, system does not properly handle update, delete jsFormatString already saved in report
-  Defect  19901  Utilizing multiple Subtotals in horizontal grids renders an extra column
-  Defect  19846  Front end conflict found in integration with underscore.js and lodash.js 
-  Defect  19668  When using Tenant Field and left/right/full/cross joins the tenant field condition results in inner join
-  Defect  19328  Change in SELECT column order for stored procedures and functions not detected on reconnect
-  Defect  19297  Filter Operator autocomplete not returning results
-  Defect  19239  In Form, Grand Total Format Doesn't Persist in PDF Export


v2.8.0 April 30, 2018
~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^

-  Import & Export Report and Dashboard Definitions 
	-  Report and Dashboard definitions can now be exported to a file. These are JSON file types which are compressed and have extension types of report (.birt) and dashboard (.bidb).
	-  Roles must be assigned the option to allow users to export definition files. See Settings>Role>Emailing and Exporting to enable these options.
	-  Exported files can be emailed but these file types cannot be scheduled or subscribed.
	-  Report & Dashboard definitions contain no user information and will only contain sharing information on roles and everyone options.
	-  Dashboard definitions contain all report definitions which are part of the dashboard
	-  The files can be imported into the same system or another Izenda instance at any tenant level (system or tenant). This requires the import system to have the same schema based on a database mapping provided at import.
	-  Imports can be completed by system administrator level users via the UI in Settings>Data Setup area. There are two new tabs for Importing the definition files and viewing the Import History.
	-  Import and export can also be accomplished via the API. Please see API export options `here <https://www.izenda.com/docs/ref/api_export.html?highlight=export#export-apis>`_  for API information for import `here <https://izenda.com/docs/swagger/import-export.html>`_  
	-  Please see the full documentation for setup and usage of this new feature  `here <https://www.izenda.com/docs/ui/doc_import_report_dashboard_definition.html>`_
	-  Dashboards can now be directly exported from the Dashboard menu to all supported export types
	
	
	.. note::
		There are new DLLs with this release included in the API download
			-  Izenda.BI.StorageProvider.dll
			-  Izenda.BI.StorageProvider.FileSystem.dll
			-  Izenda.BI.Exporting.Definition.dll
			
			If you are embedding Izenda, please be sure that you incorporate these new DLLs into your deployment.

FIXES
^^^^^
-  Defect  20236  Subreport loses field mapping filter on export.

v2.7.5 April 23, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20200  When a new filter is added to a report that is used in a dashboard, this filter is shown in the dashboard as common filter but pvalues are not accepted until the dashboard is re-saved.
-  Defect  20194  Scheduled alert does not send email when using "In Time Period" filter
-  Defect  20174  Filters should be added to Preview of calculated fields to ensure proper query performance and results.
-  Defect  19953  Column headers unaligned on pivot grids
-  Defect  19893  When copying report with Copy Console, embedded report in form breaks in destination

v2.7.4 April 19, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  20252  Resolved 500 error from API when attempting to login

v2.7.3 April 18, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19892  Performance Issue of QuerySource load in report designer with very large data model in role


v2.7.2 April 16, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^^

-  Defect  20177  User dropdown menu is hidden behind new overlay in report designer when overlay is still present.
-  Defect  20132  Query error is shown when aggregating calculated field when using self join on one table.
-  Defect  19452  Resolved security issue on API.
-  Defect  19303  Scheduling Limits functionality does not match the functionality of Access Limits.
-  Defect  19079  When adding new users to an existing role, access and scheduling rights may not be set properly.
-  Defect  18996  User is shown the wrong message when viewing a dashboard tile they do not have permission to see. User should see "You do not have permission to view this report.  Please contact your System Administrator for assistance."
-  Defect  18982  Records not returned in report if stored procedure parameters are using filter lookups and filter option is set to NULL.

v2.7.1 April 9, 2018
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  19858  P1 value passed to renderDashboardViewerPage function is not updating the results.
-  Defect  19754  Stored procedure parameter still remains in filter section of report after the stored procedure is unchecked from selected data sources
-  Defect  19641  Error message displays when user adds a Datetime field into Combination Chart x-axis
-  Defect  19504  Schedule fails to validate with "Field Comparison" filter and calculated field
-  Defect  19478  Cell and Text color options are missing calendar picker for date type fields.
-  Defect  19405  System loads all report histories of a report into memory, then picks one by version to remove history. This function is memory intensive.
-  Defect  19380  In Data Model Database read Relationships do not check for duplicate relationships.
-  Defect  19368  After deleting a schema and readding it, system should readd the deleted schema rather than create a new one
-  Defect  19362  WebAPI - /api/dataModel/LoadQuerySources, LoadQuerySourceFields; api/fusion/loadData always return false for isLastPage parameter.
-  Defect  19304  Stored procedure parameter still remains on filter section after the stored procedure is unchecked for use in report designer.
-  Defect  19278  Heat Maps would only show a label on the first value on the x-axis when using date type fields
-  Defect  19263  In Forms, subtotals are not always calculated when field is non visible. Subtotal formats are not maintained when field is non visible.
-  Defect  19259  System shows error message when user uses Non-Aggregated filter in Hidden Filter and Aggregated Field in Filter
-  Defect  19206  User in a role with view-only permission for dashboards gets logged out when trying to open a dashboard.
-  Defect  19027  System shows error message when user changes Chart Type when the existing chart has XY-Plane settings set
-  Defect  18517  Report Parts when used in integrated environments should each have their own separate progress bar
-  Defect  17488  Text 'Can create new reports?' displays in Dashboards section
-  Defect  19465  Added new setting in Web.config file of API to allow stripping of potentially dangerous characters from the schema loader. 

.. code-block:: xml

	  <appSettings> 
	  <!-- 
	  	Any characters specfied in the value fields below will be removed from any queries executed when 
		adding or reconnecting to a database. Multiple characters should be added without separator or space as 
		<add key="izenda.mssql.trimcharacters" value="*&^%" />
	  -->
	    <add key="izenda.mssql.trimcharacters" value="" />
	    <add key="izenda.mysql.trimcharacters" value="" />
	    <add key="izenda.oracle.trimcharacters" value="" />
	    <add key="izenda.postgre.trimcharacters" value="" />
	    <add key="izenda.redshift.trimcharacters" value="" />
	  </appSettings>
	  

v2.7.0 March 30, 2018
~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^

-  Redshift is now supported as a reporting database (not an Izenda configuration database).
-  System & Tenant option to hide Report Headers in Report Viewer by default. A new button was added to show the header and footer in the Report Designer and Viewer. This button will only appear if a report has a header or footer configured. API change associated `here <https://www.izenda.com/docs/ref/api_advanced_settings.html>`_. To configure the setting please see option `here <https://www.izenda.com/docs/ui/doc_advanced_settings.html?highlight=other%20settings#update-others-settings>`_
-  Added overlays and tool tips to the Report Designer to provide guidance to the user for creating reports. See styling guide for more information on CSS, **new class names associated** `here <https://www.izenda.com/docs/dev/code_bi_portal_custom_css.html#customizing-the-report-designer-tooltips-overlay>`_. 
-  Changed name of Fields tab to Design in Report Designer to give the end user more context on the functionality. 
-  Pie chart enhancement, size of pie chart is now larger when labels are enabled. 
-  The selected chart metric is now saved in the report definition. When saved and another user opens the report, the selected saved metric will be displayed.
-  Enhanced horizontal scrolling in wide grids. The horizontal scroll option is always visible. To make this change, the Freeze button has been removed from the Report options for the filter panel. In the Report Designer and Viewer the Report name and filter panel are now always displayed.  
-  Performance improvement to Role set up screen, Access Limits & Scheduling Limits are now a single tree control selection. The new APIs associated can be found `here <https://www.izenda.com/docs/ref/api_role.html>`_. 

.. note::

	This version introduces the 'Prefer' header in the API/Web.config. This header is used with the new external API. Please ensure your Web.config file is updated to include this in Access-Control-Allow-Headers.

v2.6.24 March 29, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19685  JsFormatString is used in chart but overrides the grid format using the same custom format. 
-  Defect  19383  JsFormatString does not impact gauge report part type

v2.6.23 March 26, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19672  Printing a dashboard may not work in some cases when using an Oracle configuration database.
-  Defect  19312  Users get logged out when editing "My Profile" preferences without User Setup "Edit" permission
-  Defect  19306  Cannot perform "Save As" on global report in a category at tenant level
-  Defect  18989  Grouping Set limitation of 32 columns is causing errors when creating subtotals on grid when all fields are grouped for regular grids (this is a hard limit on any drilldown style grids).
-  Defect  18910  In MySql connection strings, operator '+', '-', '*', '/' cannot be applied to operands of type 'decimal' and 'double'. 

v2.6.22 March 19, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19356  In Chart report part, "Day of Week" and "Week Number" format shows incorrectly on chart
-  Defect  19330  Changes to PK/FK relationships in the database are not picked up in the data model when using reconnect. 
-  Defect  19329  When tenant has a large data model (50k+ fields) the report list will not load for user due to query failure
-  Defect  19298  Copy management would fail if custom views had relationships set up in the data model when copying data model from one tenant or system level to another.
-  Defect  19296  Certain report permissions for a role log users out when clicking the "Access" tab in the report designer.
-  Defect  19175  P1 value passed to a dashboard via the URL is not updating the results
-  Defect  18817  When using Oracle configuration database search Report Part in dashboard does not work when user searches by Save In option

v2.6.21 March 12, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19345  Setting needed to define excluded schemas for supported databases. Please see notes & warnings on using this setting   `here <https://www.izenda.com/docs/install/supplementary_guides/excluding-sql-schemas.html>`_ 
-  Defect  19311  Issue when using special characters in * Days Old filter operators
-  Defect  19293  Emailing Global Reports fails when sending attachments or embedded html
-  Defect  19262  Join Alias behavior changes when changing join field in report designer
-  Defect  19055  Concurrency issue noted with IzendaTemporaryData table where 2 different users editing the same report are showing errors in the log file. **This release includes schema changes to the IzendaTemporaryData table. As with every upgrade, please ensure that there are no active users in the system.** 
-  Defect  18997  When making a column of pivot grid not visible, the pivot recalculates losing the grouping of the hidden column.
-  Defect  18877  When using Oracle database receiving error transaction not yet disposed when connecting to large schemas.
-  Defect  18875  Copy process should not verify items in physical data base, only model. Please note new API created for this change, details can be found `here <https://www.izenda.com/docs/ref/api_copy_console.html?highlight=copy%20console#copy-console-apis>`_
-  Defect  18344  Email will not send with Delivery Method = Attachment/Embedded HTML
-  Defect  18140  Field deleted in the physical database is still shown with field name in form, should show as "..."

v2.6.20 March 5, 2018
~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19335  Hidden filters on data model fields which are set to not visible return no data in reports.
-  Defect  19334  New option for JavaScript Format Function added to Front End API to control chart formats. Please see more details `here <https://www.izenda.com/docs/dev/api_frontend_integration.html#list-of-apis>`_ on creating the function and `here <https://www.izenda.com/docs/dev/ref_iadhocextension.html?highlight=iadhocextension#loadcustomdataformat>`_  on using the function. 
-  Defect  19315  UserContext.RequestId should be set to subscriptionId when running schedules/subscriptions
-  Defect  19254  API - /api/dataModel/loadRelationships always returns false for isLastPage parameter
-  Defect  19199  When logged in as system administrator, user is unable to print dashboard at tenant level.
-  Defect  19053  Having join alias on one object causes system error when aggregating a field from the aliased object
-  Defect  16450  Edit Report button exists when user has been shared report with "View only" mode

v2.6.19 February 26, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

- Defect  19313  When logged into application as user with simple data source access, the user selects one datasource and all datasources are removed with permissions error returned from API.
- Defect  19299  Unable to override report part definition via OnPreExecute API when rendering a report part
- Defect  19292  In some circumstances, adding a new connection string in Oracle may result in a transaction error.
- Defect  18969  Relationships are changing order and join alias is incrementing when adding several tables to report designer.
- Defect  18354  LoadCustomDataFormat does not impact charts as charts must use javascript formatters. Added optional javascript formatter to CustomDataFormat in IAdHocExtension. See usage in the documentation for `LoadCustomDataFormat <https://www.izenda.com/docs/dev/ref_iadhocextension.html?highlight=iadhocextension#loadcustomdataformat>`_


v2.6.18 February 12, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  19280  Made property ValueTokenCommandGenerator of ExpressionCommandGeneratorVisitor class overridable for creating custom data adapters
-  Defect  19274  Tenant user has proper create report permission but system fails to save report in new category
-  Defect  19251  Hiding Tenant Field in the data model prevents query data from returning
-  Defect  19235  Dashboard common filter rules do not function as expected, one filter shows when two are expected based on data sources
-  Defect  19042  Error received when using alias in function when creating a custom view in the data model
-  Defect  18895  Combination Chart Y-Axis Labels Are Cut Off when slanted at 45 degrees


v2.6.17 February 5, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  19197  The images in report header and footer are using a background image and should be imgage tag
-  Defect  19182  Column Groupings set on fields in grid report parts would cause the grid to load infinitely. 
-  Defect  19179  Forms in Internet Explorer were not rendering successfully. 
-  Defect  19033  Remove concurrency check from copy process that validates data model changes multiple times to improve performance.
-  Defect  19001  Resolved deadlock issue on MSSQL when using dashboard designer with large volume of concurrent users.
-  Defect  18993  Extended Excel exporting to allow the ability to customize the current excel exporting provider
-  Defect  18879  When using copy console and more than 4 database mappings on same schema doesn't work
-  Defect  18348  Resolved security issue on API


v2.6.16 January 30, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  19035  In time period filter not responding after changing time period in report viewer.
-  Defect  19034  Calculated Field as filter created in prior version shows as invalid field after upgrading. 
-  Defect  19007  Canceling new, unsaved reports in integrated kits would show 'The report ID is invalid' when trying to continue designing a report. 
-  Defect  19006  Removed redundant confirmation dialogues during SMTP credential configuration through the UI
-  Defect  19003  Calculated field contains another calculated field is broken, when calculated field A references another calculated field B, A is not functioning properly.
-  Defect  18998  In Dashboard when saving as a user with full report & dashboard permission, the system is removing any sharing that was added
-  Defect  18879  When using copy console and more than 4 database mappings on same schema doesn't work
-  Defect  18822  System shows can not draw chart in XY-Plane popup when user creates a chart with a separator. 
-  Defect  18571  Filter Descriptions (when using Show Filters Under Report Description) shows as undefined when using In Time Period filter
-  Defect  18438  Resolved security issue on API
-  Defect  18298  Report is Missing Save button on the report opened from sub report link
-  Defect  18118  In Tenant Setup Standalone only List of existing System Roles are displayed on the Access/Schedule section on new Tenant Permission
-  Defect  17884  Added additional methods to the Role and Tenant for integrated C# API see documentation here `Back-end Integration APIs <https://www.izenda.com/docs/dev/api_backend_integration.html?highlight=addorupdaterole#back-end-integration-apis>`_
-  Defect  17796  System should not prevent changing a user's role from [non System Admin] to [System Admin]	
-  Defect  17754  dataModel/databaseMapping accepts bad data for fromserver value
-  Defect  17707  Introduced a new API for adding new users in integrated mode. POST /api/external/user. This endpoint will return the ID of the newly created user. See documentation here `external/user <https://www.izenda.com/docs/ref/api_user.html#user-apis>`_

.. note::

	This release introduces the external Izenda API. This new API will not be used by the Izenda application, which will ensure no breaking changes as the Izenda application evolves. A simple example can be found `here <https://www.izenda.com/docs/ref/api_user.html#user-apis>`_. 
	

v2.6.15 January 22, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18991  Unable to set Subtotal using expression option as it shows permissions error
-  Defect  18973  Violation of PRIMARY KEY constraint 'PK_IzendaTemporaryData' due to concurrency
-  Defect  18970  Additional parameters are appended to the value specified in the appAuthUrl setting for the copy console tool.
-  Defect  18948  Ensure when user clicks reconnect, there are no duplicated data sources in the data model
-  Defect  18940  Report Part Context Menu Does Not Appear when using Internet Explorer
-  Defect  18939  When base URL is set to / the user is allowed access to some components they should not be allowed to enter.
-  Defect  18900  Tenant user can access the System DB & License page in some integrated modes.
-  Defect  18888  Data fails to load when turning to front side of report part tile in full screen mode for the first time	
-  Defect  18876  Unnecessary scroll bar in dashboard tile with small grid.
-  Defect  18830  System calculated incorrect data when user creates nested calculated fields: Example Calculated Field 1 = 2 fields and Calculated Field 2 = Calculated Field 1 * 2, the data returned is incorrect.
-  Defect  18815  When user removes the first field of chart's x-axis, they are unable tot configure some report part properties.
-  Defect  18780  Subtotal shows wrong value in Pivot Grid when all fields in Columns container are datetime data type
-  Defect  18645  Sub-report link is not shown in Chart x-axis when using date field type
-  Defect  18565  System shows incorrect data for DateTime Field with Group by Year when it is added 2 times in report container
-  Defect  18245  Report part is blank when copying a report part again after deleting it
-  Defect  18145  Resolved security issue on API
-  Defect  18129  Destination dashboard is empty when copying dashboard without overwrite on second copy
-  Defect  18089  Syntax error in SCSS file Izenda.Common.scss
-  Defect  17999  User is returned to specific report category after close from Quick Edit, when they never selected a category from the report list. 
-  Defect  17984  Data source categories sort incorrectly if all data sources are categorized
-  Defect  17915  In Form Grand Total/SubTotal Change Function in Sub Total pop up, is not properly changed when user updates, the user must update is again
-  Defect  17721  When copying a report part type map, fields are not properly copied to new report part in report designer.
-  Defect  17627  Front Side of Form is blank when user adds Join Alias in Relationship of report containing form report part


	
v.2.6.14 January 15, 2018
~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18967  Invalid "http://(host)/undefined" url request in report viewer. 
-  Defect  18965  Missing chart image exporting URL log when exporting
-  Defect  18951  Reconnecting to an Oracle DB fails after new items have been added to the underlying database.
-  Defect  18945  Dashboard Category Rename cause eternal loading from report list page
-  Defect  18922  Resolved transaction deadlock in Report Viewer on MSSQL server reporting database with high number of concurrent users.
-  Defect  18920  When using Filter where value is required and filter is not visible,  popup appears when the filter is required, when setting value equivalence and value set to Null/NotNull/Blank/NotBlank
-  Defect  18919  Resolved transaction deadlock in Dashboard Viewer on MSSQL server reporting database with high number of concurrent users.
-  Defect  18918  Email button does not use an XML template for customization of email template - Please note the API changes associated with this item below:
	-  GET report/emailTemplates/{isSubscription} -> GET report/emailTemplates/{templateType}
	-  GET dashboard/emailTemplates/{isSubscription} -> GET dashboard/emailTemplates/{templateType}
	-  Added new valid parameter value 2 for user to get email body template when using Email feature (old valid parameter 0 for schedule, 1 for subscription still work the same)
	-  More information can be found here `Report List API <https://www.izenda.com/docs/ref/api_report_list.html#report-list-apis>`_
-  Defect  18912   Export is blank when using Multiple grids with RUNNING(sum/average/count) in calculated field
-  Defect  18907  Field Mappings Break for Role with FullReportAndDashboardAccess when no data sources are added to the role
-  Defect  18859  Resolved security issue on API
-  Defect  18586  Resolved security issue on API
-  Defect  18548  Error message is shown to user when using SAVE AS then adds a calculated field to the new instance of the report. 
-  Defect  18526  Resolved security issue on API
-  Defect  18505  Resolved security issue on API
-  Defect  18090  Remove Dirty Form validation for report viewer page to avoid notification to user that changes will be lost when they have no ability to save a report.
-  Defect  17989  Resolved security issue on API 
-  Defect  17800  Unable to add another report part next to a blank grid
-  Defect  16512  The filter set on the calculated field is not inherited in subreports even though both reports have the same calculated fields and datasources

v.2.6.13 January 8, 2018
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18926  Error message displays when using function Average Days Old and Convert NULL to EMPTY is checked
-  Defect  18908  Caching issue in System/Tenant level for data sources, cache is not being updated when saving changes to system level users.
-  Defect  18892  Report Lifecycle is not hit without printdraft ID so pre and post execute overrides are not hit when altering the report definition, no draft Id should be required.
-  Defect  18883  Grids with 100 to 200 records per page display with gaps in row data when using Firefox browser
-  Defect  18871  Embedded Sub Report can not be exported in PDF/Word in Report Viewer only
-  Defect  18745  Some items that do not belong to the proper grouping still show in tooltip for Line/Area Chart
-  Defect  18731  Result Data in Relationship is not match with data query from database when user use function convert Null to Empty
-  Defect  18579  Full Report and Dashboard users cannot have Access Default Sharing Rights.
-  Defect  18602  Resolved security issue on API
-  Defect  18306  Resolved security issue on API
-  Defect  18013  Time and Timestamp data types are not returned from PostgreSql functions when created a stored procedure.
-  Defect  17998  APIs - advancedSetting - User can access some function of module "advancedSetting" via api
-  Defect  17993  GUI - Connection String - User can access IzendaDB by using encrypted connection string pasted into the UI Connection String
-  Defect  17992  APIs - databaseSetup- User can access some function of module "databaseSetup" 

v.2.6.12 January 2, 2018
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18894  Uncategorized report and dashboard category should not show pencil icon as name is reserved and cannot be altered.
-  Defect  18893  Added a new setting for the copy console configuration to explicitly specify the authentication URL. This setting is only applicable for integrated deployments. For more information, see documentation here `Appauthurl <https://www.izenda.com/docs/ui/doc_copy_console.html?highlight=console#the-appauthurl-setting-v2-6-12-or-greater>`_ 
-  Defect  18886  Added enhanced error handling when using clob parameters
-  Defect  18872  System hangs when setting SubTotal for 3 fields in Horizontal grid
-  Defect  18754  Cross Filtering is not working when drilling into map type report part
-  Defect  18288  When a report is created from 2 data sources joined and user removes one data source from the model the report is broken and cannot be fixed.
-  Defect  18165  Resolved routing issues when embedding in single page applications.
-  Defect  17437  Required filters set to not visible in the report designer cause report to fail copy process.
-  Defect  17338  Color icon is set and indicates values are present when user adds setting with no values on Cell Color Settings
-  Defect  17079  User is able to access to New Dashboard although has no dashboard permission on Tenant setup


v.2.6.11 December 26, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18897  When in Schedule or Subscribe "null" value does not display in filter drop down list when setting p1Value=null
-  Defect  18896  In Sparkline chart page freezes when clicking on Border and Background color gear icon
-  Defect  18891  When using Cross filtering, an error message displays after drilling down to chart/gauge containing aggregated fields
-  Defect  18874  Added User's Token to User Context in Izenda.BI.Framework.Models.Contexts.UserContext.Current.CurrentUser as CurrentAccessToken
-  Defect  18873  Disable automatic initialization of Izenda's Bootstrap.js components by default to prevent conflicts with outside Bootstrap components in integrated modes.
-  Defect  18843  In Dashboard save Global category is available in Save As popup of tenant level
-  Defect  18834  Tool tips for Font and Background Color are not altered when set in a new language file
-  Defect  18803  When exporting form report part to excel file is empty when user reformat HTML on form
-  Defect  18721  When using Oracle Izenda Configuration Database System shows error msg when user assigns a deleted data source from Visible to Available then saves
-  Defect  18710  User can apply multiple sorts in grid report although option "Allow Multiple Sorts on Grid Header" is not checked in Advanced Settings
-  Defect  18581  Some Provinces not working/missing (Quebec) in Canada
-  Defect  18481  Cannot save drilldown grid using time data type in groups 
-  Defect  18392  In report viewer page freezes if entering invalid value and triggering the filter list twice
-  Defect  18329  No value is shown in Report Designer when using a Data Model CF that is created without clicking on Preview button
-  Defect  18137  Count function on field level settings is incorrect when user turns on convert null to blank.

v2.6.10 December 18, 2017
~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^

-  Defect  18868  Dashboard shared with locked access rights should not allow user to click the background grid to add a tile.
-  Defect  18855  Setting DateFirst to ensure Sunday is the first day of the week may cause calculation of client database stored proc or function return wrong result, altered the query generation to use a different method
-  Defect  18854  Alternative Text Settings do not work on 'False' of bit data type
-  Defect  18821  Exporting PDF for FORM shrinks at horizontal dimension when add long text strings in the Form.
-  Defect  18709  Return values are empty for all Oracle Functions
-  Defect  18702  When posting a Form report containing a not-existing embedded drillDown-subReport-reportPartUsed ID, the system does not validate the ID and it is saved to DB correctly.
-  Defect  18695  When Form report is posed via API and contains not-existing drillDown-subReport-selectedReport ID it is still saved to DB correctly and displayed in Report List.
-  Defect  18665  When form report part contains not-existing embedded reportPartName it is still saved to DB successfully and displayed in Report List when sending "POST report"
-  Defect  18660  Form report containing not-existing embedded report ID is still saved to DB successfully and displayed in Report List when sending "POST report"
-  Defect  18647  Alternative text Settings are not applied for Percentage Range in the report_Grid_Chart
-  Defect  18646  Form report containing non-existing fieldId in <field-prop key="fieldId"> tag of htmlContent is still saved to DB successfully and displayed in Report List when sending "POST report"
-  Defect  18642  Report displays data corresponding with the input htmlContent-field-name instead of fieldId when opening the Form report created by sending "POST report" request on MVC GUI
-  Defect  18621  Filter Values (pvalues) does not work when user opens the link of schedule/subscribe in email
-  Defect  18614  The "No record found" message is shown after User updates calculated field filter value with Equal Tree operator
-  Defect  18551  User cannot delete calculated field from report designer once the report is saved even if it is not used in a report part
-  Defect  18544  Setting - System Configuration - Scheduling - Search fails with 500 Internal Server Error
-  Defect  18335  Stored procedure Input parameter is not properly respected as tenant field, no value is passed to the input parameter when visible or tenant field is hidden.
-  Defect  18259  System is unable to load report part of report that has name includes "/" as embedded subreport
-  Defect  18218  Error is received when using "Function" other than Group  for fields in "Labels (X-axis)" of gauge
-  Defect  18026  User is unable to delete an invalid report part in dashboard after adding
-  Defect  17313  Cell Color is set but icon is not checked to show value is set in report designer
-  Defect  16885  Postgres SQL issue with saving Connection String when input parameters exceed field length.



v.2.6.9 December 12, 2017
~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18851  Custom Data formats no longer work when used on multiple fields in the same report part
-  Defect  18837  Deadlock item resolved when using PostgreSQL as reporting database
-  Defect  18820  User who has "Full Report and Dashboard Access" can create New report although these permissions are not set in Tenant Setup
-  Defect  18775  Some settings on report part properties are changed when changing properties setting for a field of a map report part type
-  Defect  18774  Global dashboards would be visible within the tenant for system administrators if no database mapping was configured. 
-  Defect  18715  Added default sort to first x axis field in chart when adding multiple x axis fields to avoid sorting issue when drilling down on charts
-  Defect  18711  Grid columns are not sorted correctly if changing aggregated functions of the column with multiple sorts
-  Defect  18684  Alternative Text setting is not applied for Datetime field on Gauge Report
-  Defect  18671  Chart fails to redraw when adding a running field at 1st metric then another field at 2nd metric
-  Defect  18616  When using a calculated field containing a case statement and another calculated field with a case statement that refers to the first calculated field the system shows an error.
-  Defect  18615  In Scheduler Button for delete multi items (Trash icon) does not work
-  Defect  18109  Allow Customers to resolve the URL of exporting/scheduling and emailing. See example `IWebUrlResolver <https://www.izenda.com/docs/dev/ref_iadhocextension.html#iweburlresolver>`_ 
-  Defect  17729  Date format MM/dd/yyyy HH:mm:ss tt in Izenda exports to excel and shows tt instead of AM/PM format.
-  Defect  17556  Excel would lose certain DateTime formatting on un-grouped fields.
-  Defect  17417  The calculated field status is not refreshed in some cases.
	
	
v.2.6.8 December 5, 2017
~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18831  Application shows unknown error when editing a global report if it is currently opened in both system and tenant level.
-  Defect  18813  When setting alternative text on a calculated field in a chart, the alternative text is not displayed properly in the chart's breadcrumb 
-  Defect  18808  Range Only option for charts displays error can't draw chart.
-  Defect  18764  Deadlock noted in Dashboard when editing dashboard
-  Defect  18746  Can't draw city as bubble on Map report part if the report is saved at point option which is not City (This change requires alteratins to the Izenda Map table or data, please see instructions here `Import Map Data <https://www.izenda.com/docs/ui/doc_system_db_and_license.html?highlight=license#import-map-data>`_  for this process)
-  Defect  18718  When attempting to print large record sets from the report viewer the print option fails. Moving print option server side for HTML creation to reduce the volume of data processed in the browser.
-  Defect  18714  User should be able to sort the fields in Values container for Funnel chart 
-  Defect  18686  Unable to draw maps using postal codes for Canada (This change requires alteratins to the Izenda Map table or data, please see instructions here `Import Map Data <https://www.izenda.com/docs/ui/doc_system_db_and_license.html?highlight=license#import-map-data>`_ for this process)
-  Defect  18584  When user drills into a State/Province shows bubble metric for cities in surrounding state/province for Canada Map
-  Defect  18583  For Map report parts user cannot use metrics for state/province without having a country field (This change requires alteratins to the Izenda Map table or data, please see instructions here `Import Map Data <https://www.izenda.com/docs/ui/doc_system_db_and_license.html?highlight=license#import-map-data>`_ for this process)
-  Defect  18480  Mapping Field is not updated automatically when user update Field Name Alias on Field Properties for master/sub report
-  Defect  18478  On filter operator Manual Entry No Auto-Complete, no tool tip displays when hovering on the invalid input 
-  Defect  18274  Map report part is not shown when "Layout" of "Legend settings" is set "Vertical"
-  Defect  18120  Users receive repeated emails in Schedule function for some emails, this is sporadic functionality. This is due to the need to set up a database job store for schedules when runnning in distributed enviroments. Please see `Scheduler Configuration <https://www.izenda.com/docs/install/troubleshooting/scheduling.html#duplicate-scheduled-items-are-being-sent>`_  for set up instructions.
-  Defect  18042  System shows error msg when user creates nested CF with aggregated function
	
v.2.6.7 November 27, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18812  The 'Full Report and Dashboard Access' option always defaults to false when creating and saving a role.
-  Defect  18782  Some date formats cause errors when using Oracle reporting database
-  Defect  18781  Day of week date format is incorrect when selected and grouping
-  Defect  18769  Filter descriptions are not updated when altered in QuickEdit Mode until the user saves the report.
-  Defect  18742  IsRunningField in JSON response is returned as false when sending POST fusion/validateExpression containing space after RUNNING function (RUNNINGAVG/RUNNINGCOUNT/RUNNINGSUM) in expression
-  Defect  18740  Unable to add new roles in v2.6.4 when migrating from v2.0.0 and prior
-  Defect  18737  Color Settings/Cell - Percentage Range is not working on horizontal grid - rows container
-  Defect  18726  Schemas return when connecting to Oracle reporting database when user has no access to items in the schema
-  Defect  18576  In Heatmap report part clicking on the link on X axis will pass the value of Y axis when both X and Y have subreport/customURL/Javascript link configured
-  Defect  18403  Page continues to load when adding calcualted field with invalid data types for expression and clicking on OK button
-  Defect  18318  Save confirmation not shown when user adds calculated field to one data source and moves directly to another datasource without saving
-  Defect  18258  Embedded Subreport in Form is broken in destination when coyping with Copy Console
-  Defect  17952  "This filter has duplicate filter alias" displays after deselecting, then selecting a Store Procedure again in datasource tab

v.2.6.6 November 20, 2017
~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18784  Format % of Group for Subtotal calculates incorrectly in Pivot grid
-  Defect  18783  Separators data in Form report part is missing on Excel export file
-  Defect  18778  Subtotal disappears when setting % of Group for field in horizontal grid
-  Defect  18776  Preview record of Subtotal calculation does not show when setting Subtotal in pivot grid
-  Defect  18765  System returns 'Dashboard Preset Layout' popup when user clicks print on a dashboard after creating
-  Defect  18763  In some circumstances, the system does not log unhandled exception properly because of failure of resolving log4net log manager
-  Defect  18761  Any filters used after 'In Time Period' filter will not load values when cascading is used
-  Defect  18758  Error message appears when drilling in to level City of Map report part when using Oracle, PostgreSQL as Izenda configuration database.
-  Defect  18752  Datetime fields sorting incorrectly when formatted with mm-yyyy or other month year formats
-  Defect  18744  Gauge disappears when user adds Separators which is a numeric data type
-  Defect  18732  Embedded Subreports are not exporting with the top level report , the columns show blank where the subreport was added
-  Defect  18728  White listed Function Errors in when used in filter
-  Defect  18703  Error message is not shown when when filter is required and not visible
-  Defect  18680  No records display in grid when Separator field is set to not visible in Field Properties
-  Defect  18657  Grid failed to export to Word/PDF if user has configured Alternative Text/Cell Color/Text Color with Percentage Range option
-  Defect  18522  Using CTE in custom view fails with error message when saving custom view.
-  Defect  18504  When specifying filter logic and not utilizing all filter values present in the filter panel a warning should be displayed on save to show that the unspecified filters will be ignored.
-  Defect  18501  Data Refresh Interval only works once time after setting it
-  Defect  18500  "Remove Header for Export" does not work when exporting report
-  Defect  18499  Day of Week format does not work when the field is not grouped
-  Defect  18336  Resolved security issue
-  Defect  18262  Change query structure for saving role details to improve performance.
-  Defect  17967  When changing the filter field from the Filter Property panel to a different field an error is displayed when user tries to navigate back to the data source tab

v.2.6.5 November 13, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18735  Running function does not re-calculate after cross filtering
-  Defect  18722  When editing a report (grid) created from version 2.6.2 the sort option is not properly displayed
-  Defect  18712  In the Angular2 Integration example kit there is an error after navigating to the Settings page.
-  Defect  18707  Number of Records Set on Report Part not respected on Print/Export
-  Defect  18696  Forms would not display when Popup was chosen as the style for a subreport.
-  Defect  18622  When changing text color using Percentage Range, the value of the field is changed to a percentage
-  Defect  18591  Format of field effects format of SubTotal and user cannot override using subtotal format
-  Defect  18580  Drill In/Out Doesn't Always Work Until you update results on map report part
-  Defect  18578  In Form repeater the whole row of a table is moved to the top if repeated
-  Defect  18563  Running type function on fields shows incorrectly in Pivot grid report part
-  Defect  18556  Formatting Chart Value as % of Group with or without rounding, the y axis is showing the actual values with a % appended.
-  Defect  18555  Sort order is incorrect on pivot when using dates and some formats in column
-  Defect  18549  Report Review displays with no record if selecting "Decimal Number" for Filter
-  Defect  18538  Calculated Field in chart shows incorrect values and placement of points on chart. 
-  Defect  18305  Circular references to subreports will crash application, when setting Report B as subreport of Report A and then setting Report A as subreport of Report B, the system does not respond.
-  Defect  18165  Cannot render multiple Izenda components in only one Angular 2 component, relate to routing mechanism in Izenda.


v.2.6.4 November 9, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18725  Tenant, Role Fail to save and role permissions fail to load when adding default access rights or if default access rights were assigned to tenant, role prior to upgrade

v.2.6.3 November 6, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18706  When adding or updating an Oracle connection string, the system does not show Field where Data Type = VARCHAR2
-  Defect  18682  When setting up a new instance of Izenda on 2.6.1 all options on security policy tab are enabled by default.
-  Defect  18648  Error displayed displays when using case statement in calculated field in a chart report part
-  Defect  18630  When user has access to reports in uncategorized only they cannot see reports until they have access to a named category, then they see both uncategorized and the other categories 
-  Defect  18629  Browser consumes high memory when loading a role detail in Role Setup having thousands of users
-  Defect  18628  Subtotal/GrandTotal shows incorrectly for fields in Rows container of Pivot grid
-  Defect  18620  Schedule/Subscribe popup always shows default filter value even user changed and saved
-  Defect  18617  Master report from dashboard only passes the saved default filter values from the report definition to the subreport, not the new filter values added while in the dashboard tile or common filter.
-  Defect  18612  Duplicate name error received when editing filters of dashboard schedule
-  Defect  18592  Area range chart with average does not draw chart.
-  Defect  18519  Chart/Gauge/Grid Sort function works incorrectly in some instances with separators
-  Defect  18507  Sort icon does not display for field in Columns/Rows container in Pivot grid
-  Defect  18096  Permissions issue noted when items are deselected at the tenant level after role is created

v.2.6.2 November 2, 2017
~~~~~~~~~~~~~~~~~~~~~
FIXES
^^^^^
-  Defect  18692  System Fails to add new connection string when using MySQL and Oracle Izenda configuraiton databases. ***This issue only impacts customers using MySQL and Oracle Izenda configuration databases.***

v.2.6.1 November 1, 2017
~~~~~~~~~~~~~~~~~~~~~
FIXES
^^^^^
-  Defect  18679  System Fails to open a report in izenda db create from version 2.4.0 or above. This only happens if your Disabled field in the table IzendaQuerySource is in position 14 (or not the last field in the table). ***This issue can be resolved in local instances by updating the IzendaQuerySource table and setting Disabled = 0, but this will need to be done for any new items added to the database until this patch is updated.***


v.2.6.0 October 31, 2017
~~~~~~~~~~~~~~~~~~~~~
FEATURES
^^^^^^^^
-  Added Field formats for % of Grand Total and % of Subtotal. This feature will allow you to set a field to show it's % of either the sum(default) or the actual sub/grand total set in the field. Pivots also offer a % of Sidetotal. In addition, when creating a sub or grand total you can set the values to show the subtotal’s % of the grand total. Please see the  `Configure field properties in Data Formatting <https://www.izenda.com/docs/ui/doc_report_designer_fields.html#configure-field-properties-in-data-formatting-section/>`_ section guide for more information on how to use this new feature.


FIXES
^^^^^
-  Defect  18635  Could not save report when adding new filter using add filter button, user receives error message stating no operator type is defined
-  Defect  18626  Global forms type report parts are missing report columns at the tenant level 
-  Defect  18625  Global form report has relationship that contains an alias, it does not show data on Tenant level
-  Defect  18624  Error message appears when adding aggregated field into Filters then changing format of this field
-  Defect  18590  Page freezes when pressing Save on Functions page of Data Sources
-  Defect  18587  System user selects Tenant, the content panel does not load the selected item
-  Defect  18577  User cannot save Template Report Type on Oracle configuration database
-  Defect  18574  When creating subreport on x axis value date and setting the interval  on the x axis as 1 the system shows error
-  Defect  18570  Nextscheduledrundate and lastscuccessful run are incorrectly altered when schedule instance is edited.
-  Defect  18569  Sort is backward on values in chart, A-Z should be 1-x and Z-A should be x-1
-  Defect  18546  Success status is returned as TRUE when sending "POST report/validate" with EMPTY accesses-role-name
-  Defect  18531  Error message is not displayed When the Custom URL and Embedded JavaScript select the same link/icons.
-  Defect  18472  When validating Template name the response message returned is "Report name is required." ,response message should be "Template name is required."
-  Defect  18453  MaxValue(inches) for exportFormatSetting-marginSettings of Custom Margin-Landscape Orientation is not enforced properly by the system
-  Defect  18452  The API "GET report/isReportValid/(report_id)" response returned incorrectly when sending invalid report id
-  Defect  18444  System shows error msg when user clicks on Update Result after creating a report from 1 Dynamic stored procedure and 1 normal data source
-  Defect  18428  Error messages is not displayed when input Filter logic contains the word "between". System missing checking invalid expression operator check.
-  Defect  18421  Existing calculated field on Data model, report designer is not reflected the update from column alias
-  Defect  18397  Remove call to API /api/report/detectSchemaChange for static stored procedure when user moves to Field tab of report designer
-  Defect  18363  System adds new duplicated category when save a report into existed category name
-  Defect  18357  User can add duplicated Calculated Field Name by sending "POST dataModel" API request multiple times
-  Defect  18330  No filter dropdown shows under Filter Value Selection in Schedule/Subscribe popup if filter operator = Equivalence/Blank
-  Defect  18315  Stacked area chart appearance is incorrect when using large data volumes.
-  Defect  18308  List of DataSources grouped by DataSourceCaregory are still returned in JSON Response when sending "POST report/loadDataSourceCategory" api request with Non-Existing reportKey
-  Defect  18295  User can save a Custom View with empty name
-  Defect  18292  New Report contains invalid field based on DataType in Report Container (Columns,Separators,Rows,Values) and can be saved successfully to DB by sending "POST report" request
-  Defect  18080  User can save duplicated Report Category by sending "POST Report" request multiple times with non-existing categoryID
-  Defect  17934  Data Model change notifications would not disappear upon saving.
-  Defect  17788  Default URL type of Custom URL is not present once this setting is removed and re-added.
-  Defect  17755  Using Post request to add database mapping, type value is not properly verified and user can post invalid data


v.2.5.3 October 23, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18558  When input parameters are removed from a stored procedure, they are not removed from the Izenda data model
-  Defect  18539  In Time Period Filter Drop down returns no results when on back of dashboard tile of report part.
-  Defect  18537  Role setup failed to load 25k users in a single role
-  Defect  18523  User Can Be Created With Multiple Instances of the Same Role via the API
-  Defect  18510  When using text values grouped on y axis of bubble chart null values are shown which do not exist in the data
-  Defect  18503  Using a calculated field (data type date) shows application error
-  Defect  18399  Browser Print Dialogue Exponentially Slows as report becomes more complex
-  Defect  18381  Scatter chart does not show all metric of 'Value labels'
-  Defect  18271  User is unable to navigate to page 2 of user popup on schedule user popup, subscription, and access modules
-  Defect  18204  In Edge Browser the HTML of form is shown in visual tab
-  Defect  18018  API security vulnerability resolved
-  Defect  17977  Calculated Field Name is not updated on the popup after the second time the user modifies CF name in Field Name under DataSource tab
-  Defect  17699  Using MS Edge, System loads continuously when user opens SubTotal/Grand Total pop up in repeater on a form report part


v.2.5.2 October 16, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18530  Unable to save checked state of Dynamic checkbox on Stored Procedure in Data Model
-  Defect  18476  Run Copy for Data Model and Dashboards failed in Copy Management UI
-  Defect  18475  System shows "This Field is invalid" when user updates Data Model alias for report has this Field in function
-  Defect  18474  In Form report parts fields don't inherit font from parent HTML Element in PDF exports
-  Defect  18466  Grand totals are being cut off when they are money field types
-  Defect  18460  When using [NULL] in filter option for SP the value passed to param is incorrect, null is '[NULL]'
-  Defect  18417  System will not allow whitelisting of database functions which require no parameters.
-  Defect  18411  Reports created prior to v2.0 are broken when being renamed in report list
-  Defect  18311  Tenant user cannot delete subscription  they created.
-  Defect  18303  When setting alternative text in a vertical grid for value of 0 to be any other value the alternative text setting is ignored.
-  Defect  18257  Schema query to add data to data model should include database name in where clause based on given database from connection string.
-  Defect  18213  Report header is readable in the report viewer, but the spacing is overlapped in Word export.
-  Defect  18132  No roles/users are displayed when tenant user with Full sharing access in their role
-  Defect  18130  API security vulnerability resolved. 
-  Defect  18078  Sub Total is counted incorrectly when sorting in grid
-  Defect  17625  Fields with alias in data model are removed from form when saving form. 
-  Defect  17250  "The query syntax is incorrect" error message displays when creating report with "Full" join type relationship
-  Defect  17161  Chart Legend shows incorrect color values when altered in field properties.


v.2.5.1 October 9, 2017
~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18471  Invisible filter still displays in Export/Subscribe/Schedule filter area.
-  Defect  18464  User can not drag Filter Fields to change their position in Filter section without error.
-  Defect  18454  PostgreSQL Custom Views will fail when using  :: for converting data types
-  Defect  18445  System shows error msg "No operator type or operator is defined for the filter" when creating a report from 2 Dynamic stored procedures
-  Defect  18409  Calculated Fields need to allow database data type to be used in the CONVERT function
-  Defect  18386  Printing dashboad is not properly spacing tiles and results in items missing on page.
-  Defect  18383  Report part hangs after adding a Calculated Field into container then user clicks on Add a field link (the +) next to the field container.
-  Defect  18360  The print preview page is blank when User prints a form Report and the form is not printed on printer.
-  Defect  18333  Aggregated Calculated Field fails to render in Map
-  Defect  18304  Subreport Popup Option only allows you to navigate into two levels of  popup subreports
-  Defect  18270  Sorting does not change when using Day of Week format in chart when moving from A-Z and Z-A
-  Defect  18215  Required filter warning shows Position and # and should only show # of filter in viewer.
-  Defect  18040  Dashboard save popup overflows in responsive mode
-  Defect  18039  Name, title and description of dashboard tile part are overlapped in Presentation mode
-  Defect  17947  PDF scaling is incorrect, the page is not fully utilized.
-  Defect  17614  User name in users profile should not be editable in any embedded modes as it is used to keep application in sync and should not be editable.

v.2.5.0 September 29, 2017
~~~~~~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^	
- Added new filter operator "Equals (Manual Entry No Auto-Complete)". This operator does not execute any queries to the database and allows user to input any values into the text entry.
- Altered the way relationships display when more than one relationship for the same data sources are set up in the data model. These types of multiple joins will now be displayed as key joins in the UI for users with Advanced Data Source access.
- Added ability to use aggregated and non-aggregated fields in filters without changing grouping in report designer. When using aggregated and non-aggregated filters in the same report, the filter logic will be removed as only AND logic is supported.
- Performance Improvement of Data Source and Relationship Loading in the Report Designer 
- Schema Tab removed from Data Model
- Added Performance enhancements to Gauge and Map Report Parts
- Removed redundant API calls when switching tabs in the Report Designer   

FIXES
^^^^^
-  Defect  18441  All reports created from one dynamic stored procedure error when selecting the same fields in any additional reports.
-  Defect  18440  Tenant Name Dropdown doesn't show after changing Setting level to Tenant
-  Defect  18431  In Report Part Form Calculated Field is not found in report viewer and quick edit mode
-  Defect  18430  Setting Level is always enable in report designer
-  Defect  18422  Expression and name change on global report at system level do not reflect on Tenant global report
-  Defect  18390  Cannot load Oracle Stored Procedure which has nvarchar2 datatype
-  Defect  18314  Last grid column is not accessible in embedded kits for dashboard. When user makes the tile smaller and tries to make it full width again they cannot.
-  Defect  18269  Day of Week is off by one day when using this date format.
-  Defect  18230  Chart with Drill down with date format other than year shows no results when user drills down to next level on chart.
-  Defect  18083  Foreign Data Object and Field are not enabled when copying Key join with operators

v.2.4.4 September 25, 2017
~~~~~~~~~~~~~~~~~~~~~

ENHANCEMENTS
^^^^^^^^^^^^^
-  New APIs created 
	-  POST /api/report/findBySourceIds 
	-  POST /api/report/findReportPartsBySourceIds 

FIXES
^^^^^
-  Defect  18312  When Report is moved from one category to another in the report list, the role permissions do not appear to be properly updated on the role permissions, even though the user can see the report.
-  Defect  18275  Global report/dashboard which is shared to specific role can't be accessed by this newly role in existing tenant or new tenant
-  Defect  18237  Null values should show blank in pivot/drilldown but showing as 0 when convert null to empty string is enabled
-  Defect  18093  System shows dirty form message but no response after that when user config Custom URL on field with option Open Link in Current Window
-  Defect  17745  Report Part of Dashboard is cotinues loading indefinitely when user opens an existing dashboard in some Angular enviroments.
-  Defect  17724  Grand Total configuration is removed when user sets both sub total & grand total then change to HTML tag or Saves report on form report part


v.2.4.3 September 18, 2017
~~~~~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18368  Stored Procedure Lookups are Failing when Key and Value are different data types
-  Defect  18346  New Chrome release Version 61.0.3163.79 causes issues in rendering charts, maps and gauges.
-  Defect  18332  Relationships order is changed when user goes back to data source from report viewer when self join is created. 
-  Defect  18319  Grid does not export, print or show in emailed items when some fields are hidden a grid
-  Defect  18309  Latitude & longitude do not work on any map report parts.
-  Defect  18287  Existing Users Can Be Modified to have User IDs that are already in use
-  Defect  18268  When adding a date field to the x axis of any gauge and using M/d/yyyy format the year of the date is displayed incorrectly.
-  Defect  18267  Using Calculated Field for subreport field mapping Breaks and does not show proper subreport values
-  Defect  18256  Javascript declarations were being deleted upon using the visual tab.
-  Defect  18209  Scatter chart labels are shown incorrectly, value label is shown as label and label for y axis
-  Defect  18074  Subtotals of side total on Pivot grids is incorrect 
-  Defect  18073  Side Total in Pivot Are not calculating properly
-  Defect  18023  System shows blank value on filter value for parameter of stored procedure on Schedules/Subscriptions after saving
-  Defect  17991  APIs - License - User can get Izenda "License Key and Token" by sending request to "api/License/currenttoken"
-  Defect  17744  User is able to add duplicate database mappings and save. System should not allow duplicate mappings.
-  Defect  17554  SubReport link from printed PDF and embedded email shows blank page when clicked by user.

v.2.4.2 September 11, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18289  The subscription doesn't trigger the last scheduled run if the system was offline and restarts later than that moment
-  Defect  18229  When using embedded mode the URL for Custom URL and Custom JS on field values are encoded twice and cause navigation issues to the links.
-  Defect  18174  Export to Excel fails when field mapping to subreport is added to pivot
-  Defect  18127  TIMESTAMP data type with fractional seconds precision was not recognized properly 
-  Defect  18123  Adding a new field removes Embedded JavaScript from first field (On Field Properties Panel). Clickable link still available on first field.
-  Defect  18055  System shows incorrect value for Sub Total if date field has format, when user attempts to format the subtotal the data shows no results.
-  Defect  18054  Duplicated Data Object is not automatically swapped at tenant level/ tenant user
-  Defect  17988  APIs - report - User can delete archived version by sending request to "api/report/deleteAllArchiveVersions"


v.2.4.1 September 5, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18263  Calculated Field with Aggregate fails to show format tab to format the newly created field
-  Defect  18207  In Oracle and PostgreSQL timestamp datatypes are not visible in the data model.
-  Defect  18175  When sending a report which contains a Calculated Field as PDF in Email the PDF is blank
-  Defect  18160  Custom Function does not work in nested function
-  Defect  18147  In time period filter for week is picking up Sunday of next week with anything in 00:00:00 time - should cut off at Saturday 12:59:59:999

v.2.4.0 September 1, 2017
~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^^
- Copy Global Report & Dashboard in Copy Console is now supported. There is proccess change but note that Global reports can only be copied from one System level to another System level
- Custom View – allows users with the proper permissions, the ability to create views in the context of the Izenda application. These views are not persisted to the underlying databases. However, due to the nature of this functionality, SQL statements contained in these views will be executed directly against your reporting database(s). (this functionality is outside of the Izenda Query Tree). Please see user guide :doc:`/ui/doc_data_model_custom_view`.
 **We strongly recommend access to this feature should be granted with caution. If you choose to use this feature, please review the items below:** |br|
   * Ensure that only trusted users are granted access to the Custom View feature. If you have questions on doing this, please contact our support team for guidance.
   * Your connection strings for the reporting database(s) should have the most restrictive permissions necessary to the application. If you are using stored procedures, you will need “execute” permissions. Please consult your DBA for assistance.
   * This functionality can create security issues in shared multi-tenant environments if tenant fields and hidden filters are not properly configured.

- New API addded to report report/validateFilter/{report_id} to validate that all required filters in specified report have filter value :ref:`report/validateFilter/{report_id} <Validate_Filter>`.
- Removed Items per page dropdown in Report Viewer. This control was disabled in the Viewer and was confusing to users, so it has now been removed from the reports in the report viewer.
- Moved the pagination control from the right side of the report part to the left to allow ease of use when large grids are displayed.
- Added JavaScript function to allow the Report Filter block to be Open or Closed by default in Report Viewer and Report Designer:
	- To Implement this setting please see below:
		For Standalone use the izenda_config.js file 
		
		.. code-block:: javascript
		
		    // to collapse by default, the value should be 1
			UIPreferences: { 
				ReportFilterSectionExpanded: !0
			}	 
			
		For integrated scenarios like the MVC kit, use the Scripts/izenda.integrate.js (or izenda.integrate.ts for the Angular kit)

		.. code-block:: javascript
		   :emphasize-lines: 15-18
		   
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
				// to collapse by default, the value should be 1
				"UIPreferences": {
					"ReportFilterSectionExpanded": !1
				},
				"OnReceiveUnauthorizedResponse": redirectToLoginPage,
				"Timeout": 3600
			};
			
- Expanded the character limit (previously 500) for calculated fields. The field size has been increased to the maximum size text field supported by your configuration database type.
- Added lazy-loading to the dashboard filters to improve performance.
- Modified SASS files to support additional compilers.

FIXES
^^^^^
-  Defect  18222  Tenant user cannot save Subscription 
-  Defect  18166  Update result does not work for pre-selected common filter value 
-  Defect  18157  Calculated Field displays in Join Field/Field list when adding relationship
-  Defect  18153  Subscribe button is not working when user clicks it form the report list
-  Defect  18146  Categories are not shown in template list, Report without category is shown in middle panel of Template
-  Defect  18144  When setting to API's to one Izenda Configuration database the system allows copying from tenant to system - this should not be allowed
-  Defect  18128  User without permissions to overwrite existing dashboard is not shown save or save as options when attempting to save dashboard
-  Defect  18110  US country map shows javascript error when drilling down to the state
-  Defect  18104  View in Available Data Source of Connection String that has the sames name with alias of existing view in Visible Data Source can be assigned to Visible Data Source
-  Defect  17985  Tooltips do not appear on field values in drilldown grid
-  Defect  17963  ISNULL function on Fusion join is not returning proper data
-  Defect  17958  Routing is incorrect for some ares when using Angular2 host application
-  Defect  17891  In Form report part, all fields are removed in "Visual" tab after User select [Date Time] smart tag and "Remove" from "Repeater"
-  Defect  17805  System is now storing non-serializable items in the cache which only works with default memory cache causing breaking changes to custom cache provider
-  Defect  17804  Failed to save connection to a case-sensitive collation Izenda SQL database
-  Defect  18266  User cannot save a report contining a filter in an Izenda Oracle Configuraiton Database
-  Defect  18228  Configured Save process on Role update to work with CommandTimeOut Setting in Izenda System Settings Table to allow for extended Timeout values

v2.3.5 August 28, 2017
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18152  Category clean up job clears access to global reports for tenant users
-  Defect  18172  Top level of chart with drilldown is not respecting the report filter
-  Defect  18206  Filters are not respected in export with embedded mode, missing request parameter

v2.3.4 August 21, 2017
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18111  When using date value on the X-axis in chart and separator values contain # the legend of the chart shows the # as a date.
-  Defect  18107  Dashboard tile is removed until page reload after saving in the access area of the dashboard.
-  Defect  18106  No Reports can be saved in Oracle Izenda Config DB
-  Defect  18075  Fields set to not visible still display in pivot grid
-  Defect  18071  Fields in a form within a repeater that are set to not visible are still shown in the report
-  Defect  18049  Fields deleted in the database continue to show on report creation after schema update to the model.  
-  Defect  18044  When attempting to create a calculated field in IE browser, the fields added by the lightbulb pop up are removed when attempting to add another field or a function.
-  Defect  18036  Caching issue found when logging out and back in with different users under different tenants on the same browser.
-  Defect  18014  When adding subtotals to groupings, the subtotal must be calculated before formats are applied.
-  Defect  18012  PostgreSQL function parameters do not show in the data model on the function page
-  Defect  18010  Integration Mode # and & in data or filter separator breaks subreport URL
-  Defect  17930  Tree Filter values are not properly displayed in Quick Edit mode.
-  Defect  17654  Saving a report fails after user changes the data sources used in the report.
-  Defect  17218  System shows error msg when user changes aggregated function for any aggregated field which is used as a filter

v2.3.3 August 14, 2017
~~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  18043  Failed to save connection which has more than 1000+ tables or 100,000+ fields
-  Defect  17995  Join in data model causing error in report after validation of proper join syntax
-  Defect  17987  Group by date field with any format other than year is causing errors in PostgreSQL environments.
-  Defect  17986  Field value, not separator is shown in a chart when data point only has one value.
-  Defect  17983  General error message shows when formatting the same field as MM/YY with filter operator as Year/Month
-  Defect  17980  Charts fail to change x/y plane and threshold settings when there are "." in the field name
-  Defect  17976  New category does not display in left panel when copying a report with new category
-  Defect  17961  When posting a to /api/role or  api/role/intergration/saveRole with an ID for the role, if the role does not exist a success message is returned when it should be false.
-  Defect  17932  Users could add more fields through the Field Selection dialogue than were shared with them.
-  Defect  17876  Report-level calculated fields are not copied when using the copy console.
-  Defect  17818  Subtotals auto applying to numeric fields when it has format. Reproducible when adding a subtotal and removing it later.
-  Defect  17746  Configuration section of report part in Quick Edit should not be displayed in View Mode.
-  Defect  17716   Previous tenant level is set instead of system level when going back to report list from Settings
-  Defect  17675  When integrating Izenda and host application does not have a footer element, Freeze button shows error, "cannot read property getBoundingClientRect of undefined".
-  Defect  17022  Missing value on Filter drop down when deleting a self join relationship in designer and returning to the fields tab.
-  Defect  15945  No roles/users are displayed when tenant user with Full Report and Dashboard access shares their reports to role/user
-  Defect  14201  Position of tick mark is incorrect on linear gauge when metric value returns a negative number


v2.3.2 August 7, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  17567 Performance Improvements for Report Part Property Panel 
-  Defect  17566 Performance Improvements for Field Property Panel 
-  Defect  17565 Performance Improvements for Filter Property Panel
-  Defect  17702 Performance Improvements for /report/list2 and /allcategories APIs to speed report list rendering
-  Defect  16646 Performance Improvement for loading User Setup Page
-  Defect  17982 Using Filter Operators Equals and Not Equals for Datetime field creates syntax error in the query generation 
-  Defect  17959 InTimePeriod filters in Calendar Year and Calendar Month show system error when executing report while using PostgreSQL reporting connecton
-  Defect  17948 Default access rights are not properly applied to reports copied from the report list using the copy button
-  Defect  17936 When clicking update results in the Report Viewer and Quick Edit modes without updating filter values causes the report body to be blank
-  Defect  17889 Data time zone offset is not applied to separator and filter values
-  Defect  17888 When validate access token returns null, system should return 401 error, currently returning 500 error
-  Defect  17887 When creating calculated fields using other calculated fields in a report the report errors when the order is changed 
-  Defect  17866 Using the + to add all fields from a stored procedure data source the screen hangs on field selection and some fields are not properly added to report part
-  Defect  17728 System allows exporting of reports which contain required filters when no filter value is set
-  Defect  17687 Default Access Rights are not added to report definition when using Copy button from report list or Save As options
-  Defect  17671 When copying data model, report and dashboard from one tenant to another, dashboard shows empty at destination after copy shows success
-  Defect  17594 TenantName system variable in report heaader shows tenantID not Tenant Name
-  Defect  17207 When using PostgreSQL Returned Value and Input Params are empty for all functions that have parameters defined in database

v2.3.1 August 2, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect  17923  System shows error message when adding some div styling on form report parts in the designer
-  Defect  17912  InTimePeriod Filters returning errors when used in reports
-  Defect  17911  Error in initial create script for MySQL instances of Izenda database
-  Defect  17910  Cascading option is disabled for the stored procedure input parameter
-  Defect  17902  Sub and Grand totals not loading on newly report parts
-  Defect  17504  Sub and Grand total smart tags not working properly when used in form

v2.3.0 July 31, 2017
~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^
- For customers using very large data sets or views which require heavy processing. In Data Setup > Advanced Settings > Others a new setting has been added, "Show Preview section in Configuration Mode", the default is true. When set to false, users will no longer see the report part preview on the configuration side of report parts. This changes the default behavior of querying the data when adding fields to the report parts. Instead, Izenda will only query the data when the user flips the report part to view the front side of report parts. When this setting is false, the preivews on charts in adding configuration options like borders, background colors, grid lines, XY-Plane options will be hidden as well. In addition, any time the user hides the preview section by sliding it closed on the configuration side of the report part, the queries for field data will not be executed until the user either flips to the front of the report part or expands the preview section of the report part. **To incorporate this, changes the following API were made: /api/advancedSetting/miscSetting/ and corresponding model :doc:`OtherSetting </ref/models/OtherSetting>`** 
 
- New filter operators added for "Null" and "Not Null", these operators will show all Null values or values which are not Null
 
- Convert Null to Empty String enhancements. This setting in Data Setup > Advanced Settings > Others when set to true (default is false) will no longer show null in the reports for values in the database which are null. The null values will show as empty string. When using this setting, and selecting filter operators, Null and Not Null will return no results as these values have been converted to BLANK or emtpy string.
 
- Changes to common Dashboard Filter queries. Prior to this release all fields for common filters were queried and results for dropdowns were aggregated in memory to form one list of possible values. After this change, only the common filters from the first report part will be queried to obtain data for any  dropdown, popup, tree, or other filter presenting data to the end user for selection. This change will increase performance for loading large dashboards or dashboard containing many fitlers

- Improvements made to rendering Charts, Gauges and Maps by reducing the number of times these items are re-rendered and number of times data is queried to draw elements

- Changes made to stored procedure execution, prior to this change full create rights were required to make full tables, now the system uses temp tables. This requires lower permission levels for the reporting connection string when using stored procedures

- Enhance C# API to include the cascading lookup filter field along with tree filter field. :doc:`IAdHoc_Extension </dev/ref_iadhocextension>` 

.. note::

	Please note these changes as a new implementation for Filter Tree Data was added and deprecation of OnLoadFilterDataTree is planned for 3.0.0 See changes in :doc:`IAdHoc_Extension </dev/ref_iadhocextension>`

- Enhance performance of embedded subreports by reducing the number of validation requests for these report parts

- New API added to tenant /api/tenant/namesOnly to improve loading times for setting level dropdown, :doc:`Tenant </ref/api_tenant>` 


FIXES
^^^^^
-  Defect  17885  Export drops leading zeros from all text fields
-  Defect  17877  Caching issue in dashboard does not fully load the categories for the user.
-  Defect  17861  Chart breadcrumb shows undefined value when drilling down on null or blank values, should show null or blank
-  Defect  17833  Error when using 3 tables in join with 3 relationships in data model. System is not properly changing the join to accommodate the join reversal.
-  Defect  17824  In drilldown grid the list collapses again when expanding it in Report Viewer, user cannot expand report level
-  Defect  17815  Error message appears when adding filter/field of report that has Cross join type
-  Defect  17814  Error message appears when selecting Field Comparison for Filter
-  Defect  17801  Lazy loading is NOT applied when Page Break After Report Part is checked/un-checked.
-  Defect  17761  Comparing the encoded location hash on hash changed is causing infinite appending to the location hash.
-  Defect  17748  Existing categories do not display in Save popup for user with Full Report and Dashboard Access
-  Defect  17736  Charts with Separators are missing the separator after drilldown
-  Defect  17579  E-mail links for dashboards were not resolving correctly in the browser.
-  Defect  17525  Sub Totals on Form shows incorrect value, it shows the first value in the list not the actual subtotal
-  Defect  17394  Sparkine chart does not render properly when created, user must resize tile much larger than needed to have it show properly. 
-  Defect  17045  Can't change status from Deactivate to Active for user in MVC kit


v2.2.6 July 25, 2017
~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17832  Query Error on Role set up page when working with MySQL as Izenda Database
-  Defect 17784  System shows no record found when joining data sources using Fusion, Tree Filter in memory and Hidden Filters
-  Defect 17771  After adding a user to an additional role, this user does not show up in the role for sharing for users who have access to share with the role
-  Defect 17762  When using multiple aliased joins and filters passed to subreport, system error is displayed
-  Defect 17761  Comparing the encoded location hash on hash changed is causing infinite appending to the location hash
-  Defect 17730  Alternative text settings show in designer and viewer but do not properly export
-  Defect 17710  Second pvalue (p2value) for custom URL is not being validate by the system and shows an error
-  Defect 17661  SMTP info is added to logs and should not be shown in plain text
-  Defect 17622  Unknown error displays when modifying the filter of a report if this filter is the common filter in the dashboard when using only one report
-  Defect 17611  Error message is received when saving a report which contains a stored procedure data source and distinct flag is checked
-  Defect 17573  User with role which has permission on 'Visible Categories' in Dashboards is not able to open the dashboard
-  Defect 17557  When you creating a funnel chart and no sort is applied to the x axis, a sort is forced on the x axis when you alias the Y axis 
-  Defect 17096  System shows error msg when user add 1 field only to Value container of all gauges. The error can be easily removed by adding a sort to the field 

v2.2.5 July 20, 2017
~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17758	 System errors on queries where multiple relationships are set between 2 objects in the data model
-  Defect 17733	 When deleting join from report that was added by model and switching the order and then linking to a similar subreport, the join shows a query error due to extra join condition
-  Defect 17759	 Current tenant and user info wasn’t updated accordingly when updating token via SetCurrentUserContext API

v2.2.4 July 18, 2017
~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17751  Export of embedded subreports in forms fail due to dynamic variables
-  Defect 17749  Custom Tree Filters do not load in Report Viewer
-  Defect 17737  All subscriptions are run again immediately when app re-starts
-  Defect 17711  Additional fix for GetAccessToken method, lookup being performed by Tenant Name not Tenant ID causing Tenant to be generated as NULL in exporting and validation fails
-  Defect 17709  Header & Footer formatting issues, when clicking image to add focus the item is removed. Header is not fully expanded and will not accept additional items from add new
-  Defect 15236  Unable to select the field with suffix in field selection popup

v2.2.3 July 14, 2017
~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17711  In GetAccessToken method, lookup being performed by Tenant Name not Tenant ID causing Tenant to be generated as NULL in exporting and validation fails.
-  Defect 17693  All setting on "Field Properties" tab are invisible after User set subreport.
-  Defect 17674  Comparing the encoded location hash is causing infinite appending to the location hash.
-  Defect 17662  "Required" message in report viewer reflects the field name, not the alias name
-  Defect 17644  Scheduled jobs that fail to run for any reason are not rescheduled for immediate delivery.
-  Defect 17633  Modifying the Alias of a Grid Field With Grand/Sub Total causes Grand/Sub Total Expressions to error
-  Defect 17623  "No Record Found" when opening a subreport without filter values.
-  Defect 17593  KeyJoin on an existing report has blank and marked Field if alias is changed in data model for one of the data sources used
-  Defect 14605  Permissions summary data is showing Global and Local category names not the actual category names



v2.2.2 July 11, 2017
~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17656	 User cannot select a field in Subtotal/Grandtotal smart tag popup
-  Defect 17635	 User is unable to select item in dropdown lists for database mapping
-  Defect 17612	 Fixed privilege escalation issue in the myprofile settings
-  Defect 17598	 Stored Procedure cascading option is disabled in the report designer for use in OnPreLoadFilterData.
-  Defect 17561	 Reports with required filters are still querying the database prior to filter value being added to the report in the report viewer. 
-  Defect 17441	 System lost focus on Form and new added Field is not displayed in Visual tab when Form has style setting.
-  Defect 17152	 When setting time for dashboard tiles to cycle through presentation mode and clicking full screen mode, tiles are not auto advancing.
-  Defect 17065	 Subtotal does not show for field with aggregated function field for row container of pivot grid.
-  Defect 16252	 Lookup values set in the data model are not available in the dashboard filters; Stored procedure input parameters are not being shown as common filters when reports are created from the same stored procedure.

v2.2.1 July 6, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17597  Calculated fields are not working properly showing missing fields which were saved in the report.
-  Defect 17578  Successive API Calls would Result in Recursive Write Lock Errors
-  Defect 17539  Deactivate/Activate is NOT hidden in Role Setup when user has no permission to edit role
-  Defect 17505  Non-Visible Fields in Form Tables Appear in Exports
-  Defect 17499  Missing Copy/Save/Save As features when accessing report by account that is full permission in report and not admin system
-  Defect 17472  For Dashboard access button is still enabled when 'Configure Access Rights' is unchecked in Tenant Setup > Permissions
-  Defect 17469  In MVC integration example kit user cannot delete a tenant
-  Defect 17461  Cannot create new dashboard when user has permission to create dashboard but not category
-  Defect 17453  In Tenant permissions 'Register for Alerts' checkbox is not automatically unchecked and disabled when 'Schedule' is unchecked
-  Defect 17419  The field status is not refreshed when reconnecting to the database in some cases.
-  Defect 17402  System scales the slave section of data model fields and it is not fixed with the bottom of the page
-  Defect 17323  From the second field of form, when user selects 1 function from drop down list, it is not updating the field. User must select it from the function list a second time 
-  Defect 17295  Cannot use Enter or Tab when saving Category or Subcategory of Dashboard
-  Defect 17282  After user reformats HTML in Form, and changes any function for a Field, system still keeps the old function for the Field on the Visual tab. 
-  Defect 17253  After user click format HTML in form and adds a new field the HTML is no longer formatted
-  Defect 17082  Error 'The tenant ID already exists' displays when Deactivate or Activate a tenant after adding a duplicated one
-  Defect 16774  Created Date, Number of Views and Average Rendering Time of copied report/dashboard still keep values of the old report/dashboard

v2.2.0 June 30, 2017
~~~~~~~~~~~~~~~~~~~~~

FEATURES
^^^^^^^^
-  Removed Category List navigation on left side of page for Dashboard and Report Viewer
-  Drilldown Grids have new option "Collapse Drilldown by Default". This option when selected will show the entire grid collapsed when user opens the report in the report viewer.
-  Drilldown Grid now shows individual rows for subtotals even when there is only one value in the grouping
-  New Collapse/Expand all option added to drilldown grids. When user clicks the icon the entire drilldown grid will collapse to its highest/lowest level.  
-  Added Lazy Loading for Dashboard tiles to improve loading speeds. All tiles show individual loading icons to allow users to interact with tiles which have already rendered, while waiting for large dashboards to load.
-  For report part containers which do not require sorting, the system will no longer create an automatic ascending sort for each field added to a report part.
-  New option added to Data Model Others page, "Allow Multiple Sorts on Grid Header". This is selected by default. When unchecked this will allow users to resort column in the report viewer without unsorting other columns. The sort in the report viewer will be only one column at a time when the user changes the sort. These are not saved in the report, but a user defined sort on the report viewer.
-  Added new JavaScript API for rendering Dashboard "IzendaSynergy.renderDashboardViewerPage(#container, dashboardId, { p1: "abc;#def", p2: "xyz" })"
-  Added additional performance improvements

   - Changed the projection for select statements to use * rather than select specific columns
   - Unique name checking was creating table scans, so created index on Name field
   - Removed some redundant SQL queries
   - Removed redundant calls in the save process
   - Added caching for validation result of report to reduce api calls
   - Added caching for data formats of all data types
   - Performance improvement for API for /api/allcategories   
   - Removed redundant calls from Report Viewer 
   - Removed calls to api/report/loadAllFilterFieldsData from Report Viewer and Dashboard Viewer 

CHANGES FOR INTEGRATION KITS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
-  Integration kits using deployment mode 1 (Angular2Starterkit, Mvc5 Backend standalone) have been updated to use the following API  "user/integration/saveUser" endpoint when creating new users. This change resolves issues found after defect 16779 was resolved in this release. Prior to this change the user active flag was not properly checked in integrated scenarios. After this change you must use "user/integration/saveUser" to set the user to Active and InitPassword to true when creating the new user, these flags cannot be set using "/user" (POST).


.. note::

	If you experience any errors stating 'Your user ID is inactive.', please see our  `troubleshooting guide <https://www.izenda.com/docs/install/troubleshooting/general.html#your-user-id-is-inactive-integrated-mode-only>`__.


FIXES
^^^^^
-  Defect  17555 Key joins in Global reports cause errors and blank fields when tenant users can edit with save as permissions.
-  Defect  17545 Can't move to next page of results in report on Drilldown Grid which has a Subtotal
-  Defect  17529 For equals checkbox filter type user needs to refresh to load filter values on the first time entering report viewer
-  Defect  17528 Sub and Grad totals are not displaying values when exported for forms, they show field values instead.
-  Defect  17515 System shows error msg for report created using PostgreSQL stored procedure and valid value is entered in input parameter. 
-  Defect  17494 User cannot delete Report on Tenant Level, after clicking delete the report still shows, and when user tries to open, system shows: "This report is no longer valid"
-  Defect  17485 Pivots are showing incorrect values for dates as columns when changing from Grouped by year to grouped by other date formats.
-  Defect  17484 Subtotal showing first item in list of values, not the actual subtotal.
-  Defect  17445 When copying a report from a subcategory to a new category, a new subcategory is created.
-  Defect  17411 Error showing missing fields in destination from reports copied using copy console when created from Stored Procedure data source.
-  Defect  17409 When editing subtotal expression for a Calculated Field an error displays.
-  Defect  17406 User is unable to drilldown to drill down on a world map, to countries with shading and bubble metrics.
-  Defect  17390 In Copy Management new name of workspace does not save when renaming it
-  Defect  17385 For MySQL schema of all stored procedures are blank when database in Connection String is uppercase
-  Defect  17367 System shows query error when user has a grid containing a subtotal and adds a duplicate field in the separator column
-  Defect  17348 Newly added role does not display in Available Roles/Users of Scheduling after deleting a role
-  Defect  17335 High cpu usage on azure app service noted after adding 1000+ tenants
-  Defect  17321 Error received when using function "Days Old" in report part, error shows, "There is an error when querying data. Please update the configuration."
-  Defect  17297 Distinct option in report designer is changed from 'Checked' to 'Unchecked' after selecting/updating Filter's value
-  Defect  17290 Browser back button does not work from subreport to navigate back to top level report.
-  Defect  17231 Filters from top level report are lost when changing value after clicking link to  subreport and changing filter values in the report viewer.
-  Defect  17226 "This relationship is duplicated" error message doesn't display when adding duplicated relationship
-  Defect  17208 User can create a new category in Copy Report/Move Report on report list pop-up when user has no permission to create category.
-  Defect  17200 Setting level for system admins should be disabled when they are in report or dashboard viewer.
-  Defect  17183 In MVC kit provisioning Map data fails when in integration Mode
-  Defect  17120 After copying a report part, and switching to Configuration Mode, delete icons of a report part are enabled when that Report Part Type is unchecked in Permission for the role.
-  Defect  17108 In Form when adding a Smart Tag, the pill  'Click here to select field' is NOT removed after selecting a field for that tag
-  Defect  17097 System does not show embedded sub report on Form
-  Defect  17063 Missing edit report name feature in Tenant when user has permissions to edit the report name
-  Defect  17043 User cannot update 'Recurrence Pattern' when editing a subscription.
-  Defect  17030 In Copy Management "Save" popup still displays after clicking on "Save" button.
-  Defect  17003 Printed version of report is missing some records when printing a gauge report with 'Page Break After Separator' is checked
-  Defect  16990 Mouse cursor is not released when resizing the grid columns in report designer
-  Defect  16960 In Angular2 sample integration kit left panel of setting page is disabled when switch between report list and setting page, then click Connection string menu
-  Defect  16956 System failed to generate the gauge report when Label (X-axis) is a DateTime field with Function as 'Average Days Old'
-  Defect  16932 In Report Designer Field Properties system is missing validation for Value Range/Percentage Range type in Color/Alternative Text
-  Defect  16872 In Report Designer grids, user is unable to set Color Settings with 'Value Range' or Percentage Range' type after setting color with 'Value' type
-  Defect  16849 In Angular2 integration kit form report parts are not working for both Visual and HTML panes
-  Defect  16814 Filter is emptied after editing data source in report designer
-  Defect  16804 Cannot save. Message "Join Alias cannot be duplicated with the Data Object or Foreign Data Object" should display
-  Defect  16798 An error is shown when User saves a report without image on header.
-  Defect  16784 Dashboard tile does not automatically flip to backside after selecting Text type dashboard tile.
-  Defect  16779 In integrated mode user Tenant can load Data successfully although Tenant is not active
-  Defect  16720 City's metric is not shown in Country Map
-  Defect  16718 Template/Report name in Save popup is always 'Example Template/Report Name' although the name edited in Report Design
-  Defect  16661 Query execution is blank if report part uses calculated fields
-  Defect  16651 Failed to execute Oracle and Postgres Stored Procedures when input param is Ref Cursor
-  Defect  16600 Category name shows as blank in Category column after updating info in database on fields where datatype changes
-  Defect  16598 System updates the Join Alias, to blank and dot signs are displayed on the Foreign Data Object and Field when alias is set to the same name as the Foreign Data Object
-  Defect  16593 The valid report part is grey and nothing happen when add a dashboard after add an invalid report part
-  Defect  16549 Map presents Postal Code in incorrect location/Country when zip code is duplciated
-  Defect  16530 Concurrency error message appears when updating and saving any changes on Security tab of data model after the second change
-  Defect  16513 Subreport's existing filters are Ignored When Inheriting from Parent
-  Defect  16449 User can view report in dashboard that has column of Data Source that has been changed to be not visible in Data Model
-  Defect  16448 Filter displays normally when column is changed to not Filterable in Data Model
-  Defect  16438 Report Viewer export option does not work with system user level that has "Full Report and Dashboard Access" Permission in Role
-  Defect  16433 Error message appears when creating the report with Database that has special characters in name and Calculated Field in Database Source
-  Defect  16425 Exporting fails on JSon with a grid report containing a null value
-  Defect  16398 Form is rendering with incorrect source data until the loading is complete
-  Defect  16310 As System Admin user Setting level attempts to go back to System level every time refreshing a tenant level report
-  Defect  16045 When all items are removed from the footer and header & footer are visible report fails to export
-  Defect  16043 The Created Date value isn't updated correctly after user copies/moves a report
-  Defect  15928 User expands the column which contains subreport but can not save this settings
-  Defect  15909 In Integrated Examples the URL's are not consistent
-  Defect  15902 System lost the mapping Field for Sub report in Destination Report when copying Dashboard and Report.
-  Defect  15886 Category/Subcategory drop-down does not show data value in TenantLevel/SystemUser/TenantUser
-  Defect  15820 Current report should not be displayed on list of sub-report selection list
-  Defect  15777 Copied report is broken when user update Relationship Join Alias and run copy again
-  Defect  15703 When Copy Reports with Form having more than 1 part in Embedded Sub-report, Run Copy fails
-  Defect  15437 System shows Detect change icon on all stored procedure Fields after user re-assigns this item from Available to Visible on Connection String page
-  Defect  15327 Expand/Collapse icon is not on the same line with the owner data sources which were truncated text
-  Defect  15298 System shows error msg when user creates Key Join which has Time value in comparison
-  Defect  15272 Number of item in Filter Value is affected by query limit. These settings should be independent
-  Defect  15207 Updated User Name is not displayed on Report List - Report Owner, Create By, Last Edited field
-  Defect  15132 Filter doesn't apply to second tile in dashboard (even after "Update" is clicked) until the filter is modified.
-  Defect  15115 Error noted when user creates 1 new Dashboard with Pivot
-  Defect  15110 Invisible Field in Data Model is not displayed as masked data
-  Defect  15073  Subreports on Date Fields showing error, Multiple Values for Fields
-  Defect  15054 Icon for configured Tenant Field is displayed incorrectly on Data Model page
-  Defect  14054 Copy Dashboard function showing error when recopying a dashboard where the reports were deleted in the destination prior.
-  Defect  14019 System loads all Functions in calculated field and function dropdown and should only load items from currently used connection string
-  Defect  13992 Filter description does not display in dashboard tile after adding new filter into report
-  Defect  13745 No record returned is displayed the first time the user clicks to preview results for sub and grand totals
-  Defect  13524 Calculated fields are missing in report design when "Field Comparison" operator is used for filter


v2.1.5 June 22, 2017
~~~~~~~~~~~~~~~~~~~~~
FIXES
^^^^^
-  Defect 17436	 In some Angular applications using polyfills, errors occur on Dashboard page in Izenda 
-  Defect 17399  When clicking the option "Show Filters Under Report Description", filters are not consistently displayed
-  Defect 17386  Error occurs on row count queries when row count is larger than max int field limit
-  Defect 17381  User is allowed to save calculated field that is not valid and is showing error
-  Defect 17376  Some calculated fields saved in data model do not show up in reports after saving
-  Defect 17366  Dynamic Threshold color values are lost when saving a report
-  Defect 17364  Users without access to system messages still seeing system message
-  Defect 17363  In Datamodel when clicking reconnect some Calculated Fields show deleted
-  Defect 17316  Exporting fails when using 2 grids when one contains a calculated field
-  Defect 17288  Field in subreport mapping is blank when opening global report at tenant level in report designer
-  Defect 17254  After creating an active version of an archived report is is showing the configuration of the active report not the archived version
-  Defect 17244  System shows normal Field in Aggregated Group in Filter drop down list
-  Defect 17225  'Custom URL' and 'Embedded Javascript' field options are hidden in Field Properties when user has those permissions but Subreport is disabled for the user
-  Defect 17223  Remove Page Break After Each Entry setting under Report Part Properties in Forms as it is not an available feature
-  Defect 17222  When using PostgreSQL as Izenda configuration database, the report version history list shows no record found in display when viewing archived versions
-  Defect 17198  In Angular2 embedded kit, print option from report list is not working
-  Defect 17196  User can create/copy a report when 'Can create new report?' option is unchecked for a tenant
-  Defect 17186  User cannot create a new role when role has 'Create' but 'Permissions' option is unchecked for Role Setup
-  Defect 17168  In Form report part fields outside of repeater is auto changed to sort by A-Z
-  Defect 17164  Missing date and time only filter operators for datetime/time input-param field of stored procedures 
-  Defect 17163  Select All Gives Roles Tenant Permissions in Single Tenant Deployments
-  Defect 17155  'Next Scheduled Run' is showing start-date instead of next-run date after editing the schedule/subscription
-  Defect 17147  After adding join alias to joins containing additional join conditions some data is no longer returning
-  Defect 17140  In MVC kit error message appears when adding new PostgreSQL connection string for Tenant
-  Defect 17129  In MVC kit GUI is cut-off when user selects Presentation Mode icon after opening dashboard on some smaller screens
-  Defect 17110  Query execution export is blank if report part uses calculated fields
-  Defect 17099  Forms lose style settings in the HTML tab if fields are added/removed in the Visual Tab

-  Defect 17079  User is able to access to New Dashboard although has no dashboard permission on Tenant setup
-  Defect 17068  Grand total only shows on the first page in UI of paginated report
-  Defect 17066  Freeze function does not work in Quick edit mode of report viewer
-  Defect 17061  Incorrect URL is set when user clicks close button from Report Viewer and Dashboard pages
-  Defect 17033  New Setting added to SystemSetting table: RollbackSPWhenLoadSchema By default, RollbackSPWhenLoadSchema = 1. For customers using Linked Server who cannot setup DTC, this can setting can be set as: RollbackSPWhenLoadSchema = 0 to avoid distributed transaction errors when system attempts to fetch stored procedure schema data.
-  Defect 17025  In Report Part Form changes in Report Part Properties do not save properly and report shows no changes found on save
-  Defect 17013  When using Post request to /api/user/load userModeType 0 should return all but returns no results
-  Defect 17006  Some records in the last page are hidden by report footer
-  Defect 16873  In scheduled instances the same emails are sent to cc-list more than one time (in case more than one email recipient put in to-list)
-  Defect 16799  Close button on report viewer and dashboard does not work in some integrated environments
-  Defect 16551  In Form report part user cannot uncheck "Visible" of fields on Field Properties -> Data Source
-  Defect 14959  Image from relative path does not display in exported file for Tenant Logo

v2.1.4 June 16, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17258	 When using the Angular 2 kit and creating a dashboard receiving Error 'offsetHeight' of null.
-  Defect 17131	 Unable to drag and drop field into Report Body on Chrome version 59
-  Defect 16881	 Using stored procedures decimal Accuracy Is Not Being Respected
-  Defect 16839	 System is not keeping Sort setting on Field Properties if form contains multi Fields in container
-  Defect 15469	 No tooltip displays when hovering over Column Group text field

v2.1.3 June 13, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17162	 Casing issue on table IzendaReportDataSource causing errors in some MySQL instances
-  Defect 17125	 Adding aggregate function to form field is not grouping other selected fields as expected
-  Defect 17071	 Deleting repeaters on forms invalidates field names.
-  Defect 16981	 The wording for the license expiry is incorrect. It states now "The license expired x number of days ago"
-  Defect 16963	 On Header/Footer system is still validating deleted items
-  Defect 16876	 In Report Designer with aggregated field as filter, error message displays "The application has encountered an unknown error.." after removing aggregated field in Configuration section
-  Defect 16783	 In Angular 2 embedded scenarios forms are not working properly
-  Defect 15962	 On Database Mapping save button is not functioning after deleting a tenant then the whole row
-  Defect 15174	 Advance Settings page display is missing part of text "Determine common filter for the same field based on" on smaller screens

v2.1.2 June 6, 2017
~~~~~~~~~~~~~~~~~~~~~

FIXES
^^^^^
-  Defect 17100  Error when exporting a report with multiple report parts to Excel
-  Defect 16733  System shows error msg when user drills down on Charts with multiple DateTime fields in x axis when using cross filtering
-  Defect 16759  Issue with Date Based Click Through in Charts with cross filtering when drilling down from date field formatted as year, and one as Month. The system is not passing proper filter values for dates

v2.1.1 June 2, 2017
~~~~~~~~~~~~~~~~~~~~~
.. warning::

   For version 2.1.1 and above, there are code-level changes that will need to be made when using Izenda in embedded mode. The previous Encryption/Decryption logic has been refactored to use a new StringCipher class local to the kits. You can view the latest commits for more details.

* https://github.com/Izenda7Series/HtmlStarterkit
* https://github.com/Izenda7Series/Angular2Starterkit
* https://github.com/Izenda7Series/Mvc5StarterKit
* https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone
* https://github.com/Izenda7Series/WebFormsStarterkit
	   
   
FIXES
^^^^^
-  Defect 16800  In integrated instances some users can access modules not allowed for tenant
-  Defect 16802  Form reports fail to save when data source is aliased
-  Defect 17031  Calculated fields used in reports are not displayed on the report parts in the dashboard
-  Defect 17042  Subtotal is null when not using a grouping level in grid

v2.1.0 May 31, 2017
~~~~~~~~~~~~~~~~~~~~~

BREAKING CHANGES
^^^^^^^^^^^^^^^^
-  File izenda-ui-blessed1.css was removed from the UI download it was merged with izenda-ui.css, please ensure when upgrading that it is removed from your local deployment

FEATURES
^^^^^^^^
-  Cross Filtering added for charts with drilldown ability. This allows the report desginer to configure filtering for all or specific report parts in each report based on the drilldown values from each chart. This cross filtering behavior will also work with the configured reports in the dashboard and in report parts. See user guide :ref:`Cross Filtering <Apply_Cross_Filtering_to_Multiple_Report_Parts>`
-  Performance improvements for sub/grand total calculations
-  Performace improvements for saving reports

FIXES
^^^^^
-  Defect 15825  Filters Dropdown should not reload every time user hits on dropdown
-  Defect 15992  Exporting fails on excel from report list using datetime field without a format from a grid report
-  Defect 15429  Embedded subreport is not recognized when copying along with master report. 
-  Defect 13239  In stand alone mode if Admin user deactivates user they may remain active until the token is inactive
-  Defect 16348  Data Sources of MySQL connection do not show correctly when database in Connection String is uppercase
-  Defect 16356  Warning message 'The selected system/tenant level does not contain any connection string.' appears when navigating from Connection String to Data Model then logout
-  Defect 16841  Presentation Mode of dashboard not allowing interaction with report parts which have drilldowns and subreports
-  Defect 16409  No error message appears when required field 'Connection String' is blank
-  Defect 16553  Blank Filter popup displayed when using type 'Equals (Popup)' for group field
-  Defect 16213  Exporting tab, Preview not displayed if using page break in case report not yet saved
-  Defect 16403  No value data displays on drop down list of report filter when selecting "Single" option and then switching "Multiple" option
-  Defect 16311  Long report names are overlapped by Filters section
-  Defect 16442  Map does not show in document after exporting
-  Defect 16082  User should not be allowed to create relationship alias which duplicates an acutal used data object name
-  Defect 16767  Could not select the filter data value when using  aggregated filter with Average Function
-  Defect 16724  Incorrect query syntax error displayed when using calculated field with concatenated values as filter
-  Defect 16540  Non Admin users with create role permissions are unable to create new roles
-  Defect 16415  Label justification for 'Value' label on Settings>Data Setup?Advanced Settings page
-  Defect 16402  User cannot log in when they have multiple roles and one is not active
-  Defect 15433  Error occurs in Quick Edit when user attempts to remove an existing field.
-  Defect 15687  Schedule Tab displays when refreshing page on Global reports after save.
-  Defect 15808  User with System Admin rights cannot "Subscribe" to global reports
-  Defect 15901  System Admin user at Tenant Setting level can delete the report 
-  Defect 16041  For system admins at tenant level Move and Delete icons are still available for global reports but should be hidden
-  Defect 16042  For System Admins User cannot copy a global report to local  in report list
-  Defect 16331   User without full access right is able to edit category's name of Global Reports
-  Defect 15896  Cannot not copy dashboard from "Global Dashboard" to "Local Dashboard" or vice versa
-  Defect 15895  List of categories should be updated correctly in the left navigation after move/copy a global/local dashboard
-  Defect 16769  Changing Preview Records limit should drill up all parts to highest level again
-  Defect 15256  In form User cannot add more than one field at a time
-  Defect 15394  System shows error msg when user uses operator join of Date group for DateTime Field
-  Defect 15927  User can not open a sub report as Link from report Designer
-  Defect 16805  User can not open a sub report as Link on report Designer after saving the new report, error states report has not been saved.
-  Defect 16247  Form, when using the insert subreport feature on the form properly panel subreport style changes the field name to be invalid
-  Defect 15819  Rule to show/hide buttons in Dashboard and Dashboard List is incorrect for Global reports (Rename, Move, Delete, Move, Save) should not be shown to System Users in Tenant Level
-  Defect 15332  Data fails to load when sorting one of 2 similar fields with subtotal/grand total. 
-  Defect 16712  Error message shows null when navigating in embedded instances when using IE browser
-  Defect 15275  Oracle 12c - ORA-01795 found in log file 
-  Defect 16543  In Report Designer, clicking distinct Checkbox Breaks Aggregates on MSSQL Databases
-  Defect 15524  Equals (Manual Entry) Cannot Manually Enter Values that Exist in the Dropdown
-  Defect 15413  Report Parts Shifting When Navigating to Viewer
-  Defect 16412  User can not log in system after Deative then Active again. System still shows error msg for inactive user
-  Defect 16874  Coypy Management Dashboard list loading performance issue - list loading slowly
-  Defect 15869  When clicking on "Show only my workspace", the content panel still displays different owner 's workspace in copy management UI
-  Defect 16407  Unable to search any report in Report Part Selection of Dashboard under Category All
-  Defect 15794  In Text style Dahboard part when user inputs data in Body text section it is not displayed in Front side
-  Defect 15308  System does not show the dirty form msg when user creates a new Dashboard and then click on any Report link to go to Report Viewer page
-  Defect 16588  Form page break button insert does not create acutal break
-  Defect 14982  Reformatting at HTML page disables subtotal/grand total setting in Forms
-  Defect 16023  In Standalone mode System shows loading progress bar for a long time when user lets the application time out
-  Defect 16844  In map report parts, shading metric does not show when drilling up to top level of drilldown
-  Defect 15804  In Oracle Value is 0 after collapsing rows in drill down grid which has a datetime field separator
-  Defect 16778  When loading a report with an Embedded Sub Report system continues to load without finishing the subreport data
-  Defect 15924  Access rights disappear briefly after saving a new report
-  Defect 15748  System works incorrectly when appling Additional Join for Relationship and key join
-  Defect 15741  In Cross Database Join using additional join conditions drop down list for Data Object/Foreign Data Object is blank
-  Defect 15281  Missing icon to indicate datatype type of Time field 
-  Defect 14983  Print preview does not exist until the report is saved. 
-  Defect 16036  Report Designer Unable to change format of Datetime field to nonformat
-  Defect 15930  Page continues to load when creating simple gauge on Firefox/Edge/IE browsers
-  Defect 16851  Linear Gauge does not show the Metric Value on the Preview section
-  Defect 16781  System shows error msg when user selects function for one field on Horizontal Grid
-  Defect 15299  System shows error msg for failure validation when user create report with Cross join
-  Defect 15206  System navigates to Format page, instead of Fields page when design is selected from report list.
-  Defect 16780  Load Report/Dashboard list performance issue 
-  Defect 15969  Printed and Exported reports are sometimes blank for tenant users
-  Defect 15923  In System Configuration Filter Value Selection does not display in Dashboard Schedule instance
-  Defect 15205  User input wrong data in Provide Information page, system does not show error msg but let user navigates to create password page
-  Defect 16655   Simple Gauge shows 'false' instead of value when using Oracle
-  Defect 16446  Numeric formats are not properly exported on Word and PDF docs
-  Defect 16400  In Form report part Unable to delete or add more fields after pressing "Update Result" or "Save" button twice
-  Defect 15230  System shows duplicated msg when user create 1 Relationship with 2 Key Join: 1 for Field comparison and 1 for Value comparison
-  Defect 16322  Error on Schedule shows start date required, should be start time required
-  Defect 13808  Dashboard reloads each time user goes to schedule or access tabs
-  Defect 15071  Headers are Overlapped in Exports
-  Defect 15684  Popup Subreport is blank when there is NULL filter value transferred 
-  Defect 12645  Charts > Drilldowns Don't Work with DateTime Fields
-  Defect 16244  Sorting is not correct when table does not have a primary key assigned.
-  Defect 14660  Advanced Settings Data Model Query Limit will not accept more than 100K. 
-  Defect 15906  Alignment for sub/grand total lost on Export
-  Defect 15659  Changing date format does not export to CSV
-  Defect 16207  Custom Tree Filter node shows value not text for child nodes when selected
-  Defect 14796  Date formats in dd/mm/yyyy style export with mm/dd/yyyy format
-  Defect 14799  Deleted columns from physical db are not added back when recreated after reconnecting to the database
-  Defect 15569  When copying Dashboard in UAT called Dash with some reports the copy fails without any error notification and stops working 
-  Defect 15193  Exports Lose sub/grand total formatting and display as text
-  Defect 15525  Exporting fails with null value in between date filters and value in database is null not ''
-  Defect 15594  Grouping is not working properly for Separators when date is used and format is changed
-  Defect 16199  Heatmap mouse over does not show Y axis label
-  Defect 15753  Lazy loading loads data twice, only one value but removing duplicate calls
-  Defect 15783  Mapping still shows some values in the wrong areas when drilling down
-  Defect 16542  In MySQL Izenda tables are created in all lowercase, but refered to it in Pascal case causing issues in MySQL instances on AWS enviroments
-  Defect 16279  Perforamnce issues found when multiple users are saving reports at the same time
-  Defect 16690  Report Title Changed for new report In designer does populate in save dialogue
-  Defect 16776  In user profile area of Izenda, Sign out option should not appear in any embedded modes
-  Defect 16321  Sort or search in Uncategorized report/dashboard list always show blank page
-  Defect 15994  Sub/Grand Total Breaks After Changing Alias of a different field
-  Defect 16285  When adding more than 13 items to the copy management UI one of the destinations is unable to be seen in the Report copy settings area
-  Defect 15872  When column name of view is [Order By] system randomly errors

v2.0.6
~~~~~~~

FIXES
^^^^^
-  Defect 16674  In Angular integration example kit Izenda dropdowns are not working, Report List doesn't Populate, Connection String & License Information Disappears
-  Defect 16846  Changes to Copy Console tool to ensure it works properly in integration mode 1
-  Defect 16916  System freezes when trying to edit charts in designer

v2.0.5
~~~~~~~

FIXES
^^^^^
-  Defect 15571  In Data Setup, Connection String SQL Injection risk on Linux/Unix stored databases
-  Defect 15093  Export Load Dialogue Not Deleting in some integrated modes
-  Defect 16573  Lazy loading is failing for Database mapping feature for global reports 
-  Defect 16558  Browser memory causing application slow downs
-  Defect 15279  Inconsistent field types shown in front end, when user edits field time in database and reconnects. Izenda Data type is not properly updated.
-  Defect 16514  It is possible to save reports outside of the path specified for Send to Disk

v2.0.4
~~~~~~~

FIXES
^^^^^
-  Defect 15518  Exporting Grid to PDF Shows Separator Fields that are Non-Visible
-  Defect 16504  Missing state geo json files

v2.0.3
~~~~~~~

FIXES
^^^^^
-  Defect 15571  SQL Injection vunerability in MySQL
-  Defect 15755  Copy Management fails to copy when using Oracle12c when packages exist using the same names, but different parameters
-  Defect 15431  Cannot create field mapping for subreports using hidden field in report and grouping is incorrect when field is hidden
-  Defect 16292  Performace issues noted, indexes added for some tables in Izenda database 

v2.0.2
~~~~~~~

FIXES
^^^^^
-  Defect 15964  System shows missing data on some gauges when user change from Back side to Front side of report part several times
-  Defect 15946  System does not render Gauge/Pie/Donut chart on the Preview section for the first time log in
-  Defect 16022  In Calculated field Sum (Distinct[Field]) operation fails to work and user defined functions with multiple input parameters are not working properly
-  Defect 14288  System shows error msg: "At least one grouping field is required due to filter has aggreated function." when user creates 1 aggregated CF and adds it to filter and report container 

v2.0.1
~~~~~~~

FIXES
^^^^^
-  Defect 16251  Lookup key is passing an empty value to stored proc input parameters when set in the data model
-  Defect 16248  Tenant Level Users with Full Report and Dashboard access can change Global Category Names
-  Defect 15905  Simple Gauge Unit Label includes leading spaces and is cutting off the value prior to 10 characters
-  Defect 16103  White Spaces are not trimmed in certain data types causing issues in matching data
-  Defect 15883  System shows deleted Key Join when users changes data in relationship and user cannot navigate to Fields screen
-  Defect 15395  System reverts the default value on Date&Time values on key joins when user navigates from Field to Data Source Tab
-  Defect 15304  Custom Formats added cause errors in charts and gauges when applied

v2.0.0
~~~~~~~
BREAKING CHANGES
^^^^^^^^^^^^^^^^
|  API Request - added additional header "Selected Tenant" for Global Reports. This change is already made in the webconfig in the build for download.
|  Please ensure you are using the latest version of the Copy Console which is available with this download 
|  


FEATURES
^^^^^^^^
-  Lazy Loading added for Report and Dashboard List 
-  Performance Improvements made for rendering of report parts (Chart, Map, Gauge)
-  Global Reports - Allows System Administrators to create reports at the System Level and share among all tenants based on role and connection string mapping. Please see user guide :doc:`/ui/doc_global_report_setup` 

   These changes impact how report definitions are stored. Global reports are always stored at the system level, but can be shared with tenants. The mapping for the connection strings, done in the data model, is used to tell Izenda which connection string the report is running against. This mapping is databse to database or schema to schema with the assumption that the same tables/view/stored procedures exsit in the mapped connection string. If any elements are missing the report will not display at the tenant level. 

.. warning::

   Global reports cannot be copied using the Copy Management UI. By definition, Global reports are meant to be shared across the tenant base to reduce the number of report definitions required for reports that all tenant can use. The copy console does not block copying Global reports to a tenant, and we are working on a patch to restrict this. Please note that doing this will cause unintended behavior and therefore should not be done. A feature is planned for a later release to add support for copying Global Reports from one System level to another for independent Izenda configuration databases, for now please do not copy Global reports using the Copy Console.
   
   Known issue: Tenant users with Full Report and Dashboard access can alter Global Category names. 

   
   

FIXES
^^^^^
-  Defect 13981 Blank error message shows after moving some joins containing additional key joins in report designer
-  Defect 14316 Adding additional error messages to issues with Connection String
-  Defect 14681 In Time Period Filter Displays as Undefined in Filter Description
-  Defect 15057 Oracle showing errors when gradually moving more than 1000 data sources to Available Data Sources 
-  Defect 15075 Copying Reports with an Aliased Join causes errors in destination when viewing report
-  Defect 15096 Title of Border Settings popup on report designer grid is inconsistent with other report parts 
-  Defect 15227 Select data on Join Field/Field of Key Join, system resets Key Join operators automatically
-  Defect 15268 Exported file of chart/gauge does not display depending on query limit
-  Defect 15269 Field Column Group should be removed for field in Values container in Pivot grid
-  Defect 15270 Field properties for Subreport, Icon drop-down should display the first icon the same way is is shown in Custom URL/ Embedded JavaScript Settings popup, instead of empty
-  Defect 15283 System shows "No changes found" when user changes the Join operators of Key Join and click Save
-  Defect 15301 In Oracle an error is occuring when moving datasources containing some datetime format fields
-  Defect 15324 In Single Tenant Mode System does not show Template/Report in Uncategorized list on LEFT nav or on the content panel
-  Defect 15325 System does not show Uncategorized list on LEFT nav on Report List page
-  Defect 15326 Remove Value operators for DateTime/Time field on Key Join
-  Defect 15331 User should be set default for date format field when user set up via api with dateFormat = null
-  Defect 15336 Line border of the grid is removed after user removes the key Join
-  Defect 15337 List items in Data Object/Foreign Data Object is displayed incorrectly on Key Join. Items are included which should not be and are not included in the join
-  Defect 15339 System shows no information msg after moving 1 report. Blank page is displayed on content page when user clicks on Close button.
-  Defect 15364 In Map General error message shows when drilling down to country level
-  Defect 15371 Filter field displays incorrectly data value when enter URL case sensitive
-  Defect 15434 [All] value should be removed when single radio button is selected
-  Defect 15436 Filter showing  "No record found" when using Equivalent - Tree (Not equal)
-  Defect 15440 Using Cross Database Join with Additional join types System shows error msg when multi data sources join each other and have/not have key join
-  Defect 15445 Text box for additional join condition is not rendered if data sources are not categorized
-  Defect 15449 Page freezes when saving the report at the full screen mode.
-  Defect 15454 User cannot save report template without selected data source in middle panel
-  Defect 15467 Error displayed in some subreport field mappings "Can't resolve data for fields <field name>" and the subreport cannot be opened
-  Defect 15474 User can not open Calculated Field pop up to create a CF
-  Defect 15495 Users with Full Report and Dashboard Access are not shown new categories when created by system admin
-  Defect 15500 Error showing when user tries to go to the datasource tab and report is not finished loading
-  Defect 15501 Updated wording of language change message to user in profile from "new lanugage will be effected next login." to "The new language will be applied after your next login."
-  Defect 15504 Resize text box containing the page number to show entire number for larger data sets
-  Defect 15521 Hovering on Chart shows Field name instead of Separator name when only 1 value is present in the data set
-  Defect 15537 Join Alias should be selected in the Key Join > Data Object Dropdown List (Left side)
-  Defect 15568 Using Form User can not open Sub Report via Link setting
-  Defect 15649 Running copy Dashboard which contains report haing inherit filter, system shows blank page on the destination dashboard
-  Defect 15658 Dashboard is blank and other page can not be loaded when user update common filter in report
-  Defect 15682 The content of report list page is empty after user clicks Close button from report viewer page
-  Defect 15687 Schedule tab displays in error in Global report when refreshing the page at system level
-  Defect 15694 In Report List the arrow icon doesn't change when user expands or collapses category/subcatgory 
-  Defect 15702 In some cases after finishing workflow uUser cannot logout system
-  Defect 15742 Redundant component on Key Join when Join operator is NULL/NOT NULL/TRUE/FALSE, user can not navigate to Fields screen
-  Defect 15806 Data is not displayed on Sub Report as pop up / Link / New Link Window/ Embedded
-  Defect 15832 No record found return on report selection list of subreport dropdown
-  Defect 15859 Permission for Tenant License is cached when user logins by Tenant before then login as admin user
-  Defect 15868 When user clicks cancel on report list load 2 times page will not load
-  Defect 15890 In Report Designer using Key join list of items in Data Object/Foreign Data Object is displayed incorrectly after un-select/select data source on middle Panel
-  Defect 15893 Select Alias for Key Join, system shows blank drop down list and marks "...." in the Join Field
-  Defect 15897 Stored procedure does not work after adding value to the input parameter. This is due to removal of temp table
-  Defect 15974 When chaning Sort by on Report & Dashboard List page page is blank
-  Defect 15458 Print Funtionality Not workign in Angular 2 Sample Starter Kit. Due to URL encoding. Setting suupport added to Izenda_Config.js file, when using Angular 2 kit add the following setting to the config file: At the same level with TimeOut, NeedToEncodeUrl:False.
-  Defect 15523 Pagination Performance improvement for MSSQL server


v1.25.4
~~~~~~~

FIXES
^^^^^
-  Defect 15875 Dynamic Supplementary KPI is not shown on gauge after saving report
-  Defect 15873 Stacked Bar Chart fails to render when using separator and selected color values
-  Defect 15878 Exporting fails for some gauges and charts 
-  Defect 15908 Update Languages - The two language options provided in the base application are being removed. The new language pack can be accessed on a public GitHub repo `here <https://github.com/Izenda7Series/LanguagePacks>`__ with full installation instructions
-  Defect 15910 Scheduler popup locks when attempting to add user as recipient
-  Defect 15911 When using hidden filters, some field mappings are not properly passed to subreports
-  Defect 15874 Horizontal Grid does not render proper field formats


v1.25.3
~~~~~~~

FIXES
^^^^^
-  Defect 15570 When copying reports with subreports and a dashboard the subreport links do not show up in destination
-  Defect 15571 Data Setup > Connection String: SQL Injection issue noted for MySQL
-  Defect 15595 Tree filter is not displaying values when inherited from top level report
-  Defect 15640 Filters do not load for dashboard when copying reports after copying dashboard is separate copy workspace
-  Defect 15660 Oracle Issues in 12C as Izenda Configuration Database Inconsistent Data types error
-  Defect 15683 Value in Tree Filter of Dashboard is duplicated when using with Custom DLL

v1.25.2
~~~~~~~

FIXES
^^^^^
-  Defect 15498 In integrated and stand alone mode hidden filters are showing in the report designer and the viewer report is saved when new calculated field is added
-  Defect 15499 Reports copied with copy console show broken relationship screen in the report designer
-  Defect 15520 When copying a report with join alias and filter field from aliased table report errors in detination
-  Defect 15397 Cannot Create Sub-Report Mapping on Calculated Field

v1.25.1
~~~~~~~

FIXES
^^^^^
-  Defect 15457 When using a date/time field on the x axis and a separator the chart fails to render	

v1.25.0
~~~~~~~

BREAKING CHANGES
^^^^^^^^^^^^^^^^
-  For integrations using deployment mode 1 (Front End Integrated and Back End Standalone) you must update the Izenda System Settings table. The following Settings must contain the full URL including the base address AuthValidateAccessTokenUrl and AuthGetAccessTokenUrl. These would have been relative paths prior and now must be the full url including the base url.

FEATURES
^^^^^^^^
-  Additional Join Functionality with key join allows setting a comparison to another field, null, not null or a value which can be entered manually by the user. This can be used by any user with access to joins in the report designer. Currently this feature cannot be used in cross database joins. This will be implemented later with an additional option for an in comparison. 
-  Property Panel changes for simple data source users (users without ability to add joins in report designer) to show less options by default in the property panels of the report designer and the quick edit mode. The uer can still access the features using the More option on the property panel. Users with full access can select Less option to see less options in the property panels as well.		
-  Improve rendering performance of report parts Form	
-  Apply lazy loading for Popup, Combo Box, Dropdown to improve performance	
-  Add Ability for user to add more than one field at a time in the report designer or quick add mode. Using the + symbol or the link to add field from report part.		
-  Users can now use PostgreSQL functions as stored procedures. All functions which return a set are added as stored procedures 	
-  Added new filter operators for date time fields. Now a date, date time or time only option are provided	
-  Added context menu to dashboard tile so the user can flip the tile using the context menu like the report part tiles	
-  Property panel items with gear icons to show additional setting options now show the green check box when used and also display a red X to remove the additional settings and reset back to default state	
-  Added options to the Render Report API to show/hide navigation, filter panel and toolbar	
-  New Javascript API added to update results for Dashboard, Report and Report Parts 	
-  Exporting will now always export all records to the export limit or the limit set by each report part in the report designer
-  Performance enhancement when exporting to PDF with 10k records 	

FIXES
^^^^^
-  Defect 7470 Column Group for grid is not displaying in the report
-  Defect 13079 User must scroll to the bottom of the report body to get to the horizontal scroll bar due to extra vertical scroll bar
-  Defect 13255 Missing line breaks after {dashboard Link} text in schedule's email body.
-  Defect 13300 Null and Blank values are displayed as Undefined Value in Charts and Gauges
-  Defect 13457 Some areas of the application are referring to templates as reports ("Example Report Name") 
-  Defect 13575 The list of fields of a data source is sorted incorrectly when "Sort Column Name" flag is turned on in data model
-  Defect 13800 Introduction text is not refreshed for system admins when switching between system and tenant on report designer
-  Defect 13858 After saving a report containing subreport with icon style selected, system is reverting to link style
-  Defect 13935 When user selects home or end key in some input text fields a numeric is displaying in the text box
-  Defect 13953 Removed the [] brackets from custom functions used in the calculated fields
-  Defect 14002 When using multiple Grand total lines some lines display a "0" where there should be no value
-  Defect 14012 User cannot un-sort the Funnel chart labels
-  Defect 14014 Sort icons are still appearing on some chart when the value should not be sortable
-  Defect 14018 Separators for Funnel charts are still allowing an unsorted view and should always be sorted
-  Defect 14039 Add new Field indicator is not removed on Data Model page when user clicks on save button for newly added stored procedures
-  Defect 14136 Timezone offsets for data and time stamps not working properly
-  Defect 14181 Reduce margin of Linear Gauge to make them larger and use the space provided
-  Defect 14227 Build a chart with multiple data sources and it fails to render preview in the XY-Plane popup setting
-  Defect 14235 Filter Sorting Does Not Work for Pop up and Checkbox & Tool Tip Is Wrong on sort icon
-  Defect 14287 If user clicks update results after adding a filter and prior to adding an operator, error message is shown for filter logic.
-  Defect 14298 Missing Loading progress bar when user changes Preview Records in View Mode/Quick Edit Mode
-  Defect 14302 Header format color changes the sort arrow color 
-  Defect 14303 After adding a format to a field if the user selects none, the data remains formatted
-  Defect 14345 Label text is displayed incorrectly for Roles in copy management screen when selected for copy
-  Defect 14656 Save notification showing when user has just saved and clicked on Report Viewer
-  Defect 14657 Separator used in chart showing incorrect data on hover, shows all items not just the one grouping being hovered on.
-  Defect 14676 Custom URL will not work in some cases, the field value is not passed in the url only the reference as {fieldname}
-  Defect 14691 In Filter Equivalence missing scrollbar for checkbox type and not limit number of items to show
-  Defect 14738 Stored Procedure Parameter Filters do not show up in the Scheduled instance Filters
-  Defect 14762 When using Equals Tree filter child nodes are not unchecked when deleting parent node
-  Defect 14778 Using Not Equals Tree Filter Unknown error message shows when updating results 
-  Defect 14793 Full access should be applied well when user checked "Full Report and Dashboard Access" checkbox in setting
-  Defect 14795 Filter ignored on report after adding one filter saving and adding another filter. Filter logic is set by system on save and should not be.
-  Defect 14798 Typing in dates for between calendar filter when user is in dd/mm/yyyy format alters date
-  Defect 14809 If user date format is not set there are errors in the users ability to see all date formats and when executing sp with date inputs
-  Defect 14824 In forms when user adds a sub total/grand total generates a new smart tag
-  Defect 14855 When changing setting level in New Dashboard, page redirect to Dashboard List
-  Defect 14881 User has full permission on Role setup cannot set role active/deactive
-  Defect 14901 List user in User pop up is blank when user creates 1 schedule/Email in Report Designer or in Dashboard 
-  Defect 14907 List user in User pop up is blank when user creates Access right for User on Report Designer or Dashboard page
-  Defect 14920  Null value is displayed instead of blank on the rows which is not configured Grand Total/Sub Total
-  Defect 14927 Tenant link is displayed on Left Nav of Setting page while System User has no role for Tenant
-  Defect 14929 The format of Grand Total value for a separator in the preview section is different from the preview result in the popup
-  Defect 14934 Tenant link is missing of Setting page while System User has full permission role for Tenant permission
-  Defect 14935 In Tenant Permissions Access section of Role Setup permission doesn't display although it is checked in Tenant Setup permission
-  Defect 14943 When two grids are side by side even with enough space to print they are not exporting
-  Defect 14944 Report with Required Filters are executing a query prior to required filters being set
-  Defect 14945 Position Index does not work for either Custom Javascript or Custom URL
-  Defect 14946 Alternating background colors (rows and columns) not working on pivots
-  Defect 14950 Export progress bar is loading forever after editing broken reports
-  Defect 14951 Search report part on Dashboard, system returns the list of No records found
-  Defect 14955 User has "Full Report and Dashboard Access" has no permission on Save/Save As/Copy/Move/Delete/Access in Report List/Report Viewer/Report Designer
-  Defect 14956 Success message does not display after clicking Save button in System Config > Report
-  Defect 14958 Tenant Setup section is still displayed on Role Setup page in single Tenant mode
-  Defect 14965 Pagination doesn't update after user have just created new report and changed Preview Records value
-  Defect 14974 Some users may experience issues when inputting dates / times in scheduler and subscriptions. 
-  Defect 14975 Embedded pages using margins throw off dropdown calculations and dropdowns appear out of alignment with the container
-  Defect 14980 System shows a null error msg when user navigates from Report Viewer to Report Designer
-  Defect 14984 Save function doesn't work when Version History's checkboxes are checked
-  Defect 15018 Newly created user does not appear in the sharing list option 
-  Defect 15021 Category highlight status fails to update after saving as
-  Defect 15026 Default bubble size on map is too large causing many data points to over lap.
-  Defect 15027 Charts with X-Axis and interval setting not allowign decimal Intervals
-  Defect 15047 Roboto Font is not properly exporting in PDF
-  Defect 15048 Between Calendar Date filter errors when only one date is used, system should validate that both dates are entered. Also error thrown when both values are removed.
-  Defect 15051 The button has a fuzzy edge redundantly in some popups (Chart Border Settings, Grid Lines Settings, Legend Settings)
-  Defect 15052 The checkbox and field in 'Data Refresh Interval Settings' popup should be aligned for consistency.
-  Defect 15055 Introduction text does not display correctly when changing settings level.
-  Defect 15058 Subtotal/ Grand total inherits the format of column above it instead of using its own format
-  Defect 15059 API request for filtered reports requiring case sensitive information (keys and guid values must be lower case)
-  Defect 15060 Special Chars in Plaintext Connection Strings Throw Errors
-  Defect 15062 Legends Don't Respect Alternative Text settings for field data
-  Defect 15063 Page freezes when moving from copy management to any other page
-  Defect 15064 All dynamic Grids are displayed blank
-  Defect 15072 Scheduler/Subscription DateTime Time Pickers Not Working in IE
-  Defect 15120 System does not hide invisible Field on Dashboard for Pivot, Drilldown, Chart, Gauge, Map
-  Defect 15122 Change notification for Provision Map Data to "The system is importing Map data into the configuration database. Please wait for the process to complete before using Maps"
-  Defect 15127 Filters do not properly align when some are set to not visible in the viewer
-  Defect 15128 Only ONE form shows if embedded multiple similar forms 
-  Defect 15129 When creating Map, cities are showing in the wrong countries
-  Defect 15154 Column group is not working in some reports
-  Defect 15155 Report is broken when user unchecks on a datasource in Report Designer and then navigates to another page without saving
-  Defect 15160 Draft saved version of existing Report is loaded to Report Designer, not the actual saved version
-  Defect 15175 Tool tip of DateTime data type is different from the original data in Grid reports
-  Defect 15176 Relationship and Key Join is missing when user navigate from Field to Data Source
-  Defect 15179 Separator expand and collapse icons are Hidden In Dashboards
-  Defect 15181 In Time Period Filter is not showing values in scheduled instance filter dropdowns
-  Defect 15186 Embedded reports only show the icon when there is repeater in form 
-  Defect 15194 Export Fails for Form stating invalid field but data is returned in the UI
-  Defect 15202 Missing scrollbar for checkbox type and not limit number of items to show
-  Defect 15209 Unable to set subtotal/grand total for the second similar field
-  Defect 15219 All property panels are at More state on entry when user is in simple data source mode
-  Defect 15222 System shows no record in Preview when user saves report having Additional join (>=) and Filter. Relationship is reset to blank on some fields in Data Sources page
-  Defect 15223 System returns incorrect Total data before and after saving when user saves report have Additional joins
-  Defect 15224 Toggle link is disable when selecting any item in dropdown list 
-  Defect 15228 System shows incorrect data when user use Operator Different (<>) on Key Join
-  Defect 15229 User can not navigate to Data Source page on existing report which has Key Join
-  Defect 15232 System shows error msg "application has unknown error" when user set negative data for Key Join value 
-  Defect 15234 No value displays in filter popup and page is freezing after closing the popup
-  Defect 15251 The Subtotal/Grand Total setting aren't removed when user clicks on their red X icon to remove
-  Defect 15255 Printed page is blank when printing report or printing a dashboard tile in dashboard
-  Defect 15258 Column Deleted after changing format in Property Panel
-  Defect 15262 Error states relationship does not exist when attempting to edit report and system will not allow user back to data source tab
-  Defect 15264 Field Positions are duplicated causing report to error
-  Defect 15265 Text color and Cell color don't show green check-box and red X icon after user added setting with Percentage Range
-  Defect 15274 Page doesn't work and the green check-box and red X icon still show after user removed settings
-  Defect 15282 Save As 1 existing report which as Key Join, the system shows the blank data on Foreign Data Object and mask with dot symbol on Field. Some other datasources are disabled.
-  Defect 15287 Incorrect Data is returned on report when user uses LEFT Join or RIGHT Join on Relationship when using key join 
-  Defect 15289 System errors scheduling with Attachment in Standalone Frontend and Embedded BackEnd
-  Defect 15342 Default Access rights are not populated correctly when user does not have access to the access tab in the report designer
-  Defect 15365 Relationship of the new added data source is removed after user saves report
-  Defect 15366 Key Join does not work when using multi datasources in PostgreSQL
-  Defect 15379 When using new Key Join Filter Operators is reset to blank. Data Object, Foreign Data Object, Join Field, Field are changed to disable field when user saves report on Data Source page
-  Defect 15415 Collation Issues, Invalid object name 'SYS.FOREIGN_KEY_COLUMNS'. When using case sensitive collation
-  Defect 15416 When the physical database names are different for source and destination the copy fails.

v1.24.5
~~~~~~~

FIXES
^^^^^
-  Defect 15310   Copy Process from Copy Console duplicating sharing permissions on reports after tenant copy
-  Defect 15341   Custom Tree Filter values appear in report designer but not in the report viewer

v1.24.4
~~~~~~~

FIXES
^^^^^
-  Defect 15183   Charts fail to email in integrated instances. The following method needs to be added in the IzendaConfig.cs class

.. code-block:: csharp

        public static void RegisterLoginLogic()
        {
            UserIntegrationConfig.GetAccessToken = (args) =>
            {
                return IzendaBoundary.IzendaTokenAuthorization.GetToken(new Models.UserInfo()
                {
                    UserName = args.UserName,
                    TenantUniqueName = args.TenantId
                });
            }
        }
        
-  Defect 15245   Error Thrown in PostgreSQL when attempting to create Izenda config database
-  Defect 15261   Data from Query is incorrect when using Left join

v1.24.3
~~~~~~~

FIXES
^^^^^
-  Defect 15130   Multiple joins in model between two tables not creating and relationship between both relationships
-  Defect 15140   Dashboard performance improvements
-  Defect 15142   Updated assembly references in the Izenda.BI.Framework

v1.24.2
~~~~~~~

FIXES
^^^^^

-  Defect 15061    After making a field not visible in the data model the field is still shown in existing reports
-  Defect 15124    Hidden Filters are showing as actual filters in subreport when filter inheritance is turned on
-  Defect 15126    Filter aliases not shown under the report filter descriptions
-  Defect 15123    System is adding joins from the tenant model to report after copy
-  Defect 15074    User can still access and design a report they are given No Access to report if it resides in a Visible Category for their role, and there is a higher scope access set (ie Everyone - Full Access)
-  Defect 15177    Hidden Filter fails if the user enters join alias for item in report designer. Documentation Updated (See IAdhocExtension, Hidden report filters)

v1.24.1
~~~~~~~

FIXES
^^^^^

-  Defect 15001 Report Render is taking a long time in the Report Viewer
-  Defect 15023 AVG function on field is truncating all decimals
-  Defect 15032 API POST request to trigger export with filter values
   not working properly. This resolves the initial issue but please note
   all values are case sensitive and GUID values for filter key must be
   lower case. Example request body below for route /api/export/pdf::

    {
     "reportID":"ff1b105c-fffc-407e-98c4-2fc17c3d79b1",
     "filters":[{
      "key" : "0d01fe9f-10ff-4b42-a8f3-b7e4f8983817",
      "value":"800"
     },
     {
      "key":"dea8ee0e-08bf-4a8f-9158-240837b26e2f",
      "value":"10250;#10248"
     }]}
     

-  Defect 15046 Updated insert process for new datasources. This is now
   batched into multiple insert statements to avoid timeout errors. A
   new setting has been added to IzendaSystemSetting table with this
   release to allow control over the number of items in each batch.
   Setting value is InsertBatchSize and default is 10000. Added setting
   to configure Command Timeout in IzendaSystemSetting table, this
   timeout is for the insert and update statements to the Configuration
   Database.
-  Defect 15024 Custom Functions defined JSON are not working, they
   require use of [] around function name which are not added in the
   expression builder. These should be auto added when selected.

v1.24.0
~~~~~~~

FEATURES
^^^^^^^^

-  Added the ability for subreports to inherit filters and their values
   from parent reports

   -  The datasources for the parent/subreport must be exactly the same
   -  The inherit filter checkbox must be checked when setting up
      subreports
   -  These filters will not have to be present on the subreport ahead
      of time

-  Added ability to create Custom In Time Period values for filters
-  Updated support for mapping fields to subreports when values are
   datetime and numeric fields
-  Extended ability for customer to add custom formats for field
   properties
-  Added setting at tenant level to add logo by tenant for header image.
   Setting is located in System Configuration > Report
-  Moved Filter Operator just under Source in Filter Property Panel for
   ease of use and visibility in the property panel
-  Added Default Filter Operators for each Datatype

   -  Date: Equivalence Equals Calendar
   -  Text: Equivalence Manual Entry
   -  Number: Equivalence Manual Entry
   -  Money: Equivalence Manual Entry
   -  Subtotal Auto Add name for subtotal so user is not required to configure a name

-  Change Filter Descriptions default should be set to off
-  Removed extra white space on back of Dashboard Tiles
-  Enhanced search feature for Reports for dashboard and subreport so
   more report results are shown on independent screen
-  Add button on Repoirt List to Navigate to Quick Edit Mode
-  In Report Viewer Hide the View mode button until the user is in quick
   edit mode
-  When navigating to edit a report in report designer user is brought
   to Fields tab not Datasource tab
-  In Role Permissions added option to select all items in each section
-  In Tenant Permissions added option to select all items in each
   section
-  Change Update Results Behavior in report designer, user is not
   required to update results for saving and when navigating to fields
   tab with proper configuration
-  Data Setup > Advanced Settings > Others: Added settings to define Common Filters for Dashboard

   -  Same field of the same data object from the same Database Schema
   -  Same field name regardless of the Database Schema or connection string
   -  Same alias name in Data Model regardless of Database Schema or connection
      string

-  Added support for Export API to accept filter and filter values
-  Remove Copy icon from the backside of report part tile and dashboard
   tile to reduce accidental copy of report part when attempting to flip
   tile. It is now only available on the front side.
-  For Charts and Gauges the items per row and pagination items can now
   be used independently
-  Changed the default size for the filter panel in all areas to default
   2 rows high instead of 3
-  Reports broken from data model changes can now be edited to remove
   fields no longer available in report designer
-  Access limits for sharing will now maintain the parent node so any
   new users to a role will be added to that sharing group by default
   when entire role is selected
-  Increased width of Tenant dropdown in the setting level to ease
   viewing the tenant being selected

FIXES
^^^^^

-  Defect 13990 Label height is inconsistent for filter control boxes in
   the report viewer based in filter control type
-  Defect 14006 When using $/100 format in the sub/grand total the
   preview of the sub/grand total is not displaying properly even when
   actual total is formatted
-  Defect 14020 System missing validated indicator on Connection String
   level when user does not create mapping for these connection strings
-  Defect 14024 Grand Total value for a separator is calculated
   differently in the preview section compared to the preview result in
   the popup for the Grand Total Field
-  Defect 14029 Roles with no access to Functions (not moved to visible
   for this role) can use them in the report designer field function
   dropdown
-  Defect 14031 If report or dashboard was saved with sharing access for
   a role or user will not save change to share with everyone
-  Defect 14035 Missing background color for fields added into Visual
   tab of form designer
-  Defect 14042 Some date time formats are not displaying correctly for
   Grand totals
-  Defect 14124 Subscribe option should not be shown to users with Save
   As access to dashboard, as user has permissions to schedule
-  Defect 14125 View Mode button in the report viewer is showing
   progress bar when clicked and still disabled
-  Defect 14176 Settings Level should be disabled when user is in my
   profile area of application
-  Defect 14177 Source and Destination trees are hidden after clicking
   Validate in Data Advanced Options screen
-  Defect 14186 When using alternating row colors, PDF export is
   different than what is on the screen
-  Defect 14203 Need space between radio button and labels 'Linear' /
   'Value'
-  Defect 14207 Intervals are not presented when user switches back old
   X-axis Type
-  Defect 13501 Currently the system is missing Help indicator in
   following places in Copy Management Mapping areas (In All Mappings,
   in Merge Duplicated Mappings, and in Object Label of To area)
-  Defect 13504 Mapping area in Main page: System variable TenantName
   does not work
-  Defect 13505 The system does not have the checkbox "Merge Duplicate
   Mappings" in Advanced Copy Options page of Copy Management
-  Defect 13523 In Role Setup Tenant Setup anchor link still displays in
   Permissions page for setting level = tenant
-  Defect 13599 In Dashboard list the subcategory does not remain
   expanded when user opens report from list
-  Defect 13655 "There are no records returned" error raised when
   configuring subtotal for a field of a table having data
-  Defect 13775 Link and icons should be removed from report if
   subreport is not copied with report in destination.
-  Defect 13859 Suggested data type is not changed when user changes the
   field in the calculated field expression text box
-  Defect 13868 Fields of newly added stored procedures are not selected
   by default while the Advanced Settings> Set Additive Field Auto
   Visible/Filterable are checked
-  Defect 13876 Subcategory is not displaying when added again after
   deleting
-  Defect 13908 Tool tip error message for Query Limit, Field Limit and
   Pivot Column Limit still show reference to Data Source Limit when set
   to an unsupported number like -1
-  Defect 14216 Missing horizontal scrollbar on popup of subreport when
   needed
-  Defect 14224 X-Axis updates incorrectly when user changes value of
   Interval in XY-Plane settings
-  Defect 14233 After building a report with one report part and saving,
   if deleted without save and moving to the viewer will cause error
-  Defect 14234 General error message shows when copying a
   report/dashboard with deleted report part.
-  Defect 14306 Null value on chart X axis takes name of total label
-  Defect 14761 Using Oracle error message is shown when user selects
   Function = Group Days Old for Date field in Report Container
-  Defect 14774 General error message shows when changing a UserID
-  Defect 14802 Sub report data fails to load when using popup and form
-  Defect 14807 Close button does not work when user clicks on Report
   Name in Report List then clicks on Open button to open the Report
   Viewer
-  Defect 14808 The "Link/this icon was configured to show in other
   settings (Sub-report/Custom URL/ Embedded Javascript). Please select
   the other ones" warning is displayed when user sets both Custom URL
   and Embedded Javascript
-  Defect 14812 Page continues to load if ENTER is clicked to close the
   generate password successful popup.
-  Defect 14815 Sharing record temporarily dismisses when saving then
   updating result.
-  Defect 14867 The "There is no relationship(s) among the following
   data objects. Please manually unselect them or creat relationship for
   them...." message is displayed when user clicks Data Source icon from
   Field tab page
-  Defect 14890 Responsive - Change mobile mode from 1280 to 1024
-  Defect 14933 Unable to go to fields page when selecting another data
   objects from Datasource page
-  Defect 14938 Function for applying Format on DateTime Field does not
   works with Group or without Group function
-  Defect 14940 Unable to export pivot grid
-  Defect 14961 System shows error msg when user open Sub Report while
   Master = Data of Week, Sub Report = Group Date & Time
-  Defect 14963 System shows "No record found" when user opens Sub
   Report while Master = M/d/yy or Week Number, Sub Report = Date of
   Week
-  Defect 14967 System returns incorrect "Day of Week" on Sub Report
   while Master and Sub Report is build from the same table in the same
   Connection String
-  Defect 14978 System shows error msg when user updates Report
   Properties/Field Properties and then changes the report from Front
   side to Back side
-  Defect 14242 Page continues to load when deleting a CF then turning
   to front side of Form
-  Defect 14277 In Oracle cannot add SP to Visible Data Sources
-  Defect 14295 Clicking report name expands report info and should not,
   should take the user to the report viewer directly without this step
-  Defect 14894 Format for page numbers in header and footer do not
   change
-  Defect 14659 PDF Exports are scaling smaller even when printed
   columns per page on.
-  Defect 14672 When export types are disabled at the tenant level
   giving user full report and dashboard access is still showing these
   options
-  Defect 14674 Filter Operator In Time Period showing "Undefined" on
   Dashboard when not a common filter
-  Defect 14679 Gauge pagination is showing when turned off after any
   configuration change to the gauge. It can be turned on and off again
   and will be removed but it must be done after each change.
-  Defect 14228 ReactJS loads twice when integrating with another
   ReactJS app
-  Defect 13925 Out of memory errors occurring when validating many
   tenants using copy function for data model or reports.
-  Defect 14215 Pivot grids do not render columns where all values are 0

v1.23.2
~~~~~~~

FIXES
^^^^^

-  Defect 14771 Cross-Database Issues with Izenda configuration Database
-  Defect 14724 When grouping a date field and changing the format some
   dates are appearing out of order
-  Defect 14727 Setting up the custom tree filter when parent node is
   checked all child elements should be selected
-  Defect 14737 In Time period filter causing errors and report & query
   will not export
-  Defect 14751 MySQL errors logged in accessing report & dashboard
   categories
-  Defect 14794 Tree Filter is adding each list multiple times in
   dashboard when common filter
-  Defect 14698 Error is shown when attempting to use a between date
   filter for any date values in Oracle

v1.23.1
~~~~~~~

FIXES
^^^^^

-  Defect 14690 Simple style gauge is not exporting from standalone
   environments.
-  Defect 14682 Oracle 12c giving errors on inconsistent datatypes of
   CLOB.
-  Defect 14671 Filter aliases not being displayed in the report viewer.
-  Defect 14680 Filter query fails in some cases where certain special
   characters are used in the field name. Fields with aliases in the
   data model may fail in expressions when used with an expression and
   field in the same report.
-  Defect 14685 Authorization error preventing exporting in integrated
   environments.

v1.23.0 (GA)
~~~~~~~~~~~~

FEATURES
^^^^^^^^

-  The Copy Console Utility is now available. This utility can copy
   reports, dashboards, etc to separate API instances

FIXES
^^^^^

-  Defect 14297 Tenants and Roles with access to all report part types
   could only see grids in integrated modes.
-  Defect 14296 A report's QuerySourceId as set to 0 after being copied
   via the copy management console application
-  Defect 14240 Javascript API was unable to set a new locale in a
   standalone deployment
-  Defect 14238 Stored Procedure Lookup Key/Value Inputs did not
   Properly Convert Int Input to Text
-  Defect 14229 Using Calculated Fields as a Filter would return no data
-  Defect 14214 Pivot Grids would not allow for the same field to be
   used as a row and value
-  Defect 14210 Fields with an image data type would not render
-  Defect 14209 Drilldown grids would expand shortly after closing when
   subtotals were applied; subtotals would lose their aggregate metric
   when collapsed
-  Defect 14208 Platform crashes when pulling back reports with large
   record sets (10K/30K)
-  Defect 14109 PostgreSQL input arguments do not carry through to the
   Function area of the data model
-  Defect 14319 Revised UI Grammatical and Spelling Errors
-  Defect 14317 Calculated field queries would identify the wrong field
   to be used for grouping
-  Defect 14318 Users with Full Report and Dashboard Access could not
   save reports that contained report part types they weren't explicity
   granted access to.

