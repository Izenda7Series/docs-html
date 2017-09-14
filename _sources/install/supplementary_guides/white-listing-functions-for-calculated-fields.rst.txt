====================================================
White-Listing Functions for Calculated Fields
====================================================
|
|

Introduction
------------------------------------------

Izenda allows users to white-list SQL functions for calculated fields. This allows the use of native SQL functions supported by database type, which are not available in Izenda out of the box. This is accomplished by configuring and deploying a custom config file.

The following are some examples (not all encompassing) of aggregated functions which should not be white-listed (the only supported aggregated functions are already included within Izenda): 

-  STDEV
-  STDEVP
-  VAR
-  VARP
-  STDDEV_POP
-  VAR_POP
-  VAR_SAMP
-  VARIANCE
|

Installation & Configuration
----------------------------------------------------
|

Creating the custom configuration file
#############################################

A sample config file *CustomFunctionSample.config* is included as part of the Izenda API. It is located in **API > bin > Resources**. A snippet of this file is below:

.. code-block:: json
	:linenos:
	
	{
	  "Functions": [
		{
		  "Name": "SUBSTRING",
		  "Description": "This is my custom function to get the sub string of the given string",
		  "Syntax": "SUBSTRING(expression ,start ,length)",
		  "Parameters": [
			{
			  "Name": "expression",
			  "Type": "TEXT",
			  "Description": "The column or value to get the sub string."
			},
			{
			  "Name": "start",
			  "Type": "NUMBER",
			  "Description": "The start position."
			},
			{
			  "Name": "length",
			  "Type": "NUMBER",
			  "Description": "The number of characters."
			}
		  ],
		  "ReturnType": "TEXT",
		  "Mappings": [
			{
			  "Id": "572BD576-8C92-4901-AB2A-B16E38144813",
			  "DatasourceName": "[MSSQL] SQLServer",
			  "FunctionName": "SUBSTRING",
			  "FunctionQueryPattern": "SUBSTRING(expression ,start ,length)"
			}
		  ]
		},
		{
		  "Name": "RTRIM",
		  "Description": "Returns a character string after truncating all trailing blanks.",
		  "Syntax": "RTRIM(character_expression)",
		  "Parameters": [
			{
			  "Name": "character_expression",
			  "Type": "TEXT",
			  "Description": "An expression of character data."
			}
		  ],
		  "ReturnType": "TEXT",
		  "Mappings": [
			{
			  "Id": "572BD576-8C92-4901-AB2A-B16E38144813",
			  "DatasourceName": "[MSSQL] SQLServer",
			  "FunctionName": "RTRIM",
			  "FunctionQueryPattern": "RTRIM(character_expression)"
			}
		  ]
		},
		{
		  "Name": "FLOOR",
		  "Description": "Returns the largest integer value that is equal to or less than a given value.",
		  "Syntax": "FLOOR(character_expression)",
		  "Parameters": [
			{
			  "Name": "n",
			  "Type": "NUMBER",
			  "Description": "The value"
			}
		  ],
		  "ReturnType": "NUMBER",
		  "Mappings": [
			{
			  "Id": "572BD576-8C92-4901-AB2A-B16E38144813",
			  "DatasourceName": "[MSSQL] SQLServer",
			  "FunctionName": "FLOOR",
			  "FunctionQueryPattern": "FLOOR(n)"
			}
		  ]
		}
	  ]
	}

In the example above, we are white-listing the *FLOOR* function starting at line 55. The floor function returns the largest integer less than or equal to *n*. This function receives input of type *NUMBER* and also returns a value of type *NUMBER*. The example is fairly straight-forward, but ensure that you are using the correct DatasourceName and Id for your desired database. A table of these values has been provided below:


==================   ============
DatasourceName                 		Id
==================   ============
[AZSQL] AzureSQL        				d968e96f-91dc-414d-9fd8-aef2926c9a18
[MYSQL] MySQL	    					3d4916d1-5a41-4b94-874f-5bedacb89656
[ORACL] Oracle      					93942448-c715-4f98-85e2-9292ed7ca4bc
[PGSQL] PostgreSQL					f2638ed5-70e5-47da-a052-4da0c1888fcf
[MSSQL] SQLServer					572bd576-8c92-4901-ab2a-b16e38144813
==================   ============


Deploying the configuration file
####################################

After white-listing the desired functions, save the file and deploy it to the API folder. You may find it easier to copy the file to a 'customizations' folder as shown below to better organize any customizations.

.. figure:: images/customizations_folder.png

Next, you will need to update the 'CustomFunctionFilePath' in the IzendaSystemSettings table. You can use the script below, be sure to include the full path to your file.

.. code-block:: sql

	-- This is a MSSQL snippet, you may need to adjust the query for other databases.
	UPDATE [dbo].[IzendaSystemSetting]
	SET Value = 'C:\inetpub\wwwroot\API\customizations\CustomFunctionSample.config' -- << Use your actual path here
	WHERE Name = 'CustomFunctionFilePath'


Restarting the web sites
###############################

After deploying the configuration file, restart the API and front-end sites.

Verifying the changes
###################################

Functions should now be listed in the calculated fields window.

.. figure:: images/floor_function1.png

We can also verify that the function works as expected.

.. figure:: images/floor_function2.png
