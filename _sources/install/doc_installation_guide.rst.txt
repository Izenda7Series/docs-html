==========================
Installation Guide
==========================

.. contents:: Table of Contents
      :depth: 3

|br|

Standalone Installation Options
=================================
There are two main options when deploying a "vanilla" instnace of our standalone environment.
      -  Installing Izenda's front end and back end as two separate sites
      -  Installing Izenda's front end and back end as virtual directories/applications under a host site

The architectural goal, pre-installation preparations, and web server setup are the same for both deployment options.


Architectural Goal
=======================

.. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/Slide1B.PNG

   A diagram of implementation

Install Izenda Standalone on Window OS
========================================

Pre-installation Preparations
------------------------------

The setup of Izenda requires a download of the latest version of the stand-alone front-end and the back-end and a proper web server setup. Izenda can be installed on a local machine on a Windows machine for testing purposes and is a best practice for ensuring permissions and performance can be validated locally prior to moving toward more embedded and integrated examples, but it is not recommended for live deployments.

-  Izenda installation packages, download them from https://downloads.izenda.com/latest/

   *  .. _Izenda_App_folder: 
      An Izenda Front-end Package (Default name "App") |br|

      .. figure:: /_static/images/Izenda_App_folder.png
         :align: center
         :width: 482px

         Content of Front-end package

      
   *  .. _Izenda_API_folder:
      An Izenda Back-end Package (Default name "API") |br|

      .. figure:: /_static/images/Izenda_API_folder.png
         :align: center
         :width: 482px

         Content of Back-end package

-  Server

   *  Windows Server with Internet Information Services (IIS) Web Server.

.. note::

   All of the information covered in this document can also be found in video from `here <https://www.izenda.com/7-series-installation-videos/#portal-install>`__

Web Server Setup
----------------

To ensure that Izenda works properly, your Web Server requires additional components that may not be present on your server by default.

Add Web Server Role and .NET Framework
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Open Server Manager.
#. Click Quick Start, then Add roles and features to open Add Roles and
   Features dialog box.
#. Click Next to accept default selections until Select Server Roles.
#. Tick the Web Server (IIS) check-box.
#. Click Add Features in the next dialog box.
#. Expand .NET Framework 3.5 features and tick .NET Framework 3.5
   check-box.
#. Expand .NET Framework 4.5 features and tick .NET Framework 4.5
   check-box.

   .. note::
            For Windows Server 2016, also check ASP.NET 4.6 in this step and skip adding "IIS:ASP.NET 4.5" in next step. |br|

   .. figure:: /_static/images/Server_Role_Web_Server_ASP.NET_4.6.png
      :align: center
      :width: 524px

      Install Server ASP.NET 4.6 

      
#. Accept other default options then click Install.

.. _Install_ASP.NET_4.5_and_URL_Rewrite_Components:

Install ASP.NET 4.5 and URL Rewrite Components
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Open Microsoft Web Platform Installer’s `download page <https://www.microsoft.com/web/downloads/platform.aspx>`__.

       This can also be opened from IIS Manager Actions panel, "Get New
       Web Platform Components" link.

#. Download and run the installer.
#. Open Microsoft Web Platform Installer.
#. Search for "ASP.NET", select "IIS:ASP.NET 4.5" and click Add. (Not applicable for Windows Server 2016)
#. Similarly search for URL Rewrite 2.0 and click Add.
#. Click Install.

.. _IIS_ASP.NET_install:

   .. figure:: /_static/images/IIS_ASP.NET_install.png
      :width: 667px
      :align: center

      Install IIS ASP.NET 4.5 |br|

Application Pool Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
When creating your Izenda Sites please ensure you set the Managed pipeline mode to Integrated. Classic is not supported.

|

----------------------------------------------------------------

Izenda Installation As Two Separate Sites
------------------------------------------

The most common testing scenario places the front-end and the back-end on two separate sites. Virtual Directories and Virtual Applications deployments are possible with additional configuration and are outlined in another section below.

#. Extract the Izenda Front-end and Back-end packages to 2 separate
   folders, preferably at C:\\inetpub\\wwwroot\\Izenda\\App and
   C:\\inetpub\\wwwroot\\Izenda\\API.
