

============================
User APIs
============================

The User APIs are used in the log in, log out, user setup and migration features.

Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 45 30
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `GET user/all/(tenant_id)`_
     - Returns an array of users, filtered by tenant_id if available.

       Deprecated, please use `POST user/all`_ to avoid timeouts loading large data.
     - Settings menu > User Setup
   * - `POST user/all`_
     - Returns an array of users by tenant.
     - Settings menu > User Setup
   * - `POST user/load`_
     - Returns an array of users for Report Access or Schedule, with paging.
     - Report Designer > Schedule > Add Schedule > select Recipient(s) |br|
       Report Designer > Access > Add Sharing > Share With > User > select
   * - `POST user/login`_
     - Performs login.
     - Login page
   * - `POST user/logout`_
     - Performs logout.
     - User section in page header > Sign Out
   * - `POST user`_
     - Saves a user.

       .. note::

          To set up a user with password, this API is only the first step. See :doc:`/dev/code_javascript_add_internal_user` for the guide.
     - Settings menu > User Setup > Add User > Save
   * - `POST user/userProfile`_
     - Saves a user profile.
     - not used
   * - `POST user/passwordProfile`_
     - Saves a password profile.
     - not used
   * - `POST user/securityQuesitions`_
     - Saves security questions for a user.

       .. note::

          Will be renamed to securityQuestions
     - User section in page header > My Profile > Security Options > Change Security Options > Save
   * - `POST user/password`_
     - Saves password for a user.

       .. note::

          Obsolete, use `POST user/passwordAndSecurityQuestion`_ instead
     - Not used
   * - `POST user/active`_
     - Activates a user.
     - Settings menu > User Setup > Activate link
   * - `POST user/deactive`_
     - Deactivates a user.
     - Settings menu > User Setup > Deactivate link
   * - `DELETE user/{user_id}`_
     - Deletes a user.
     - Settings menu > User Setup > Delete link
   * - `POST user/passwordAndSecurityQuestion`_
     - Saves a user password and security question.
     - Password Link page > Save
   * - `GET user/securityQuestion/{user_name}/(tenant_display_id)`_
     - Returns security question for a user and tenant.
     - User section in page header > My Profile > Security Options
   * - `POST user/generatePasswordLink`_
     - Generates :term:`password link`.
     - Settings menu > User Setup > Configure Password Option > Generate Password Link
   * - `POST user/validatePasswordLink`_
     - Validates :term:`password link`.
     - Not used
   * - `POST user/validateSecurityQuestion`_
     - Validates security questions.
     - Not used
   * - `POST user/validateUserInfo`_
     - Validates user information.
     - Not used
   * - `POST user/validateExpirationPasswordLink`_
     - Validates password expiration link.
     - When user opens password link
   * - `POST user/sendPasswordLink`_
     - Sends :term:`password link` via email to user.
     - Settings menu > User Setup > Configure Password Option > Generate Password Link > Send password link in email
   * - `POST user/integration/saveUser`_
     - Adds or updates external user.

       .. versionchanged:: 1.25

          Used to be named "intergration"
     - Not used
   * - `POST user/validateUserRoleAssociation`_
     - Validates user and role association after some roles are removed.
     - Settings menu > User Setup > remove a role > Save
   * - `POST user/allowedSharingUsers/(tenant_id)`_
     - Returns a list of users allowed to be selected in report/dashboard access.
     - Report Designer > Access > Add Sharing
   * - `GET user/isLastSystemAdmin`_
     - Checks if the number of not deleted system admins equals 1.
     - Settings menu > User Setup > delete a system admin
   * - `POST external/user`_
     - Add or update external user.

       .. versionadded:: 2.6.16

     - To be updated

GET user/all/(tenant_id)
--------------------------------------------------------------

Returns an array of users, filtered by tenant_id if available.

**Request**

    No payload

**Response**

    An array of :doc:`models/UserDetail` objects

**Samples**

   .. code-block:: http

      GET /api/user/all HTTP/1.1

   .. container:: toggle

      .. container:: header
      
         Sample Response:

      .. code-block:: json

         [
            {
               "password": null,
               "roles": [],
               "userRoles": null,
               "userSecurityQuestions": null,
               "status": 1,
               "issueDate": "0001-01-01T00:00:00",
               "autoLogin": false,
               "newPassword": null,
               "userName": "johndoe@system.com",
               "emailAddress": "johndoe@system.com",
               "firstName": "John",
               "lastName": "Doe",
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "tenantDisplayId": null,
               "tenantName": null,
               "dataOffset": null,
               "timestampOffset": null,
               "initPassword": false,
               "active": true,
               "retryLoginTime": null,
               "lastTimeAccessed": null,
               "passwordLastChanged": null,
               "locked": null,
               "lockedDate": null,
               "cultureName": null,
               "securityQuestionLastChanged": null,
               "dateFormat": "MM/DD/YYYY",
               "systemAdmin": false,
               "notAllowSharing": false,
               "numberOfFailedSecurityQuestion": null,
               "fullName": "John Doe",
               "currentModules": null,
               "id": "f6923261-b8bf-4f7a-a5a6-7d7ca61d8ccb",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-09-08T07:54:22.597",
               "createdBy": "$RootAdmin$",
               "modified": "2017-09-08T07:54:22.597",
               "modifiedBy": "$RootAdmin$"
            },
            {
               "password": null,
               "roles": [
                     {
                        "name": "Manager",
                        "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
                        "active": true,
                        "notAllowSharing": false,
                        "id": "d256d058-aeb7-468f-9f95-962d65979707",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 4,
                        "created": "2017-09-08T07:11:11.24",
                        "createdBy": "$RootAdmin$",
                        "modified": "2017-09-15T07:12:01.527",
                        "modifiedBy": null
                     }
               ],
               "userRoles": null,
               "userSecurityQuestions": null,
               "status": 1,
               "issueDate": "0001-01-01T00:00:00",
               "autoLogin": false,
               "newPassword": null,
               "userName": "Acme@system.com",
               "emailAddress": "acme@system.com",
               "firstName": "Anna",
               "lastName": "Belle",
               "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
               "tenantDisplayId": null,
               "tenantName": null,
               "dataOffset": null,
               "timestampOffset": null,
               "initPassword": false,
               "active": true,
               "retryLoginTime": null,
               "lastTimeAccessed": null,
               "passwordLastChanged": null,
               "locked": null,
               "lockedDate": null,
               "cultureName": null,
               "securityQuestionLastChanged": null,
               "dateFormat": "MM/DD/YYYY",
               "systemAdmin": false,
               "notAllowSharing": false,
               "numberOfFailedSecurityQuestion": null,
               "fullName": "Poke Pippi",
               "currentModules": null,
               "id": "14fbf9ac-2d7b-41e9-a272-dd51e161914d",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 2,
               "created": "2017-09-15T07:12:01.74",
               "createdBy": "$RootAdmin$",
               "modified": "2017-09-15T07:26:29.357",
               "modifiedBy": "$RootAdmin$"
            }
         ]

