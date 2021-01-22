===================================
MvcCoreStarterkit
===================================

*Understanding the MVC Starter Kit* outlines the contents of the kit and
where particular functionality is showcased.

.. note::

   The MVC Kit is designed for demonstration purposes and should not be
   used as an "as-is" fully-integrated solution. You can use the kit for
   reference or a baseline but ensure that security and customization meet
   the standards of your company.

For MVC set up steps, please refer to the :doc:`/install/doc_mvc_setup_guide`.


Packages Used
^^^^^^^^^^^^^^
The following is not a comprehensive list but it will give you a good idea of the packages used for Izenda’s authentication/authorization.
   - **.Net MVC Core Starter Project:** In order to maintain simplicity, our kit uses Microsoft’s default MVCCore Project structure. There may be slight modifications to the code to showcase certain Izenda concepts. This skeleton simulates the role of your application in the embedded process. 
   - **OWIN Authentication:** In our kit, the OWIN Authentication component simulates the method of logging in to your application. Once you are authenticated with your application, a UserInfo object is generated that contains the username and tenant needed for Izenda authorization.
      * Where/how your authorization token is generated/stored is completely up to you.
      * For more information, please visit https://blogs.msdn.microsoft.com/webdev/2013/07/03/understanding-owin-forms-authentication-in-mvc-5/
   
   - **Izenda:** The main goal of the project is to showcase how to embed Izenda into your MVC application. Of the Izenda portion of the kit, there are components that are required standards for Izenda and other components that are designed as useful guidelines for managing and rendering Izenda. The following are not comprehensive lists—if you have any additional questions regarding what is required, please contact our support team.
      * Required: Required components should not be changed at their core. If they are modified, unexpected behavior may occur.
         * All API resources downloaded from the Upgrade tab in the `Customer Portal<https://app.izenda.com/>`_. Decompilations of the packaged API is strictly prohibited by your EULA.
         * All Embedded UI resources downloaded from the Upgrade tab in the `Customer Portal<https://app.izenda.com/>`_. Note: If an open source version of the Embedded UI is released, modifications will not be supported by the Izenda Support team. Decompilations of the packaged Embedded UI is strictly prohibited by your EULA.
         * Where/how your authorization is stored is completely up to you. For embedded scenarios, however, we require that you provide the Izenda user name and the unique tenant name.
      * Suggested: Our kit is home to a plethora of embedded examples ranging from tenant CSS cusomization to numerous configurations of rendering the Izenda UI. These examples may not be necessary to build a fully-operational Application. For more information, please see the "Location and Description of Features" section below.



Location and Description of Features
-------------------------------------

    *This section outlines the key features of the MVC starter kit and
    which files to review for each feature.*

Unique Styling For Tenants
^^^^^^^^^^^^^^^^^^^^^^^^^^

-  Content Folder for tenants

   * Equals TenantID
   * Top of Layout.cshtml

Izenda User Creation
^^^^^^^^^^^^^^^^^^^^

-  •	~\\ Areas\\Identity\\Pages\\Account\\Register.cshtml.cs

   * Register, line 75

Izenda User Authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^

-  **~\\Areas\\Identity\\Pages\\Account\\Login.cshtml** User input form for login information
-  **UserInfo.cs:** Contains the definition of the token required for Izenda. This includes 2 public strings UserName and TenantUniqueName. Upon successful authentication, a UserInfo object is created in the model.
-  **UserController.cs:** The UserController only handles users logging
   into the MVC application. Once they log in, a token generated with
   their information that will then be used in IzendaTokenAuthorization
-  **IzendaTokenAuthorization.cs**
   * GetToken (line 18): Used to get/generate the token based off of a UserInfo object in order to use it for RESTful API calls. This function is called whenever you are attempting an Izenda process.
   * GetUserInfo (line 36): Takes the token from Izenda and decrypts it to get the user info to use it for RESTful API calls


-  **AccountController.cs**

   * Login, line 73

Rendering Izenda UI
^^^^^^^^^^^^^^^^^^^

-  **Izenda.integrate.js:** This is the backbone for rendering Izenda into our kit. The 216 lines of code contain a plethora of examples of how to render single Izenda components, how to render single Izenda pages, and even how to embed Izenda as a whole. You are certainly welcome to use this file in your own development but you may find it useful to tailor it to your needs.
-  Views -> Home and Views -> Report

Rendering Report Parts & Reports
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
-  Report Parts are rendered using MVCCoreStarterKit -> Views -> Report -> ReportParts.cshtml
-  Report Parts to be rendered are defined by report part id in MVCCoreStarterKit -> Scripts -> izenda.integrate.js

::

   var izendaInitReportPartDemo = function () {

      function successFunc(data, status) {
         console.info(data);
         var currentUserContext = {
            token: data.token
         };

         // You can add report parts after creating reports using the context below 
         // Add the report part ID's in the <add your report part id here> area
         IzendaSynergy.setCurrentUserContext(currentUserContext);
         IzendaSynergy.renderReportPart(document.getElementById('izenda-report-part1'), {
            "id": "<insert your id here>",
         });

         IzendaSynergy.renderReportPart(document.getElementById('izenda-report-part2'), {
            "id": "<insert your id here>",
         });
    
         IzendaSynergy.renderReportPart(document.getElementById('izenda-report-part3'), {
            "id": "<insert your id here>"
         });
      }
      this.DoRender(successFunc);
   };
   
-  Reports can be rendered using a specific report id using MVCCoreStarterKit -> Views -> Report -> ReportViewer.cshtml
-  The report id can be configured MVCCoreStarterKit -> Views -> Shared -> _Layout.cshtml

::

   <li>@Html.ActionLink("Report Viewer", "ReportViewer", "Report", new { id = "<add your report id here>" }, null)</li>

Hidden Filters
^^^^^^^^^^^^^^^^^^^	
-  Hidden Filter examples are shown in MVCCoreStarterKit -> IzendaBoundary -> CustomAdhocReport.cs

Understanding the Front End Contents
------------------------------------

    *This section outlines the front end components defined in the MVC
    starter kit. It does not outline Izenda's front end but rather the
    front end components a developer might define in an integrated
    scenario.*

Understanding the Back End Contents
-----------------------------------

    *This section outlines the back end components defined in the MVC
    starter kit. It does not outline Izenda's API but rather the back
    end components a developer might define in an integrated scenario.*

Startup.cs
^^^^^^^^^^



Izenda's AppSettings.json
^^^^^^^^^^^^^^^^^^^^^^^^^^^^



Understanding the Data Model
----------------------------

    *This section outlines the databases defined in the MVC starter
    kit.*

Izenda Configuration Database 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:doc:`/ref/spec_izendasystemsetting_table`


MVCCore User Database
^^^^^^^^^^^^^^^^^^

    ''The MVCCore User Database is located within the *'[insert database
    location here]. It simulates a your company's database information
    and is used to accurately route to a user in the Izenda
    Configuration Database.*

Methods of Calling the Izenda API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Depending on your deployment mode, you may want to invoke the Izenda API in different ways. Our standard MVC Kit provides examples for both RESTful API Calls and .Net API Calls 
   * RESTful API Calls
      * Home Controller
      * IzendaUtlility.cs
         * Add Role
         * Alter Data Sources
   * .Net API Calls
      * Home Controller
         * GetToken (line 536): Hard-coded for the default admin to allow user to set Izenda database connection string and license key
   * Account Controller
      * OnPostAsync (line 75): Login to your.net application with tenant, email, password
      * Register




