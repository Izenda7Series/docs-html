=================================
Using SSL/TLS
=================================
|

Introduction
------------------------------------------

Izenda supports and strongly recommends the use of SSL/TLS to secure traffic between the Front-end, Backend (API) sites. This guides demonstrates how to configure Izenda to us HTTPS.

|

Steps 
-------------------------
#. Add SSL bindings for the API and Front-end sites. The process for doing this will vary, please consult with your technical staff for assistance.
#. Update the izenda_config.js (Front-end) to use the new HTTPS binding for the API

    WebApiUrl:"https://localhost/api/"|br|
    
#. Update the following settings in the IzendaSystemSetting table to use HTTPS. 

.. note::

	The values below are examples, you will need to use values relevant to your particular setup.

.. list-table::
   :widths: 15 30
   :header-rows: 1

   * - Name
     - Value
   * - WebAPIUrl
     - https://localhost:5555/
   * - WebUrl
     - https://localhost:5556/
   * - AuthValidateAccessTokenUrl
     - https://example.com/api/validateAccessToken
   * - AuthGetAccessTokenUrl
     - http://example.com/api/getAccessToken

Common Log Errors
-------------------------

.. note::

	Self-signed & untrusted certificates must be installed on the server hosting the API in order for the Izenda application to "trust" them.
	

* The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.
* System.Security.Authentication.AuthenticationException: The remote certificate is invalid according to the validation procedure.

	    
	 
