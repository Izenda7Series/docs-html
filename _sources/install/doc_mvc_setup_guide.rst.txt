=====================
MVC Setup Guide
=====================

For this installation guide of the MVC5StarterKit, Izenda will demonstrate the process using Visual Studio, SQL Server Management Studio, and Google Chrome. 

Also, for a visual representation of the following guide, please check out our MVC Setup Guide video by clicking `here <https://www.izenda.com/7-series-installation-videos/#mvc5starter>`_.

Downloads and Materials
------------------------------------------

To begin the process of installing the kit, download the EmbeddedUI.zip and API.zip from the latest directory of the Izenda downloads page. 

As well, download the MVC5StarterKit.zip from the Izenda GitHub site. 
This installation guide will reference Visual Studio, SSMS, and Google Chrome. Each of these will be on their latest up-to-date version as of 04/07/2017. 

First Steps
--------------
#. Unzip the MVC5StarterKit.zip contents into an easy to access location to be referenced later. 

#. Unzip the contents of the downloaded EmbeddedUI.zip and API.zip files into an equally easy to access location. 

#. Navigate through the MVC5StarterKit directory to the file named Mvc5StarterKit.sln and double-click to open the project in Visual Studio. When open, the contents of the project should be listed on the right panel of the screen. 

#. Now, with the project open, pull up the file explorer with the unzipped API directory open. Navigate to the API\bin directory and copy all of the contents and move them to the Mvc5StarterKit\IzendaReferences directory. 

#. Then navigate back to the API home directory. Take the API\Content, API\EmailTemplates, and API\Export Template directories and move the folders into the Mvc5StarterKit\IzendaResources directory. 

#. Finally, move to the unzipped EmbeddedUI directory and copy all files and folders contained within and move them into the Mvc5StarterKit\Scripts\izenda directory of the project. 

Sample Reporting Database Setup
------------------------------------------

#. Open SQL Server Management Studio. Right click on the “Databases” dropdown and select “New Database”. Give the new database the name “Retail”. 

#. Now, locate the Retail database script contained within the Mvc5StarterKit directory in the SQLScript folder (Mvc5StarterKit\SQLScript). Then run that script on the newly created Retail database to update it. Once the script has successfully executed, the project and reporting database should be in a runnable state. 

Starting the Application
----------------------------
In Visual Studio, right click on the project to build, and then run the application in the desired browser (for the purposes of this installation, Google Chrome will be the default browser).

When the application loads up, use the default System Administrator login credentials to log into the platform for the first time. Select the “Login” button at the top of the screen and enter System into the Tenant field, then use the Username IzendaAdmin@system.com with the Password Izenda@123. 

Once logged in, navigate to the System tab at the top of the screen. This is where the user will need to enter in their license key and token to validate the deployment. With the deployment validated, the user can then navigate to the Data Model tab to load in that Retail database for reporting purposes. 

Under the Data Model area, select the Connection String tab. With the Connection String tab open, press the “Add Connection” button at the top of the second panel. Then, enter in the Database name as “Retail”, select SQLServer from the Data Server Type dropdown, and then, either through the connection string builder or manually, enter in the connection string to the Retail database hosted in SSMS.

Once in place, the user can select the Test button to ensure a stable connection to the database and then the connect button to load in references to any Tables, Views, Stored Procedures, and User Defined Functions contained within the Retail Database. 

Now the MVC5StarterKit is in a state that reports and dashboards can begin to be built and deployed. 

Feel free to navigate through the code to see how Izenda was programmatically integrated into the MVC5 default application offered by Microsoft. 

Please review the following file: mvc5starterkit\mvc5starterkit\izendaboundary\customadhocreport.cs This is where you can find samples for: Hidden Filters Filter Dropdown Overrides See more information here: All About IAdhocExtension, Hidden Filters, and Filter Dropdown Overrides

Alternative Environments
----------------------------
Contained within the kit are some tenants with custom themes that can be explored by logging in using their specific credentials. 
There are three environments that can be analyzed through the UI and styling assets that can be observed at the code level for each.

The logins are listed below:
For each Tenant the following users / roles are configured all use the same password: Izenda@123


**Tenant: DELDG** 

User: employee@deldg.com Role: employee 

User: manager@deldg.com Role: manager 

User: vp@deldg.com Role: VP 



**Tenant: NATWR**

User: employee@natwr.com Role: employee

User: manager@natwr.com Role: manager

User: VP@natwr.com Role: VP



**Tenant: RETCL** 

User: employee@retcl.com Role: employee

User: manager@retcl.com Role: manager 

User: vp@retcl.com Role: VP 


When registering a new user in this sample all users are hardcoded to the manager role here: Mvc5StarterKit\Controllers\AccountController.cs.

The CSS can be configured per tenant and an example is provided see below: This is configured here ~\mvc5starterkit\Mvc5StarterKit\Views\Shared_Layout.cshtml And folder structures are located here ~\mvc5starterkit\Mvc5StarterKit\Content
