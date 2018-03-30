

=========================================
RoleVirtualNode
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **isLastPage** |br|
         boolean
      -  
      -  Is the last page or not
      -
   *  -  **name** |br|
         string
      -  
      -  The role name or user name
      -
   *  -  **childNodes** |br|
         an array of object
      -
      -  An array of :doc:`RoleVirtualNode`
      -
   *  -  **numOfChilds** |br|
         integer
      -  
      -  The number of children
      -
   *  -  **checked** |br|
         boolean
      -  
      -  Whether this instance is selected
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  *  true if 0 < numOfCheckedChilds < numOfChilds
         *  false if not
      -
   *  -  **numOfCheckedChilds** |br|
         integer
      -
      -  The number of selected children
      -
   *  -  **totalItems** |br|
         integer
      -
      -  The total of items
      -
   *  -  **id** |br|
         string(GUID)
      -
      -  The id of role or user
      -