#. Izenda can be installed in multiple configurations: new website, new
   application to an existing website, or new virtual application under
   an existing website:

   -  New website

      #. Right-click the local connection and select Add Website...
      #. Name the website IzendaApp and accept the Application pool with
         the same name.
      #. Click the ellipsis (...) button to select the location of the
         extracted Izenda Front-end package
         (C:\\inetpub\\wwwroot\\Izenda\\App).
      #. Skip the Connect as... and Test Settings... buttons for now,
         since permissions have not been set for Izenda package folders.
      #. Keep the port as 80 by default or change to any available port.
      #. Optionally enter the website address into host name box, but
         you will have to bind that address with the correct ip in
         "C:\\WINDOWS\\System32\\drivers\\etc\\hosts" file.

             e.g. with website address www.acme.com and the ip
             127.0.0.1, the following line needs to be added in hosts
             file:
             ``127.0.0.1    www.acme.com``

      #. Click OK to create the website.

      .. _IIS_Add_Website:

      .. figure:: /_static/images/IIS_Add_Website.png
         :width: 439px

         New Website |br|

#. Add new website for Back-end package:

   *  .NET infrastructure: Similarly to Front-end site set-up but with different port
   *  .NET Core infrastructure: Please prefer to the .NET Core Back-end Standalone set-up guide :ref:`Deploy_NET_Core_BE`

#. .. _IIS_Folder_Permissions:

   .. figure:: /_static/images/IIS_Folder_Permissions.png
      :align: right
      :width: 239px

      Folder Permissions

   Set folder permissions

   #. Right-click the newly-created website, application or virtual
      application and select Edit Permissions to open the folder
      properties.
   #. In Security tab, click Edit to open Permissions dialog box.
   #. Click Add then enter ``IUSR`` then click OK (for IIS 7 and above).

          For older IIS versions, use ``NT AUTHORITY\\NETWORKSERVICE``.

   #. Back in Permissions dialog box, tick the Modify check-box for
      IUSR.
   #. Click OK to close all dialogs. |br|
   #. Set similar permissions for the other package.

#. Update the Back-end API url in Front-end package: 

      Edit the file ``App\izenda_config.js``, replace the default value "WebApiUrl" with the correct ip and port:
      ``"WebApiUrl": "http://127.0.0.1:8888/api/",``
      
 This concludes the steps necessary to install Izenda using two separate websites. 
 Please refer to the following guides below: 
 - Troubleshooting & Verifying the Installation
 - Common Izenda Stand-alone Installation Issues
 - Editing the Configuration Files

.. _Deploy_NET_Core_BE:



----------------------------------------------------------------


Deploying Izenda as a Virtual Directory or Application
------------------------------------------------------
 Installing Izenda as a virtual directorys will mirror the steps taken required to deploy Izenda using two separate websites but additional modifications are necessary for the front end and back end to interact correctly together.


Initial Set Up
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*  Add your Front-end package to IIS as a virtual directory. (For the purpose of this tutorial we have given it the alias of IzendaFront)
*  Add your Back-end package but then convert it to an application. (For the purpose of this tutorial we have given it the alias of IzendaBack)

Within the UI Folder of your Deployment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Edit the izenda\_config.js, point the BaseURL and the WebApiUrl to
   the virtual directory for your front/back-end respectively

   -  Target code:

      .. code-block:: text

         BaseUrl:"/<your Url here>/"

         WebApiUrl:"http://<Your API URL here>/api/"

   -  Example change:

      .. code-block:: text

         BaseUrl:"/IzendaFront/"

         WebApiUrl:"http://localhost:80/IzendaBack/api/"

#. Edit the index.html file and add the URL for the Virtual Directory as
   below, this should follow the ending </style> tag

   -  Target code:

      .. code-block:: html

         <script>
            window.IzendaPublicPath = '/<your Url here>/';
         </script>

   -  Example change:

      .. code-block:: html

         <script>
            window.IzendaPublicPath = '/IzendaFront/';
         </script>

#. Alter the location of the files in the index.html file to point to
   the new location:

   -  Target code:

      .. code-block:: html

          <link rel="shortcut icon" href="/<your Url here>/favicon.png">
          <link href="/<your Url here>/izenda-app.css?
             4676ff4fe0cdf3cd2bab" rel="stylesheet"></head>

          <body>
             <div class="container" id="izenda-root"></div>
             <script type="text/javascript" src="/<your Url here>/izenda-vendors.js?4676ff4fe0cdf3cd2bab"></script>
             <script type="text/javascript" src="/<your Url here>/izenda_app.js?4676ff4fe0cdf3cd2bab"></script>
          </body>

   -  Example change:

      .. code-block:: html

         <link rel="shortcut icon" href="/IzendaFront/favicon.png">
         <link href="/IzendaFront/izenda-app.css?
         4676ff4fe0cdf3cd2bab" rel="stylesheet"></head>

         <body>
            <div class="container" id="izenda-root"></div>
            <script type="text/javascript" src="/IzendaFront/izenda-vendors.js?4676ff4fe0cdf3cd2bab"></script>
            <script type="text/javascript" src="/IzendaFront/izenda_app.js?4676ff4fe0cdf3cd2bab"></script>
         </body>

