===========================================
Building the Webforms Starter Kit
===========================================

.. contents:: Table of Contents

Introduction
===========================================

This guide will give you an overview of the major aspects of an Izenda integration with a webforms web application.

The purpose of the guide is to abstract from the core of the Izenda Webforms Starter Kit guide the overarching concepts of back end and front-end integration.

Many of the concepts executed upon in the integration sections of this guide can be re-used in other applications, .NET or otherwise. 

The three major features of an Izenda integration, and the three major sections of this summary section are as follows:

•  Front-end Integration
•  Security Handshake
•  Back-end Integration

Front-end Integration
===========================================

Front-end integration with Izenda involves taking the EmbeddedUI codebase and integrating it with an existing application’s front-end codebase and placing it behind that application’s authentication process.

Izenda’s EmbeddedUI is based upon the ReactJS framework. It is lightweight, easy to embed, and works with most modern web technologies, whether it’s another JavaScript framework like Angular, or application technologies like .NET, Java, PHP, Python, or Ruby.

The EmbeddedUI provides access to the Izenda Synergy JavaScript function library which allows for easy rendering of Izenda’s front-end containers throughout the target application.

You can learn more about the IzendaSynergy configuration, authentication, and render functions in the :doc:`Front-end Integration API documentation </dev/api_frontend_integration>`.

Integrating the Embedded UI
-------------------------------------------

This is as simple as just dropping in the Izenda EmbeddedUI Code base.

Once the Izenda ReactJS library is present you’ll have direct access to the IzendaSynergy render functions.

This is done in the `Copying Izenda Resources and References`_ section of the guide below.

The Izenda.integrate.js file
-------------------------------------------

This file is a good representation of how to bundle together IzendaSynergy configuration, authentication, and render functions.

You may choose to create a similar file in your own application code base as it greatly simplifies the amount of on page code you might write to manage your resource references, API endpoint references, passing of the Izenda currentusercontext token, and specific render function.

This is done in the `Copying Izenda Resources and References`_ section of the guide below.

You can view the contents of Izenda.integrate.js `here <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Scripts/izenda.integrate.js>`__.

Using the render functions
-------------------------------------------

Once the EmbeddedUI front-end resources are in place, and we’ve configured the configuration, authentication, and render functions. The last thing to do is use these bundled JavaScript functions within our application’s front-end to render specific Izenda containers/pages.

This is done in the `Embedded Front-end <Embedding Front-end Izenda (Izenda UI)>`_ section of the guide below.

Security Handshake
===========================================

The basic Izenda security handshake is handled through a token which contains two key pieces of user metadata, a unique user identifier, and a unique tenant identifier. You’ll handle role level details through the back-end integration.

The point here is to create the medium through which Izenda will authenticate interactions between the front-end and back-end API endpoints.

In the `IzendaConfig`_ we’ll create the token for the end-user authentication that will eventually be passed to Izenda’s API endpoints through IzendaSynergy currentUserContext.

As you’ll see in that section, that token contains two values originating from the application’s tenant and user store. 

We then pass these values through the token we create along with Izenda’s render functions in the Izenda.integrate.js file.

There is no separate login process for Izenda specifically, rather Izenda just sits behind the existing application’s authentication process and inherits a few key values.

You can see an example of the token getting passed into Izenda’s currentUserContext in `izenda.integrate.js <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Scripts/izenda.integrate.js>`__.

Most of the work here is done in the `Custom Authentication Logic`_ section of the guide below.

There is work beyond just generating the handshake token in that section, as there is additional configuration being done specific to the application to add a Tenant concept to its security model.

Back-end Integration
===========================================

Through front-end integration we are rendering pages, parts, and containers. Through the security handshake we are placing Izenda behind an existing authentication process.

Through back-end integration we are using hooks within Izenda to inherit an existing security model.

The basic concept here is that we want to populate existing tenant, role, and user associations in Izenda.

Now, when users are authenticated, Izenda will be able to appropriately govern what data, features, and reports or dashboards it might expose to the end-user. You can also define these permissions through the EmbeddedUI interfaces, C#, or API endpoints.

This can be done through either exposed C# methods, or through REST API endpoints.

Back-end Integration through C#
-------------------------------------------

This method of back-end integration is typically done when integrating with other .NET web applications, however you might use this approach in scenarios where you would want Izenda to pull (through LINQ expressions, SQL Queries, Web Services, or other REST APIs) the Tenant, Role, and User Metadata you would like Izenda to inherit.

`Sample Starter Kit <https://github.com/Izenda7Series/WebFormsStarterkit>`__

The Webforms Starter Kit demonstrates the C# method approach in depth. This application has both the Izenda EmbeddedUI and API as a part of its codebase, with no components of Izenda running separately.

Most of the interaction is done in the `Register.aspx code-behind <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Account/Register.aspx.cs>`__.

In that file, you can see several references to Izenda DLLs which provide access to exposed methods and classes that are relevant to managing Tenants, Roles, and Users programmatically.

We are syncing between the webforms application’s security model and Izenda’s to make them essentially equivalent.

You can see starting `here <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Account/Register.aspx.cs#L20>`__ that we are using methods to pass values directly from the webforms application’s security model into Izenda’s by equivocating the webforms application’s Tenant, Role, and User variables with Izenda’s. While some areas of this code contain hard-coded values, in real world implementations those values would get replaced with variables or lookups.

