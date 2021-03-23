=====================
MVC Core Integration
=====================

.. contents:: Table of Contents

Introduction
====================

This tutorial will teach you the basics of embedding Izenda into an ASP.NET MVC Core web application using Visual Studio 2017.

Download the `completed project <https://github.com/Izenda7Series/MVCCoreStarterKit>`__. This is important! You’ll need to use files and code samples from this codebase throughout the guide.

This starter kit will guide you through the implementation and deployment of the full integration mode, this means both front-end (UI) and back-end (API Service) are integrated into one MVC 5 application.

See more details for :ref:`Fully_Integrated_Deployment`.



Prerequisites
======================

To complete this walkthrough, you will need the following:

*  Visual Studio 2017
*  .NET Core 2.2
*  Izenda API package
*  Izenda Embedded UI package
*  Sql Server 2016

The Izenda API service is built on .NET framework 4.6.1 and Core 2.2, you can build your integrated application on .NET Framework 4.0 or higher and .NET Core 2.2, this document will guide you step by step on integrating Izenda into your application with .NET Core 2.2. Please note this guide was developed using the versions of each component specified above. For more details on supported components please see other sections in the :doc:`Izenda documentation </index>`.

Create Your MVC Core Starter Kit Application
==============================================

Open Visual Studio IDE then select menu New > New Project

.. figure:: /_static/images/install/mvc_core_new_project.PNG
   :width: 627px

   New ASP.NET Core Web Application

On New Project dialog, select Templates > Visual C# > Web then select target .NET Core Framework and ASP.NET Core Web Application.

Name your project “MvcCoreStarterKit” then click OK. This is important! It will affect reference names throughout the code base.

In the New ASP.NET Core Project dialog, choose .Net Core framework and ASP .NET Core 2.2 then click Web Application (Model-View-Controller).

.. figure:: /_static/images/install/mvc_core_new_project_template.PNG
   :width: 524px

   MVC Core Template

The default template of MVC Core is created, you will use this template to implement Izenda integrated application from now.

Copying Izenda Resources and References
=========================================

In Solution Explorer of MvcCoreStarterKit project, add new folders below:

*  IzendaBoundary
*  IzendaReferences
*  IzendaResources
*  wwwroot\js\izenda

Copy Izenda Resource to starter kit project:

*  Download and copy `izendadb.config <https://github.com/Izenda7Series/MvcCoreStarterKit/blob/master/MvcCoreStarterKit/izendadb.config>`__ file into ~\\MvcCoreStarterKit
*  Download latest Izenda API package (API.zip) extract zip file and then:

   -  Copy all sub folders and files in ~\\API\\bin to ~ \\MvcCoreStarterKit\\IzendaReferences
   -  Copy 3 folders API\\Content, API\\EmailTemplates and API\\Export to ~ \\MvcCoreStarterKit\\IzendaResources

*  Download latest Izenda Embedded UI package (EmbeddedUI.zip), extract zip file then copy all sub folders and files to ~\\MvcCoreStarterKit\\Scripts\\izenda
*  Download `izenda.integrate.js <https://github.com/Izenda7Series/MvcCoreStarterKit/blob/master/MvcCoreStarterKit/Scripts/izenda.integrate.js>`__, `izenda.utils.js <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Scripts/izenda.utils.js>`__ and `alertify.js <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Scripts/alertify.js>`__ then copy to ~\\MvcCoreStarterKit\\wwwroot\js\

Configuring the Project Build
===========================================

Add Izenda DLLs reference and other dependencies
------------------------------------------------

#. Right click Reference node in MvcCoreStarterKit Solution Explorer then select Add Reference…

#. On Reference Manager dialog click Browse… button then browse to folder ~\\MvcCoreStarterKit\\IzendaReferences, select all DLL files having `Izenda` prefix and `Rhino.License.dll` file

   .. note:: In this step if you encounter errors regarding reference conflicts, you must configure Redirecting Assembly as required or contact Izenda Support.

#. You also need to add System.ComponentModel.Composition. |br|
   Go to Add References again, Assemblies-> Framework and check System.ComponentModel.Composition.

#. Finally, go to Tools->NuGet Packet Manager->Package Manager Console and run the following:

   .. code-block:: console

      Install-Package Microsoft.AspNet.WebApi.Client

Adding post build events to copy the resources
------------------------------------------------