#. Update the web.config file in the UI folder

   -  Target code:

      .. code-block:: html

         <action type="Rewrite" url="/<your Url here>/" />

   -  Example change:

      .. code-block:: html

         <action type="Rewrite" url="/IzendaFront/" />

Within the API Folder of your Deployment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Update the Web.config file

   -  Target code:

      .. code-block:: xml

          <httpHandlers>
             <add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="/<Your API URL here>/api/*" />
          </httpHandlers>

          <handlers>
             <add name="Nancy" verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="/<Your API URL here>/api/*"/>
          </handlers>

   -  Example change:

      .. code-block:: xml

         <httpHandlers>
            <add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="/IzendaBack/api/*" />
         </httpHandlers>

         <handlers>
            <add name="Nancy" verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="/IzendaBack/api/*"/>
         </handlers>

 This concludes the steps necessary to install Izenda using virtual directories/applications.
 Please refer to the following guides below: 
 - Troubleshooting & Verifying the Installation
 - Common Izenda Stand-alone Installation Issues
 - Editing the Configuration Files
 

Troubleshooting & Verifying the Installation
-------------------------------------------------------

*  To ensure that your API site is running correctly, navigate to http://YOUR_API_URL/api/404 (e.g. http://localhost:8080/api/404)

   If your API is installed correctly, you should see the graphic below:

   .. figure:: /_static/images/SuccessfulAPI.png
   
      Successful Connection to API displays a stylized 404 error

*  Navigate to the API folder, you should see a 'logs' folder with with at least one log file. If you do not see the folder and/or files, verify that the application pool and/or web site user have write permissions to the API folder.




Common Izenda Standalone Installation Issues
-------------------------------------------------------

.. container:: toggle

      .. container:: header 

            **IIS Issues**:

      * ASP.NET
            Izenda’s API is a .NET web application compatible with .NET 4.0 and higher.

            For .NET web applications to run through IIS you need to install IIS ASP.NET through your server’s Add Roles and Feature Wizard, or through the `IIS Web Platform Installer <https://www.microsoft.com/web/downloads/platform.aspx>`__.

            *  `Add Web Server Role and .NET Framework`_
            *  `Install ASP.NET 4.5 and URL Rewrite Components`_

            |br|

            Without these features installed you may encounter errors like the following:

            .. container:: bold red

                  HTTP Error 500.xx – Internal Server Error

            .. container:: bold

                  The requested page cannot be accessed because the related configuration data for the page is invalid.

            |br|

      * URL Rewrite Module
            Izenda’s Stand-alone UI web.config makes use of the IIS URL Rewrite Module for routing.

            You’ll install this module through the `IIS Web Platform Installer <https://www.microsoft.com/web/downloads/platform.aspx>`__.

            *  `Install ASP.NET 4.5 and URL Rewrite Components`_

            |br|

            Without this feature installed you may encounter errors like the following navigating to the UI.

            .. container:: bold red

                  Configuration Error

            .. container:: bold

                  An error occurred during the processing of a configuration file required to service this request.

            |br|

      * API Permissions
            If you can get Izenda running and see the UI, but get an error after setting your Izenda Configuration Database Connection String, you may be encountering permission issues at the API level.

            Izenda’s API needs proper write permissions to its own directory to create the izendadb.config file and generate log files.

            Often there are issues using just the default IUSR or NT AUTHORITY\\NETWORKSERVICE roles to provide these permissions.

            Try the following to get past the issue:

            *  Give the IIS Application Pool Full Access to the API directory.

                  You can see the API’s Application Pool name just by looking at the application’s basic settings in IIS.

                  .. figure:: /_static/images/install_IIS_basic_settings.png
                        :width: 395px

                  IIS basic settings |br|

                  You can then use that name in setting your folder permissions as you see below. |br| 
                  ``IIS AppPool\YouApplicationPoolName``

                  .. figure:: /_static/images/install_IIS_AppPool_name.png
                        :width: 344px

                  IIS Select Application Pool name |br|

                  After giving this IIS Application Pool Full Access rights, you can restart the API, and try using the UI again.

            |br|



