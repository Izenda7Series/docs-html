

=========================================
UserVerification
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id of user
      -
   *  -  **firstName** |br|
         string
      -
      -  The first name
      -
   *  -  **lastName** |br|
         string
      -
      -  The last name
      -
   *  -  **emailAddress** |br|
         string
      -
      -  The email
      -
   *  -  **userName** |br|
         string
      -
      -  The user name
      -
   *  -  **verification** |br|
         string
      -
      -  The encoded info of user from :term:`password link`
      -
   *  -  **issueDate** |br|
         datetime
      -
      -  The time when token was generated
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantDisplayId** |br|
         string
      -
      -  The user-entered id of the tenant
      -
   *  -  **tenantName** |br|
         string
      -
      -  The name of the tenant
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "tenantDisplayID" : null,
        "userName" : "jdoe",
        "firstName" : "John",
        "lastName" : "Doe",
        "emailAddress" : "jdoe@acme.com",
        "verification" : "H8K....RU="
      }