Adding post build events to copy the resources
Open Project Properties page select Build Events then click Edit Post-build… button and then enter the commands below into Post-build event command line box:

.. code-block:: console

    XCOPY /S /I /Y "$(ProjectDir)IzendaResources\Content" "$(TargetDir)Content\"
    XCOPY /S /I /Y "$(ProjectDir)IzendaResources\EmailTemplates" "$(TargetDir)EmailTemplates\"
    XCOPY /S /I /Y "$(ProjectDir)IzendaResources\Export" "$(TargetDir)Export\"
    XCOPY /S /I /Y "$(ProjectDir)IzendaResources\Themes" "$(TargetDir)Themes\"
    XCOPY /S /I /Y "$(ProjectDir)IzendaReferences\Resources" "$(TargetDir)bin\Resources\"


.. figure:: /_static/images/install/mvc_core_post_build_events.PNG
   :width: 806px

   Copy Resources on Post build event

Configuring the Script and Style Bundle
===========================================

Open ~\\Views\\Shared\\_Layout.cshtml and add bundle script:

.. literalinclude:: included_samples/mvc_core/_Layout.cshtml
   :lines: 3-15
   :emphasize-lines: 8-12

Then add the below script:

.. literalinclude:: included_samples/mvc_core/_Layout.cshtml
   :lines: 38-54
   :emphasize-lines: 9-16

Configuring the Routes
===========================================

Open ~\\MvcCoreStarterKit\\Startup.cs then modify the routing config as shown below:

.. literalinclude:: included_samples/mvc_core/Startup.cs
   :lines: 121 - 

`View Code Here <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/App_Start/RouteConfig.cs>`__

The statement ``app.UseOwin(x => x.UseNancy(opt => opt.Bootstrapper = new CustomBootstraper()));`` and the ``CustomBootstraper`` class are important, do not miss it. This route will instruct MVC routine ignore any request API which is begin with ``api/`` prefix (instead of response as Controller and View request, it will treat as API Service request), and this prefix must be same with value of Izenda API prefix setting ``<add key="izendaapiprefix" value="api" />`` that you will config in section `Izenda API Service Hosting Config`_ later.

Some of the routing configuration may seem strange, but they will be explained later. The table below details the purpose of each URL route:

.. list-table::
   :widths: 15 25 60
   :header-rows: 1

   * - Name
     - URL
     - Description
   * - ReportPart
     - viewer/reportpart/{id}
     - This route is used by Izenda BE Service to capture html content of report party type chart, gauge or map. Mostly used for report exporting function
   * - ReportViewer
     - report/view/{id}
     - This route is used by Izenda BE Service to capture report content in html format. It is using in exporting report content to embedded html and send it to email (send to email directly or send by report subscription function)
   * - DashboardViewer
     - dashboard/view/{id}
     - The route used by Izenda BE Service to capture dashboard content in html format. Using for exporting dashboard content to email.
   * - CustomAuth
     - api/user/login
     - The route used by the CopyConsole tool to login to your integrated Izenda API for executing Copy Management feature.

Setting up the Database
===========================================

In this starter kit, we use SQL Server for the database server. Izenda supports many database engines such as: [MSSQL] SQL Server, [AZSQL] AzureSQL, [MYSQL] MySQL, [ORACL] Oracle and [PGSQL] PostgreSQL. The steps to setting up these databases are similar.

Create Izenda DB
-------------------------------------------

On your SQL Server create an empty database named IzendaMvc. This database stores Izenda data (report definitions, dashboards, etc.) and the configuration necessary to run Izenda.

Download `IzendaMvc.sql <https://github.com/Izenda7Series/MVCCoreStarterKit/blob/master/SQLScript/MSSQL/IzendaMVC.sql>`__ then execute on IzendaMvc database to generate the schema and default data.

Updating the Izenda DB
-------------------------------------------

The IzendaMvc.sql script will generate a configuration database for Izenda 1.24.4.

If you use an EmbeddedUI and API for a later version of Izenda you will need to run update scripts against your IzendaMvc database.

Upgrade scripts can be compiled and downloaded using the `Schema Migration Assistant <https://tools.izenda.com/>`_ . Here, you will specify your current version (1.24.4) and your target version for upgrade and download the resulting SQL script.

Create Authentication DB
-------------------------------------------

On your SQL Server create an empty database named MvcCoreStarterKit. This database is used for storing user authentication information. In your real integrated application, it can be replaced by your system database with your custom user credential information.

