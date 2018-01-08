

====================
Izenda Copy Console
====================

Introduction
------------

The Izenda Copy Console Tool will allow you to copy templates, reports
and dashboards from one Izenda Configuration database to another. If you need to copy reports within the same configuration database (eg. copying a report from one tenant to another) you can use the Copy Management Tool.

Usage
-----

#. Download both the CopyConsoleTool.zip and SampleConfig.xml from the
   izenda `utilities <https://downloads.izenda.com/Utilities>`__.
#. Unzip this application to the location you select.
#. Edit the SampleConfig.xml using the following as a template:

   * The Source Block tells the application where you are copying from as below:

     .. code-block:: xml

          <source>
              <!-- Specify the api credentials and the url of the source api-->
              <credentials userName="Admin" password="Admin" apiUrl="http://localhost:2525/api"/>
              <!—Tenant id is not a GUID, but rather the 'Tenant ID' field from the UI. If Tenant ID is BLANK your source location is System Level-->
              <tenant id=""></tenant>
              <!-- Specify the reports to copy based on the report id-->
              <reports>
                  <report id="4FA0D1D6-C4B5-435E-99D3-8B059724BE7C"/>
                  <report id="41212145-C4B5-435E-99D3-8B059724BHC3"/>
              </reports>
              <!-- Specify the templates to copy using the template id -->
              <templates>
                  <!--  <template id="51D71299-FCD0-402E-9DE0-AD428D26FAAA"/> -->
              </templates>
              <!-- Specify the dashboards to copy using the dashboard id-->
              <dashboards>
                  <!-- <dashboard id="B68574CC-89EC-462F-9ED8-DF2F12FACC58"/>  -->
              </dashboards>
          </source>

   * Now you can configure the destination(s).

     Each destination can have a name, this will allow you to run one or all destinations from the command line (the destination name can be specified using the /d: command and the name).

     The destination block can be configured as below:

     .. code-block:: xml

          <!-- Specify the destination(s)-->
          <destinations>
             <!-- Destination 1, These destinations can be run one at a time or all at once based on the name given for each destination by using the d:/parameter in the command line-->
             <destination name="UAT">
                <!-- Specify the api credentials -->
                <credentials userName="Admin" password="Admin" apiUrl="http://10.100.5.86:80/api" />
                <!-- Specify the tenant(s)-->
                <tenants>
                   <!-- id is not a GUID, but rather the 'Tenant ID' field from the UI. If Tenant ID is BLANK this is System Level. IF you would like to overwrite anything at the destination set overwrite to “yes” if not set to “no”-->
                   <tenant id="" overwriteIfAlreadyExist="yes">
                      <!-- Specify the database mappings -->
                      <databaseMappings>
                         <!-- The database name is the name given to to the connection string in the UI of the application. This name is visible in the connection string page of the Izenda Application UI this is not the actual name of the database on your server. You must add the name and the schema for both the source and the destination -->
                         <databaseMapping sourceDatabaseName="northwind" sourceSchema="dbo" destinationDatabaseName="northwind" destinationSchema="dbo" />
                         <databaseMapping sourceDatabaseName="northwind.100" sourceSchema="northwind" destinationDatabaseName="northwind" destinationSchema="northwind"/>
                      </databaseMappings>
                      <!-- Specify the role mappings, this is not required but if you need to map a role like IT from system to IT Department at the tenant location you can do so here. This is not required. If the role does not exist at the destination is will not be copied.-->
                      <roleMappings>
                         <!-- <roleMapping sourceRole="Accounting" destinationRole="Accounting"/> -->
                         <!-- <roleMapping sourceRole="IT" destinationRole="IT Department"/> -->
                      </roleMappings>
                   </tenant>
                </tenants>
             </destination>
             <!-- Destination 2, These destinations can be run one at a time or all at once based on the parameters used in the command line-->
             <destination name="DEV">
                <!-- Specify the api credentials -->
                <credentials userName="Admin" password="Admin" apiUrl="http://10.100.5.87:80/api" />
                <!-- Specify the tenant(s)-->
                <tenants>
                   <!-- id is not a guid, but rather the 'Tenant ID' field from the UI. If Tenant ID is BLANK this is System Level-->
                   <tenant id="Tenant01" overwriteIfAlreadyExist="yes">
                      <!-- Specify the database mappings -->
                      <databaseMappings>
                         <!-- The database name is the name given to to the connection string in the UI of the applicaiotn -->
                         <databaseMapping sourceDatabaseName="southwind" sourceSchema="dbo2" destinationDatabaseName="northwind" destinationSchema="dbo2" />
                         <databaseMapping sourceDatabaseName="northwind" sourceSchema="northwind" destinationDatabaseName="northwind" destinationSchema="northwind" />
                      </databaseMappings>
                      <!-- Specify the role mappings, this is not required but if you need to map a role ex. IT from system to IT Department at the tenant location input here-->
                      <roleMappings>
                         <!-- <roleMapping sourceRole="Accounting" destinationRole="Accounting"/> -->
                         <!-- <roleMapping sourceRole="IT" destinationRole="IT Department"/> -->
                      </roleMappings>
                   </tenant>
                </tenants>
             </destination>
          </destinations>

