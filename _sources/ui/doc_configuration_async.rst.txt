.. _Async_Configuration:
==========================
System Configuration/Async Exporting
==========================

The **System Configuration/Email** page allows user to set up email
sending options.

#. In browser, log in to Izenda as a user with System Configuration
   permission.

#. Click Settings, then System Configuration then Exporting in the left
   menu.

#. Select the Setting Level: either System or a specific tenant.

     .. _System_Configuration_Async_Tenant_Configuration:

     .. figure:: /_static/images/System_Configuration_Async_Tenant_Config.png
        :align: right
        :width: 323px

        Custom Async Configuration

     For tenant level, select to re-use configuration from system or to define a separate one. |br|

#. Turn ON the Exporting Service and enter the details into the configuration seciton

#. Save the configuration.

	 .. _System_Configuration_Async:

	 .. figure:: /_static/images/System_Config_Async.png
      :width: 652px

Node Based Deployment Support
-----------------------------
1. New values have been added to the application settings to help with deployment and scaling

 -  **izenda.jobs.routineprovisioned**

    -  Page layouts are immutable.

    -  CSS Stylesheets and basic logo replacement available.

 -  **izenda.jobs.asyncjobsenabled**

    -  All async exporting jobs will scale using this setting

2. New values have been added to the application settings to help with resource usage

 -  **AsyncJobMaxCpuUsage**

    -  This setting checks total CPU usage in percentages and stops executing jobs when this threshold is met

    -  By default, this is set to 70

 -  **AsyncJobMaxRamUsage**

    -  This setting checks the total memory in use in percentages and stops executing when this threshold is me

    -  By default, this is set to 80
	

Troubleshooting
---------------

If you get the following error on Windows environment

   .. code-block:: console

		2021-03-16 13:37:51,939 [30   ][ERROR] [(null)] [(null)] [JobRunShell] Job ExportQueue.ExportQueueJob threw an unhandled Exception:  
		System.UnauthorizedAccessException: Access to the registry key 'Global' is denied.
		at Microsoft.Win32.RegistryKey.Win32Error(Int32 errorCode, String str)
		at Microsoft.Win32.RegistryKey.InternalGetValueCore(String name, Object defaultValue, Boolean doNotExpand)
		at System.Diagnostics.PerformanceMonitor.GetData(String item)


 Please update the app pools permission using following the commands

   .. code-block:: console
   
		net localgroup "Performance Monitor Users" "IIS APPPOOL\<POOL NAME>" /add
		net localgroup "Performance Log Users" "IIS APPPOOL\<POOL NAME>" /add
