=================================
General
=================================
|

Your user ID is inactive. (Integrated Mode Only)
------------------------------------------------------------------------------------------------------------
This issue can occur if you used the /api/user (POST) endpoint to create users in integrated modes. Please ensure that you are using the user/integration/saveUser (POST) endpoint to create users in integrated modes.

You can use the script below to manually active users.
  
  .. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [IzendaSystemSetting]
	SET [Value] = '<your url here including the trailing slash>'
	WHERE [Name] = 'WebUrl'


.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.
