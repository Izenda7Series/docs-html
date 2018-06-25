===============================
Subreports
===============================

| Subreports in Izenda are utilized to navigate to a separate, or sub, report. Utilizing various methods, the content of the subreport can be narrowed down based on context of the main report.
| For visualizing and exploring related data without leaving a single report, see :doc:`Drill Downs <./doc_drilldown>`.
| 


Creating An Initial Subreport
----------------------------

- In order to create a reference from a main report to a subreport, a separate report must first be created to link to. For this example, a grid report containing all relevant data has been generated.

.. figure:: /_static/images/subreports/sample_grid.PNG

      Complete Data Report

- Once the data grid has been prepared, a main report displaying less content, but potentially more relevant data, has been created. It is from this report, the subreport will be called.

.. figure:: /_static/images/subreports/main_report.PNG

      Main Report

- In the main report, it is now possible to associate a field to reference the data subreport. This is accomplished by clicking on the gear icon next to "Sub Report" in the Field Properties tab.

.. figure:: /_static/images/subreports/subreport_icon.png

      Subreport Icon

- The Sub Report gear icon will open up the Subreport Settings dialog box. In this window all the specifications for the subreport will be configured. Clicking on the magnifying glass in the upper left corner will open the Report Selection window.

.. figure:: /_static/images/subreports/subreport_dialog_box.PNG

      Subreport Dialog Box

- The Report Selection window allows for searching potential subreports based on a set of criteria. These search parameters can include categories, partial report names, creator, last editor, as well as created and last edited dates.

.. figure:: /_static/images/subreports/subreport_selection_search.PNG

      Subreport Search Dialog Box

- Once the desired report has been selected for use as a subreport, it's title will appear in the Reports search box.

.. figure:: /_static/images/subreports/subreport_selected.png

      Subreport Selected

- Click "OK" will close the Subreport Settings dialog box. The main report now has the field associated with the subreport as a link. Now clicking on any of the ShipCountry values will navigate to the data report originally created.

.. figure:: /_static/images/subreports/subreport_ready.PNG

      Main Report with Associated Subreport





Inherit Filters
----------------
While opening other whole reports as a subreport is useful, being able to open a subreport with data parsed down corresponding to the main report can provide more relevant and practical.
One method of passing data from a main report to a subreport is through the inheriting of filter values.

- The first step for this method is to apply a filter to the main report. In this example, a filter of ShipCountry = Argentina has been configured. The main report thus only displays countries and cities corresponding to Argentina.

.. figure:: /_static/images/subreports/applied_filter.PNG

      Filtered Main Report

- The next step is to enter the Subreport Settings dialog via the gear icon again. From here, check the option for "Subreport's filters inherit filters from current report". Clicking "OK" will close the dialog box and apply the changes.

.. figure:: /_static/images/subreports/inherit_filter_checked.png

      Subreport Settings Dialog Box w/ Inherit Filters

- From the main report, clicking on the ShipCountry value of Argentina now navigates to the data report displaying only content relevant to Argentina.

.. figure:: /_static/images/subreports/sample_grid_filtered.PNG

      Subreport Filtered Based on Main Report's Filter

Field Mappings
--------------

The second method for passing data from a main report to a subreport is by applying a Field Mapping.

- The first step for this method is to apply the desired field mapping. Under the Subreport Settings dialog window, click "Add Field Mapping" at the bottom. This creates an association that only displays data from the subreport that matches the value clicked on in the main report. Clicking "OK" saves the settings and returns to the main report.

.. figure:: /_static/images/subreports/field_map.PNG

      Subreport Settings Dialog Box w/ Field Mapping

- The main report now appears with the new field mapping applied and without a filter configured.

.. figure:: /_static/images/subreports/no_filter_main_report.PNG

      Non-filtered Main Report w/ Field Mapping

- Clicking on a ShipCountry value, such as France, will navigate to the data subreport and render only content corresponding to France.

.. figure:: /_static/images/subreports/sample_grid_mapped.PNG

      Subreport Data Narrowed Based on Field Mapping

Subreport Access Options
-----------------------

- By default, subreports are opened in a new web browser window. This enables users to switch back and forth between windows containing the original and subreports for comparision. As alternatives, the Link options navigates to the subreport in the current web broswer window. The Embedded option renders the entire subreport inside the cell of the main report. Finally, the Popup method opens the subreport in a dialog box, over top of the current web browser window.

.. figure:: /_static/images/subreports/style_options.PNG

      Display Style Options

- Instead of having the subreport available by clicking on the data value in the main report, Izenda provides the option of generating an icon in front of the data value. This navigation can be represented by a number of built in icon images.

.. figure:: /_static/images/subreports/icon_options.PNG

      Subreport Icon Options