Much of the code used in the register page's logic is supported by contents of the `IzendaBoundary <https://github.com/Izenda7Series/WebFormsStarterkit/tree/master/WebFormsStarterKit/IzendaBoundary>`__ directory and `Models <https://github.com/Izenda7Series/WebFormsStarterkit/tree/master/WebFormsStarterKit/Models>`__ from the webforms kit.

Back-end Integration through the API
-------------------------------------------

Currently there is no webforms kit that implements Izenda through REST API calls. For an example that uses the REST API, you can review the `MVC5 back-end standalone <https://www.izenda.com/docs/dev/dev_dep_1_key_components.html>`__ documentation and example kit to learn about that approach.

Other Integration Concepts
===========================================

Beyond front-end, handshake, and back-end, there’s of course an expectation that you’ll want to white label Izenda, integrate with a specific deployment model, and manage record level data permissions beyond what you might define at a Tenant and Role level in Izenda.  

There are many more capabilities and features you may want to explore.

Please reference our GitHub, documentation site, and developer guides for more:

*  `GitHub <https://github.com/Izenda7Series>`__
*  :doc:`Izenda Docs </index>`
*  :doc:`Developer Guide </dev/.developer_guide>`

White Labeling
-------------------------------------------

Izenda provides a fully exposed presentation layer, which includes exposed CSS files.

`Customizing Izenda’s CSS <https://www.izenda.com/docs/dev/code_bi_portal_custom_css.html>`__

Deployment Modes
-------------------------------------------

You may need to integrate only specific areas of Izenda’s codebase, depending upon your integration goals, deployment style, and application technology.

:doc:`/intro/understanding_the_three-tiered_architecture`.

Hidden Filters
-------------------------------------------

Hidden Filters in Izenda are the mechanism by which you can dynamically append to the WHERE clause of Izenda’s queries to ensure it only pulls back highly personalized record sets from your data sources.

See: :ref:`SetHiddenFilters`.

Webforms Integration
===========================================

This tutorial will teach you the basics of embedding Izenda into an ASP.NET webforms application using Visual Studio 2015.

Download the `completed project <https://github.com/Izenda7Series/WebFormsStarterkit>`__. This is important! You’ll need to use files and code samples from this codebase throughout the guide.

This starter kit will guide you through the implementation and deployment of the full integration mode, this means both front-end (UI) and back-end (API Service) are integrated into one webforms application.

See more details for :ref:`Fully_Integrated_Deployment`.

Prerequisites
===========================================

To complete this walkthrough, you will need the following:

*  Visual Studio 2015
*  .NET Version 4.5.2
*  Izenda API package
*  Izenda Embedded UI package
*  Sql Server 2016

The Izenda API service is built on .NET framework 4.0. You can build your integrated application on .NET Framework 4.0 or higher to be compatible with the Izenda API. This document will guide you step by step on integrating Izenda into your application. Please note this guide was developed using the versions of each component specified above. For more details on supported components please see other sections in the :doc:`Izenda documentation </index>`.

Create Your webforms Starter Kit Application
============================================

Open Visual Studio IDE then select menu New > New Project

.. figure:: /_static/images/mvc_new_project.png
   :width: 509px

   New ASP.NET Web Application

On New Project dialog, select Templates > Visual C# > Web then select target .NET Framework and ASP.NET Web Application.

Name your project “WebFormsStarterKit” then click OK. This is important! It will affect reference names throughout the code base.

In the New ASP.NET Project dialog, click Web Forms and click Change Authentication then chose Individual User Accounts, click OK buttons to close dialogs.

.. figure:: /_static/images/webforms_new_project.png
   :width: 590px

   Web Forms Template

The default template of a webforms application will be created. You will use this template to implement Izenda fully integrated into the application.

Copying Izenda Resources and References
===========================================

In Solution Explorer of WebFormsStarterKit project, add new folders below:

*  IzendaBoundary
*  IzendaReferences
*  IzendaResources
*  Scripts\\izenda

Copy Izenda Resource to starter kit project:

*  Download and copy `izendadb.config <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/izendadb.config>`__ file into ~\\WebFormsStarterKit
*  Download latest Izenda API package (API.zip) extract zip file and then:

   -  Copy all sub folders and files in ~\\API\\bin to ~ \\WebFormsStarterKit\\IzendaReferences
   -  Copy 3 folders API\\Content, API\\EmailTemplates and API\\Export to ~ \\WebFormsStarterKit\\IzendaResources

*  Download latest Izenda Embedded UI package (EmbeddedUI.zip), extract zip file then copy all sub folders and files to ~\\WebFormsStarterKit\\Scripts\\izenda
*  Download `izenda.integrate.js <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Scripts/izenda.integrate.js>`__, `izenda.utils.js <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Scripts/izenda.utils.js>`__ and `alertify.js <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Scripts/alertify.js>`__ then copy to ~\\WebFormsStarterKit\\Scripts
*  Download `alertify.css <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Content/alertify.css>`__ and copy to ~\\WebFormsStarterKit\\Content

Configuring the Project Build
===========================================
Add Izenda DLLs reference and other dependencies
------------------------------------------------

