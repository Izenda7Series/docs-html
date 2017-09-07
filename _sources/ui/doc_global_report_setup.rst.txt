==========================
Global Report Setup Guide
==========================

.. tip::

   Global Report is available from release v2.0.0.

The Global Categories (Global Report) is a central place to share system reports/templates among all tenants. This section, categories/sub-categories and reports underneath will be visible in Report List of tenants.

Usages of Global Categories may include a category of sample reports or common reports that are shared among all tenants.

.. _Global_Report_List_ACME_user:

.. figure:: /_static/images/Global_Report_List_ACME_user.png
   :width: 765px

   Global Categories containing sample and common reports in Report List of one tenant

For the global report to display relevant data, each tenant must have a connection to the same database or one with structure similar to that of the global report. 

.. comment: need Full Report and Dashboard?

Setup Steps 
-------------------------------------

#. Set up tenants, for example ACME and Globex Online.
#. Add connection for the global report (Northwind) then add connections for tenants (ACME_Northwind and GO_Northwind).
#. Map connections of tenant to the system connection in Data Setup > Database Mapping.

   .. _Global_Report_Database_Mapping:

   .. figure:: /_static/images/Global_Report_Database_Mapping.png
      :width: 785px

      Database Mapping

#. Set up tenant roles and users that can access reports.
#. .. _Save_report_into_Global_Categories:

   .. figure:: /_static/images/Save_report_into_Global_Categories.png
      :align: right
      :width: 455px

      Save report into Global Categories

   Create the report at system level, then save it into Global Categories. |br|
#. .. _Global_Report_List_Globex_user:

   .. figure:: /_static/images/Global_Report_List_Globex_user.png
      :align: right
      :width: 765px

      Global Categories in Report List of sample tenant

   The Global Categories and global reports are visible to tenant users. |br| 

Features of Global Report 
-------------------------------------

*  Best way to share reports among tenants (using Copy Management to copy reports takes more time).
*  The Global Categories is well positioned in Left Navigation, easily accessible.
*  Report data is read from the tenant's connection only.
*  The names "Global Categories" and "Local Categories" can be aliased in :ref:`Report Setting <Customize_the_names_for_Global_Categories_and_Local_Categories>`.
*  When saving an existing report in a local system category as a global report, please note that any subreports used in the report must also be saved into global categories as well. Once this is complete the subreport links must be udpated to point to the correct global subreport as the report ids will be new in the global categories.
