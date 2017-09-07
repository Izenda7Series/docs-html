

=========================================
UserDetail
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **password** |br|
         string
      -
      -  The password
      -
   *  -  **roles** |br|
         array of objects
      -
      -  An array of :doc:`Role` objects
      -
   *  -  **userRoles** |br|
         array of objects
      -
      -  An array of :doc:`UserRole` objects
      -
   *  -  **userSecurityQuestions** |br|
         array of objects
      -
      -  An array of :doc:`UserSecurityQuestion` objects
      -
   *  -  **status** |br|
         integer
      -
      -  The status

         -  1 = Active
         -  2 = Deactive
         -  3 = PasswordNotSet
         -  4 = LoginAttemptFailed
         -  5 = AnswerAttempFailed
      -
   *  -  **issueDate** |br|
         datetime
      -
      -  The time when token was generated
      -
   *  -  **autoLogin** |br|
         boolean
      -
      -  Whether system will auto login this user
      -
   *  -  **newPassword** |br|
         string
      -
      -  The new password
      -

Inherited fields:

.. include:: User.rst

.. container:: toggle

   .. container:: header

      **UserDetail Sample**:

   .. code-block:: json

      {
           "password" : null,
           "roles" : [],
           "userName" : "Anna",
           "emailAddress" : null,
           "firstName" : "An",
           "lastName" : "Na",
           "passwordHash" : null,
           "passwordSalt" : null,
           "currentTokenHash" : null,
           "tenantId" : null,
           "active" : false,
           "deleted" : false,
           "dataOffset" : 0,
           "timestampOffset" : 0,
           "fullName" : "An Na",
           "id" : "9f58703e-0dff-4690-9dc6-c595a6fd84e5",
           "state" : 0,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
        }
