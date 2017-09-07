

==========================
Report Designer/Gauge
==========================

Gauge is a built-in type of report part that displays data using a
speedometer.

Define a Linear Gauge
---------------------

.. _Gauge_Properties:

.. figure:: /_static/images/Gauge_Properties.png
   :align: right
   :width: 251px

   Report Designer - Gauge Properties

#. Select the chart in Report Body (See :ref:`Manage_Report_Parts` for how to
   add a chart).
#. Click the expand icon (<) on the right to open the Properties boxes
   if needed.
#. Select the vertical Report Part Properties box.
#. The properties are listed in Report Part Properties box in these
   sections. (:numref:`Gauge_Properties`)

   -  General Info
   -  Gauge
   -  Grouping
   -  View
   -  Printing |br|

User can configure the properties and see changes reflected in
Preview pane:

-  Select Linear Gauge in Gauge Type drop-down. (See below for Solid
   Gauge and Simple Gauge.)

-  .. _Gauge_Border_Settings:

   .. figure:: /_static/images/Gauge_Border_Settings.png
      :align: right
      :width: 458px

      Report Designer - Gauge Border Settings

   Configure border settings:

   #. In Gauge group, click the gear icon (⚙) to open Gauge Border Settings pop-up.
   #. Choose the border to be visible or not.
   #. Select a border color.
   #. Select the border thickness (in pixels).
   #. Click OK to close the Border Settings pop-up. |br|

-  Customize the relative distance between the tick marks (in Intervals
   box for Linear Gauge only).
-  Select to use Separator. (See `Define
   Separator`_)
-  It looks better to invert the Linear Gauge (to horizontal direction).
-  .. _Gauge_Data_Refresh_Interval_Settings:

   .. figure:: /_static/images/Gauge_Data_Refresh_Interval_Settings.png
      :align: right
      :width: 460px

      Report Designer - Gauge Data Refresh Interval Settings

   Configure Data Refresh Interval if needed. |br|
-  Optionally display a long report in multiple pages.
-  Optionally choose to print each grid in a new page by checking Page
   Break After Separator in Printing group.

.. _NW_Orders_Linear_Gauge_Sum(Freight)_Group(ShipCity):

.. figure:: /_static/images/NW_Orders_Linear_Gauge_Sum(Freight)_Group(ShipCity).png
   :width: 950px

   Northwind Orders Linear Gauge

To define the above sample gauge:

#. Select Northwind Orders table in Data Source.
#. Add a gauge report part and select Linear Gauge as the type.
#. Add [ShipCity] to Labels (X-axis) box, it will show up as
   Group(ShipCity).
#. Click Add Metrics to create Metrics 1.
#. Add [Freight] to Value box, it will show up as Sum(Freight).
#. Optionally set the threshold values like following:

.. _NW_Orders_Linear_Gauge_Sum(Freight)_Group(ShipCity)_Threshold:

.. figure:: /_static/images/NW_Orders_Linear_Gauge_Sum(Freight)_Group(ShipCity)_Threshold.png
   :width: 950px

   Northwind Orders Line Gauge with Threshold

Screenshot for Dynamic Threshold to be updated.

Define Separator
----------------

The Separator option displays multiple sections of gauges according to
each unique value of the field(s) defined in Separators box.

For example: this report with multiple gauges, each one for each country in
Northwind Orders table.

.. _NW_Orders_Gauge_Separator_ShipCountry_Sum(Freight)_Group(ShipCity):

.. figure:: /_static/images/NW_Orders_Gauge_Separator_ShipCountry_Sum(Freight)_Group(ShipCity).png
   :width: 950px

   Northwind Orders Gauge with ShipCountry Separator

#. Tick Use Separator check-box in Grouping in Report Part Properties to
   see Separators box inside the gauge configuration.
#. Add [ShipCity] to Labels (X-axis) box, it will show up as
   Group(ShipCity).
#. Click Add Metrics to create Metrics 1.
#. Add [Freight] to Value box, it will show up as Sum(Freight).
#. Add [ShipCountry] to Separators box, it will show up as
   Group(ShipCountry).

Define a Solid Gauge
--------------------

#. Select Solid Gauge in Gauge Type drop-down.
#. The rest of the properties are similar to Linear Gauge.

An example solid gauge with separator and threshold:

.. _NW_Orders_Gauge_Separator_ShipCountry_Sum(Freight)_Group(ShipCity)_Threshold:

.. figure:: /_static/images/NW_Orders_Gauge_Separator_ShipCountry_Sum(Freight)_Group(ShipCity)_Threshold.png
   :width: 950px

   Northwind Orders Gauge with ShipCountry Separator and Threshold

.. _Report_Simple_Gauge:

.. figure:: /_static/images/Report_Simple_Gauge.png
   :align: right
   :width: 350px

   Sample Simple Gauge

Sample Simple Gauge. |br|
