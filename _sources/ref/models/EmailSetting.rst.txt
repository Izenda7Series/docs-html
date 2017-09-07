

===================
EmailSetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **displayName** |br|
         string
      -
      -  The display name
      -
   *  -  **emailFromAddress** |br|
         string
      -
      -  The From email address
      -
   *  -  **useSystemConfiguration** |br|
         boolean
      -
      -  Whether to use system email configuration
      -
   *  -  **server** |br|
         string
      -
      -  The server
      -
   *  -  **port** |br|
         integer
      -
      -  The port
      -
   *  -  **secureConnection** |br|
         boolean
      -
      -  Whether to use SSL/TLS
      -
   *  -  **login** |br|
         string
      -
      -  The login
      -
   *  -  **password** |br|
         string
      -
      -  The password
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -



Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
       "displayName": null,
       "emailFromAddress": "contact@izenda.com",
       "useSystemConfiguration": false,
       "server": "localhost",
       "port": 25,
       "secureConnection": false,
       "login": "mail",
       "password": "EW+9H/VRg8TH0sWNiPuwpg==",
       "tenantId": null,
       "id": "1262295f-2b44-4fa2-9446-cda5e029a15c",
       "state": 0,
       "deleted": false,
       "inserted": true,
       "version": 1,
       "created": "2017-01-05T04:58:20.6430000+07:00",
       "createdBy": "John Doe",
       "modified": "2017-01-05T04:58:20.6430000+07:00",
       "modifiedBy": "John Doe"
      }