POST user/all
--------------------------------------------------------------

Returns an array of users by tenant.

**Request**

    A :doc:`models/PagedRequest` object

    .. note::
       
       The keys for :doc:`models/SearchCriteria` that this API support: |br|
       - UserName |br|
       - EmailAddress |br|
       - Role |br|
       - FullName |br|
       - All

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/UserDetail` objects

**Samples**

   .. code-block:: http

      POST /api/user/all HTTP/1.1

   Request Payload::

      {
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "skipItems": 0,
         "pageSize": 100,
         "criteria": [{
            "key": "FullName",
            "value": "John",
            "operation":1
         }]
      }

   Sample response::

      {
         "result": [
            {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "John Doe",
                  "emailAddress": "johndoe@system.com",
                  "firstName": "John",
                  "lastName": "Doe",
                  "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": null,
                  "timestampOffset": null,
                  "initPassword": false,
                  "active": true,
                  "retryLoginTime": null,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": null,
                  "lockedDate": null,
                  "cultureName": null,
                  "securityQuestionLastChanged": null,
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": null,
                  "fullName": "John Doe",
                  "currentModules": null,
                  "id": "f6923261-b8bf-4f7a-a5a6-7d7ca61d8ccb",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-09-08T07:54:22.597",
                  "createdBy": "$RootAdmin$",
                  "modified": "2017-09-08T07:54:22.597",
                  "modifiedBy": "$RootAdmin$"
            }
         ],
         "pageIndex": 1,
         "pageSize": 100,
         "total": 1,
         "skipItems": 0,
         "isLastPage": true
      }

POST user/load
--------------------------------------------------------------

Returns an array of users for Report Access or Schedule, with paging.

**Request**

    A :doc:`models/UserPagedRequest` object

    .. note::
       
       The keys for :doc:`models/SearchCriteria` that this API support: |br|
       - UserName |br|
       - EmailAddress |br|
       - Role |br|
       - FullName |br|
       - All

**Response**

    A :doc:`models/PagedResult` object with **result** field containing an array of :doc:`models/UserDetail` objects

**Samples**



   .. code-block:: http

      POST /api/user/load HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload for Report Access:

      .. code-block:: json

         {
            "userModeType": 1,
            "searchByRole": [
               {
                  "id": "38bf8593-6a66-46e5-92a4-8d901f0088a9",
                  "name": "anna_role",
                  "users": [
                     {
                        "id": "9b54835b-0743-46e1-9353-a17a5380f3f3",
                        "userName": "anna",
                        "lastName": "domino",
                        "firstName": "anna",
                        "emailAddress": null
                     }
                  ]
               },
               {
                  "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd283",
                  "name": "Appraiser",
                  "users": [
                     {
                        "id": "9d2f1d51-0e3d-44db-bfc7-da94a7681bf9",
                        "userName": "juan",
                        "lastName": "Carlos",
                        "firstName": "Juan",
                        "emailAddress": "izendateam@gmail.com"
                     },
                     {
                        "id": "5cf7e984-bb0e-46b5-b856-530389b3b885",
                        "userName": "teddy",
                        "lastName": "Bear",
                        "firstName": "Teddy",
                        "emailAddress": "izendateam@gmail.com"
                     }
                  ]
               },
               {
                  "id": "00653587-3604-45ae-ad08-178bf4554fe4",
                  "name": "DB",
                  "users": [
                     {
                        "id": "9d2f1d51-0e3d-44db-bfc7-da94a7681bf9",
                        "userName": "juan",
                        "lastName": "Carlos",
                        "firstName": "Juan",
                        "emailAddress": "izendateam@gmail.com"
                     }
                  ]
               }
            ],
            "tenantId": null,
            "criteria": [
               {
                  "key": "all",
                  "value": "",
                  "operation": 1
               }
            ],
            "pageIndex": 1,
            "pageSize": 10,
            "sortOrders": [
               {
                  "key": "userName",
                  "descending": true
               }
            ]
         }


   .. container:: toggle

      .. container:: header

         Sample Response:

      .. code-block:: json

         {
            "result": [
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "anna_role",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "38bf8593-6a66-46e5-92a4-8d901f0088a9",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 3,
                        "created": "2017-05-22T07:30:07.55",
                        "createdBy": "anna domino",
                        "modified": "2017-07-26T06:36:53.897",
                        "modifiedBy": "anna domino"
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 3,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "anna",
                  "emailAddress": null,
                  "firstName": "anna",
                  "lastName": "domino",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": null,
                  "timestampOffset": null,
                  "initPassword": false,
                  "active": false,
                  "retryLoginTime": null,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": null,
                  "lockedDate": null,
                  "cultureName": null,
                  "securityQuestionLastChanged": null,
                  "dateFormat": null,
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": null,
                  "fullName": "anna domino",
                  "currentModules": null,
                  "id": "9b54835b-0743-46e1-9353-a17a5380f3f3",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "anna domino",
                  "modified": null,
                  "modifiedBy": null
               },
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "Appraiser",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd283",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 44,
                        "created": null,
                        "createdBy": "anna domino",
                        "modified": "2017-05-22T06:39:38.657",
                        "modifiedBy": null
                     },
                     {
                        "name": "DB",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "00653587-3604-45ae-ad08-178bf4554fe4",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 10,
                        "created": "2016-10-08T08:27:18.807",
                        "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                        "modified": "2017-06-20T04:56:44.947",
                        "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 3,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "juan",
                  "emailAddress": "izendateam@gmail.com",
                  "firstName": "Juan",
                  "lastName": "Carlos",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": null,
                  "timestampOffset": null,
                  "initPassword": false,
                  "active": false,
                  "retryLoginTime": null,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": null,
                  "lockedDate": null,
                  "cultureName": null,
                  "securityQuestionLastChanged": null,
                  "dateFormat": null,
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": null,
                  "fullName": "Juan Carlos",
                  "currentModules": null,
                  "id": "9d2f1d51-0e3d-44db-bfc7-da94a7681bf9",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "anna domino",
                  "modified": null,
                  "modifiedBy": null
               },
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "Appraiser",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd283",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 44,
                        "created": null,
                        "createdBy": "anna domino",
                        "modified": "2017-05-22T06:39:38.657",
                        "modifiedBy": null
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 3,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "teddy",
                  "emailAddress": "izendateam@gmail.com",
                  "firstName": "Teddy",
                  "lastName": "Bear",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": null,
                  "timestampOffset": null,
                  "initPassword": false,
                  "active": false,
                  "retryLoginTime": null,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": null,
                  "lockedDate": null,
                  "cultureName": null,
                  "securityQuestionLastChanged": null,
                  "dateFormat": null,
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": null,
                  "fullName": "Teddy Bear",
                  "currentModules": null,
                  "id": "5cf7e984-bb0e-46b5-b856-530389b3b885",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": null,
                  "created": null,
                  "createdBy": "anna domino",
                  "modified": null,
                  "modifiedBy": null
               }
            ],
            "pageIndex": 1,
            "pageSize": 10,
            "total": 3,
            "skipItems": 0,
            "isLastPage": false
         }

   Request payload for Report Schedule::

      {
         "userModeType": 2,
         "searchByRole": null,
         "tenantId": null,
         "criteria": [
            {
               "key": "all",
               "value": "",
               "operation": 1
            }
         ],
         "pageIndex": 1,
         "pageSize": 10,
         "sortOrders": [
            {
               "key": "userName",
               "descending": true
            }
         ]
      }


   .. container:: toggle

      .. container:: header
      
         Sample Response:

      .. code-block:: json

         {
            "result": [
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "1211",
                  "emailAddress": null,
                  "firstName": "1211",
                  "lastName": "1211",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 0,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2016-12-11T12:20:05.187",
                  "passwordLastChanged": "2016-12-11T11:04:47.453",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2016-12-11T11:04:47.453",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "1211 1211",
                  "currentModules": null,
                  "id": "719868a5-daeb-4e8a-a884-9f697b94b8d1",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 2,
                  "created": "2016-12-11T11:04:07.22",
                  "createdBy": "System Admin",
                  "modified": "2016-12-11T12:20:05.2",
                  "modifiedBy": "System Admin"
               },
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "Theo Role",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "804eeed1-e8cf-44a6-a180-a896250f9990",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 1,
                        "created": "2017-04-11T10:07:48.343",
                        "createdBy": "Theo Nord",
                        "modified": "2017-04-11T10:07:48.343",
                        "modifiedBy": "Theo Nord"
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "14773",
                  "emailAddress": null,
                  "firstName": "14773",
                  "lastName": "14773",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 6,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-04-13T06:41:43.02",
                  "passwordLastChanged": "2017-04-13T04:27:02.003",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-04-13T04:27:02.003",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "14773 14773",
                  "currentModules": null,
                  "id": "70e0cca5-9772-4798-84c4-89e2d9e62263",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-04-13T04:26:01.097",
                  "createdBy": "Theo Nord",
                  "modified": "2017-04-13T04:27:02.003",
                  "modifiedBy": "Theo Nord"
               },
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "Analyst",
                        "tenantId": "c06b5e2e-6ac2-499d-938d-04846efc37e8",
                        "active": true,
                        "notAllowSharing": false,
                        "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd281",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 1,
                        "created": null,
                        "createdBy": "System Administrator",
                        "modified": null,
                        "modifiedBy": null
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "3",
                  "emailAddress": "izendateam@gmail.com",
                  "firstName": "First",
                  "lastName": "Last",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 0,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": null,
                  "dateFormat": null,
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "First Last",
                  "currentModules": null,
                  "id": "fa567f4f-574b-456c-a2a5-912a6bb9c621",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 4,
                  "created": "2016-09-21T09:56:36.03",
                  "createdBy": "System Administrator",
                  "modified": "2016-09-26T10:01:51.727",
                  "modifiedBy": null
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "aa",
                  "emailAddress": "aa@aa.com",
                  "firstName": "aa",
                  "lastName": "aa",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 6,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-07-25T10:57:28.767",
                  "passwordLastChanged": "2017-05-08T10:48:32.193",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-05-08T10:48:32.193",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": true,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "aa aa",
                  "currentModules": null,
                  "id": "d41fb48b-ba69-40c7-827e-afb41d18149a",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-05-08T10:48:05.02",
                  "createdBy": "lee mak",
                  "modified": "2017-07-25T10:42:32.067",
                  "modifiedBy": "lee mak"
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "abc",
                  "emailAddress": "abc@gmail.com",
                  "firstName": "abc",
                  "lastName": "abc",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 0,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2016-11-18T08:40:29.69",
                  "passwordLastChanged": "2016-11-18T08:40:29.66",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2016-11-18T08:40:29.66",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "abc abc",
                  "currentModules": null,
                  "id": "11e84611-58f1-47d2-a4c1-46877ae19134",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2016-11-18T08:39:54.363",
                  "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "modified": "2016-11-18T08:40:29.69",
                  "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "adminfull",
                  "emailAddress": "izendateam@gmail.com",
                  "firstName": "admin",
                  "lastName": "pavillion",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 0,
                  "initPassword": false,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": null,
                  "passwordLastChanged": null,
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": null,
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": true,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "admin pavillion",
                  "currentModules": null,
                  "id": "c62f2865-ad07-446c-8dca-bcf057ddf00f",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2016-11-07T03:08:02.74",
                  "createdBy": "f5206c3d-2d77-40cf-969b-80168fb80a8b",
                  "modified": "2016-11-07T03:08:02.74",
                  "modifiedBy": "f5206c3d-2d77-40cf-969b-80168fb80a8b"
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "anna",
                  "emailAddress": null,
                  "firstName": "Anna",
                  "lastName": "Domino",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 6,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-06-29T10:15:51.67",
                  "passwordLastChanged": "2017-05-05T06:19:55.403",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-05-05T06:19:55.403",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": true,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "Anna Domino",
                  "currentModules": null,
                  "id": "656de137-ed6a-4a6f-a9b2-e714db05630b",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-05-05T06:19:10.467",
                  "createdBy": "Anna Domino",
                  "modified": "2017-06-29T04:20:32.13",
                  "modifiedBy": "Anna Domino"
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "anlee",
                  "emailAddress": "an@email.com",
                  "firstName": "An",
                  "lastName": "Lee",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 0,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-07-24T14:01:41.667",
                  "passwordLastChanged": "2017-05-11T07:13:27.41",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-05-11T07:13:27.41",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": true,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "An Lee",
                  "currentModules": null,
                  "id": "c822feaa-d07d-454e-9343-63437081e3d9",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 13,
                  "created": "2016-11-03T03:15:52.903",
                  "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                  "modified": "2017-07-24T13:02:46.433",
                  "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
               },
               {
                  "password": null,
                  "roles": [
                     {
                        "name": "anna_role",
                        "tenantId": null,
                        "active": true,
                        "notAllowSharing": false,
                        "id": "38bf8593-6a66-46e5-92a4-8d901f0088a9",
                        "state": 0,
                        "deleted": false,
                        "inserted": true,
                        "version": 3,
                        "created": "2017-05-22T07:30:07.55",
                        "createdBy": "Theo Nord",
                        "modified": "2017-07-26T06:36:53.897",
                        "modifiedBy": "Theo Nord"
                     }
                  ],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "anna",
                  "emailAddress": null,
                  "firstName": "anna",
                  "lastName": "king",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 6,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-05-22T09:41:29.337",
                  "passwordLastChanged": "2017-05-22T07:31:28.237",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-05-22T07:31:28.237",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": false,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "anna king",
                  "currentModules": null,
                  "id": "9b54835b-0743-46e1-9353-a17a5380f3f3",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-05-22T07:30:40.597",
                  "createdBy": "Theo Nord",
                  "modified": "2017-05-22T09:41:29.337",
                  "modifiedBy": "Theo Nord"
               },
               {
                  "password": null,
                  "roles": [],
                  "userRoles": null,
                  "userSecurityQuestions": null,
                  "status": 1,
                  "issueDate": "0001-01-01T00:00:00",
                  "autoLogin": false,
                  "newPassword": null,
                  "userName": "antou",
                  "emailAddress": null,
                  "firstName": "An",
                  "lastName": "Tou",
                  "tenantId": null,
                  "tenantDisplayId": null,
                  "tenantName": null,
                  "dataOffset": 0,
                  "timestampOffset": 6,
                  "initPassword": true,
                  "active": true,
                  "retryLoginTime": 0,
                  "lastTimeAccessed": "2017-07-25T05:10:34.733",
                  "passwordLastChanged": "2017-04-18T04:51:18.647",
                  "locked": false,
                  "lockedDate": null,
                  "cultureName": "en-US",
                  "securityQuestionLastChanged": "2017-04-18T04:51:18.647",
                  "dateFormat": "MM/DD/YYYY",
                  "systemAdmin": true,
                  "notAllowSharing": false,
                  "numberOfFailedSecurityQuestion": 0,
                  "fullName": "An Tou",
                  "currentModules": null,
                  "id": "5a474141-c85d-42ed-adda-7768dc689c52",
                  "state": 0,
                  "deleted": false,
                  "inserted": true,
                  "version": 1,
                  "created": "2017-04-18T04:50:51.46",
                  "createdBy": "System Admin",
                  "modified": "2017-07-25T05:10:34.733",
                  "modifiedBy": "System Admin"
               }
            ],
            "pageIndex": 1,
            "pageSize": 10,
            "total": 80,
            "skipItems": 0,
            "isLastPage": false
         }

.. _POST_user/login:

POST user/login
--------------------------------------------------------------

Performs login.

**Request**

    A :doc:`models/Credential` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing an :doc:`models/AccessToken` object

**Samples**

   .. code-block:: http

      POST /api/user/login HTTP/1.1

   Request payload::

      {
        "userName" : "johndoe",
        "password" : "secret"
      }

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data" : {
           "token" : "UWmQLI13sORSrN5VLodTxqO9e/yElV4RwRb2K6PzW6l4tYtw7kkbHH2Im9oQNxToVBHCihEIophicrWyCf6J7w==",
           "tenant" : null,
           "isExpired" : false,
           "notifyDuringDay" : null
        }
      }


POST user/logout
--------------------------------------------------------------

Performs logout.

**Request**

    No payload

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/user/logout HTTP/1.1

   Sample response::

      true

.. _POST_user:

POST user
--------------------------------------------------------------

Saves a user.

.. note::

   To set up a user with password, this API is only the first step. See :doc:`/dev/code_javascript_add_internal_user` for the guide.

**Request**

    A :doc:`models/UserDetail` object

    .. note::

       The mandatory fields required to post are listed as below:

         - userName
         - tenantId
         - Ids of the roles
         - lastName
         - firstName


**Response**

     An :doc:`models/OperationResult` object with **success** field true and **data** field containing a :doc:`models/User` object

**Samples**

   .. code-block:: http

      POST /api/user HTTP/1.1

   Request payload::

      {
         "id": null,
         "systemAdmin": false,
         "userName": "nina@retcl.com",
         "tenantId": "1bd615d4-d3c4-4820-80bb-f34348b85f98",
         "emailAddress": "nina@retcl.com",
         "roles": [{
            "id": "d41378bd-0b22-4085-b90f-f9ccaa85e9e6"
         }],
         "state": 1,
         "inserted": true,
         "version": 1,
         "created": "2017-12-20T06:42:44.337",
         "createdBy": "$RootAdmin$",
         "modified": "2017-12-20T06:42:44.337",
         "modifiedBy": "$RootAdmin$",
         "lastName": "Doe",
         "firstName": "John",
         "fullName": "John Doe",
         "active": true,
         "password": null,
         "deleted": false,
         "userSecurityQuestions": null,
         "userRoles": null,
         "dataOffset": null,
         "timestampOffset": null,
         "initPassword": false,
         "status": 1,
         "cultureName": null,
         "dateFormat": "MM/DD/YYYY"
      }

   Sample response::

      {
         "success": true,
         "messages": null,
         "data": {
            "password": "",
            "roles": [{
               "name": null,
               "tenantId": null,
               "active": false,
               "notAllowSharing": false,
               "id": "d41378bd-0b22-4085-b90f-f9ccaa85e9e6",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": "System Admin",
               "modified": null,
               "modifiedBy": null
            }],
            "userRoles": [{
               "userId": "4fb95725-1e32-4f09-99f1-aa994de5de82",
               "roleId": "d41378bd-0b22-4085-b90f-f9ccaa85e9e6",
               "id": "bca85e44-d508-4538-9c8a-e07c6c593f25",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-12-20T06:44:50.445425",
               "createdBy": "System Admin",
               "modified": "2017-12-20T06:44:50.445425",
               "modifiedBy": "System Admin"
            }],
            "userSecurityQuestions": null,
            "status": 1,
            "issueDate": "0001-01-01T00:00:00",
            "autoLogin": false,
            "newPassword": null,
            "userName": "nina@retcl.com",
            "emailAddress": "nina@retcl.com",
            "firstName": "John",
            "lastName": "Doe",
            "tenantId": "1bd615d4-d3c4-4820-80bb-f34348b85f98",
            "tenantDisplayId": null,
            "tenantName": null,
            "dataOffset": null,
            "timestampOffset": null,
            "initPassword": false,
            "active": true,
            "retryLoginTime": null,
            "lastTimeAccessed": null,
            "passwordLastChanged": null,
            "locked": null,
            "lockedDate": null,
            "cultureName": null,
            "securityQuestionLastChanged": null,
            "dateFormat": "MM/DD/YYYY",
            "systemAdmin": false,
            "notAllowSharing": false,
            "numberOfFailedSecurityQuestion": null,
            "fullName": "John Doe",
            "currentModules": null,
            "id": "4fb95725-1e32-4f09-99f1-aa994de5de82",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": "2017-12-20T06:42:44.337",
            "createdBy": "$RootAdmin$",
            "modified": "2017-12-20T06:42:44.337",
            "modifiedBy": "$RootAdmin$"
         }
      }


POST user/userProfile
--------------------------------------------------------------

Saves a user profile.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing the saved :doc:`models/User` object

**Samples**

   .. code-block:: http

      POST /api/userProfile HTTP/1.1

   Request payload::

      {
        "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
        "systemAdmin": true,
        "userName": "jdoe",
        "firstName": "John",
        "lastName": "Doe",
        "cultureName": "en-US",
        "dateFormat": "MM/DD/YYYY",
        "tenantId": null,
        "emailAddress": "jdoe@acme.com",
        "roles": [],
        "dataOffset": 0,
        "timestampOffset": 0,
        "tenantName": null,
        "hasChangeLanguage": false
      }

   Sample response::

      {
        "success": true,
        "messages": null,
        "data": {
          "password": "",
          "roles": [],
          "userRoles": null,
          "userSecurityQuestions": null,
          "status": 3,
          "issueDate": "0001-01-01T00:00:00",
          "autoLogin": false,
          "newPassword": null,
          "userName": "jdoe",
          "emailAddress": "jdoe@acme.com",
          "firstName": "John",
          "lastName": "Doe",
          "tenantId": null,
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
          "systemAdmin": true,
          "notAllowSharing": false,
          "numberOfFailedSecurityQuestion": null,
          "fullName": "John Doe",
          "currentModules": null,
          "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": null,
          "created": null,
          "createdBy": "John Doe",
          "modified": null,
          "modifiedBy": null
        }
      }


POST user/passwordProfile
--------------------------------------------------------------

Saves a password profile.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing an :doc:`models/AccessToken` object

**Samples**

   .. code-block:: http

      POST /api/user/passwordProfile HTTP/1.1

   Request payload::

      {
        "newPassword": "secret",
        "password": "secret",
        "userName": "jdoe",
        "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c"
      }

   Sample response::

      {
        "success": true,
        "messages": null,
        "data": {
          "token": "123Abc..=",
          "tenant": null,
          "cultureName": "en-US",
          "dateFormat": "MM/DD/YYYY",
          "isExpired": false,
          "notifyDuringDay": null
        }
      }


POST user/securityQuesitions
--------------------------------------------------------------

Saves security questions for a user.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing the updated :doc:`models/UserDetail` object

**Samples**

   .. code-block:: http

      POST /api/user/securityQuestions HTTP/1.1

   Request payload::

      {
        "userSecurityQuestions": [
          {
            "securityQuestionId": "5784ece5-d2e7-42b1-89bb-859737b7b2a9",
            "answer": "Jenny Doe"
          },
          {
            "securityQuestionId": "3771bdc2-1add-481a-9649-18a7e494860b",
            "answer": "911"
          }
        ],
        "userName": "jdoe",
        "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c"
      }

   .. container:: toggle

      .. container:: header
      
         Sample Response:

      .. code-block:: json

         {
         "success": true,
         "messages": null,
         "data": {
            "password": null,
            "roles": [],
            "userRoles": null,
            "userSecurityQuestions": [
               {
               "userId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
               "securityQuestionId": "5784ece5-d2e7-42b1-89bb-859737b7b2a9",
               "question": null,
               "id": "b3131be9-e39a-46b2-aa59-dc112fcff5f0",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-01-06T07:48:13.281359",
               "createdBy": "John Doe",
               "modified": "2017-01-06T07:48:13.281359",
               "modifiedBy": "John Doe"
               },
               {
               "userId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
               "securityQuestionId": "3771bdc2-1add-481a-9649-18a7e494860b",
               "question": null,
               "id": "c50a5b68-20b2-4c0d-b8f0-20072104ac51",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": 1,
               "created": "2017-01-06T07:48:13.281359",
               "createdBy": "John Doe",
               "modified": "2017-01-06T07:48:13.281359",
               "modifiedBy": "John Doe"
               }
            ],
            "status": 3,
            "issueDate": "0001-01-01T00:00:00",
            "autoLogin": false,
            "newPassword": null,
            "userName": "jdoe",
            "emailAddress": null,
            "firstName": null,
            "lastName": null,
            "tenantId": null,
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
            "cultureName": null,
            "securityQuestionLastChanged": "2017-01-06T07:48:13.2387372",
            "dateFormat": null,
            "systemAdmin": false,
            "notAllowSharing": false,
            "numberOfFailedSecurityQuestion": null,
            "fullName": "jdoe",
            "currentModules": null,
            "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": null,
            "created": null,
            "createdBy": "John Doe",
            "modified": null,
            "modifiedBy": null
         }
         }

POST user/password
--------------------------------------------------------------

Saves password for a user.

**Request**

    A :doc:`models/UserDetail` object.

**Response**

    The updated :doc:`models/OperationResult` object.

**Samples**

   .. code-block:: http

      POST /api/user/password HTTP/1.1

   Simple Request Payload::

      {
         "password": "P4@ssW0rd",
         "userSecurityQuestions": null,
         "newPassword": "P1k@P1k@123",
         "userName": "acme@system.com",
         "emailAddress": "ecme@system.com",
         "firstName": "John",
         "lastName": "Doe",
         "tenantId": "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "id":"88ca2835-81e0-443b-b29e-e694a66b8e7a"
      }

   Sample Response::

      {
         "success": true,
         "messages": null,
         "data": {
            "token": "",
            "tenant": null,
            "cultureName": null,
            "dateFormat": null,
            "systemAdmin": false,
            "isExpired": false,
            "notifyDuringDay": null
         }
      }

POST user/active
--------------------------------------------------------------

Activates a user.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    The updated :doc:`models/UserDetail` object

**Samples**

   .. code-block:: http

      POST /api/user/active HTTP/1.1

   Request payload::

      {
        "isDirty" : false,
        "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
        "userName" : "jdoe",
        "password" : null,
        "tenantId" : null,
        "emailAddress" : "jdoe@acme.com",
        "roles" : [{
              "name" : "CreateUserRole",
              "tenantId" : null,
              "active" : true,
              "id" : "b992c772-6cb1-4103-b6b1-0da581368862",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-10T07:25:55.653",
              "createdBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
              "modified" : "2016-10-10T07:25:55.653",
              "modifiedBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
           }
        ],
        "state" : 0,
        "inserted" : true,
        "version" : 2,
        "created" : "2016-10-10T07:50:26.237",
        "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "modified" : "2016-10-10T08:31:13.89",
        "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "selected" : true,
        "lastName" : "Doe",
        "firstName" : "John",
        "fullName" : "John Doe",
        "active" : false,
        "initPassword" : true,
        "deleted" : false,
        "userSecurityQuestions" : null,
        "userRoles" : null,
        "dataOffset" : 0,
        "timestampOffset" : 0,
        "passwordLink" : null,
        "failedlogin" : false,
        "status" : 2,
        "rolesValue" : "b992c772-6cb1-4103-b6b1-0da581368862",
        "recipientValue" : [],
        "clearSercurityQuestion" : false,
        "sendEmail" : false
      }

   Sample response::

      {
        "password" : null,
        "roles" : [{
              "name" : "CreateUserRole",
              "tenantId" : null,
              "active" : true,
              "id" : "b992c772-6cb1-4103-b6b1-0da581368862",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-10T07:25:55.653",
              "createdBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
              "modified" : "2016-10-10T07:25:55.653",
              "modifiedBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
           }
        ],
        "userRoles" : null,
        "userSecurityQuestions" : null,
        "status" : 1,
        "issueDate" : "0001-01-01T00:00:00",
        "autoLogin" : false,
        "newPassword" : null,
        "userName" : "jdoe",
        "emailAddress" : "jdoe@acme.com",
        "firstName" : "John",
        "lastName" : "Doe",
        "tenantId" : null,
        "tenantDisplayId" : null,
        "dataOffset" : 0,
        "timestampOffset" : 0,
        "initPassword" : true,
        "active" : true,
        "retryLoginTime" : null,
        "lastTimeAccessed" : null,
        "passwordActiveDate" : null,
        "locked" : null,
        "lockedDate" : null,
        "fullName" : "John Doe",
        "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
        "state" : 0,
        "deleted" : false,
        "inserted" : true,
        "version" : 2,
        "created" : "2016-10-10T07:50:26.237",
        "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "modified" : "2016-10-10T08:31:13.89",
        "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62"
      }


POST user/deactive
--------------------------------------------------------------

Deactivates a user.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    The updated :doc:`models/UserDetail` object

**Samples**

   .. code-block:: http

      POST /api/user/deactive HTTP/1.1

   Request payload::

      {
        "isDirty" : false,
        "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
        "userName" : "jdoe",
        "password" : null,
        "tenantId" : null,
        "emailAddress" : "jdoe@acme.com",
        "roles" : [{
              "name" : "CreateUserRole",
              "tenantId" : null,
              "active" : true,
              "id" : "b992c772-6cb1-4103-b6b1-0da581368862",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-10T07:25:55.653",
              "createdBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
              "modified" : "2016-10-10T07:25:55.653",
              "modifiedBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
           }
        ],
        "state" : 0,
        "inserted" : true,
        "version" : 2,
        "created" : "2016-10-10T07:50:26.237",
        "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "modified" : "2016-10-10T08:31:13.89",
        "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "selected" : true,
        "lastName" : "Doe",
        "firstName" : "John",
        "fullName" : "John Doe",
        "active" : true,
        "initPassword" : true,
        "deleted" : false,
        "userSecurityQuestions" : null,
        "userRoles" : null,
        "dataOffset" : 0,
        "timestampOffset" : 0,
        "passwordLink" : null,
        "failedlogin" : false,
        "status" : 1,
        "rolesValue" : "b992c772-6cb1-4103-b6b1-0da581368862",
        "recipientValue" : [],
        "clearSercurityQuestion" : false,
        "sendEmail" : false
      }

   Sample response::

      {
        "password" : null,
        "roles" : [{
              "name" : "CreateUserRole",
              "tenantId" : null,
              "active" : true,
              "id" : "b992c772-6cb1-4103-b6b1-0da581368862",
              "state" : 0,
              "deleted" : false,
              "inserted" : true,
              "version" : 1,
              "created" : "2016-10-10T07:25:55.653",
              "createdBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
              "modified" : "2016-10-10T07:25:55.653",
              "modifiedBy" : "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
           }
        ],
        "userRoles" : null,
        "userSecurityQuestions" : null,
        "status" : 2,
        "issueDate" : "0001-01-01T00:00:00",
        "autoLogin" : false,
        "newPassword" : null,
        "userName" : "jdoe",
        "emailAddress" : "jdoe@acme.com",
        "firstName" : "John",
        "lastName" : "Doe",
        "tenantId" : null,
        "tenantDisplayId" : null,
        "dataOffset" : 0,
        "timestampOffset" : 0,
        "initPassword" : true,
        "active" : false,
        "retryLoginTime" : null,
        "lastTimeAccessed" : null,
        "passwordActiveDate" : null,
        "locked" : null,
        "lockedDate" : null,
        "fullName" : "John Doe",
        "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
        "state" : 0,
        "deleted" : false,
        "inserted" : true,
        "version" : 2,
        "created" : "2016-10-10T07:50:26.237",
        "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
        "modified" : "2016-10-10T08:31:13.89",
        "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62"
      }


DELETE user/{user_id}
--------------------------------------------------------------

Deletes a user.

**Request**

    No payload

**Response**

    * true if user was successfully deleted
    * false if not

**Samples**

   .. code-block:: http

      DELETE /api/user/2727bb4a-ee5c-4f55-8ec3-dd73f4ffd440 HTTP/1.1

   Sample response::

      true

.. _POST_user/passwordAndSecurityQuestion:

POST user/passwordAndSecurityQuestion
--------------------------------------------------------------

Saves a user password and security question.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing an :doc:`models/AccessToken` object

**Samples**

   .. code-block:: http

      POST /api/user/passwordAndSecurityQuestion HTTP/1.1

   Request payload::

      {
        "tenantDisplayID" : null,
        "password" : "secret",
        "verification" : "H8K...swUc=",
        "userName" : "jdoe",
        "firstName" : "John",
        "lastName" : "Doe",
        "emailAddress" : "jdoe@acme.com",
        "userSecurityQuestions" : [],
        "autoLogin" : true
      }

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data" : {
           "token" : "3AfY....yKg==",
           "tenant" : null,
           "isExpired" : false,
           "notifyDuringDay" : null
        }
      }


GET user/securityQuestion/{user_name}/(tenant_display_id)
--------------------------------------------------------------

Returns security question for a user and tenant.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing an :doc:`models/AccessToken` object

**Samples**

   .. code-block:: http

      GET /api/user/securityQuestion/jdoe HTTP/1.1

   Sample response::

      {
       "success": true,
       "messages": null,
       "data": [
         {
           "userId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
           "securityQuestionId": "3771bdc2-1add-481a-9649-18a7e494860b",
           "question": "Which phone number do you remember most from your childhood?",
           "id": "c50a5b68-20b2-4c0d-b8f0-20072104ac51",
           "state": 0,
           "deleted": false,
           "inserted": true,
           "version": 1,
           "created": "2017-01-06T07:48:13.28",
           "createdBy": "John Doe",
           "modified": "2017-01-06T07:48:13.28",
           "modifiedBy": "John Doe"
         }
       ]
      }

.. _POST_user/generatePasswordLink:

POST user/generatePasswordLink
--------------------------------------------------------------

Generates :term:`password link`.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing a hash value from the user details.

**Samples**

   .. code-block:: http

      POST /api/user/generatePasswordLink HTTP/1.1

   Request payload::

      {
        "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
        "username" : "jdoe",
        "firstname" : "John",
        "lastname" : "Doe",
        "emailaddress" : "jdoe@acme.com"
      }

   Sample response::

      {
         "success": true,
         "messages": null,
         "data": "Abc/Def/..=="
      }


POST user/validatePasswordLink
--------------------------------------------------------------

Validates :term:`password link`.

**Request**

    A :doc:`models/UserVerification` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing the :doc:`models/UserVerification` object

**Samples**

   .. code-block:: http

      POST /api/user/validatePasswordLink HTTP/1.1

   Request payload::

      {
        "tenantDisplayID" : null,
        "userName" : "jdoe",
        "firstName" : "John",
        "lastName" : "Doe",
        "emailAddress" : "jdoe@acme.com",
        "verification" : "H8K....RU="
      }


POST user/validateSecurityQuestion
--------------------------------------------------------------

Validates security questions.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true if the question and answers are valid

**Samples**

   .. code-block:: http

      POST /api/user/validateSecurityQuestion HTTP/1.1

   Request payload::

      {
        "tenantDisplayID": null,
        "userName": "jdoe",
        "userSecurityQuestions": [
          {
            "userId": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
            "securityQuestionId": "5784ece5-d2e7-42b1-89bb-859737b7b2a9",
            "answer": "Jenny Doe"
          }
        ]
      }

   Sample response::

      {
        "success": true,
        "messages": null,
        "data": null
      }


POST user/validateUserInfo
--------------------------------------------------------------

Validates user information.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing a :doc:`models/User` object

**Samples**

   .. code-block:: http

      POST /api/user/validateUserInfo HTTP/1.1

   Request payload::

      {
        "tenantName": "",
        "userName": "jdoe",
        "firstName": "John",
        "lastName": "Doe",
        "emailAddress": "jdoe@acme.com",
        "verification": ""
      }

   Sample response::

      {
        "success": true,
        "messages": null,
        "data": {
          "userName": "jdoe",
          "emailAddress": "jdoe@acme.com",
          "firstName": "John",
          "lastName": "Doe",
          "tenantId": null,
          "tenantDisplayId": null,
          "tenantName": null,
          "dataOffset": 0,
          "timestampOffset": 0,
          "initPassword": true,
          "active": true,
          "retryLoginTime": 0,
          "lastTimeAccessed": "2017-01-06T08:18:22.393",
          "passwordLastChanged": "2017-01-06T07:45:58.813",
          "locked": false,
          "lockedDate": null,
          "cultureName": "en-US",
          "securityQuestionLastChanged": "2017-01-06T07:48:13.24",
          "dateFormat": "MM/DD/YYYY",
          "systemAdmin": true,
          "notAllowSharing": false,
          "numberOfFailedSecurityQuestion": 0,
          "fullName": "John Doe",
          "currentModules": null,
          "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
          "state": 0,
          "deleted": false,
          "inserted": true,
          "version": 14,
          "created": "2016-11-21T06:58:27.203",
          "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
          "modified": "2017-01-06T08:18:26.077",
          "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
        }
      }


POST user/validateExpirationPasswordLink
--------------------------------------------------------------

Validates password expiration link.

**Request**

    A :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field containing a :doc:`models/ValidateExpiration` object

**Samples**

   .. code-block:: http

      POST /api/user/validateExpirationPasswordLink HTTP/1.1

   Request payload::

      {
        "verification" : "H8K....Uc="
      }

   Sample response::

      {
        "success" : true,
        "messages" : null,
        "data" : {
           "tenantId" : null,
           "isExpired" : false,
           "notifyDuringDay" : null
        }
      }


POST user/sendPasswordLink
--------------------------------------------------------------

Sends :term:`password link` via email to user.

**Request**

    Payload: a :doc:`models/PasswordOption` object

**Response**

    * true if the action was successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/user/sendPasswordLink HTTP/1.1

   Request payload::

      {
        "passwordLink" : "http://127.0.0.1:8888/account/activation?verification=H8K....RU%3D",
        "user" : {
           "userName" : "jdoe",
           "id" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3"
        },
        "sendEmail" : false,
        "clearSercurityQuestion" : false,
        "emailAddresses" : ["jdoe@acme.com"]
      }

   Sample response::

      true


POST user/integration/saveUser
--------------------------------------------------------------

Adds or updates external user.

**Request**

    A :doc:`models/UserDetail` object
   
    .. note::

       The mandatory fields required to post are listed as below:

         - userName
         - tenantDisplayID
         - Name of the roles (when adding or updating the external user, system will only save the external roles that their names are existing and ignore the others)
         - lastName
         - firstName

**Response**

    * true if the operation is successful
    * an error if not

**Samples**

   .. code-block:: http

      POST /api/user/integration/saveUser HTTP/1.1

   .. container:: toggle

      .. container:: header
      
         Request Payload:

      .. code-block:: json

         {
            "id": null,
            "systemAdmin": false,
            "userName": "nina@retcl.com",
            "tenantId": null,
            "tenantDisplayId": "RETCL",
            "emailAddress": "nina@retcl.com",
            "roles": [{
                  "name": "Emploee"
               }],
            "state": 0,
            "inserted": true,
            "version": 0,
            "created": "2017-12-20T06:42:44.337",
            "createdBy": "$RootAdmin$",
            "modified": "2017-12-20T06:44:48.527",
            "modifiedBy": "$RootAdmin$",
            "lastName": "Doe",
            "firstName": "Nina",
            "fullName": "Nina Doe",
            "active": true,
            "password": "",
            "deleted": false,
            "userSecurityQuestions": null,
            "userRoles": null,
            "dataOffset": null,
            "timestampOffset": null,
            "initPassword": false,
            "status": 1,
            "cultureName": null,
            "dateFormat": "MM/DD/YYYY"
         }

   Sample Response::

      true

POST user/validateUserRoleAssociation
--------------------------------------------------------------

Validates user and role association after some roles are removed.

**Request**

    A :doc:`models/ValidateUserRoleAssociationParam` object

**Response**

    * true if valid
    * false if not

**Samples**

   .. code-block:: http

      POST /api/user/validateUserRoleAssociation HTTP/1.1

   Request payload::

      {
         "userId": "14fbf9ac-2d7b-41e9-a272-dd51e161914d",
         "removedRoleIds": ["d256d058-aeb7-468f-9f95-962d65979707"],
         "addedRoleIds": []
      }

   Sample Response::

      true

POST user/allowedSharingUsers/(tenant_id)
--------------------------------------------------------------

Returns a list of users allowed to be selected in report/dashboard access.

**Request**

    Payload: a :doc:`models/SharingRoleUserParameter` object

**Response**

    An array of :doc:`models/UserDetail` objects

**Samples**

   .. code-block:: http

      POST /api/user/allowedSharingUsers HTTP/1.1

   Request payload::

      {
         "reportId":"45f17b8a-3708-4f36-80ef-9178b7124841"
      }

   .. container:: toggle

      .. container:: header
      
         Sample Response:

      .. code-block:: json

         [
         {
            "password": null,
            "roles": [],
            "userRoles": null,
            "userSecurityQuestions": null,
            "status": 1,
            "issueDate": "0001-01-01T00:00:00",
            "autoLogin": false,
            "newPassword": null,
            "userName": "jdoe",
            "emailAddress": "jdoe@acme.com",
            "firstName": "John",
            "lastName": "Doe",
            "tenantId": null,
            "tenantDisplayId": null,
            "tenantName": null,
            "dataOffset": 0,
            "timestampOffset": 0,
            "initPassword": true,
            "active": true,
            "retryLoginTime": 0,
            "lastTimeAccessed": "2017-01-06T08:16:21.593",
            "passwordLastChanged": "2017-01-06T07:45:58.813",
            "locked": false,
            "lockedDate": null,
            "cultureName": "en-US",
            "securityQuestionLastChanged": "2017-01-06T07:48:13.24",
            "dateFormat": "MM/DD/YYYY",
            "systemAdmin": true,
            "notAllowSharing": false,
            "numberOfFailedSecurityQuestion": 0,
            "fullName": "John Doe",
            "currentModules": null,
            "id": "9fc0f5c2-decf-4d65-9344-c59a1704ea0c",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 14,
            "created": "2016-11-21T06:58:27.203",
            "createdBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "modified": "2017-01-06T08:14:42.863",
            "modifiedBy": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe"
         },
         {
            "password": null,
            "roles": [],
            "userRoles": null,
            "userSecurityQuestions": null,
            "status": 1,
            "issueDate": "0001-01-01T00:00:00",
            "autoLogin": false,
            "newPassword": null,
            "userName": "IzendaAdmin",
            "emailAddress": null,
            "firstName": "System",
            "lastName": "Admin",
            "tenantId": null,
            "tenantDisplayId": null,
            "tenantName": null,
            "dataOffset": 0,
            "timestampOffset": 0,
            "initPassword": true,
            "active": true,
            "retryLoginTime": 0,
            "lastTimeAccessed": "2017-01-05T03:58:35.073",
            "passwordLastChanged": null,
            "locked": null,
            "lockedDate": null,
            "cultureName": null,
            "securityQuestionLastChanged": null,
            "dateFormat": "MM/DD/YYYY",
            "systemAdmin": true,
            "notAllowSharing": false,
            "numberOfFailedSecurityQuestion": 0,
            "fullName": "System Admin",
            "currentModules": null,
            "id": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": 1,
            "created": null,
            "createdBy": "John Doe",
            "modified": "2017-01-05T03:58:49.12",
            "modifiedBy": null
         }
         ]


GET user/isLastSystemAdmin
--------------------------------------------------------------

Checks if the number of not deleted system admins equals 1.

**Request**

    No payload

**Response**

    An :doc:`models/OperationResult` object with **success** field true and **data** field true if the number of not deleted system admins equals 1

**Samples**

   .. code-block:: http

      GET /api/user/isLastSystemAdmin HTTP/1.1

   Sample response::

      {
         "success": true,
         "messages": null,
         "data": false
      }

POST external/user
--------------------------
Add or update external user

**Request**

    An :doc:`models/UserDetail` object

**Response**

    An :doc:`models/OperationResult` object  **data** field contains an :doc:`models/UserDetail` object.

**Samples**

   .. code-block:: http

      POST /api/external/user HTTP/1.1

   Request Payload::

      {
         "id": null,
         "systemAdmin": false,
         "userName": "nina@retcl.com",
         "tenantId": "14fbf9ac-2d7b-41e9-a272-dd51e161914d",
         "tenantDisplayId": "RETCL",
         "emailAddress": "nina@retcl.com",
         "roles": [{
               "name": "Employee"
            }],
         "state": 0,
         "inserted": true,
         "version": 0,
         "created": "2017-12-20T06:42:44.337",
         "createdBy": "$RootAdmin$",
         "modified": "2017-12-20T06:44:48.527",
         "modifiedBy": "$RootAdmin$",
         "lastName": "Doe",
         "firstName": "Nina",
         "fullName": "Nina Doe",
         "active": true,
         "password": "",
         "deleted": false,
         "userSecurityQuestions": null,
         "userRoles": null,
         "dataOffset": null,
         "timestampOffset": null,
         "initPassword": false,
         "status": 1,
         "cultureName": null,
         "dateFormat": "MM/DD/YYYY"
      }

   Sample Reponse::

      {
         "success": true,
         "messages": null,
         "data": 
            {
               "id": "a3a3a5cc-123d-1c23-ae85-ba92ec3b934e",
               "systemAdmin": false,
               "userName": "nina@retcl.com",
               "tenantId": "14fbf9ac-2d7b-41e9-a272-dd51e161914d",
               "tenantDisplayId": "RETCL",
               "emailAddress": "nina@retcl.com",
               "roles": [{
                     "name": "Employee"
                  }],
               "state": 0,
               "inserted": true,
               "version": 0,
               "created": "2017-12-20T06:42:44.337",
               "createdBy": "$RootAdmin$",
               "modified": "2017-12-20T06:44:48.527",
               "modifiedBy": "$RootAdmin$",
               "lastName": "Doe",
               "firstName": "Nina",
               "fullName": "Nina Doe",
               "active": true,
               "password": "",
               "deleted": false,
               "userSecurityQuestions": null,
               "userRoles": null,
               "dataOffset": null,
               "timestampOffset": null,
               "initPassword": false,
               "status": 1,
               "cultureName": null,
               "dateFormat": "MM/DD/YYYY"
            }
      }