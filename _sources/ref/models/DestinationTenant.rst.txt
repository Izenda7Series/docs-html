
===================
DestinationTenant
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **tenantId** |br|
         string
      -
      -  The user-defined tenant id
      -
   *  -  **roleMappings** |br|
         array of objects
      -
      -  An array of :doc:`RoleMapping` objects
      -
   *  -  **databaseMappings** |br|
         array of objects
      -
      -  An array of :doc:`DatabaseMapping` objects
      -
   *  -  **overwrite** |br|
         object
      -
      -  An :doc:`Overwrite` object
      -
   *  -  **lineNumber** |br|
         integer
      -
      -  The line number of the item in config xml file
      -
