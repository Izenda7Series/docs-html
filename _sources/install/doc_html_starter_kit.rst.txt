=================================
HTML Starter Kit Setup Guide
=================================

The HTML Starter Kit allows for developers to interact with embedding concepts utilizing an impersonated authentication model in which every transaction with the Izenda API is done through the lens of a System Level Administrator. This kit creates an impersonated token to give complete access to embed report parts, lists, and dashboards into an existing application. 

Also, for a visual representation of the following guide, please check out our HTML Starter Kit Setup Guide video by clicking `here <https://www.izenda.com/7-series-installation-videos/>`_.

Downloads and Materials
------------------------------------------

For this walkthrough, the guide will utilize the latest versions of Microsoft Internet Information Services, SQL Server Management Studio, and Visual Studio.

As well, download the HTMLStarterKit.zip from the Izenda GitHub site and unzip the contents into an easily accessible location.

Database Setup
------------------------------------------

Izenda’s configuration database is normally created during initial setup in the Administration UI. In order for this deployment to work properly, an Izenda configuration database needs to be established prior to deploying. If there is an existing Izenda configuration database that is up to date with the HTMLStarterKit, that database can be utilized for this deployment as well. Otherwise, the developer can use the database creation script located in the HTMLStarterKit/DB/ directory to build an Izenda Configuration database. 

Note: If using an existing Izenda Configuration database, the only alteration necessary is to change the deployment mode in the IzendaSystemSettings table to “3”. 

#. Open SQL Server Management Studio (SSMS) and login. 

#. Open the IzendaSampleDB creation script found in the DB directory of the unzipped HTMLStarterKit in SSMS. 

#. With the creation script opened, executive the script. When the script successfully executes, refresh the list of databases within SSMS to see the IzendaSampleDB database appear in the list of available databases.  

#. Prior to moving on, make sure that the proper credentials are attached to the database as the developer will need to create a connection string using proper User ID and Password credentials later in the process. 

Modifying HTML Starter Kit Project Files
------------------------------------------

#. Open the HTML Starter Kit project file to launch the project inside Visual Studio. 

#. The files that need to be adjusted are the izendadb.config file located in the APIStarterKit directory and the index.html file under the Website directory. For any reason, if one of these files does not appear in Visual Studio, they will need to be added manually. To do this, right click on the directory of the missing file, and select “Add File”. Navigate to the file’s location and select it to import it into the project. 

#. First, open the izendadb.config file to be edited. Find the Connection String field and remove the value.

#. Between quotation marks, enter in the connection string cooresponding to the database setup in the previous step. Note: If the connection string contains a forward slash (“\”), the developer will need to double the slash in order to avoid it being commented out during compile time. 
Example: “Server=PC\SQLEXPRESS;Database=IzendaSampleDB;User Id=test;Password=test;” becomes “Server=PC\\SQLEXPRESS;Database=IzendaSampleDB;User Id=test;Password=test;”

#. With the modifications in place, save the altered izendadb.config file. 

#. Next, the developer will modify the WebAPIUrl variable in the IzendaSynergy.config function in the html.index file. This value will need to reflect the URL to the API that will be established later in IIS. For the purposes of this setup, the URL will be changed to use the port number “82” and will be modified to look like: http://localhost:82/api/. 

#. Make sure the altered files are saved prior to moving on to the next step. 

Publishing Directories in Visual Studio
------------------------------------------

These two directories contained within the kit need to be hosted in IIS at sites. One way to accomplish this is to publish these directories to a specific location and then reference the published versions during the creation of the sites in IIS. 

#. In Visual Studio, right click on the APIStarterKit directory and click the “Publish” option. 

#. Select “Custom” to specify exactly where the developer wants to publish this directory to be referenced later. Give the profile a name and point to a directory to house the published APIStarterKit. In this walkthrough, an API directory has been created and the published files will live in that directory. When named and pointed to the proper place, select “Publish”.

#. Repeat steps 1 and 2 on the “Website” directory in the project and point the published files in a location different than the APIStarterKit. 

Creating Sites in IIS
------------------------------------------

#. In IIS, right click on “Sites” and select “New Site”. 

#. For the API, name the new site “HTML API” and point it to the directory that the APIStarterKit was published to. 

#. For this site, be sure to adjust the Port number to match the WebAPIUrl that was setup earlier in the process. For this example, that url was set as http://localhost:82/api/ so our port number will be set as “82”. Select OK to create the site. 

#. To set the proper security on this site, right click on the newly created site and select Edit Permissions. Navigate to the Security tab and select “Add”. For the purposes of this walkthrough, the security role of “Everyone” will be added with all the available rights. This can be adjusted later to add additional security to the site, but for the initial deployment, “Everyone” will be sufficient. 

#. To ensure the API was properly setup, navigate to the newly created site’s URL. In this case, the developer would navigate to http://localhost:82/api/. If the deployment of this site was successful, the developer should be presented with a 404 screen with a cartoon character on it. If the developer does not see this, it may be beneficial to try and publish the APIStarterKit again and re-build the site in IIS. Also, ensure that the port number selected is open and available for a site to be hosted on it. 

#. Repeat steps 1-4 to create a site for the HTML Website directory that was published earlier. Assign it a new port number and point to the published Website directory. 

Launching the Deployment
------------------------------------------

#. With the sites setup and the API confirmed as working (via checking for the 404 image), it is important to reset IIS to lock in any changes to the sites. This can be done either through the Command Line run as an Administrator by entering “iisreset” or manually through the UI of IIS by selecting the restart icon.

#. Once the reset is complete, select the HTML Website created in IIS, and browse to it using the Browse button on the right side of the screen. If setup was successful, a browser should open with an Izenda report list screen logged in as the System Administrator. 

#. Now, to ensure that the deployment can be used, the developer will need to drop their License Key and/or Token into the settings page of the deployment. 

#. Copy and past the License Key and/or Token into the settings page and then hit the “Validate” button to validate the deployment. 

#. Once the deployment is validated and a subscription period has been established, the developer can then move on to adding connection strings to reporting databases and creating reports and dashboards in the conventional way for all deployments. 

Helpful Documentation 
------------------------------------------

`Front End Integration APIs – Useful for integrating aspects of this kit into an existing application <https://www.izenda.com/docs/dev/api_frontend_integration.html>`_.

`Styling Concepts and Guide <https://www.izenda.com/docs/dev/code_bi_portal_custom_css.html>`_.

`Report Styling Concepts <https://www.izenda.com/docs/ui/doc_styling_your_report.html>`_.

`Developer Guide <https://www.izenda.com/docs/dev/.developer_guide.html>`_.