Download `MvcCoreStarterKit.sql <https://github.com/Izenda7Series/MVCCoreStarterKit/blob/master/SQLScript/MSSQL/MVCCoreStarterKit.sql>`__ and execute on MvcCoreStarterKit database to create schema and default user authentication settings.

Verifying Izenda DB and Authentication DB
-------------------------------------------

After creating the IzendaDB, select all rows in the IzendaSystemSetting table and verify that the values are the same as below:

.. list-table::
   :widths: 15 15 70
   :header-rows: 1

   * - Name
     - Value
     - Description
   * - DeploymentMode
     - 3
     - The setting for deployment mode, in this starter kit it is fully integrated.
   * - WebUrl
     - http://localhost:14809/
     - The setting value must be base address of your front-end web page url.

Next you must ensure the UserName value of records in AspNetUsers table in MvcCoreStarterKit DB must be matched with UserName value in IzendaUser table of IzendaMvc DB.

Configuring the Izenda API Service
===========================================

The full configuration files  `web.config <https://github.com/Izenda7Series/MVCCoreStarterKit/blob/master/MVCCoreStarterKit/web.config>`__  and `appsettings.json <https://github.com/Izenda7Series/MVCCoreStarterKit/blob/master/MVCCoreStarterKit/appsettings.json>`__ of Izenda API Service are available on GitHub.

`View Code Here <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Web.config>`__

Izenda API Service Hosting Config
-------------------------------------------

Open the MvcCoreStarterKit\\Web.config and add below Izenda setting key into <appSettings> node:

.. literalinclude:: included_samples/mvc/Web.config
   :language: xml
   :lines: 77-89
   :emphasize-lines: 0

.. list-table::
   :widths: 15 20 65
   :header-rows: 1

   * - Key Name
     - Value
     - Description
   * - ``izendaapiprefix``
     - api
     - This is prefix of your Izenda API service, it is used for distinguish the Izenda API with other api in your application if it expose more than one service endpoint.
   * - ``izendapassphrase``
     - vqL7SF+9c9FIQEKUOhSZapacQgUQh
     - The key used for encryption
   * - ``IzendaApiUrl``
     - http://localhost:14809/api/
     - Your Izenda API endpoint, used to call the Izenda API in your .NET code
   * - ``izusername``
     - IzendaAdmin@system.com
     - Default system level account, in this kit it is used for authentication of specific functions like adding new users, updating the data model, etc. This value must match with the Username in MvcCoreStarterKit.AspNetUsers table and IzendaMvc.IzendaUser table
   * - ``iztenantname``
     -
     - The tenant of system level account, have same purpose with ``izusername``

In <system.webServer> config node, add below config:

.. literalinclude:: included_samples/mvc_core/web.config
   :language: xml
   :lines: 4-12
   :emphasize-lines: 0

Logging Config
-------------------------------------------

In <configSections> add a new section named name="log4net" to config logging for Izenda API.

.. literalinclude:: included_samples/mvc_core/startup.cs
   :language: xml
   :lines: 33-35
   :emphasize-lines: 0

Then add log4net node below:

.. literalinclude:: included_samples/mvc_core/web.config
   :language: xml
   :lines: 15-56
   :emphasize-lines: 0

Configuring Database Connection
-------------------------------------------

Open ~\\ MvcCoreStarterKit\\izendadb.config then update the connection string to your IzendaMvc DB which was created in the steps above. For example with [MSSQL] SQLServer:

.. code-block:: json

   {"ServerTypeId":"572bd576-8c92-4901-ab2a-b16e38144813","ServerTypeName":"[MSSQL] SQLServer","ConnectionString":"[your connection string to IzendaMvc]","ConnectionId":"00000000-0000-0000-0000-000000000000"}

The ``ServerTypeName`` would be one of [MSSQL] SQL Server, [AZSQL] AzureSQL, [MYSQL] MySQL, [ORACL] Oracle and [PGSQL] PostgreSQL.

.. list-table::
   :widths: 40 60
   :header-rows: 1

   * - DatasourceName
     - Id
   * - [AZSQL] AzureSQL
     - d968e96f-91dc-414d-9fd8-aef2926c9a18
   * - [MYSQL] MySQL
     - 3d4916d1-5a41-4b94-874f-5bedacb89656
   * - [ORACL] Oracle
     - 93942448-c715-4f98-85e2-9292ed7ca4bc
   * - [PGSQL] PostgreSQL
     - f2638ed5-70e5-47da-a052-4da0c1888fcf
   * - [MSSQL] SQLServer
     - 572bd576-8c92-4901-ab2a-b16e38144813

