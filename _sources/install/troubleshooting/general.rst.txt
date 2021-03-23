=================================
General
=================================


Your user ID is inactive. (Integrated Mode Only)
------------------------------------------------------------------------------------------------------------
This issue can occur if you used the /api/user (POST) endpoint to create users in integrated modes. Ensure that you are using the user/integration/saveUser (POST) endpoint to create users in integrated modes.

Use the script below to manually active users.

  .. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [IzendaSystemSetting]
	SET [Value] = '<your url here including the trailing slash>'
	WHERE [Name] = 'WebUrl'


.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.


----------------------------------------------------------------


Reports And/Or Dashboards Not Visible After Upgrading
-----------------------------------------------------

This issue can occur if the User Interface and API versions are not the same. See: Check the Izenda Version subsection below

----------------------------------------------------------------


Cannot Load Repository
----------------------

------------------------------
*Check the Connection String:*
------------------------------

The error suggests that you may not have a clear connection from the API to the Izenda Configuration database. In the izendadb.config file of the API, there should be a connection string.
  - If this value is in plain text, attempt to connect to it via SSMS
  - If this value is in plain text, any '\' present will need to be escaped (e.g. '\\')
  - If this value is encrypted, replace it with an unencrypted version and reset IIS

-----------------------------
*Check the Deployment Mode:*
-----------------------------

If you can successfully connect to the database using the connection string above, check the deployment mode.
  - In the SystemSetting table of the Izenda Configuration Database, check the deployment mode value is set to the correct value for your kit. If using the Back End Standalone Kit, this should be a value of 1.

---------------------------
*Check the Izenda Version:*
---------------------------

In order for Izenda to run successfully, the Izenda Configuration Database, Izenda API, and Izenda Front End resources must be the same version.
  - The Izenda Configuration Database: Found in the IzendaDBVersion table.
  - The Izenda API: Navigate to the bin directory of the API. Select an Izenda prefixed dll (e.g. Izenda.BI.Core). Right click this dll, select properties, and navigate to the details tab. The version can be found in the properties panel.
  - The Izenda UI: The simplest way to ensure that your Izenda front end resources match the API and Configuration Database is to download the corresponding version from the Upgrade tab in the `Customer Portal <https://app.izenda.com>`_.
