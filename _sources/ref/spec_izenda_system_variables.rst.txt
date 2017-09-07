==================================
Izenda System Variables
==================================

System variables are placeholders that will be replaced by actual values
while being used.

General Placeholders
--------------------

General placeholders can be used anywhere in the sytem:

.. list-table::
   :widths: 15 85
   :header-rows: 1
   :stub-columns: 1

   * - Name
     - Description
   * - {reportName}
     - Replaced by the name of the report. |br| |br|
       Sample: "Sales by Year"
   * - {currentDateTime}
     - Replaced by the date and time when the report is generated. |br| |br|
       Sample: "05/09/2016 10:35:02 AM"
   * - {currentUserName}
     - Replaced by the full name of the user currently logging in the sytem, in the format <firstName> + " " + <lastName>. |br| |br|
       Sample: "John Doe"
   * - {tenantName}
     - Replaced by the name of the tenant of the user currently logging in the sytem. |br| |br|
       Sample: "ACME Corporation"
   * - {reportLink}
     - Replaced by the url of the report.. |br| |br|
       Sample: "http://127.0.0.1:8888/report/ebb003c2-d6c7-4c08-b949-4373cc9ab844"

Email-Template-specific Placeholders
------------------------------------

In addition to `General Placeholders`_, the
following are additional placeholders that can be used in Email
Templates:

.. list-table::
   :widths: 15 85
   :header-rows: 1
   :stub-columns: 1

   * - Name
     - Description
   * - {embedReportHTML}
     - Replaced by the report content in HTML format. It will be displayed correctly in any HTML-capable email client.
   * - {recipientName}
     - Replaced by the name of each recipient selected in "Recipient(s)" field, in the format <firstName> + " " + <lastName>.
   * - {currentUserName}
     - Replaced by the full name of the user currently logging in the sytem, in the format <firstName> + " " + <lastName>


Report-Formatting-specific Placeholders
---------------------------------------

In addition to `General Placeholders`_, the
following are additional placeholders that can be used in Report
Designer - Format section:

.. list-table::
   :widths: 15 85
   :header-rows: 1
   :stub-columns: 1

   * - Name
     - Description
   * - {pageNumber}
     - Replaced by the page number for each page of the report.
   * - {horizontalRule}
     - Displayed as a horizontal line on the report.
   * - {verticalRule}
     - Displayed as a vertical line on the report.