For starter kit authentication database open ~\\MvcCoreStarterKit\\Web.config then modify the DefaultConnection value in connectionStrings node:

.. literalinclude:: included_samples/mvc_core/web.config
   :language: xml
   :lines: 58-60
   :emphasize-lines: 0

The first run of Izenda API Service
===========================================

64-bit Oracle DLL Dependencies
-------------------------------------------

If you encounter an error related to OracleDataAccesssDTC in Visual Studio navigate to Tools -> Options -> Projects and Solutions -> Web Projects -> Turn on Use the 64 bit version of IIS Express for web sites and projects.

.. figure:: /_static/images/install/mvc_core_64bit_iis_express.PNG
   :width: 657px

   64-bit IIS Express

Run Starter Kit
-------------------------------------------

In Visual Studio you can press F5 to run your starter kit for the first time, the application page will look like the screenshot below:

.. figure:: /_static/images/install/mvc_core_run_starter_kit.png
   :width: 911px

   Starter kit screen

There is nothing present from the Izenda UI at this time. At this step we are just checking whether Izenda API is able to start up completely or not. On your browser address add /api/ to the end of url (http://localhost:14809/api/) then press enter, you will see Izenda API is hosted completely:

.. figure:: /_static/images/install/mvc_core_landingpage.png
   :width: 900px

   Landing Page

In ~\\MvcCoreStarterKit project folder you will see a logs folder with the log files mvccorekit-log.log (~\\MvcCoreStarterKit\\logs).

Izenda API Hosting Troubleshooting
-------------------------------------------

If you do not see logs file and landing page above check following:

*  Nany hosting configuration in appsettings.json
*  Check your routing configuration in startup.cs

Adding Izenda Boundary
===========================================

Get all files in `IzendaBoundary <https://bitbucket.org/izenda-development/mvccorestarterkit/src/master/MVCCoreStarterKit/IzendaBoundary/>`__ folder from GitHub repository then include into MvcCoreStarterKit project. Build the project, if there are any errors regarding missing references, update the references as needed.

The table below describes the functionality of each source code file:

.. list-table::
   :widths: 25 25 50
   :header-rows: 1

   * - File and Folder
     - Classes
     - Description
   * - Models
     - Model Entity
     - The definition of transferring model data which is used when communicating between your code and Izenda API.
   * - CustomAdhocReport.cs
     - CustomAdhocReport
     - The IAdHocExtension is used to override many default functions in your Izenda installation. This extension will be automatically injected into the runtime by the Izenda API application. More information on this can be found :doc:`here </dev/ref_iadhocextension>`
   * - IzendaTokenAuthorization.cs
     - IzendaTokenAuthorization
     - The helper class to decrypt and deserialize authentication token to UserInfo object and vice versa (serialize UserInfo object then encrypt to token key).
   * - IzendaUtility.cs
     - IzendaUtility
     - Helper class to get list of data connection info for specific tenant.
   * - StringCipher.cs
     - StringCipher
     - The helper class to encrypt and decrypt string value.
   * - WebAPIService.cs
     - WebAPIService
     - The service proxy class supports to call to Izenda API Service.

These classes just demonstrate simple examples of using each functionality. It is recommended that in your actual integration you use security best practices that follow your organizations established security policies and procedures.

Custom Authentication Logic
===========================================

In this starter kit, we use simple authentication with username, password and tenant info. Basically, authorization logic (role, permissions …etc.) will depend on implementation of Izenda backend.

In MvcCoreStarterKit database we add a table named Tenants and add a column named TenantID into AspNetUsers table, this new column is a foreign key reference to the Tenants table which demonstrates a one to many relationship between Tenant and User. Other tables are kept same as ASP.NET MVC 5 template, that helps us modify login logic at little as possible, but allows us to show a simple use case for multi-tenant support.

.. figure:: /_static/images/mvc_AspNetUsers_Tenants.png
   :width: 419px

   Users and Tenants

In integrated mode, authentication is handled by the MVC Core application, not Izenda. In this starter kit, the Izenda backend will get a token via the ``UserIntegrationConfig.GetAccessToken`` method. You must implement your own code logic to provide this token containing the authenticated user’s information. To ensure security, each request to the Izenda API service will call back to MVC application to validate the token it received from the originating request. You must provide this validation logic in your app inside the ``UserIntegrationConfig.ValidateToken`` method. The diagram below illustrates the token retrieval and validation process in fully integrated mode:

.. figure:: /_static/images/mvc_authentication_sequence_diagram.png
   :width: 500px

   Authentication Sequence Diagram

To customize the authentication logic, we must modify some existing classes in the ASP.NET MVC Core application template. The table below lists all the modified classes:

.. list-table::
   :widths: 30 20 5 45
   :header-rows: 1

   * - File
     - Class
     - State
     - Description
   * - IzendaConfig.cs
     - IzendaConfig
     - New
     - The extension class provides Izenda token and token validation for the Izenda backend.
   * - Areas\\Identity\\Model\\IzendaUser.cs
     - ApplicationUser
     - New
     - The entity class present user identity model. This model maps to AspNetUsers table.
   * - Areas\\Identity\\Model\\Tenant.cs
     - Tenant
     - New
     - The entity model presents a tenant, maps to Tenants table.
   * - Data\\ApplicationDbContext.cs
     - ApplicationDBContext
     - New
     - Entity Framework DB context.
   * - Areas\\Identity\\ApplicationUserManager.cs
     - ApplicationUserManager
     - New
     - Manage authentication user and login context.
   * - Areas\\Identity\\ApplicationSignInManager.cs
     - ApplicationSignInManager
     - New
     - Custom sign in logic.
   * - Areas\\Identity\\Pages\\Account\\Login.cshtml.cs
     - LoginModel
     - New
     - Custom login logic
   * - Areas\\Identity\\Pages\\Account\\Logout.cshtml.cs
     - LogoutModel
     - New
     - Custom logout logic
   * - Areas\\Identity\\Pages\\Account\\Register.cshtml.cs
     - RegisterModel
     - New
     - Custom register logic
   * - Areas\\Identity\\ApplicationUserClaimsPrincipalFactory.cs
     - ApplicationUserClaimsPrincipalFactory
     - New
     - Handle user identity


IzendaConfig
-------------------------------------------

Create IzendaConfig.cs file within the top level of the project and implement subscription for ``UserIntegrationConfig.GetAccessToken`` action and ``UserIntegrationConfig.ValidateToken`` action.

.. literalinclude:: included_samples/mvc_core/IzendaConfig.cs
   :lines: 8-31
   :emphasize-lines: 6,15

Action ``UserIntegrationConfig.GetAccessToken`` will convert user info to a token value.

Action ``UserIntegrationConfig.ValidateToken`` convert access token to user info.


IzendaUser and ApplicationUserClaimsPrincipalFactory
---------------------------------------------------------

#. Open Areas\\Identity\Model\\IzendaUser.cs
#. Add the following namespaces so that it appears as below:

    .. literalinclude:: included_samples/mvc_core/IzendaUser.cs
        :lines: 1-2
        :emphasize-lines: 0

#. Add Tenant_Id property like below:

    .. literalinclude:: included_samples/mvc_core/IzendaUser.cs
        :lines: 6-12
        :emphasize-lines: 3-5

#. Open Areas\\Identity\ApplicationUserClaimsPrincipalFactory.cs
#. Add the following namespaces so that it appears as below:

        .. literalinclude:: included_samples/mvc_core/ApplicationUserClaimsPrincipalFactory.cs
            :lines: 1-6
            :emphasize-lines: 0

#. Add custom claim identity like below:

        .. literalinclude:: included_samples/mvc_core/ApplicationUserClaimsPrincipalFactory.cs
            :lines: 18-34
            :emphasize-lines: 3-16

The ApplicationUser class represents the user model and maps to AspNetUsers table. The Tenant_Id property is the foreign key reference to the tenant of the user. In the ``GenerateClaimsAsync`` method we add tenantId into user identity, this value will be used to establish “claims” based on the user’s tenant.

Tenant
----------

#. Open Areas\\Identity\\Model\\Tenant.cs.
#. Add a new Tenant class to represent a tenant object. This class is an entity model that maps to the Tenants table. The example below utilizes a very simple tenant model. You can customize this model to store more complex information.

.. literalinclude:: included_samples/mvc_core/Tenant.cs
   :linenos:
   :lines: 1-
   :emphasize-lines: 0

ApplicationDBContext
----------------------

This is the Entity Framework DB context of the entire authentication database. Because we added a new Tenants table, we must update the DB context to set of Tenant into this class.

.. literalinclude:: included_samples/mvc_core/ApplicationDbContext.cs
   :lines: 7-25
   :emphasize-lines: 0

ApplicationUserManager
-------------------------------------------

#. Open Areas\\Identity\\ApplicationUserManager.cs
#. Add the following namespaces so that it appears as below:

    .. literalinclude:: included_samples/mvc_core/ApplicationUserManager.cs
        :lines: 1-10
        :emphasize-lines: 0

#. Add a new method ``FindTenantUserAsync``. This will be used to query and retrieve users by tenant, username, and password.

    .. literalinclude:: included_samples/mvc_core/ApplicationUserManager.cs
        :lines: 35-47
        :emphasize-lines: 0

ApplicationSignInManager
-------------------------------------------

#. Open Areas\\Identity\\ApplicationSignInManager.cs
#. Add the following namespaces so that it appears as below:

    .. literalinclude:: included_samples/mvc_core/ApplicationSignInManager.cs
        :lines: 1-7
        :emphasize-lines: 0

#. Add a new method ``PasswordSigninAsync`` to customize sign in logic. This method utilizes the FindTenantUserAsync method added above to find a user with the specified username, password and tenant.

    .. literalinclude:: included_samples/mvc_core/ApplicationSignInManager.cs
        :lines: 23-34
        :emphasize-lines: 0

Account
-------------------------------------------

#. Open Areas\\Identity\\Pages\\Account\\Login.cshtml.cs
#. In Login POST method, implement the ApplicationSignInMangager/PasswordSigninAsync method as shown below.

.. literalinclude:: included_samples/mvc_core/Login.cshtml.cs
   :lines: 73-96
   :emphasize-lines: 9-19

UserInfo
------------

#. Create Models\\UserInfo.cs
#. Add the following:

.. literalinclude:: included_samples/mvc_core/UserInfo.cs

InputModel
-------------------------------------------

#. Open Areas\\Identity\\Pages\\Account\\Login.cshtml.cs and Areas\\Identity\\Pages\\Account\\Register.cshtml.cs
#. Add public class ``InputModel`` so that it appears as below.

.. literalinclude:: included_samples/mvc_core/Login.cshtml.cs
   :lines: 38-54
   :emphasize-lines: 0

Update Login Page
-------------------------------------------

#. Open Views\\Account\\Login.cshtml.
#. Replace the contents of this file with the following from the `GitHub MVCCoreStarterKit equivalent <https://bitbucket.org/izenda-development/mvccorestarterkit/src/master/MVCCoreStarterKit/Areas/Identity/Pages/Account/Login.cshtml>`__. This will add a Tenant section to the login page.

.. literalinclude:: included_samples/mvc_core/Login.cshtml
   :lines: 12-50
   :emphasize-lines: 5-9

Run First Login
===========================================

Press F5 to run application, navigate to login page and enter the values below for the respective fields:

*  Tenant = System
*  Email = IzendaAdmin@system.com 
*  Password = Izenda@123 

Then click Login. You will see the home page with the logged in user’s email on top right of the page.

.. figure:: /_static/images/mvc_current_user_ui.png
   :width: 730px

   Current user and Log off button

Update Shared Layout
===========================================

Construct Izenda Menu Items
-------------------------------------------

#. Open ~\\Views\\Shared\\_Header.cshtml then add menu items for Izenda pages:

    .. literalinclude:: included_samples/mvc_core/_Header.cshtml
        :lines: 9-40
        :emphasize-lines: 0

#. Open ~\\Views\\Shared\\_Layout.cshtml then add the header for Izenda pages:

    .. literalinclude:: included_samples/mvc_core/_Layout.cshtml
        :lines: 17-36
        :emphasize-lines: 12-18

Note that the menu routing requires the creation of 2 new controllers: ReportController and DashboardController. These will be created in a later section.

Implement Izenda Configuration Initialization
----------------------------------------------

Add Javascript code below into the bottom of the _Layout.cshtml to initialize Izenda Config and sub menu dropdown display. The function DoIzendaConfig() is located in ~\\wwwroot\\js\\izenda.integrate.js. It initializes main config value needed to run Izenda’s integrated UI such as API Service Url, the path of the Izenda embedded JavaScript package, custom CSS styling, Izenda UI routing config, and the request timeout.

.. literalinclude:: included_samples/mvc_core/_Layout.cshtml
   :lines: 55-63

Embedding Front-end Izenda (Izenda UI)
===========================================

Embedding Izenda full page
-------------------------------------------

In the HomeController add a new action named Izenda and then create the view Izenda.cshtml for it.

.. literalinclude:: included_samples/mvc_core/HomeController.cs
   :lines: 40-43
   :emphasize-lines: 0

This action is used to embedded the entire Izenda application into one view. The Izenda/* routes are subroutes inside of the fully embedded Izenda page.

In the Izenda.cshtml view, call function izendaInit(), which is defined in ~\\Scripts\\izenda.integrate.js. The full Izenda UI will be rendered when opening this page, including Report, Dashboard and Setting page.

.. literalinclude:: included_samples/mvc/Izenda.cshtml

We have 2 empty div elements for each Izenda page, the ``loader`` div is used for display progress bar when the page is waiting for response from Izenda back-end, the div ``izenda-container`` is the container for Izenda page content.

Embedding Specific Izenda Pages
-------------------------------------------

Embedding the Izenda Settings Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create the Settings action in the HomeController

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 42-45
   :emphasize-lines: 0

The settings page view Settings.cshtml:

.. literalinclude:: included_samples/mvc/Settings.cshtml

Embedding the Izenda Report List Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create the Reports action in HomeController

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 47-50
   :emphasize-lines: 0

The report list view Reports.cshtml:

.. literalinclude:: included_samples/mvc/Reports.cshtml
   :emphasize-lines: 12

Embedding the Izenda Report Designer Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create the ReportDesigner action in HomeController

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 52-55
   :emphasize-lines: 0

The report designer view ReportDesigner.cshtml:

.. literalinclude:: included_samples/mvc/ReportDesigner.cshtml
   :emphasize-lines: 12

Report Part for Exporting
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This action is not displayed directly to the end-users. It is used for rendering report parts (charts, gauges, and maps) for exporting. Reports containing these report part types must be rendered to capture html content then converted it to image when creating exported material (pdf, word, excel, etc.).

This view is requested by Izenda backend over the route url ``viewer/reportpart/{id}`` in route config ~\\View_Start\\RouteConfig.cs.

Add the ReportPart action in HomeController:

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 57-62
   :emphasize-lines: 0

This view is only used by Izenda backend, so it requires a minimal view containing only the report part content. Create a new simple layout named ``_IzendaLayout.cshtml``. This layout does not contain UI for menu item, signed in user information.

The ``_IzendaLayout.cshtml`` content:

.. literalinclude:: included_samples/mvc/Izenda_Layout.cshtml

The ReportPart.cshtml content:

.. literalinclude:: included_samples/mvc/ReportPart.cshtml
   :emphasize-lines: 9

Embedding the Report Viewer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create the ReportController and add a new action named ReportViewer:

.. literalinclude:: included_samples/mvc/ReportController.cs
   :lines: 18-23
   :emphasize-lines: 0

Create the view ReportViewer.cshtml:

.. literalinclude:: included_samples/mvc_core/ReportViewer.cshtml
   :emphasize-lines: 10

Note that this page also used by Izenda backend in function to export report html content when user wants to send a report via email (directly or over subscription scheduler). The Izenda backend uses the route ``report/view/{id}`` to get report content, then in RouteConfig.cs we have a custom route for this. You must ensure your report viewer page has the same controller and action with the custom route ``ReportViewer``.

.. literalinclude:: included_samples/mvc/RouteConfig.cs
   :lines: 23-27
   :emphasize-lines: 0

Embedding Report Parts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page demonstrates how to display multiple report parts on a page outside of the Report Viewer.  The function ``izendaInitReportPartDemo`` in ~\\wwwroot\\js\\izenda.integrate.js is implemented to handle this.

.. literalinclude:: included_samples/mvc/izenda.integrate.js
   :lines: 96-121
   :emphasize-lines: 0

In the ReportController create the action ReportParts:

.. literalinclude:: included_samples/mvc/ReportController.cs
   :lines: 25-28
   :emphasize-lines: 0

Create the ReportParts.cshtml view:

.. literalinclude:: included_samples/mvc_core/ReportParts.cshtml
   :emphasize-lines: 9

Embedding the Dashboard
-------------------------------------------

Dashboard List
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page displays the dashboard list.

In the HomeController create the action Dashboards:

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 64-67
   :emphasize-lines: 0

Create the Dashboards.cshtml view:

.. literalinclude:: included_samples/mvc/Dashboards.cshtml
   :emphasize-lines: 12

New Dashboard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The page for creating a new dashboard.

In the HomeController create the action DashboardDesigner:

.. literalinclude:: included_samples/mvc/HomeController.cs
   :lines: 69-72
   :emphasize-lines: 0

Create the DashboardDesigner.cshtml view:

.. literalinclude:: included_samples/mvc/DashboardDesigner.cshtml
   :emphasize-lines: 9

Dashboard Viewer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Display detail of dashboard, this page also is requested by Izenda backend for dashboard exporting function over route ``dashboard/view/{id}``. In RouteConfig.cs we have a custom route named ``DashboardViewer``, this custom route will map to the controller and view of this page.

Create the DashboardController and action DashboardViewer:

.. literalinclude:: included_samples/mvc_core/DashboardController.cs

Create the DashboardViewer.cshtml view:

.. literalinclude:: included_samples/mvc_core/DashboardViewer.cshtml
   :emphasize-lines: 10

Run Your Izenda Integrated Application
===========================================

Press F5 to run debug

Navigate to login page and enter the values below for the respective fields:

*  Tenant = System
*  Email = IzendaAdmin@system.com 
*  Password = Izenda@123 

On top menu click Settings link then add your license key

.. figure:: /_static/images/mvc_license_key.png
   :width: 900px

   Settings license key

Stop your application and start again (this step ensures Izenda reloads the cache).

Click Izenda link on top menu to open full Izenda app

.. figure:: /_static/images/mvc_full_izenda_app.png
   :width: 900px

   Full Izenda app

Now feel free to explore Izenda integrated application.

Implement Register New Account
===========================================

Modify register new user layout in ASP.NET MVC Core

.. figure:: /_static/images/mvc_new_account.png
   :width: 900px

   New account screen

Add new class InputModel in ~\\Areas\\Identity\\Pages\\Account\\Register.cshtml.cs

.. literalinclude:: included_samples/mvc_core/Register.cshtml.cs
   :lines: 46-68
   :emphasize-lines: 0

Add new tenant input element into ~\\Areas\\Identity\\Pages\\Account\\Register.cshtml

.. literalinclude:: included_samples/mvc_core/Register.cshtml
   :lines: 9-38
   :emphasize-lines: 0

Create Services folder and Add new TenantManager class to project (~\\Services\\TenantManager.cs), this class is used to get Tenant and create new tenant info from your authentication DB.

.. literalinclude:: included_samples/mvc_core/TenantManager.cs

Open Areas\\Identity\\Pages\\Account\\Register.cshtml.cs and modify ``OnPostAsync`` action  to handle new user registration logic.

When registering a new user the new user’s information is stored on both the authentication DB and the Izenda DB, following that we split the registration logic into the steps below:

*  Save new Tenant if needed
*  Save User and Role in authentication DB
*  Save User and Role in Izenda DB
*  Sign in with new user

All step are encapsulated in the Register action in AccountController.

Register tenant:

.. literalinclude:: included_samples/mvc_core/Register.cshtml.cs
   :lines: 80
   :emphasize-lines: 0

Save user and role information into authentication DB:

.. literalinclude:: included_samples/mvc_core/Register.cshtml.cs
   :lines: 83-85
   :emphasize-lines: 0

Save user and role into IzendaDB:

.. literalinclude:: included_samples/mvc_core/Register.cshtml.cs
   :lines: 87-131
   :emphasize-lines: 0

Login with newly created user:

.. literalinclude:: included_samples/mvc_core/Register.cshtml.cs
   :lines: 133-134
   :emphasize-lines: 0

You can refer to completed implementation of Register in Register.chtml.cs on Github `here <https://bitbucket.org/izenda-development/mvccorestarterkit/src/master/MVCCoreStarterKit/Areas/Identity/Pages/Account/Register.cshtml.cs>`__.

Call Izenda API Service in C#
===========================================

On completed sample starter kit on Github, we provide an example demonstrating how to call Izenda API service in C# code, reference to the ~\\IzendaBoundary\\WebAPIService.cs and ~\\IzendaBoundary\\IzendaUtility.cs for more detail. 
