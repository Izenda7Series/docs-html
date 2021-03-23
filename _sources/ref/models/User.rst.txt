

User
--------

.. list-table::
   :header-rows: 1
   :widths: 25 5 45 25

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **userName** |br|
         string
      -
      -  The name of the user
      -
   *  -  **emailAddress** |br|
         string
      -
      -  The email address of the user
      -
   *  -  **firstName** |br|
         string
      -
      -  The first name of the user
      -
   *  -  **lastName** |br|
         string
      -
      -  The last name of the user
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantDisplayId** |br|
         string
      -
      -  The user-entered id of the tenant for display
      -
   *  -  **tenantName** |br|
         string
      -  Y
      -  The name of the tenant if available
      -
   *  -  **dataOffset** |br|
         decimal
      -  Y
      -  The time shift to be applied to datetime data from client database connections to match user's local time
      -  As of v2.9.5, offset will accept partial hours as .25, .5 or .75
   *  -  **timestampOffset** |br|
         decimal
      -  Y
      -  The time shift to be applied to timestamp data (created date time, last updated date time) from Izenda system database to match user's local time zone
      -  As of v2.9.5, offset will accept partial hours as .25, .5 or .75
   *  -  **initPassword** |br|
         boolean
      -
      -  Has the password been initialized for a new user
      -
   *  -  **active** |br|
         boolean
      -
      -  Is the user activated
      -
   *  -  **retryLoginTime** |br|
         integer
      -  Y
      -  The number of consecutive times that user fails to log in
      -
   *  -  **lastTimeAccessed** |br|
         datetime
      -  Y
      -  The time when user last accessed the system
      -
   *  -  **passwordLastChanged** |br|
         datetime
      -  Y
      -  The time when user last changed the password
      -
   *  -  **locked** |br|
         boolean
      -  Y
      -  Is the user locked
      -
   *  -  **lockedDate** |br|
         datetime
      -  Y
      -  The time when user was locked
      -
   *  -  **cultureName** |br|
         string
      -  Y
      -  The culture name
      -
   *  -  **securityQuestionLastChanged** |br|
         datetime
      -  Y
      -  The time when user last changed security questions
      -
   *  -  **dateFormat** |br|
         string
      -
      -  The user-selected date format
      -
   *  -  **systemAdmin** |br|
         boolean
      -
      -  Whether user is a system admin
      -
   *  -  **notAllowSharing** |br|
         boolean
      -
      -  Is sharing not allowed
      -
   *  -  **numberOfFailedSecurityQuestion** |br|
         integer
      -  Y
      -  The number of security questions that user failed to answer
      -
   *  -  **fullName** |br|
         string
      -
      -  The full name
      -
   *  -  **currentModules** |br|
         array of strings
      -  Y
      -  The list of assigned modules
      -



Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **User Sample**:

   .. code-block:: json

      {
         "password" : null,
         "roles" : [{
               "name" : null,
               "tenantId" : null,
               "active" : false,
               "id" : "b992c772-6cb1-4103-b6b1-0da581368862",
               "state" : 0,
               "deleted" : false,
               "inserted" : true,
               "version" : null,
               "created" : null,
               "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
               "modified" : null,
               "modifiedBy" : null
            }
         ],
         "userRoles" : [{
               "userId" : "6c447061-8f1d-4ff4-803c-b6b15695b8c3",
               "roleId" : "b992c772-6cb1-4103-b6b1-0da581368862",
               "id" : "b15da0f4-d97d-4c78-bd52-22af0e02aae0",
               "state" : 0,
               "deleted" : false,
               "inserted" : true,
               "version" : 1,
               "created" : "2016-10-10T07:50:26.2366983",
               "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
               "modified" : "2016-10-10T07:50:26.2366983",
               "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62"
            }
         ],
         "userSecurityQuestions" : null,
         "status" : 3,
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
         "initPassword" : false,
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
         "inserted" : false,
         "version" : 1,
         "created" : "2016-10-10T07:50:26.2366983",
         "createdBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62",
         "modified" : "2016-10-10T07:50:26.2366983",
         "modifiedBy" : "e5dabf75-c5b7-4877-86cc-b3afd83eed62"
      }
