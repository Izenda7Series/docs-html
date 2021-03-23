

===============================
System Configuration/Report
===============================

The **System Configuration/Report** page allows user to:

-  configure Report Version History feature
-  set a default background image for report header, for each tenant.
-  customize the names for "Global Categories" and "Local Categories" in a multi-tenant system (see :doc:`/ui/doc_global_report_setup`).

Configure Report Version History
----------------------------------

#. In browser, log in to Izenda as a user with System Configuration
   permission.
#. The Setting Level must be System.

*  Untick the Enforce Version History check-box will disable Report Version and remove all version history.
*  Change the maximum number of versions per report in "No. archived versions to keep" box.

   .. note::

      The existing report versions that exceed this number are not removed. Setting this number only limits future report versions.

*  Click the Clear Archived Versions Now button at the top will remove all current version history but still keep tracking versions.
*  To use a schedule to remove all current version history, tick the Remove Archived Versions check-box then set up the time and recurrence.

.. figure:: /_static/images/System_Configuration_Report_Version.png
   :width: 792px

   Report Version History Configuration

Set Default Header Image
----------------------------------

#. In browser, log in to Izenda as a user with System Configuration
   permission.
#. Click Settings, then System Configuration then Report in the left
   menu.
#. Select the Setting Level: either System or a specific tenant.
#. In Default Header Image section, enter a relative path or the full url to the image.

   *  Sample relative path in web server box: ``/images/contoso.png``
   *  Sample full url: ``http://image.google.com/contoso.png``

#. Click Save button at the top.

.. _Customize_the_names_for_Global_Categories_and_Local_Categories:

Customize the names for "Global Categories" and "Local Categories"
--------------------------------------------------------------------

#. In browser, log in to Izenda as a user with System Configuration
   permission.
#. The Setting Level must be System.
#. Change the names in Global Name and Local Name boxes.
#. Click Save button at the top.

.. figure:: /_static/images/Customize_Global_And_Local_Names.png
   :width: 792px

.. _Set_Default_Color_Theme:

Set Default Color Theme for Chart, Gauge, and Map
---------------------------------------------------
   .. figure:: /_static/images/Customize_Color_Pallete_Selection_Popup.PNG
      :width: 604px
      :align: right

   #. In browser, log in to Izenda as a System Admin.
   #. Click Settings, then System Configuration then Report on the left
      menu.
   #. Select the Setting Level: either System or a specific tenant.
   #. In Default Color Theme for Chart, Gauge, and Map section, click gear icon
   #. Choose any theme then click OK to close Default Color Theme Selection popup. |br|
   #. **Once a default is set all existing reports and dashboards using charts will assume the new default color theme for that setting level. This can be configured at the report level by editing the report and selecting a new theme or no theme.** |br|
   #. When a default is set, all new charts, gauges and maps will use the default for that setting level unless the user selects a different theme or No Theme. |br|
   #. Global reports when set to use the System default, will show in the tenant level using the Tenant's default. If no default is set for the tenant the System default will be used at the tenant level. |br|
   #. Report level settings are the highest priority for themes, so any theme other than the default set for a report will be the theme used. |br|  
   #. Field level settings for color values will work with color themes, taking higher priority than the default or selected themes. |br|

.. note::

   * The preview limitation for the number of colors in each theme is 12. In case :ref:`the color theme file <Color_Theme_File>` exceeds this, system will load and populate the first 12 colors.
   * When a theme has invalid color(s), the system will ignore and load the others.
   * See Guide here for creating a custom :ref:`color theme file <Color_Theme_File>`.

   
Global Reports and Default Themes 
----------------------------------
   * Please see the grid below to understand how themes work with Global Reports and Dashboards. 
   
.. list-table::
   :widths: 15 15 15 15 40
   :header-rows: 1
   
   * - Default Theme in System Level 
     - Default Theme in Tenant Level
     - Theme Used in Global Report
     - Theme Seen in Tenant Level
     - Notes 
   * - A 
     - B 
     - No Theme 
     - No Theme
     - Theme A is set as system default and B is set as Tenant default but Global report creator **chose No Theme to override defaults**	 
   * - A 
     - B 
     - A 
     - B 
     - Theme A is set as system default and B is as Tenant default and Global report creator **left default theme** so tenant user will see thier default
   * - A 
     - B 
     - B 
     - B 
     - Theme A is set as system default and B is set as Tenant default but Global report creator **chose theme B to override defaults** 
   * - No Theme
     - B
     - No Theme
     - B
     - No Theme is set as system default and B is set as Tenant default and Global report creator **left No Theme default in report** as default so tenant will see their default
   * - No Theme
     - B
     - A
     - A
     - No Theme is set as system default and B is set as Tenant default and Global report creator **chose theme A to override defaults**
   * - A
     - No Theme
     - No Theme
     - No Theme
     - Theme A is set as system default and No Theme is set as Tenant default but Global report creator **chose No Theme to override defaults**
   * - A
     - No Theme
     - A
     - A
     - Theme A is set as system default and No Theme is set as Tenant default and Global report creator **left report as default so tenant will see System Default**
   * - A
     - No Theme
     - B
     - B
     - Theme A is set as system default and No Theme is set as Tenant default but Global report creator **chose Theme B to override defaults**
