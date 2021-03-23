

=================================
System Configuration/Google Map
=================================

The **System Configuration/Google Map** page allows user to set up email
sending options.

#. In browser, log in to Izenda as a user with System Configuration
   permission.

#. Click Settings, then System Configuration then Google Map in the left
   menu.

#. Select the Setting Level: either System or a specific tenant.

      For tenant level, select to re-use configuration from system or to define a separate one. |br|

      .. _System_Configuration_GoogleMap_Configuration:

      .. figure:: /_static/images/System_Configuration_GoogleMap_Configuration.png
         :align: center
         :width: 560px

         Google Map Configuration

#. Enter an Google Map API Key in the proper textbox. Please refer to `Google Map Javascrip API <https://developers.google.com/maps/documentation/javascript/get-api-key/>`_ for the guide to register a key with Google.

#. Turn Google Address toogle ON or OFF to define whether the tenant can use the Geocoding service to draw Google map as Address level or not. Please refer to `Google Geocoding Service <https://developers.google.com/maps/documentation/javascript/geocoding/>`_ for more details.

.. note::

   * Please note that the Google Map API key as well as Geocoding service will be validated from Google side. 
   * Turn ON the Google Address for a tenant that means users in tenant can user the Geocoding service to load the Google Map part as Address Point Option. To specify tenant user can create Google Map part with Address, please turn ON the Tenant Setup > Permission

      .. _System_Configuration_GoogleMap_Configuration:

      .. figure:: /_static/images/System_Configuration_GoogleMap_Tenant_Permission.png
         :align: center
         :width: 320px

         Google Address permission