#. Right click Reference node in the WebFormsStarterKit Solution Explorer then select Add Reference…

   .. figure:: /_static/images/webforms_add_reference.png
      :width: 361px

      Add reference

#. On Reference Manager dialog click Browse… button then browse to folder ~\\WebFormsStarterKit\\IzendaReferences, select all DLL files to reference but ignore below dlls (because those dlls have already been referenced in the webforms project template by default):

   *  Microsoft.Web.Infrastructure.dll
   *  Newtonsoft.Json.dll

   .. note:: In this step if you encounter errors regarding reference conflicts, you must configure Redirecting Assembly as required or contact Izenda Support.

#. You also need to add System.ComponentModel.Composition. |br|
   Go to Add References again, Assemblies-> Framework and check System.ComponentModel.Composition.

#. Finally, go to Tools->NuGet Packet Manager->Package Manager Console and run the following:

   .. code-block:: console

      Install-Package Microsoft.AspNet.WebApi.Client
      Install-Package Microsoft.AspNet.WebApi.Core
      Install-Package Microsoft.AspNet.WebApi.WebHost

Adding post build events to copy the resources
------------------------------------------------

Adding post build events to copy the resources
Open Project Properties page select Build Events then click Edit Post-build… button and then enter the commands below into Post-build event command line box:

.. code-block:: console

   XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\Content" "$(ProjectDir)\bin\Content\"
   XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\EmailTemplates" "$(ProjectDir)\bin\EmailTemplates\"
   XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\Export" "$(ProjectDir)\bin\Export\"

.. figure:: /_static/images/webforms_post_build_events.png
   :width: 806px

   Copy Resources on Post build event

Configuring the Script and Style Bundle
===========================================

Open ~\\WebFormsStarterKit\\App_Start\\BundleConfig.cs then config for Izenda as below:

.. literalinclude:: included_samples/webforms/BundleConfig.cs
   :lines: 32-48

`View Code Here <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/App_Start/BundleConfig.cs>`__

Open ~\\Site.master and add CSS and bundle scripts:

.. literalinclude:: included_samples/webforms/Site.master
   :lines: 9-25
   :emphasize-lines: 4,14-17

Configuring the Routes
===========================================

Open ~\\WebFormsStarterKit\\App_Start\\RouteConfig.cs then modify the routing config as shown below:

.. literalinclude:: included_samples/webforms/RouteConfig.cs
   :lines: 9-

`View Code Here <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/App_Start/RouteConfig.cs>`__

The statement ``routes.IgnoreRoute("izapi/{*pathInfo}")`` is important, do not miss it. This route will instruct the web infrastructure routine to ignore any request API that begins with the ``izapi/`` prefix (instead of handling the request as a route, the application will treat it as an API Service request), and this prefix must have the same value as the Izenda API prefix setting ``<add key="izendaapiprefix" value="izapi" />`` that you will configure in the section `Izenda API Service Hosting Config`_ later.

Some of the routing configuration may seem strange, but it will be explained later. The table below details the purpose of each URL route:

.. list-table::
   :widths: 15 25 60
   :header-rows: 1

   * - Name
     - URL
     - Description
   * - ReportPart
     - viewer/reportpart/{id}
     - This route is used by the Izenda BE Service to capture html content of the report part types chart, gauge or map. Mostly used for report exporting functions.
   * - ReportViewer
     - report/view/{id}
     - This route is used by the Izenda BE Service to capture report content in html format. It is using in exporting report content to embedded html and sending it to email (send to email directly or send via the report subscription function).
   * - DashboardViewer
     - dashboard/view/{id}
     - The route used by the Izenda BE Service to capture dashboard content in html format. Used for exporting dashboard content to email.

Setting up the Database
===========================================

In this starter kit, we use SQL Server for the database server. Izenda supports many database engines such as: [MSSQL] SQL Server, [AZSQL] AzureSQL, [MYSQL] MySQL, [ORACL] Oracle, and [PGSQL] PostgreSQL. The steps to setting up these databases are similar.

Create Izenda DB
-------------------------------------------

On your SQL Server, create an empty database named IzendaWebForms. This database stores Izenda data (report definitions, dashboards, etc.) and the configuration necessary to run Izenda.

Download `IzendaWebForms.sql <https://raw.githubusercontent.com/Izenda7Series/WebFormsStarterkit/master/SQLScript/MSSQL/IzendaWebForms.sql>`__ then execute the script on your IzendaWebForms database to generate the schema and default data.

Updating the Izenda DB
-------------------------------------------

The IzendaWebForms.sql script will generate a configuration database for Izenda 2.6.20.

If you use an EmbeddedUI and API for a later version of Izenda you will need to run update scripts against your IzendaWebForms database. You can find a tool to generate the required scripts `here <https://tools.izenda.com/>`__.

For example, if you deploy version 2.11.1 of the EmbeddedUI and API, you would select v2.6.20 as your current version and v2.11.1 as your target version and (for the purposes of this tutorial) [MSSQL] SQLServer as your database type. You can choose to download the script as a SQL file or (if the check box is unchecked) view the file directly in your browser window.

Create Authentication DB
-------------------------------------------