.. container:: toggle

      .. container:: header 
           
            **Oracle Issues**:

      *  Microsoft Visual C++ 2010 Redistributable for Izenda’s Oracle Drivers

            Izenda’s Oracle Drivers utilize the Microsoft Visual C++ 2010 Redistributable.

            These can be installed by downloading the installer from Microsoft: |br|
            `Microsoft Visual C++ 2010 Redistributable Package (x64) <https://www.microsoft.com/en-us/download/details.aspx?id=14632>`__

            Without this dependency installed you may encounter errors like the following.

            .. container:: bold red

                  Could load file or assembly ‘Oracle.ManagedDataAccess’ or one of its dependencies. An attempt was made to load a program with an incorrect format.

            .. container:: bold

                  An unhandled exception occurred during the execution of the current web request.

            |br|



.. container:: toggle

      .. container:: header 
           
            **Resource Configuration**:

      * Virtual Directory vs Individual Sites
            There are two different ways to install Izenda Stand-alone, as two separate applications with distinct ports or domains or as one application with a virtual directory. 

            Concepts from these two separate installation options cannot be mixed together without creating issues. Make sure to follow just one guide or the other:

            *  `Izenda Installation as Two Separate Sites`_
            *  `Deploying Izenda as a Virtual Directory or Application`_

            |br|

            Once you have followed one set of instructions to completion, you can move on to `Troubleshooting & Verifying the Installation`_ guides, and :doc:`Install Izenda System Database and Apply License </ui/doc_system_db_and_license>` guides.

            |br|

      * The izenda.config.js File
            You’ll need to edit the izenda_config.js file during installation and it’s important to use fully qualified URLs for the WebApiURL.

            For example, a fully qualified URL to the API should include ``http://`` at the beginning and ``/api/`` at the end. It should look something like what you see below. For `Izenda Installation as Two Separate Sites`_ this is all you need to edit. |br|
            ``WebApiUrl:"http://192.168.45.37:8200/api/"``

            For `Deploying Izenda as a Virtual Directory or Application`_ you need to edit the BaseUrl. This should look like the following, per the instructions with the trailing slash. |br|
            ``BaseUrl:”/IzendaDirectory/”``

            If you don’t properly configure this file you may be able to see the Izenda login UI, but not get directed to the setup UI, or you may see many console errors in your browser’s dev tools.

            |br|


.. container:: toggle

      .. container:: header 
           
            **Connection Strings**:

      * Misconfigured Connection Strings and Difficulty Connecting
            Izenda supports many different database types, and has specific drivers for these specific database types.

            -  Make sure you’ve selected the right Data Server Type in the dropdowns near Connection String UIs.

                  .. figure:: /_static/images/install_select_data_server_type.png
                        :width: 900px

                  Select Data Server Type |br|

            -  Make sure you’ve used the proper syntax for your Connection String.
            -  Certain characters may cause issues when used in Connection Strings. Avoid using characters such as semicolons, single-quotes, or double-quotes

                  MSSQL, PostgreSQL, Oracle, and MySQL Connection Strings are all formatted a little different, provide different options, and expect different syntaxes. Use resources like `ConnectionStrings.com <https://www.connectionstrings.com/>`__ to make sure you’re including the right details, options, and port numbers:

                  + MSSQL
                  + PostgreSQL
                  + Oracle
                  + MySQL

                  |br|

            -  Make sure you’ve allowed the connection through your Network Security.

                  If you use custom ports for your database you’ll need to factor that into both the web server running Izenda as well as your Connection String.

                  If you use Azure or AWS you may need to add the web server running Izenda to your Network Security Groups, or whitelist the IP address so that it can connect to your database.

                  |br|

            -  Make sure you’ve given your Connection String user proper permissions.

                  Double check that the connection string user has permissions to the databases and schemas you want to connect to. You’ll need to give read/write permissions to the user for the Izenda Configuration Database. Izenda cannot get around your RDBMS security, as you might expect. 

                  |br|

            -  Try connecting with another tool or application.

                  If you’re continuing to have issues with a Connection String you may want to ensure that it’s an Izenda specific problem before reaching out.

                  Try using your RDBMS management tools to connect to the database with the same user, and preferably from the same server, that you are trying to connect with using Izenda.

            |br|

