
=================================
ConnectionVerificationResult
=================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **serverNotValid** |br|
         boolean
      -
      -  Is the server not valid
      -
   *  -  **databaseNotValid** |br|
         boolean
      -
      -  Is the database not valid
      -
   *  -  **differentDatabase** |br|
         boolean
      -
      -  Does the connection string point to a different database
      -
   *  -  **loginFail** |br|
         boolean
      -
      -  Did the login succeed
      -
   *  -  **hasValidLicense** |br|
         boolean
      -
      -  Has the database already had a valid license
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "serverNotValid" : false,
        "databaseNotValid" : false,
        "loginFail" : false,
        "hasValidLicense" : false,
        "success" : true,
        "messages" : []
      }
