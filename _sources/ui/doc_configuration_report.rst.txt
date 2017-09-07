

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