Install Izenda Standalone on Ubuntu OS
=======================================

Pre-install preparations
----------------------------

#. Create instance of Ubuntu 18.04
#. Login using ``ssh`` as default user
#. Download ans install .NET core 2.2 sdk and run time env. `Download here <https://dotnet.microsoft.com/download/linux-package-manager/rhel/runtime-2.2.3>`_

   * If you recieve any error, please follow the below steps

      .. code-block:: console

         wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
         sudo dpkg -i packages-microsoft-prod.deb	
         sudo add-apt-repository universe
         sudo apt-get install apt-transport-https
         sudo apt-get update
         sudo apt-get install aspnetcore-runtime-2.2
         sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
         sudo apt-get update
         sudo apt-get install aspnetcore-runtime-2.2

   * If the issues were not resolved, please follow the below steps to re-install

      .. code-block:: console

         sudo apt-get install -y gpg
         wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
         sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
         wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
         sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
         sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
         sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
         sudo apt-get install -y apt-transport-https
         sudo apt-get update
         sudo apt-get install aspnetcore-runtime-2.2

#. Use ``dotnet --info`` to check the installation of .NET Core. You suppose to recieve the following result if .NET Core 2.2 was successfully installed

   .. figure:: /_static/images/install/Ubuntu_Standalone_NET_Core.png
      :width: 847px

#. Install Appache2 as reverse proxy

   #. Update Ubuntu packages to the latest stable version: ``sudo apt-get update``
   #. Install vim: ``sudo apt-get install vim -y``
   #. Install the Apache web server on Ubuntu: ``sudo apt-get install apache2 -y``
   #. Enable the Apache required modules

      .. code-block:: console

         sudo a2enmod rewrite
         sudo a2enmod proxy
         sudo a2enmod proxy_http
         sudo a2enmod headers
         sudo a2enmod ssl –- if you want to configure as SSL
         sudo service apache2 restart

   #. Verify Apache installation by running localhost.

      .. figure:: /_static/images/install/Ubuntu_Stadnalone_Apache.png
         :width: 689px

#. Download Izenda Font-end and Back-end packages

   * Download the lasted Izenda packages from `<https://downloads.izenda.com/latest/>`_

      .. code-block:: console

         sudo wget  -P /home/ubuntu/ https://downloads.izenda.com/latest/StandaloneUI.zip
         sudo wget  -P /home/ubuntu/ https://downloads.izenda.com/latest/API_AspNetCore.zip


   * Unzip the Izenda Font-end and Back-end packages

      .. code-block:: console

         sudo apt-get install zip unzip // Download the zip tool
         sudo unzip 'StandaloneUI.zip' -d /var/www/izenda-ui // Unzip the Izenda Front-end package
         sudo unzip 'API_AspNetCore.zip' -d /var/www/izenda-api // Unzip the Izenda Back-end package

#. Configure Apache reverse proxy

   #. Enter domain name in to **apache2.conf** file

      .. code-block:: console

         sudo vim /etc/apache2/apache2.conf
         ServerName localhost
 
Install Izenda as two separate sites
-----------------------------------------

#. Create **izenda-ui.conf** under /etc/apache2/sites-available: ``sudo vim /etc/apache2/sites-available/izenda-ui.conf``

   .. code-block:: xml

      Listen 8080
      <VirtualHost *:8080>
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/izenda-ui/StandaloneUI
            ErrorLog /var/log/apache2/izenda-ui-error.log
            CustomLog /var/log/apache2/Izenda-ui-access.log common
            <Directory "/var/www/izenda-ui/StandaloneUI">
                     RewriteEngine on
                     # Don't rewrite files or directories
                     RewriteCond %{REQUEST_FILENAME} -f [OR]
                     RewriteCond %{REQUEST_FILENAME} -d
                     RewriteRule ^ - [L]
                     # Rewrite everything else to index.html to allow html5 state links
                     RewriteRule ^ index.html [L]
            </Directory>
      </VirtualHost>

#. Create **izenda-api.conf** under //etc/apache2//sites-available: ``sudo vim /etc/apache2/sites-available/izenda-api.conf``

   .. code-block:: xml

      Listen 8081
      <VirtualHost *:8081> 
         ProxyPreserveHost On
         ProxyRequests Off
         ProxyPass / http://127.0.0.1:5000/
         ProxyPassReverse / http://127.0.0.1:5000/
         ServerName localhost
         ErrorLog /var/log/apache2/izenda-api-error.log
         CustomLog /var/log/apache2/Izenda-api-access.log common
      </VirtualHost>

