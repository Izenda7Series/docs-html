=========================
DataSecurityRule
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **accessMode** |br|
         integer
      -
      - The access mode of this object

         -  1 = Block
         -  2 = Allow
      -
   *  -  **accessibleValues** |br|
         array of string values
      -
      -  The list of values to block or allow.

         There are also some preset values

         - {all} - all values
         - {tenantId} - the current Tenant ID
         - {tenantName} - the current Tenant Name
         - {roleName} - any role name of the current user
         - {userName} - the current User ID
      -
   *  -  **accessors** |br|
         array of objects
      -
      -   An array of :doc:`DataSecurityAccessor` objects.
      -
   *  -  **id** |br|
         string (GUID)
      -
      -  The ID of the data security rule.
      -
   *  -  **position** |br|
         integer
      -
      -  The position in the list of data security rules.
      -
   *  -  **state** |br|
         integer
      -
      -  The state of this object

         -  0 = None
         -  1 = Insert
         -  2 = Delete
         -  3 = Update
      -
   *  -  **userGroup** |br|
         integer
      -
      -  The selected user group of this object

         -  1 = Everyone
         -  2 = Role
         -  3 = User
      -