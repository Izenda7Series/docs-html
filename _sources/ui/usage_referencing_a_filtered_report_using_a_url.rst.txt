
==========================================
Referencing A Filtered Report Using A URL
==========================================

Izenda gives users the ability to reference a filtered reports using a
URL.

Common Use Cases Include:

*  Creating a generic invoice with a "Case Number" filter to display
   information unique to a particular invoice
*  Referencing a subreport with filtered information

Setup
-----

In the following example, we've created a simple table using Country,
City, And Ship Address.

.. figure:: /_static/images/UrlFilters1.png

   Sample report

Additionally, we've added a filter on Country.

.. figure::  /_static/images/UrlFilters2.png

   Filter on Country

Adding A Filter And Sharing A Static URL
----------------------------------------

If you wish to filter on the country Argentina, you can select
"Argentina" in the report viewer or the report designer Filter
Properties Panel and update the Results to see the new results. If you
save this report, the filter will default to Argentina.

.. figure::  /_static/images/UrlFilters3.png

   Filter value

If you wish to link to the report, you can simply provide the URL to a
user. For instance,
**http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce**

.. figure::  /_static/images/UrlFilters5.png

   Opened from Report Link 

Dynamically Passing A Filter Value
----------------------------------

-  If you wish to change the filter dynamically, we would use the
   following expression: "URL" + "?" + "p" + "FILTER\_NUMBER" + "value="
   + "VALUE\_FOR\_THE\_FILTER"

   For instance, if you would like to filter on USA instead of
   Argentina, you would follow the formula:

        **URL** + **?** + **p** + **FILTER\_NUMBER** + **value=** + **VALUE\_FOR\_THE\_FILTER** |br|
        **http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce** + **?** + **p** + **1** + **value=** + **USA** |br|
        **http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce?p1value=USA**

.. figure::  /_static/images/UrlFilters4.png

   Opened from Report Link with filter value


-  In this report, we've added a Custom URL to the Country field. Within
   this Custom URL, we've passed the URL to this report along with a
   filter value pointing to each particular Country value. Therefore, if
   we click on "Argentina," we will be able to filter this report to
   Argentina only. Similarly, if we click on "USA," we will be able to
   filter this report to USA only.

   The custom URL takes the following form:

      **http://xxxx/report/view/52602346-e6ea-4027-ab75-344fd93c66ce?p1value={[Country]}**

.. figure::  /_static/images/UrlFilters6.png

   Custom URL setting

Dynamically Passing Multiple Filter Values
------------------------------------------

If you wish to pass more than one filter dynamically using a URL, you
can use the expression in the section above and add additional filters
with "&" + "p" + "FILTER\_NUMBER" + "value=" . This formula can be
followed for as many filters that you have available for a particular
report.

   Suppose we also had a filter on City where Country is the first
   filter and City is the second filter. If you want to filter on the
   country USA and the city Portland, you would follow the formula:

        **URL** + **?** + **p** + **FILTER\_NUMBER** + **value=** + **VALUE\_FOR\_THE\_FILTER** + **&** + **p** + **FILTER\_NUMBER** + **value=** |br|
        **http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce** + **?** + **p** + **1** + **value=** + **&** + **USA** + **p** + **2** + **value=** + **Portland** |br|
        **http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce?p1value=USA&p2value=Portland**

.. figure::  /_static/images/UrlFilters7.png

   Opened from Report Link with multiple filter values
   
   
Passing Filter Values To Dashboards
------------------------------------

Older versions only allowed users to pass filter values to reports. With a slight modification to the processes described above, you can now pass filter values to dashboards.

* To reference the report viewer, you would use the subdirectory **/report/view/** in the URL (e.g.http://xxxx:8081/report/view/....)
* To reference the dashboard editor/viewer, you woud use the subdirectory **/dashboard/edit/** in the URL (e.g.http://xxxx:8081/editor/viewer....)


* To reference a parameter value for reports, you would use **p** + **Filter Number** + **value** + **=** + **Filter_Value**
* To reference a parameter value for dashboards, you would use **p** + **Filter Number** + **=** + **Filter_Value**


* Example report URL: **http://xxxx:8081/report/view/52602346-e6ea-4027-ab75-344fd93c66ce?p1value=USA&p2value=Portland**
* Example dashboard URL: **http://xxxx:8081/dashboard/edit/52602346-e6ea-4027-ab75-344fd93c66ce?p1=USA&p2=Portland**