On your SQL Server, create an empty database named WebFormsStarterKit. This database is used for storing user authentication information for the webforms kit. In your real integrated application, it can be replaced by your system database with your custom user credential information.

Download `WebFormsStarterKit.sql <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/SQLScript/MSSQL/WebFormsStarterKit.sql>`__ and execute the script on your WebFormsStarterKit database to generate the schema and default user authentication settings. These settings mirror the Izenda configuration database user data as closely as possible.

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
     - http://localhost:14909/
     - The setting value must be the base address of your front-end web page url.

Next you must ensure the UserName value of the records in the AspNetUsers table in WebFormsStarterKit DB are matched with the UserName value in the IzendaUser table of IzendaWebForms DB.

Configuring the Izenda API Service
===========================================

The full configuration file `Web.config <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Web.config>`__ of Izenda API Service is available on GitHub.

`View Code Here <https://raw.githubusercontent.com/Izenda7Series/WebFormsStarterkit/master/WebFormsStarterKit/Web.config>`__

Izenda API Service Hosting Config
-------------------------------------------

Izenda uses the Nancy Framework to host the REST API service. To configure Nancy, open the WebFormsStarterKit\\Web.config and add a new section like below:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 6-21
   :emphasize-lines: 0

Then add the following email config after ``</nancyFx>`` close tag:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 19-30
   :emphasize-lines: 0

Add below Izenda setting key into <appSettings> node:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 99-107
   :emphasize-lines: 0

.. list-table::
   :widths: 15 20 65
   :header-rows: 1

   * - Key Name
     - Value
     - Description
   * - ``izendaapiprefix``
     - izapi
     - This is prefix of your Izenda API service, it is used for distinguish the Izenda API with other api in your application if it exposes more than one service endpoint.
   * - ``izendapassphrase``
     - vqL7SF+9c9FIQEKUOhSZapacQgUQh
     - The key used for encryption
   * - ``IzendaApiUrl``
     - http://localhost:14909/izapi/
     - Your Izenda API endpoint, used to call the Izenda API in your .NET code
   * - ``izusername``
     - IzendaAdmin@system.com
     - Default system level account, in this kit it is used for authentication of specific functions like adding new users, updating the data model, etc. This value must match with the Username in the WebFormsStarterKit.AspNetUsers and IzendaWebForms.IzendaUser tables.
   * - ``iztenantname``
     - [blank]
     - The tenant of the system level account. This serves the same purpose as the ``izusername`` setting and equates to the "System" value in the WebFormsStarterKit.Tenants but does not have a corresponding entry in the IzendaWebForms.IzendaTenant table. The system tenant is implicitly null in Izenda.

In <system.webServer> config node, add below config:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 157-179
   :emphasize-lines: 0

This config includes the http header attribute and api action verb for the Izenda API. It is also used to configure the http handler for the API url convention which will be reserved by the Izenda API Service. Using the config above, all API urls with a prefix of izapi/ will be handled by Izenda. Recall that this handler API prefix must match the value of the ``izendaapiprefix`` setting.

Logging Config
-------------------------------------------

In <configSections> add a new section to configure logging for the Izenda API.

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 9-12
   :emphasize-lines: 0

Then add a new log4net node in the config file as well:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 32-94
   :emphasize-lines: 0

Configuring Database Connection
-------------------------------------------

Open ~\\ WebFormsStarterKit\\izendadb.config then update the connection string to your IzendaWebForms DB which was created in the steps above. For example with [MSSQL] SQLServer:

.. code-block:: json

   {"ServerTypeId":"572bd576-8c92-4901-ab2a-b16e38144813","ServerTypeName":"[MSSQL] SQLServer","ConnectionString":"[your connection string to IzendaMvc]","ConnectionId":"00000000-0000-0000-0000-000000000000"}

The ``ServerTypeName`` would be one of the following: [MSSQL] SQL Server, [AZSQL] AzureSQL, [MYSQL] MySQL, [ORACL] Oracle, or [PGSQL] PostgreSQL. The ServerTypeId mappings are listed below.

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

Next, open ~\\WebFormsStarterkit\\Web.config again and modify the DefaultConnection value in the connectionStrings node to configure the Webforms application database link:

.. literalinclude:: included_samples/webforms/Web.config
   :language: xml
   :lines: 96-98
   :emphasize-lines: 0

The first run of Izenda API Service
===========================================
64-bit Oracle DLL Dependencies
-------------------------------------------

If you encounter an error related to OracleDataAccesssDTC in Visual Studio, navigate to Tools -> Options -> Projects and Solutions -> Web Projects -> Check "Use the 64 bit version of IIS Express for web sites and projects".

.. figure:: /_static/images/mvc_64bit_iis_express.png
   :width: 560px

   64-bit IIS Express

Run Starter Kit
-------------------------------------------

Before you run your starter kit, ensure the Project Url setting in your project settings is set to use the same port that you configured for your ``IzendaApiUrl`` setting in your web.config.

.. figure: /_static/images/webforms_project_url.png
	:width: 560px
	
	Webforms Project Url
	
With that minor detail taken care of, you can press F5 in visual studio to run your starter kit for the first time. The application page will look like the screenshot below:

.. figure:: /_static/images/webforms_run_starter_kit.png
   :width: 900px

   Starter kit screen

