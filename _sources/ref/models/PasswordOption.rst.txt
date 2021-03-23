

=========================================
PasswordOption
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **passwordLink** |br|
         string
      -
      -  The :term:`password link`.
      -
   *  -  **user** |br|
         object
      -
      -  A :doc:`UserDetail` object
      -
   *  -  **sendEmail** |br|
         boolean
      -
      -  Send password link via email or not
      -
   *  -  **clearSecurityQuestion** |br|
         boolean
      -
      -  Clear all security questions or not
      -
   *  -  **emailAddresses** |br|
         array of strings
      -
      -  The list of email addresses to send password link
      -


Inherited fields:

.. include:: Expiration.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

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