#. Active the Front-end and Back-end sites.

   .. code-block:: console

      sudo a2ensite izenda-api.conf
      sudo a2ensite izenda-ui.conf

#. Verify the configuration: ``sudo apachectl configtest``. If the configuration is correct, the result will be ``Syntax Ok``. If not, there is an issue in the configuration.

#. Update WebURL in **Izenda_Config.js** file with the proper prt (8081). ``WebApiUrl:"http://localhost:8087/api/``
#. Provide write permission to current user

   .. code-block:: console

      sudo gpasswd -a "$USER" www-data
      sudo chown -R "$USER":www-data /var/www
      find /var/www -type f -exec chmod 0660 {} \;
      sudo find /var/www -type d -exec chmod 2770 {} \;

#. Restart the website: ``sudo service apache2 restart``
#. Start your dotnet application: ``sudo dotnet Izenda.BI.API.AspNetCore.dll``. If the installation is success, you can browse you website via localhost with the 8080 port

Create monitor service
--------------------------

#. Install Supervisor, a monitor service app: ``sudo apt-get install supervisor``
#. Create supervisor config file: ``sudo vim /etc/supervisor/conf.d/izenda-api.conf``
#. Add the following content to the above file

   .. code-block:: console

      [program:dotnettest]
      command=/usr/bin/dotnet /var/www/izenda-api/API_AspNetCore/Izenda.BI.API.AspNetCore.dll  --urls "http://*:5000"
      directory=/var/www/izenda-api/API_AspNetCore
      autostart=true
      autorestart=true
      stderr_logfile=/var/log/izenda-api.err.log
      stdout_logfile=/var/log/izenda-api.out.log
      environment=ASPNETCORE_ENVIRONMENT=Production
      user=www-data
      stopsignal=INT

#. Command to start/stop the service

   * Start Supervisor: ``sudo service supervisor start``
   * Stop Supervisor: ``sudo service supervisor stop``

#. Verifying the service running progress ``sudo tail -f /var/log/izenda-api.out.log``


Configuring Exporting
--------------------------

#. Configuring Exporting

   * To convert HTML to PDF in Linux using the WebKit rendering engine, the following packages should be installed in the Linux machine where the conversion takes place:

      .. code-block:: console

         $ sudo apt-get update
         $ sudo apt-get install xvfb
         $ sudo apt-get install libssl-dev
         $ sudo apt-get install libx11-dev libx11-xcb-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-keysyms1-dev libxcb-randr0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-shm0-dev libxcb-util0-dev libxcb-xfixes0-dev libxcb-xkb-dev libxcb1-dev libxfixes-dev libxrandr-dev libxrender-dev
   
   * Give permission to run the Syncfusion WebKit

      .. code-block:: console  

         sudo chmod 755 /var/www/izenda-api/API_AspNetCore/Export/QtBinariesLinux/Syncfusion.WebKitWrapper

Additional Reference
========================
* Understanding Configuration vs. Reporting Connection Strings
      The Izenda Configuration Database Connection String and Reporting Data Source Connection Strings are set in two different places, it totally separate UIs or underlying APIs.

      -  Izenda Configuration Database Connection String

            The Izenda Configuration Database Connection String will be set in the Settings page under the System DB & License tab. 

            Be very careful when setting and/or changing this connection string!

            This connection string will point Izenda to a database where it can create its schema and store report metadata, dashboard metadata, data model metadata, Tenant, Role, and User metadata, and much more.

            If you set this to an existing database you will end up with Izenda specific tables in your schema, it’s usually best to use a separate empty database for the Izenda Configuration Database unless you’re comfortable with mixing Izenda’s storage schema with your database schema.

            |br|

      -  Reporting Data Source Connection Strings

            Reporting Data Source Connection Strings will be set in the Settings page under the Data Setup/Connection String tab. 

            After connecting Izenda will query the database to establish the available data source listing, so that you can choose specific objects to move into the visible data sources. 

            These selected objects can then be further modeled upon, aliased, secured, and exposed to end-users within report designers.

            Do not delete Connection Strings if you simply need to change connection strings to another database with a similar schema, or if you need to add new objects to the available/visible data source lists, you can change/rebuild Connection Strings or press reconnect and refresh the schema.

            Deleting and recreating Connection Strings will break your reports and dashboards, where just resetting the Connection Strings or reconnecting generally will not.

      |br|

