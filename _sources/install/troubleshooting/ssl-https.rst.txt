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
