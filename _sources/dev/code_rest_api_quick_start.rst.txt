:orphan:

===========================================
REST API Quick Start
===========================================

This page provides a quick guide on REST API.

API Endpoint
------------

For convenience, API endpoints are mentioned without the full hostname
and API part. For usage , please prefix the API endpoints with:

    ``http://hostname:port/api/``

For example, with the following API:

   .. code-block:: http
   
      GET databaseSetup/SupportedDatabaseType HTTP/1.1

On our specific server, it would be called as:

   .. code-block:: http
   
      GET http://izenda04.com:8200/api/databaseSetup/SupportedDatabaseType HTTP/1.1

Browser API Clients
-------------------

Some browser API clients for manual testing:

-  `Chrome Advanced REST
   client <https://chrome.google.com/webstore/detail/advanced-rest-client/hgmloofddffdnphfgcellkdfbfbjeloo>`__
-  `Firefox
   RESTclient <https://addons.mozilla.org/en-US/firefox/addon/restclient/>`__

External resources
------------------

-  Another tutorial on REST API - http://www.restapitutorial.com/