#. Once you have configured the xml file you can begin to copy.

   You will need to run this from a command window. Navigate to the
   location of the exe where you unzipped it above. You will need to
   provide the path to the xml file configured above and the parameter for
   the destination if used. If this parameter is not used, all destinations
   will be run.

   Command Line example to run:

   .. code-block:: doscon

      C:\CopyConsoleV1\CopyConsoleTool>IzendaCopyConsoleApp.exe SampleConfig.xml /d:UAT

   To view usage at the command line:

   .. code-block:: doscon
   
      C:\CopyConsoleV1\CopyConsoleTool>IzendaCopyConsoleApp.exe /?
      Usage: IzendaCopyConsoleApp.exe <path to mapping file> [/d:<destination name>]

   Options:

   .. code-block:: text
   
      /d:destinationname     (Optional) Specify the destination name. If this switch is omitted, all destinations will be copied.
      
Using the Copy Console for Integrated Modes
---------------------------------------------------



In order for the copy console to function properly, it must be able to login to the source and destination sites and retrieve an access token that will be used throught the copy process. By default, the copy console will attempt to authenticate against the "api/user/login" endpoint for each site specified in the copy console configuration file. 

Exposing the "api/user/login" endpoint
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For integrated modes, you can expose this route in the host application and add the corresponding Action method to handle the authentication. A simple example, along with a sample config file, can be found below:


*  :download:`A quick sample config file </_static/images/CopyConfig.xml>`
*  If you are using an MVC Kit that was not downloaded from the GitHub repository, the following code needs to be added to your RoutConfig.cs file. Refer to the following link for an example: https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/App_Start/RouteConfig.cs (Line 23)

   .. code-block:: csharp

        //configure a custom route to handle requests for "api/user/login"
       routes.MapRoute(
                 name: "CustomAuth",
                 url: "api/user/login",
                 defaults: new { controller = "Home", action = "CustomAuth" }
             );
             
   Then implement a custom action to process requests for "api/user/login" as seen in the example:
   https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Controllers/HomeController.cs (Line 548)

The "appAuthUrl" setting (v2.6.12 or greater)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Alternatively, you can explicitly specify the authentication URL for integrated deployments via the "appAuthUrl" setting.
	 
	 
	 .. code-block:: xml
			:emphasize-lines: 7
			
				<!-- Specify the api credentials -->
				<credentials 
					tenant="" 
					userName="myuser" 
					password="mypassword" 
					apiUrl="http://localhost:2277/api/"
					appAuthUrl="http://localhost:14777/login.aspx"/>
								 
	 	 
This endpoint should process requests as shown in the example below:
https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Controllers/HomeController.cs#L548
	 
