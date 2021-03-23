=========================================================
Add Internal User
=========================================================

.. note::

   Tenant, Data Model and Role should have been created before this step.

   *  :ref:`Add Tenant <POST_tenant>`
   *  :ref:`Add Data Model <POST_dataModel>`
   *  :ref:`Add Role <POST_role>`

It requires 3 steps to fully create an internal user with password and security questions:

#. Create a user with an associated role.

   #. Prepare an empty :doc:`/ref/models/UserDetail` object.
   #. Populate user details.
   #. Populate user role.
   #. Call :ref:`POST_user` API, and receive back the saved id.
#. Generate a :term:`password link` for the user.

   #. Prepares a :doc:`/ref/models/UserDetail` object as API input.
   #. Call :ref:`POST_user/generatePasswordLink` API, and receive back the hash value.
#. Save the password and security questions for user.

   #. Prepares a :doc:`/ref/models/UserDetail` object as API input.
   #. Populate the user password.
   #. Populate the hash value for verification.
   #. Call :ref:`POST_user/passwordAndSecurityQuestion` API.

Empty UserDetail object
------------------------------------------------------------

.. container:: toggle

   .. container:: header

      Empty UserDetail object:

   .. code-block:: json
      :linenos:
      :emphasize-lines: 0

      {
         "id": null,
         "systemAdmin": false,
         "userName": "",
         "tenantId": null,
         "emailAddress": null,
         "roles": [],
         "lastName": "",
         "firstName": "",
         "fullName": null,
         "dataOffset": 0,
         "timestampOffset": 0,
         "cultureName": "",
         "dateFormat": ""
      }

Populate UserDetail object
------------------------------------------------------------

Populate the fields.

*  ``userName``, ``firstName``, ``lastName``,  ``emailAddress``, ``dataOffset``, ``timestampOffset`` and ``dateFormat`` with the user details
*  ``tenantId`` with the actual tenant id |br|
   Get the list of tenants from :ref:`GET_tenant/activeTenants`
*  ``roles`` with the selected role id |br|
   Get the list of roles from :ref:`GET_role/all/(tenant_id)`


.. container:: toggle

   .. container:: header

      Sample populated UserDetail object:

   .. code-block:: json
      :linenos:

      {
         "id": null,
         "systemAdmin": false,
         "userName": "dwebb",
         "tenantId": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
         "emailAddress": null,
         "roles": [
            {
               "id": "98bfcd0c-76eb-46e3-acca-500a6bc18caf"
            }
         ],
         "lastName": "Webb",
         "firstName": "David",
         "fullName": null,
         "dataOffset": 0,
         "timestampOffset": 0,
         "cultureName": "en-US",
         "dateFormat": "MM/DD/YYYY"
      }

Call POST user API
------------------------------------------------------------

#. Receive back the :doc:`/ref/models/OperationResult` object
#. Check that the **success** field equals true.
#. Remember the assigned value in **data.id**.

