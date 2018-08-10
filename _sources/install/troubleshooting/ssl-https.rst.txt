=================================
SSL and HTTPS
=================================
|

Application throws errors when SSL is used
--------------------------------------

Self-signed & untrusted certificates must be installed on the server hosting the API in order for the Izenda application to "trust" them.

Common log errors:

* The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.
* System.Security.Authentication.AuthenticationException: The remote certificate is invalid according to the validation procedure.

When using TLS v1.2 Certificates 
--------------------------------------

The following error may appear in your Izenda log file

* System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The request was aborted: Could not create SSL/TLS secure channel.

Please change the API Web.Config file to use the 4.6 httpRuntime element as below:

.. code-block:: xml

	
  <system.web>
    <compilation debug="true" targetFramework="4.6" />
    <httpRuntime maxRequestLength="1048576" targetFramework="4.6"/>
    <httpHandlers>
      <add verb="*" type="Nancy.Hosting.Aspnet.NancyHttpRequestHandler" path="api/*" />
    </httpHandlers>
  </system.web>