* Editing Configuration Files
      Additional features can be set for a customized deployment experience. For live sites, several of the features below are recommended.

      -  Change the Back-end passphrase, which is the key to encrypt and decrypt data in Izenda.

            Enter a 29-character value into the value of this key:
            ``<appSettings>``, ``<add key="izedapassphrase" value="" />``

      .. warning::

            This passphrase cannot be changed afterwards since already encrypted data cannot be decrypted with another passphrase.

      -  Recommended: add :ref:`security configurations <Web_Server_Security_Configurations>`

      -  Optionally change the default Back-end path ``/api/``

            e.g. change the path to ``/rest/``

            #. Edit the file ``API\Web.config``, replace the default value "api"
                  with the new value at the following places:

                  -  ``<appSettings>``, ``<add key="izedaapiprefix" value="api" />``
                  -  ``<system.web>``, ``<httpHandlers>``, ``<add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="api/*" />``
                  -  ``<system.webServer>``, ``<handlers>``, ``<add name="Nancy" verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="api/*" />``

            #. Also edit the file ``App\izenda_config.js``, replace the default
                  value "api" with the new value at the following places:

                  -  ``"WebApiUrl": "http://127.0.0.1:8888/api/",``

      -  Optionally change Izenda log file settings

            -  Change the default log file location in ``<log4net ..>``, ``<appender name="RollingFileAppender" ..>``, ``<file value="logs\izenda-log.log" />``, which resolves to C:\\inetpub\\wwwroot\\Izenda\\API\\logs in a typical installation.
            -  Change how the log files are archived/rotated/rolled in ``<log4net ..>``, ``<appender name="RollingFileAppender" ..>``.

                  The default setting is to keep maximum 1000 last files of 5MB
                  each every day. See other examples at `log4net
                  document <https://logging.apache.org/log4net/release/config-examples.html#rollingfileappender>`__.

            -  Enable folder compression: log file content is all text and will compress up to 2% of the original size.

                  #. Right-click on the folder (C:\\inetpub\\wwwroot\\Izenda\\API\\logs) and click Properties.
                  #. Click Advanced button in General tab.
                  #. Tick Compress contents to save disk space check-box, then click OK twice.
                  #. Select either option: this folder only, or this folder, subfolders and files then click OK.
                  #. Confirm the compression status: the folder will have blue name, or have two arrows added at the top right of its icon (from Windows 10).

      -  Optionally enter settings for `EVO PDF Azure <http://www.evopdf.com/azure-html-to-pdf-converter.aspx>`__ option, or accept the default values to use the local embedded library.

            #. Under ``<configuration>``, find or add the following section:
            
                  .. code-block:: mxml

                        <evoPdfSettings cloudEnable="false">
                              <azureCloudService server="" port="" servicePassword="" />
                        </evoPdfSettings>

            #. Set ``cloudEnable="true"`` to use the Azure option, then enter the server IP, port and password.

      -  Optionally change the default quartz thread count settings.

            #. In ``<configSections>`` element, add quartz configure section to create the quartz configuration. For example:

                  .. code-block:: mxml

                        <configSections>
                              <section name="quartz" type="System.Configuration.NameValueSectionHandler, System, Version=1.0.5000.0,Culture=neutral, PublicKeyToken=b77a5c561934e089" />
                        </configSections>

            #. In ``<configuration>`` element, specify the maximum thread count by an integer. For example:

                  .. code-block:: mxml

                        <configuration>
                              <quartz>
                                    <add key="quartz.threadPool.threadCount" value="20" />
                              </quartz>
                        </configuration>

Next: :doc:`Install Izenda System Database and Apply License </ui/doc_system_db_and_license>`
------------------------------------------------------------------------------------------------------------

 

.. seealso::

   -  `Installing IIS 8.5 on Windows Server 2012
      R2 <http://www.iis.net/learn/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2>`__.
   -  `Install IIS and ASP.NET
      Modules <http://www.iis.net/learn/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-1-install-iis-and-asp-net-modules>`__
   -  `Understanding built in user and group accounts in
      IIS <https://www.iis.net/learn/get-started/planning-for-security/understanding-built-in-user-and-group-accounts-in-iis>`__
