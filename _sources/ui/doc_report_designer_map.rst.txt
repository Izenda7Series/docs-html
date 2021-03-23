

==========================
Report Designer/Map
==========================

Map is a built-in type of report part that displays data on geographic
maps, ranging from world map to continent and country maps.

Configure Report Part Properties for Map
----------------------------------------

.. _Report_Part_Properties_for_Map:

.. figure:: /_static/images/Report_Part_Properties_for_Map.png
   :align: right
   :width: 245px

   Report Part Properties for Map

#. Select the chart in Report Body (See :ref:`Manage_Report_Parts` for how to
   add a chart).
#. Click the expand icon (<) on the right to open the Properties boxes
   if needed.
#. Select the vertical Report Part Properties box.
#. The properties are listed in Report Part Properties box in 6
   sections. (:numref:`Report_Part_Properties_for_Map`)

   -  General Info
   -  Map
   -  Labels
   -  Legends
   -  Data
   -  View |br|

User can configure the properties and see changes reflected in
Preview pane:

-  Select a type in Map Type drop-down.

   -  World
   -  Continent
   -  Country

-  .. _Report_Map_Border_Settings:

   .. figure:: /_static/images/Report_Map_Border_Settings.png
      :align: right
      :width: 454px

      Map - Border Settings

   Configure border settings:

   #. In Map group, click the gear icon (⚙) to open Border Settings
      pop-up.
   #. Choose the border to be visible or not.
   #. Select a border color.
   #. Select a dash style.
   #. Select the border thickness (in pixels).
   #. Click OK to close the Border Settings pop-up. |br|

-  .. _Map_Color_Theme_Selection:

      .. figure:: /_static/images/Color_Theme_Selection.PNG
         :width: 604px
         :align: right

         Map - Color Theme Selection |br|
         
   Configure color theme settings:

   #. In Map group, click the gear icon (⚙) next to the Color Theme option to open Color Theme Selection pop-up.
   #. Select a color theme and click OK to the pop-up. 

   **Notes:**

   When System Admin change the :ref:`Default Color Setting <Set_Default_Color_Theme>`, all report parts using the default color theme will update properly. |br|

-  .. _Report_Map_Background_Color_Settings:

   .. figure:: /_static/images/Report_Map_Background_Color_Settings.png
      :align: right
      :width: 455px

      Map - Background Color

   Set the background color.

   #. In Map group, click the gear icon (⚙) to open Map Background Color
      Settings pop-up.
   #. Select a background color.
   #. Choose to apply the color to the entire map (covering the legend
      Sum(Freight)) or to the plot area only (covering the map only).
   #. Click OK to close the Map Background Color Settings pop-up. |br|

-  .. _Report_Map_Labels_Settings:

   .. figure:: /_static/images/Report_Map_Labels_Settings.png
      :align: right
      :width: 246px

      Map - Labels Settings

   Configure the text direction for the labels |br|
-  To be updated: Hover Labels
-  To be updated: Show Map Labels


-  Configure the legends.

   .. _Report_Map_Legend_Settings:

   .. figure:: /_static/images/Report_Map_Legend_Settings.png
      :width: 684px

      Map - Legend Settings

-  Choose to display values of data
   points or not.

   .. _Report_Map_Data_Show_Value_Labels:

   .. figure:: /_static/images/Report_Map_Data_Show_Value_Labels.png
      :width: 635px

      Map - Show Value Labels

-  To be updated: Zoom into a region of the map.

-  .. _Map_Report_Designer_Data_Refresh_Interval:

   .. figure:: /_static/images/Report_Designer_Data_Refresh_Interval.png
      :align: right
      :width: 455px

      Report Designer - Data Refresh Interval

   Configure how
   often data is refreshed when report is being viewed.

   #. Click the gear icon (⚙) to open Data Refresh Interval Settings
      pop-up.
   #. Choose to have data refreshed automatically or manually.
   #. Enter an interval between each refresh (in seconds).
   #. Choose to view all data or enter a number to view that specific
      number of latest records only. |br|

.. note::

   If the **Show Preview section in Configuration Mode** checkbox (In Others tab in Advanced Settings) is unticked then The Preview section will not be displayed for following pop-ups: 

      \- Map Border Settings |br|
      \- Map Background Color Settings |br|
      \- Legend Settings |br|
      \- Zoom Settings


      .. figure:: /_static/images/Report_Map_Border_Settings_No_Preview.PNG
         :align: center
         :width: 464px

         Report Designer - Chart Border Settings without Preview section |br|

   Please see :ref:`Advanced_Settings_Others` for more details.


Others
------------

.. _Report_Map_Grid_View:

-  Grid view popup option. This option is available from version 2.10.0.

   Click |gridViewIcon| icon to see the grid view of the map data associated with the current metric.

   .. figure:: /_static/images/Map_Grid_View_Popup.png
      :align: right
      :width: 653px

      Grid View Popup Showing Count(OrderID) of cities in WA |br|
      
   .. |gridViewIcon| image:: /_static/images/icons/Grid_View_Icon.png

|br|
-  Metric dropdown.

      .. figure:: /_static/images/Map_Metric_Dropdown.png
         :align: right
         :width: 308px

         Map Metric dropdown |br|

|br|

