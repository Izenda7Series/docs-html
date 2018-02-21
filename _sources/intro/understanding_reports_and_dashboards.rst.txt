================================================
Understanding Reports and Dashboards
================================================

Reports and Dashboards are the blank canvases of Izenda.

Reports vs. Dashboards
----------------------

Reports
~~~~~~~

Reports allow you to select data sources and build data visualizations
of your data in containers called *report parts.*

-  Report Parts are the smallest units of a report and allow you to
   build reports modularly with ease.
-  Report Parts are re-sizable, movable, and editable. Interaction with
   them within the Report Designer is built to be intuitive.
-  Report Parts can consist of 5 different Report Part types. These
   include Grids, Gauges, Maps, Forms, and Charts.
-  For more, see :doc:`/ui/doc_report_list`.

Dashboards
~~~~~~~~~~

Dashboards give you the ability to create a “hub” of data visualizations
for any and all users to consume. Like reports, dashboards have an
elemental container called a *tile.* Essentially these tiles act as a
collection of report parts combined into one visualization.

-  Tiles are re-sizable, movable, and editable. Interaction with them
   within the Report Designer is built to be intuitive.
-  Tiles hold a report part definition from reports that have previously
   been created.

   -  Since dashboards don't *own* any report parts, dashboards do not
      have the ability to select additional data sources.

-  For more, see :doc:`/ui/doc_dashboard_designer`.

Reports and Dashboards
----------------------

Sample Sizes
~~~~~~~~~~~~

-  Sample sizes of your data can be manipulated to allow you to design
   quickly with a small data set and display accurately with a large
   data set.

.. _Filtering:

Filtering
~~~~~~~~~

Filtering can be applied to limit the data seen in a report/dashboard. For instance, if you had a *Country* field in your data, you could filter the report/dashboard to only display data for the country of Argentina.

-  Report filtering is report-wide.

   - You cannot filter per report part or per field.
   - For more information on Report Filters, feel free to check out the :doc:`/ui/usage_adding_filters_to_a_report` documentation.

-  Dashboard filtering depends on filters applied to the included report tiles.

   -  If all tiles share the same filters, filters can be set globally.
   -  If tiles share some of the same filters but have some unique filters, unique
      filters can be set individually by flipping the tile into
      configuration mode, while common filters can still be set globally.
   -  If tiles only have unique filters, unique filters can be set
      individually by flipping the tile into configuration mode.
   - For more information on Dashboard Filters, feel free to check out the :ref:`Dashboard Filters <dashboard_filters>` documentation.


Sharing and Permissions
~~~~~~~~~~~~~~~~~~~~~~~

-  As a report/dashboard designer, you will be able to limit the
   visibility and access of your creations.

   -  By default, all reports/dashboards are shared at a role level.
   -  If a user doesn't have access to data pertaining to a particular
      dashboard tile, the tile will not display any information.
   -  There are also a number of different access rights that can be
      granted to indvidual roles and users. These include offering Full
      Access, No Access, View Only, Quick Edit, Save As, and Locked.
   -  For more, see :doc:`understanding_the_tenant_role_user_relationship`.

.. _Exporting_and_Scheduling:

Exporting and Scheduling
~~~~~~~~~~~~~~~~~~~~~~~~

-  Reports and Dashboards are exportable

   -  Izenda supports exporting to various file formats including: Word,
      Excel, PDF, XML, CSV, and JSON.

-  Reports/Dashboards can be scheduled

   -  Reports and dashboards can be exported through the Email body as a
      link, embedded, attached as an export, or saved to a file location
      as an export.
   -  For more, see :doc:`How to Schedule </ui/doc_configuration_scheduling>`.
