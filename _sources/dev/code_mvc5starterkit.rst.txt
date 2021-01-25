===================================
Mvc5Starterkit
===================================

*Understanding The MVC Starter Kit* outlines the contents of the kit and
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
	- **.Net MVC5 Starter Project:** In order to maintain simplicity, our kit uses Microsoft’s default MVC5 Project structure. There may be slight modifications to the code to showcase certain Izenda concepts. This skeleton simulates the role of your application in the embedded process. For more information of the default structure, please see http://jameschambers.com/2014/06/day-2-examining-the-solution-structure/
	- **OWIN Authentication:** In our kit, the OWIN Authentication component simulates the method of logging in to your application. Once you are authenticated with your application, a UserInfo object is generated that contains the username and tenant needed for Izenda authorization.
		* Where/how your authorization token is generated/stored is completely up to you.
		* For more information, please visit https://blogs.msdn.microsoft.com/webdev/2013/07/03/understanding-owin-forms-authentication-in-mvc-5/
	
	- **Izenda:** The main goal of the project is to showcase how to embed Izenda into your MVC application. Of the Izenda portion of the kit, there are components that are required standards for Izenda and other components that are designed as useful guidelines for managing and rendering Izenda. The following are not comprehensive lists—if you have any additional questions regarding what is required, please contact our support team.
		* Required: Required components should not be changed at their core. If they are modified, unexpected behavior may occur.
			* All API resources downloaded from the Upgrade tab in the Izenda Customer Portal. Decompilations of the packaged API is strictly prohibited by your EULA.
			* All Embedded UI resources downloaded from the Upgrade tab in the `Customer Portal <https://app.izenda.com>`_. Note: If an open source version of the Embedded UI is released, modifications will not be supported by the Izenda Support team. Decompilations of the packaged Embedded UI is strictly prohibited by your EULA.
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

-  AccountController.cs

   * Register, line 162

Izenda User Authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^

-  **Login.cshtml:** User input form for login information
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
-  Report Parts are rendered using Mvc5StarterKit -> Views -> Report -> ReportParts.cshtml
-  Report Parts to be rendered are defined by report part id in Mvc5StarterKit -> Scripts -> izenda.integrate.js

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
	
-  Reports can be rendered using a specific report id using Mvc5StarterKit -> Views -> Report -> ReportViewer.cshtml
-  The report id can be configured Mvc5StarterKit -> Views -> Shared -> _Layout.cshtml

::

	<li>@Html.ActionLink("Report Viewer", "ReportViewer", "Report", new { id = "<add your report id here>" }, null)</li>

Hidden Filters
^^^^^^^^^^^^^^^^^^^	
-  Hidden Filter examples are shown in Mvc5StarterKit -> IzendaBoundary -> CustomAdhocReport.cs

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

App\_Start
^^^^^^^^^^

   This folder is contained at the root directory and is among the main
   driving components of an MVC Solution. This folder's classes are
   explained below

   *  **Startup.Auth.cs:** This class supports OWIN authentication. For a
      high level understanding, OWIN defines a standard interface between .NET
      web servers and web applications. The Startup.Auth.cs gives you the
      flexibility to integrate your application to allow users for quick
      authentication modes such as using google and facebook accounts as their
      preferred logins.

   *  **BundleConfig.cs**: This class allows developers to bundle
      javascript and css files. With so many javascript and css classes that
      an MVC solution might reference, each call to a resource for example has
      the potential to reference multiple of these files which as a result can
      significantly impact the load time of a page. Below are some of Izenda's
      bundled javascipt files to allow your page for faster rendering.

      .. code-block:: javascript

          bundles.Add(new ScriptBundle("^/bundles/izenda").Include(
                                  "^/Scripts/izenda/izenda_common.js",
                                  "^/Scripts/izenda/izenda_locales.js",
                                 "^/Scripts/izenda/izenda_vendors.js",
                                 "^/Scripts/izenda/izenda_ui.js",
                                 "^/Scripts/izenda.integrate.js",
                                 "^/Scripts/izenda.utils.js"));

   *  **RouteConfig.cs:** This class contains all the routing
      configuration for your urls in an MVC application. A Route simply
      defines a url pattern that is mapped to handler. Notice, that the url
      doesn't necessarily have to point to a file. A developer can define a
      more user friendly url pattern. This in return will be mapped to a
      handler to reference the MVC controllers.

Izenda's Web.config overview
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Izenda utilizes **Nancy**, a light-weight framework for building HTTP
based services on .NET and Mono. Nancy supports all the common HTTP
methods such as the DELETE, GET, HEAD, OPTIONS, POST, PUT and PATCH
requests.

Below is the default configuration for both httpHandlers and Handlers
settings.

.. code-block:: xml

    <httpHandlers>
          <add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="api/*" />
    </httpHandlers>

    <handlers>
          <add name="Nancy" verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="api/*" />
    </handlers>

.. note::

   * httpHandlers ->     this setting is used for sites running on  IIS 5 – 6, or IIS 7.x in Classic mode (IIS 6 compatibility mode).
   * handlers     ->     this setting is used for sites running on sites running on IIS 7.x (Integrated mode).

Understanding the Data Model
----------------------------

    *This section outlines the databases defined in the MVC starter
    kit.*

Izenda Configuration Database 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

:doc:`/ref/spec_izendasystemsetting_table`


