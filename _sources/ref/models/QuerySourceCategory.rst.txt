

=========================
QuerySourceCategory
=========================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -
      -  The id
      -
   *  -  **name** |br|
         string
      -
      -  The name
      -
   *  -  **parentCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the parent category
      -
   *  -  **connectionId** |br|
         string (GUID)
      -
      -  The id of the connection
      -
   *  -  **querySources** |br|
         array of objects
      -
      -  An array of :doc:`QuerySource` objects
      -
   *  -  **childs** |br|
         array of objects
      -
      -  An array of :doc:`QuerySourceCategory` objects
      -
   *  -  **connection** |br|
         object
      -
      -  A :doc:`Connection` object
      -
   *  -  **physicalChange** |br|
         integer
      -
      -  The change state
      -
   *  -  **existed** |br|
         boolean
      -
      -  Exist flag
      -
   *  -  **deleted** |br|
         boolean
      -
      -  Whether this has been deleted
      -
   *  -  **checked** |br|
         boolean
      -
      -  Whether this is checked on workspace for copying purpose
      -
   *  -  **totalTableChildNodes** |br|
         integer
      -
      -  The number of child nodes that are tables
      -
   *  -  **totalTableCheckedNodes** |br|
         integer
      -
      -  The number of selected for copying child nodes that are tables
      -
   *  -  **totalStoredProcedureChildNodes** |br|
         integer
      -
      -  The number of child nodes that are stored procedures
      -
   *  -  **totalStoredProcedureCheckedNodes** |br|
         integer
      -
      -  The number of selected for copying child nodes that are stored procedures
      -
   *  -  **totalViewChildNodes** |br|
         integer
      -
      -  The number of child nodes that are views
      -
   *  -  **totalViewCheckedNodes** |br|
         integer
      -
      -  The number of selected for copying child nodes that are views
      -
   *  -  **totalFunctionChildNodes** |br|
         integer
      -
      -  The number of child nodes that are functions
      -
   *  -  **totalFunctionCheckedNodes** |br|
         integer
      -
      -  The number of selected for copying child nodes that are functions
      -
