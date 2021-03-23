==============================
Modifying Default Email Template
==============================

This article contains how to change the default footer in emails for Schedules and Subscriptions. The default templates can be found under API/EmailTemplates. Before modifying the templates, please take note of the below:

.. figure:: /_static/images/Settings_Schedule_Scope.PNG


        The "External User" permission as found under Role Setup -> Permissions

    - Files under API/EmailTemplates/en-US/Report/Schedule/Inside: The email body will default to these templates if a role has the "External User" permission unchecked in their Scheduling Scope.
    - Files under API/EmailTemplates/en-US/Report/Schedule/Outside: The email body will default to these templates if a role has the "External User" permission checked in their Scheduling Scope.
    - Files under API/EmailTemplates/en-US/Report/Subscription: The email body will default to these templates when Subscribing to a report.
    - Scheduling under a System Admin will pull its template from API/EmailTemplates/en-US/Report/Schedule/Outside.

    |br|

Change the Default Footer in Emails
-------------------------------------------

.. note::

    The following steps cover modifying the template for the "Link" delivery method for schedules and subscriptions. Modifying the template of other delivery methods can be done by changing its respective file.

#. In Windows explorer, navigate to API/EmailTemplates/en-US/Report/Schedule/Inside. Modify the "Link.xml" file to include the desired text (e.g. Add "Have a nice day" to the end of the email body).
#. In Windows explorer, navigate to API/EmailTemplates/en-US/Report/Schedule/Outside. Modify the "Link.xml" file to include the desired text.
#. In Windows explorer, navigate to API/EmailTemplates/en-US/Report/Subscription. Modify the "Link.xml" file to include the desired text. 

    - Sample template for "Link.xml":

    .. code-block:: xml

        <?xml version="1.0" encoding="utf-8" ?>
        <Body>
        <![CDATA[
            Please find the report link below. Have a nice day.
            <br/>
            <br/>    
            {reportLink}
            <br/>
            <br/>
            Regards,
            <br/>
            {currentUserName}

        ]]>
        </Body>

#. Reset IIS and clear your browser cache.
#. Navigate to Izenda and select a report in the Report List
#. Add a scheduled instance (link) to the report and observe the email body. If the "External User" permission is unchecked, this reflects our change in step 1. Otherwise, this reflects our change in step 2.
#. Add a subscription (link) to the report and observe the email body. This reflects our change from step 3.

    .. figure:: /_static/images/Custom_Email_Footer.PNG
        :width: 500px

        Test Result of Step 6
