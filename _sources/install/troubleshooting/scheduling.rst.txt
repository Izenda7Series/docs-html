=================================
Scheduling
=================================
|

Scheduled items are not being sent on time 
-----------------------------------------------------------------

This issue can occur if the API site has been shutdown or stopped via an IIS reset/recycle or a similar event. This may be evident in the API logs by large time gaps in activity.

If there is a scheduled iis reset or recycle, the application must be reinitialized for the scheduler to continue to ping and operate as expected. This can be as simple as logging in to the application, or a scheduled task that re-initializes the application. Once the  Izenda application has been initialized, it will continue to ping the server to keep iis running every 5 minutes (default interval).

The system will use the settings below (IzendaSystemSetting table) to ping our API to ensure that scheduled and subscribed items are delivered as expected. The SubscriptionJobInterval value will determine (in minutes) how often the API gets a ping to keep it up and running.

========================   ============
Name                 		    Value
========================   ============
WebAPIUrl        				     http://localhost/api/
SubscriptionJobInterval      5 (default)
========================   ============

If the WebAPIUrl is not set, you will see the error message below in the Izenda API logs:

 [DefaultQuartzScheduler_Worker-1][INFO ][SubscriptionJob] Ping system status failure: The remote server returned an error: (404) Not Found. 


You can use the script below to add the WebAPIUrl: 

.. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [IzendaSystemSetting]
	SET [Value] = '<your url here including the trailing slash>'
	WHERE [Name] = 'WebAPIUrl'


.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.


Duplicate scheduled items are being sent 
-----------------------------------------------------------------

The Izenda Scheduler will store scheduling information in RAM of the server by default. If you are using any type of a distributed environment where there is more than one instance of the Izenda API (webfarms, etc.) you will need to use a database (ADO.NET job store) for storage of the scheduling information.

For setting up the scheduler to run in a distributed environment, please follow the instructions outlined `here <https://www.izenda.com/docs/install/supplementary_guides/load_balancing.html#scheduling>`_.
