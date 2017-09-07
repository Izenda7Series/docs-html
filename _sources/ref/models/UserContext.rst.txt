
==============
UserContext
==============

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **Identity** |br|
         object
      -
      -  The name of the user
      -
   *  -  **CurrentUser** |br|
         object
      -
      -  A :doc:`User` object
      -
   *  -  **CurrentTenant** |br|
         object
      -
      -  A :doc:`Tenants` object
      -
   *  -  **RequestId** |br|
         string (GUID)
      -
      -  The id of the request
      -
   *  -  **RequestSource** |br|
         string
      -
      -  The request source, e.g. "User request"
      -
   *  -  **Roles** |br|
         array of objects
      -
      -  An array of :doc:`Role` objects
      -
   *  -  **Permissions** |br|
         object
      -
      -  A :doc:`Permission` object
      -
   *  -  **LicenseModules** |br|
         array of strings
      -
      -  The list of assigned modules
      -
   *  -  **Culture** |br|
         string
      -
      -  The culture of the user
      -
   *  -  **Current** |br|
         object
      -
      -  The UserContext of the current logged in user, e.g. ``UserContext.Current.CurrentTenant``
      -
   *  -  **bool IsInRole(string role)** |br|
         boolean function
      -
      -  Returns true if the user has the role in parameter
      -