.. container:: toggle

   .. container:: header

      Sample response:

   .. code-block:: json
      :linenos:

      {
         "success": true,
         "messages": null,
         "data": {
            "password": null,
            "roles": [
               {
                  "name": null,
                  "tenantId": null,
                  "active": false,
                  "notAllowSharing": false,
                  "id": "98bfcd0c-76eb-46e3-acca-500a6bc18caf",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "John Doe",
                  "modified": null,
                  "modifiedBy": null
               }
            ],
            "userRoles": [
               {
                  "userId": "ab4f931f-bd35-420c-b341-b022ea1d1e7c",
                  "roleId": "98bfcd0c-76eb-46e3-acca-500a6bc18caf",
                  "id": "386fb900-2d36-46fe-bc8c-dcebbe88fc4d",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-05-10T04:13:54.7143356",
                  "createdBy": "John Doe",
                  "modified": "2017-05-10T04:13:54.7143356",
                  "modifiedBy": "John Doe"
               }
            ],
            "userSecurityQuestions": null,
            "status": 3,
            "issueDate": "0001-01-01T00:00:00",
            "autoLogin": false,
            "newPassword": null,
            "userName": "dwebb",
            "emailAddress": null,
            "firstName": "David",
            "lastName": "Webb",
            "tenantId": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
            "tenantDisplayId": null,
            "tenantName": null,
            "dataOffset": 0,
            "timestampOffset": 0,
            "initPassword": false,
            "active": false,
            "retryLoginTime": null,
            "lastTimeAccessed": null,
            "passwordLastChanged": null,
            "locked": null,
            "lockedDate": null,
            "cultureName": "en-US",
            "securityQuestionLastChanged": null,
            "dateFormat": "MM/DD/YYYY",
            "systemAdmin": false,
            "notAllowSharing": false,
            "numberOfFailedSecurityQuestion": null,
            "fullName": "David Webb",
            "currentModules": null,
            "id": "d4fdd98f-ac63-4836-a011-6567b2641b3a",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-05-10T04:13:54.7119596",
            "createdBy": "John Doe",
            "modified": "2017-05-10T04:13:54.7119596",
            "modifiedBy": "John Doe"
         }
      }

Generate a :term:`password link` for the user
------------------------------------------------------------

1. Prepare the input :doc:`/ref/models/UserDetail` object.

.. container:: toggle

   .. container:: header

      UserDetail object

   |br|

   *  ``id`` filled with the assigned id
   *  ``userName``, ``firstName``, ``lastName`` and ``emailAddress`` must be the same as the values in the saved user |br|

   .. code-block:: json
      :linenos:
      :emphasize-lines: 2

      {
         "id": "d4fdd98f-ac63-4836-a011-6567b2641b3a",
         "userName": "dwebb",
         "firstName": "David",
         "lastName": "Webb",
         "emailAddress": null
      }

2. Call :ref:`POST_user/generatePasswordLink` API.
3. Receive back the :doc:`/ref/models/OperationResult` object

   #. Check that the **success** field equals true.
   #. Remember the hash value in **data**.

.. container:: toggle

   .. container:: header

      Sample response

   .. code-block:: json
      :linenos:
      :emphasize-lines: 4

      {
         "success": true,
         "messages": null,
         "data": "Abc/Def/...=="
      }

Save the password and security questions for user
------------------------------------------------------------

1. Prepare the input :doc:`/ref/models/UserDetail` object.

.. container:: toggle

   .. container:: header

      UserDetail object

   |br|

   *  ``verification`` filled with the hash value from last step
   *  ``password`` populated with user-selected password
   *  ``userSecurityQuestions`` populated with the secret answers for security questions
   *  ``autoLogin`` true to login the user after this step to immediately use the system

   .. code-block:: json
      :linenos:
      :emphasize-lines: 4,5, 10, 11

      {
         "tenantDisplayID": "stark",
         "tenantName": "Stark Industries",
         "password": "secret",
         "verification": "Abc/Def/...==",
         "userName": "dwebb",
         "firstName": "David",
         "lastName": "Webb",
         "emailAddress": null,
         "userSecurityQuestions": [],
         "autoLogin": true
      }

2. Call :ref:`POST_user/passwordAndSecurityQuestion` API.

   #. Check that the **success** field equals true.
   #. If autoLogin, use the value in **data.token** as ``access_token`` in subsequent REST API calls.

.. container:: toggle

   .. container:: header

      Sample response:

   .. code-block:: json
      :linenos:
      :emphasize-lines: 5

      {
         "success": true,
         "messages": null,
         "data": {
            "token": "Abc/Def/.../==",
            "tenant": "d34515f6-cd6f-4e40-bb65-c930ef61f528",
            "cultureName": "en-US",
            "dateFormat": "MM/DD/YYYY",
            "systemAdmin": false,
            "isExpired": false,
            "notifyDuringDay": null
         }
      }