There is nothing present from the Izenda UI at this time. At this step we are just checking whether Izenda API is able to start up completely or not. On your browser address add /api/ to the end of url (http://localhost:14809/api/) then press enter, you will see Izenda API is hosted completely:

.. figure:: /_static/images/webforms_api_url_404.png
   :width: 900px

   API screen

In the ~\\WebFormsStarterkit project folder you will see a logs folder with the log files webforms-kit.log and izenda-log.log (~\\WebFormsStarterkit\\logs).

Izenda API Hosting Troubleshooting
-------------------------------------------

If you do not see the log files and 404 page above, check the following:

*  Nancy hosting configuration is correct in the Web.config
*  Ensure Nancy.dll and Nancy.Hosting.Aspnet.dll are referenced in the project.
*  Check your routing configuration in RouteConfig.cs

Adding Izenda Boundary
===========================================

Get all files in the `IzendaBoundary <https://github.com/Izenda7Series/WebFormsStarterkit/tree/master/WebFormsStarterKit/IzendaBoundary>`__ folder from the GitHub repository and include them in your WebFormsStarterkit project. Build the project. If there are any errors regarding missing references, update the references as needed.

The table below describes the functionality of each source code file:

.. list-table::
   :widths: 25 25 50
   :header-rows: 1

   * - File and Folder
     - Classes
     - Description
   * - Models
     - Model Entity
     - Contains the definition of objects used for transferring model data when communicating between your code and the Izenda API.
   * - CustomAdhocReport.cs
     - CustomAdhocReport
     - Contains an implementation the IAdHocExtension interface that is used to override many default functions in your Izenda installation. This extension will be automatically located and injected into the runtime by the Izenda API application. More information on this can be found :doc:`here </dev/ref_iadhocextension>`
   * - IzendaTokenAuthorization.cs
     - IzendaTokenAuthorization
     - The helper class used to decrypt and deserialize the authentication token corresponding to the UserInfo object and vice versa (serialize UserInfo object then encrypt to token key. The UserInfo object will be added below).
   * - IzendaUtility.cs
     - IzendaUtility
     - The helper class to access specific Izenda REST APIs to get connection, tenant, role, and user info from Izenda.
   * - StringCipher.cs
     - StringCipher
     - The helper class to encrypt and decrypt the UserInfo and authentication token between each other.
   * - WebAPIService.cs
     - WebAPIService
     - The service proxy class that provides the framework for making REST API requests to Izenda using Izenda authentication tokens.

These classes just demonstrate simple examples of using each functionality. It is recommended that in your actual integration you use security best practices that follow your organization's established security policies and procedures.

Custom Authentication Logic
===========================================

In this starter kit, we use simple authentication with only a username, password and tenant info. Basically, authorization logic (role, permissions …etc.) will depend on the implementation of the Izenda BE.

If you recall, in the WebFormsStarterkit database we added a table named Tenants and a column in the AspNetUsers table named TenantID. Those objects normally don't exist in a standard Webforms kit. The TenantID column is a foreign key reference to the Tenants table which demonstrates a one-to-many relationship between Tenant and User. The other tables are kept same as in a webforms template project. This helps us minimize the changes in the login logic, but allows us to show a simple use case for multi-tenant support.

.. figure:: /_static/images/mvc_AspNetUsers_Tenants.png
   :width: 419px

   Users and Tenants

In integrated mode, authentication is handled by the webforms application, not Izenda. In this starter kit, the Izenda backend will get a token via the ``UserIntegrationConfig.GetAccessToken`` method. You must implement your own code logic to provide this token containing the authenticated user’s information. To ensure security, each request to the Izenda API service will call back to the webforms application to validate the token it received from the originating request. You must provide this validation logic in your app inside the ``UserIntegrationConfig.ValidateToken`` method. The diagram below illustrates the token retrieval and validation process in fully integrated mode:

.. figure:: /_static/images/mvc_authentication_sequence_diagram.png
   :width: 500px

   Authentication Sequence Diagram

To customize the authentication logic, we must modify some existing classes in the ASP.NET webforms application template. The table below lists all the modified classes and pages:

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
   * - Models\\IdentityModels.cs
     - ApplicationUser
     - Modify
     - The entity class present user identity model. This model maps to AspNetUsers table.
   * - Models\\IdentityModels.cs
     - Tenant
     - New
     - The entity model presents a tenant, maps to Tenants table.
   * - Models\\IdentityModels.cs
     - ApplicationDBContext
     - Modify
     - Entity Framework DB context.
   * - App_Start\\IdentityConfig.cs
     - ApplicationUserManager
     - Modify
     - Manage authentication user and login context.
   * - App_Start\\IdentityConfig.cs
     - ApplicationSignInManager
     - Modify
     - Custom sign in logic.
   * - App_Start\\WebApiConfig.cs
     - WebApiConfig
     - Add
     - Required to handle a specific callback to the GenerateToken route
   * - Account\\Login.aspx
     - [N/A]
     - Modify
     - Include the tenant in the page.
   * - Account\\Login.aspx.cs
     - Login
     - Modify
     - Update login logic to use the customizations.
   * - ApiControllers\\UserController.cs
     - UserController
     - Add
     - Required for handling the GenerateToken route.
   * - Global.asax.cs
     - Global
     - Modify
     - Implement the route mapping from the WebAPIConfig

IzendaConfig
-------------------------------------------

Create IzendaConfig.cs file within the top level of the project and implement subscription for ``UserIntegrationConfig.GetAccessToken`` action and ``UserIntegrationConfig.ValidateToken`` action.

.. literalinclude:: included_samples/webforms/IzendaConfig.cs
   :lines: 6-26
   :emphasize-lines: 5,14

Action ``UserIntegrationConfig.GetAccessToken`` will convert user info to a token value.

Action ``UserIntegrationConfig.ValidateToken`` convert access token to user info.


Identity Models – Namespaces
-------------------------------------------

#. Open Models\\IdentityModels.cs.
#. Add the following namespaces so that it appears as below:

.. literalinclude:: included_samples/webforms/IdentityModels.cs
   :lines: 1-8
   :emphasize-lines: 0

Identity Models – ApplicationUser class
-------------------------------------------

#. Next in Models\\IdentityModels.cs.
#. Add Tenant_Id property and custom claim identity like below:

.. literalinclude:: included_samples/webforms/IdentityModels.cs
   :lines: 13-36
   :emphasize-lines: 3-5,9-

The ApplicationUser class represents the user model and maps to the AspNetUsers table. The Tenant_Id property is the foreign key reference to the tenant of the user. In the GenerateUserIdentityAsync method, we are adding the tenantId into the user identity. This value will be used to establish “claims” based on the user’s tenant.

Identity Models – Tenant
-------------------------------------------

#. Next in Models\\IdentityModels.cs.
#. Add a new Tenant class to represent a tenant object. This class is an entity model that maps to the Tenants table. The example below utilizes a very simple tenant model. You can customize this model to store more complex information.

.. literalinclude:: included_samples/webforms/IdentityModels.cs
   :linenos:
   :lines: 38-42
   :emphasize-lines: 0

Identity Models – ApplicationDBContext
-------------------------------------------

This is the Entity Framework DB context of the entire authentication database. Because we added a new Tenants table, we must update the DB context to include our new model and link it to the entity.

.. literalinclude:: included_samples/webforms/IdentityModels.cs
   :lines: 45-57
   :emphasize-lines: 8

If your starter kit contains another ApplicationDBContext definition, you may need to remove the duplicate to prevent errors.

Identity Config – Namespaces
-------------------------------------------

#. Open App_Start\\IdentityConfig.cs.
#. Add the following namespaces so that it appears as below:

.. literalinclude:: included_samples/webforms/IdentityConfig.cs
   :lines: 1-11
   :emphasize-lines: 2-3

Identity Config – ApplicationUserManager
-------------------------------------------

#. Next in App_Start\\IdentityConfig.cs.
#. Add a new method to the ApplicationUserManager class called FindTenantUserAsync. This will be used to query and retrieve users by tenant, username, and password.

.. literalinclude:: included_samples/webforms/IdentityConfig.cs
   :lines: 41-55
   :emphasize-lines: 0

Identity Configs – ApplicationSignInManager
-------------------------------------------

#. Next in App_Start\\IdentityConfig.cs. 
#. Add a new method PasswordSigninAsync to customize sign in logic. This method utilizes the FindTenantUserAsync method added above to find a user with the specified username, password and tenant.

.. literalinclude:: included_samples/webforms/IdentityConfig.cs
   :lines: 105-126
   :emphasize-lines: 6-

App_Start - WebApiConfig
-------------------------------------------

#. Create App_Start\\WebAPIConfig.cs
#. Add the following:

.. literalinclude:: included_samples/webforms/WebAPIConfig.cs

Login.aspx.cs - Namespace
-------------------------------------------

#. Open Acount\\Login.aspx.cs
#. Add the following namespaces so that it appears as below:

.. literalinclude:: included_samples/webforms/Login.aspx.cs
   :lines: 1-11
   :emphasize-lines: 0

Login.aspx.cs
-------------------------------------------

#. Next in Acount\\Login.aspx.cs
#. In Login method, implement the ApplicationSignInMangager/PasswordSigninAsync method as shown below.

.. literalinclude:: included_samples/webforms/Login.aspx.cs
   :lines: 30-70
   :emphasize-lines: 6-17

UserInfo
-------------------------------------------

#. Create Models\\UserInfo.cs
#. Add the following:

.. literalinclude:: included_samples/webforms/UserInfo.cs

Update Login Page
-------------------------------------------

#. Open Account\\Login.aspx
#. Replace the contents of this file with the following from the `GitHub WebFormsStarterKit equivalent <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Account/Login.aspx>`__. This will add a Tenant section to the login page.

.. literalinclude:: included_samples/webforms/Login.aspx
   :lines: 12-34
   :emphasize-lines: 8-15

ApiControllers - UserController
-------------------------------------------

#. Create ApiControllers\\UserController.cs
#. Add the following:

.. literalinclude:: included_samples/webforms/UserController.cs

global.asax.cs
-------------------------------------------

#. Open global.asax.cs
#. Add the following code:

.. literalinclude:: included_samples/webforms/Global.asax.cs
   :lines: 13-23
   :emphasize-lines: 6,9

Run First Login
===========================================

Press F5 to run application, navigate to login page and enter the values below for the respective fields:

*  Tenant = System
*  Email = IzendaAdmin@system.com 
*  Password = Izenda@123 

Then click Login. You will see the home page with the logged in user’s email on top right of the page.

.. figure:: /_static/images/webforms_current_user_ui.png
   :width: 730px

   Current user and Log off button

Update Shared Layout
===========================================

Construct Izenda Menu Items
-------------------------------------------

Open ~\\Site.master then add menu items for Izenda pages:

.. literalinclude:: included_samples/webforms/Site.Master
   :lines: 59-96
   :emphasize-lines: 5-36

Note that the menu redirects require the creation of several new pages. These will be created in a later section.

Important! The webforms starter project will include the main placeholder for body content inside a form tag. This will cause some Izenda buttons to improperly issue a 'submit' event. To fix this, place the following code 

.. literalinclude:: included_samples/webforms/Site.Master
   :lines: 116-128
   :emphasize-lines: 6-9
   
In addition, another change is required to allow the Login page to continue working. Notice that in the above sample, we have added another placeholder inside the form tag with the ID "LoginContent". We will need to change the placeholder reference in Login.aspx to match.

.. literalinclude:: included_samples/webforms/Login.aspx
   :lines: 3-8
   :emphasize-lines: 3
   
Optional: Izenda uses a class called "container" with some CSS to scale Izenda's components to fit the container's size. The webforms sample project uses the container class to limit the available display area of contents. To expand the available space, you can perform the following actions:

Remove the container class completely from the nav bar

.. literalinclude:: included_samples/webforms/Site.Master
   :lines: 48-50
   :emphasize-lines: 2
   
Change the container class to "izenda-container" in the body-content div

.. literalinclude:: included_samples/webforms/Site.Master
   :lines: 121-124
   :emphasize-lines: 1
   
Add the following css to the Site.css file

.. code-block:: css

   .izenda-container {
      width: 100%;
      height: 100vh;
      min-height: 100vh;
   }
	  
Implement Izenda Configuration Initialization
----------------------------------------------

Add Javascript code below into the bottom of the Site.Master to initialize the Izenda Configuration and sub menu dropdown display. The function DoIzendaConfig() is located in ~\\Scripts\\izenda.integrate.js. It initializes the main config values needed to run Izenda’s integrated UI such as the API Service Url, the path of the Izenda embedded JavaScript package, custom CSS styling, Izenda UI routing config, and the request timeout.

.. literalinclude:: included_samples/webforms/Site.Master
   :lines: 130-
   :emphasize-lines: 2-10

Embedding Front-end Izenda (Izenda UI)
===========================================
Embedding Izenda full page
-------------------------------------------

Create ~\\Izenda.aspx

This page is used to embedded the entire Izenda application into one view.

In this page, we will call the function izendaInit() defined in ~\\Scripts\\izenda.integrate.js. The full Izenda UI will be rendered when opening this page, including the ReportViewer, ReportDesigner, Dashboard, and Setting pages. Navigation will be fully contained within the single page.

.. literalinclude:: included_samples/webforms/Izenda.aspx

We have 2 empty div elements for each Izenda page. The ``loader`` div is used for displaying the progress bar when the page is waiting for a response from the Izenda back-end. The div ``izenda-container`` is the container for Izenda page content.

Embedding Specific Izenda Pages
-------------------------------------------
Embedding the Izenda Settings Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create ~\\Settings.aspx

.. literalinclude:: included_samples/webforms/Settings.aspx

The struture here is very similar to the Izenda.aspx page, as it contains the same elements, but this will specifically embed the Settings page into the page.

Embedding the Izenda Report List Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create ~\\Report\\Reports.aspx:

.. literalinclude:: included_samples/webforms/Reports.aspx

Continue following the pattern of calling the appropriate javascript function in izenda.integrate.js.

Embedding the Izenda Report Designer Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create ~\\Report\\ReportDesigner.aspx:

.. literalinclude:: included_samples/webforms/ReportDesigner.aspx

Report Part for Exporting
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page is not displayed directly to the end-users. It is used for rendering report parts (charts, gauges, and maps) for exporting. Reports containing these report part types must be rendered to capture html content then converted to an image when creating exports (pdf, word, excel, etc.).

This page is requested by the Izenda backend over the route url ``viewer/reportpart/{id}`` and mapped to ``report/reportpart.aspx`` in route config ~\\App_Start\\RouteConfig.cs.

Create ~\\Report\\ReportPart.aspx:

.. literalinclude:: included_samples/webforms/ReportPart.aspx
   :emphasize-lines: 33
   
This page is only used by Izenda backend, so it requires a minimal view containing only the report part content. Therefore, it will not require a master page. The call to ``izendaInitReportPartExportViewer`` is the pivotal portion of this file and it requires an additional piece to work.

Open ReportPart.aspx.cs:

.. literalinclude:: included_samples/webforms/ReportPart.aspx.cs

The properties in this code-behind are used to populate the arguments for the ``izendaInitReportPartExportViewer`` function.

Embedding the Report Viewer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Create ~\\Report\\ReportViewer.aspx:

.. literalinclude:: included_samples/webforms/ReportViewer.aspx
   :emphasize-lines: 5

Note from the highlighted line that this page also used by Izenda backend in function to export report html content when the user wants to send a report via email (directly or via the subscription scheduler). The Izenda backend uses the route ``report/view/{id}`` to get report content, then in RouteConfig.cs we have a custom route for this to map it to ``Report/ReportViewer.aspx``. 

.. literalinclude:: included_samples/webforms/ReportViewer.aspx.cs

You must ensure your report viewer page handles the ID parameter passed in via the route data.

Embedding Report Parts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page demonstrates how to display multiple report parts on a page outside of the Report Viewer.  The function ``izendaInitReportPartDemo`` in ~\\Scripts\\izenda.integrate.js is implemented to handle this.

.. literalinclude:: included_samples/webforms/izenda.integrate.js
   :lines: 96-130
   :emphasize-lines: 0

Create ~\\Report\\ReportParts.aspx:

.. literalinclude:: included_samples/webforms/ReportParts.aspx
   :emphasize-lines: 6

Embedding the Dashboard
-------------------------------------------
Dashboard List
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page displays the dashboard list.

Create ~\\Dashboard\\Dashboards.aspx:

.. literalinclude:: included_samples/webforms/Dashboards.aspx
   :emphasize-lines: 5

New Dashboard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The page for creating a new dashboard.

Create ~\\Dashboard\\DashboardDesigner.aspx:

.. literalinclude:: included_samples/webforms/DashboardDesigner.aspx
   :emphasize-lines: 5

Dashboard Viewer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This page displays details of a dashboard. It is also requested by the Izenda backend for dashboard exporting functions over the route ``dashboard/view/{id}``. In RouteConfig.cs we have a custom route named ``DashboardViewer``. This custom route will map to the ``dashboard/DashboardViewer.aspx`` page.

Create ~Dashboard\\DashboardViewer.aspx:

.. literalinclude:: included_samples/webforms/DashboardViewer.aspx
   :emphasize-lines: 5
   
.. literalinclude:: included_samples/webforms/DashboardViewer.aspx.cs

The RouteData is used to handle incoming requests to pass the Dashboard Id into the javascript function.

Run Your Izenda Integrated Application
===========================================

Press F5 to run debug

Navigate to login page and enter the values below for the respective fields:

*  Tenant = System
*  Email = IzendaAdmin@system.com 
*  Password = Izenda@123 

On top menu click Settings link then add your license key

.. figure:: /_static/images/webforms_license_key.png
   :width: 900px

   Settings license key

Stop your application and start it again (this step ensures Izenda reloads the cache).

Click Izenda link on the top menu to open the full Izenda app

.. figure:: /_static/images/webforms_full_izenda_app.png
   :width: 900px

   Full Izenda app

Now feel free to explore the entire Izenda integrated application.

Implement Register New Account
===========================================

Modify Register.aspx

.. figure:: /_static/images/webforms_new_account.png
   :width: 900px

   New account screen

Add a new Tenant TextBox field into ~\\Acount\Register.aspx

.. literalinclude:: included_samples/webforms/Register.aspx
   :lines: 11-22
   :emphasize-lines: 3-10

Also, in accordance with the change to Login.aspx to properly nest it inside the form tag, change the ContentPlaceHolderID to the aforementioned placeholder:

.. literalinclude:: included_samples/webforms/Register.aspx
   :lines: 1-4
   :emphasize-lines: 3
   
Create a new folder called "Managers" and Add a new class called "TenantManager" to your project (~\\Managers\\TenantManager.cs). This class is used to get Tenant information from your application's database and create new tenant info for your authentication DB.

.. literalinclude:: included_samples/webforms/TenantManager.cs

Open ~\\Account\Register.aspx.cs and modify the CreateUser_Click method to handle the new registration logic.

When registering a new user, the new user’s information is stored on both the authentication DB and the Izenda DB. To achieve this, we split the registration logic into the steps below:

*  Save new Tenant if needed
*  Save User and Role in authentication DB
*  Save User and Role in Izenda DB
*  Sign in with new user

All steps are encapsulated in the CreateUser_Click method of the Register.aspx.cs file.

Register tenant:

.. literalinclude:: included_samples/webforms/Register.aspx.cs
   :lines: 23-29
   :emphasize-lines: 0

Save user and role information into authentication DB:

.. literalinclude:: included_samples/webforms/Register.aspx.cs
   :lines: 31-34
   :emphasize-lines: 0

Save user and role into IzendaDB:

.. literalinclude:: included_samples/webforms/Register.aspx.cs
   :lines: 35-77
   :emphasize-lines: 0

Login with newly created user:

.. literalinclude:: included_samples/webforms/Register.aspx.cs
   :lines: 84-85
   :emphasize-lines: 0

You can refer to completed implementation of the Register logic on Github `here <https://github.com/Izenda7Series/WebFormsStarterkit/blob/master/WebFormsStarterKit/Account/Register.aspx.cs>`__.

Call the Izenda API Service in C#
===========================================

In the completed sample starter kit on Github, we provide an example demonstrating how to call Izenda's API service in C# code. Reference the ~\\IzendaBoundary\\WebAPIService.cs and ~\\IzendaBoundary\\IzendaUtility.cs files for more detail. 