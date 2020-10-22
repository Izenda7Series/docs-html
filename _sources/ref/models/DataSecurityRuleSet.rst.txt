=========================
DataSecurityRuleSet
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **description** |br|
         string
      -
      -  The description of the data security rule set.
      -
   *  -  **fields** |br|
         array of objects
      -
      -  An array of :doc:`DataSecurityField` objects.
      -
   *  -  **id** |br|
         string (GUID)
      -
      -  The ID of the data security rule set.
      -
   *  -  **name** |br|
         string
      -
      -  The name of the data security rule set.
      -
   *  -  **position** |br|
         integer
      -
      -  The position in the list of data security rule sets.
      -
   *  -  **rules** |br|
         array of objects
      -
      -  An array of :doc:`DataSecurityRule` objects.
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
   *  -  **tenantId** |br|
         string (GUID)
      -
      -  The ID of the tenant (null if the setting belongs to System).
      -