MVC5 User Database
^^^^^^^^^^^^^^^^^^

    ''The MVC5 User Database is located within the *'[insert database
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
   		* GetToken (line 481): Hard-coded for the default admin to allow user to set Izenda database connection string and license key
   *  Account Controller
	   * Account/login (line 73): Login to your.net application with tenant, email, password
	   * Register




Updates
-------

06/23/2017
^^^^^^^^^^

If you are using a different route thatn Izenda's default API route (/api), the URL must be set in the web.config.


05/08/2017
^^^^^^^^^^

**Updates to the Mvc5StarterKit required for exporting:**

If your API is separate (deployment mode 1), you will need to set Public and Private RSA Keys. Previous versions of the deployment mode didn’t require any sort of keys and, since you don’t need a password to be authorized for this deployment mode, you can simply call the API with the tenant unique name and user name have access to Izenda (bad). We implemented the RSA Keys for verification that the source of your API calls are correct.

With the latest update of Izenda, we have made a few changes to the database to ensure that deployment mode 1 is as secure as deployment modes 0 and 3. There are now two RSA keys (public and private) found within Izenda. Since these values aren't updated, a System.Security.XmlSyntaxException was thrown and documented in your log file.

The keys can be declared in the following locations:

  1. AuthRSAPublicKey value in the IzendaSystemSettings table of the Izenda database (note: only use keysize < 1024 to generate because max-length for this field in database is 256) . This value is your public key and should be in XML format.
  2. And RSAPrivateKey value in Web.config file of the MVC Kit. This value is your private key and should be in PEM format.
  
To generate your RSA keys, you can use our RSA Key Generator utility found at https://izenda.com/utilities/Izenda.Synergy.RSATool.zip .

02/08/2017
^^^^^^^^^^

**Updates to the Mvc5StarterKit required for exporting:**

1. Ensure you have set the front end url in the IzendaSystemSettings
table for WebUrl If you are using the standard MvcStarterKit it will be
set in dbo.IzendaSystemSetting table in Izenda.mdf file. The standard
value for the kit is: http://localhost:14809/

2. Add a new route to Mvc5StarterKit/App\_Start/RouteConfig.cs
routes.MapRoute(

| ``               name: "ReportPart",``
| ``               url: "viewer/reportpart/{id}",``
| ``               defaults: new { controller = "Home", action = "ReportPart" }``
| ``           );``

3. Add the following method to
Mvc5StarterKit/Controllers/HomeController.cs

::

     public ActionResult ReportPart(Guid id, string token)
            {
                ViewBag.Id = id;
                ViewBag.Token = token;
                return View();
            }

4. Add the following methods to
Mvc5StarterKit/Scripts/izenda.integrate.js

::

    // Render report part
    var izendaInitReportPartViewer = function (reportPartId) {
        function successFunc(data, status) {
            var currentUserContext = {
                token: data.token
            };
            IzendaSynergy.setCurrentUserContext(currentUserContext);
            IzendaSynergy.renderReportPart(document.getElementById('izenda-root'), {
                id: reportPartId
            });
        }
        this.DoRender(successFunc);
    };
    var izendaInitReportPartExportViewer = function (reportPartId, token) {
        var currentUserContext = {
            token: token
        };
        IzendaSynergy.setCurrentUserContext(currentUserContext);
        IzendaSynergy.renderReportPart(document.getElementById('izenda-root'), {
            id: reportPartId,
            useQueryParam: true,
            useHash: false
        });
    };

5. Create a new View named Mvc5StarterKit/Views/Home/ReportPart.cshtml:

::

    @{
       Layout = "^/Views/Shared/Izenda_Layout.cshtml";
       ViewBag.Title = "Report Viewer";
    }

    @section scripts
    {
       <script type="text/javascript">
           $(document).ready(function () {
               izendaInitReportPartExportViewer('@ViewBag.Id', '@ViewBag.Token');
               
           });
       </script>
    }
    <style>
       #izenda-root>.izenda {
           background-color: transparent !important;
       }
    </style>

    <div class="izenda-container" id="izenda-root" style="margin-top:0px;"></div>

6. Move the line below in
Mvc5StarterKit/Views/Shared/Izenda\_Layout.cshtml Move line below
(originally at line 58)

::

    @RenderSection("scripts", required: false)

Just before the closing body tag, e.g.

::

       @RenderSection("scripts", required: false)
    </body>
    </html>

7. Move the line below in Mvc5StarterKit/Views/Shared/\_Layout.cshtml

Move line below (originally at line 99)

::

    @RenderSection("scripts", required: false)

Just before the closing body tag, e.g.

::

       @RenderSection("scripts", required: false)
    </body>
    </html>

8. Alter the file Mvc5StarterKit/Web.config (Optional) At line 44,
change the extension of the Izenda-log file to .log

::

    <file value="logs\izenda-log.txt" />

Change to

::

    <file value="logs\izenda-log.log" />

9. Edit the Post Build Events replace what is currently there with
below. This will allow maps to be used as report parts in the
Mvc5StarterKit:

::

    XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\Content" "$(ProjectDir)\bin\Content\"
    XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\EmailTemplates" "$(ProjectDir)\bin\EmailTemplates\"
    XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\Export" "$(ProjectDir)\bin\Export\"
    XCOPY /S /I /Y  "$(ProjectDir)IzendaReferences\Resources" "$(ProjectDir)\bin\Resources\"
    XCOPY /S /I /Y  "$(ProjectDir)IzendaResources\Content\maps" "$(ProjectDir)\Content\maps\"
