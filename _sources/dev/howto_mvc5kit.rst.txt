================================================
Deployment Mode 3: Building the MVC Starter Kit
================================================

.. contents:: Table of Contents

Introduction
===========================================

This guide will give you an overview of the major aspects of an Izenda integration with an MVC5 web application.

The purpose of the guide is to abstract from the core of the Izenda MVC 5 Starter Kit guide the overarching concepts of back end and front-end integration.

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

You can view the contents of Izenda.integrate.js `here <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Scripts/izenda.integrate.js>`__.

Using the render functions
-------------------------------------------

Once the EmbeddedUI front-end resources are in place, and we’ve configured the configuration, authentication, and render functions. The last thing to do is use these bundled JavaScript functions within our application’s front-end to render specific Izenda containers/pages.

This is done in the `Embedded Front-end <https://www.izenda.com/docs/dev/howto_mvc5kit.html#embedding-front-end-izenda-izenda-ui>`_ section of the guide below.

Security Handshake
===========================================

The basic Izenda security handshake is handled through a token which contains two key pieces of user metadata, a unique user identifier, and a unique tenant identifier. You’ll handle role level details through the back-end integration.

The point here is to create the medium through which Izenda will authenticate interactions between the front-end and back-end API endpoints.

In the `IzendaConfig`_ we’ll create the token for the end-user authentication that will eventually be passed to Izenda’s API endpoints through IzendaSynergy currentUserContext.

As you’ll see in that section that token contains two values originating from the MVC application’s tenant and user store. 

We then pass these values through the token we create along with Izenda’s render functions in the Izenda.integrate.js file.

There is no separate login process for Izenda specifically, rather Izenda just sits behind the existing application’s authentication process and inherits a few key values.

You can see an example of the token getting passed into Izenda’s currentUserContext in `izenda.integrate.js <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Scripts/izenda.integrate.js#L54>`__.

Most of the work here is done in the `Custom Authentication Logic`_ section of the guide below.

There is work beyond just generating the handshake token in that section, as there is additional configuration being done specific to the MVC application to add a Tenant concept to its security model.

Back-end Integration
===========================================

Through front-end integration we are rendering pages, parts, and containers and through the security handshake we are placing Izenda behind an existing authentication process.

Through back-end integration we are using hooks within Izenda to inherit an existing security model.

The basic concept here is that we want to populate in Izenda existing tenant, role, and user associations.

Now when users are authenticated Izenda will be able to appropriately govern what data, features, and reports or dashboards it might expose to the end-user. You can also define these permissions through the EmbeddedUI interfaces, C#, or API endpoints.

This can be done through either exposed C# methods, or through REST API endpoints.

Back-end Integration through C#
-------------------------------------------

This method of back-end integration is typically done when integrating with other .NET web applications, however you might use this approach in scenarios where you would want Izenda to pull, through LINQ expressions, SQL Queries, Web Services, or other REST APIs, the Tenant, Role, and User Metadata you would like Izenda to inherit.

`Sample Starter Kit <https://github.com/Izenda7Series/Mvc5StarterKit>`__

The MVC5 Starter Kit demonstrates the C# method approach in depth. This application has both the Izenda EmbeddedUI and API as a part of its codebase, with no components of Izenda running separately.

Most of the interaction is done in the `AccountController <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Controllers/AccountController.cs>`__.

In that file, you can see several references to Izenda DLLs which provide access to exposed methods and classes that are relevant to managing Tenants, Roles, and Users programmatically.

We are syncing between the MVC application’s security model and Izenda’s to make them essentially equivalent.

You can see starting `here <https://github.com/Izenda7Series/Mvc5StarterKit/blob/master/Mvc5StarterKit/Controllers/AccountController.cs#L159>`__ that we are using methods to pass values directly from the MVC application’s security model into Izenda’s by equivocating the MVC application’s Tenant, Role, and User variables with Izenda’s. While some areas of this code contain hard-coded values, in real world implementations those values get replaced with variables or lookups.

Much of the code used in the account controller is supported by contents of the `IzendaBoundary <https://github.com/Izenda7Series/Mvc5StarterKit/tree/master/Mvc5StarterKit/IzendaBoundary>`__ directory and `Models <https://github.com/Izenda7Series/Mvc5StarterKit/tree/master/Mvc5StarterKit/Models>`__ from the MVC kit.

Back-end Integration through the API
-------------------------------------------

For non-.NET applications, or API push event based approaches you can interact purely with Izenda’s REST API endpoints without having to interact with the application layer at a C# level.

`Sample Starter Kit  <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone>`__

The MVC5 Starter Kit Back-end Standalone demonstrates integration of Izenda with an MVC application with only the Izenda EmbeddedUI being a part of the MVC application’s codebase, while Izenda’s API runs as a separate application.

Because the Izenda .NET codebase is not local to the MVC application, the only method by which security models can be synced is through the Izenda API REST API endpoints.

In this codebase we do some of the work in the `AccountController <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/Controllers/AccountController.cs>`__ and some of the work in `IzendaBoundary <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/tree/master/Mvc5StarterKit/IzendaBoundary>`__ files.

In `AccountController <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/Controllers/AccountController.cs#L155>`__ we are creating push events that ensure when new tenants, roles, or users and here we are using an administrative token to handle system level interactions. This is a separate token specifically for back-end work, rather than a token for end-user authentication.

The Admin token gets generated in the `IzendaTokenAuthorization <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/IzendaBoundary/IzendaTokenAuthorization.cs>`__ file separately from the end-user token. 

In the `IzendaBoundary <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/tree/master/Mvc5StarterKit/IzendaBoundary>`__ directory we’re defining the basic `WebAPIService <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/IzendaBoundary/WebApiService.cs>`__ and `Tenant <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/IzendaBoundary/Models/TenantDetail.cs>`__, `Role <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/IzendaBoundary/Models/RoleInfo.cs>`__, and `User <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/blob/master/Mvc5StarterKit/IzendaBoundary/Models/UserDetail.cs>`__ models that the MVC application will use to interact with the Izenda API endpoints. 

Within any application codebase you’ll need to design and implement similar concepts to sync Izenda with existing security models.

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

MVC Setup guide
======================

* MVC5 Integration Setup, please prefer: :doc:`/dev/mvc5_setup_guide`
* MVC Core Integration Setup, please prefer: :doc:`/dev/mvc_core_setup_guide`