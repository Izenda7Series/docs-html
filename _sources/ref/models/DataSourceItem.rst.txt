

=========================
DataSourceItem
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
      -  The id of item
      -
   *  -  **name** |br|
         string
      -
      -  The name of the item
      -
   *  -  **childNodes** |br|
         array of objects
      -
      -  An array of :doc:`DataSourceItem` objects
      -
   *  -  **parentId** |br|
         string (GUID)
      -
      -  The id of the parent item
      -
   *  -  **checked** |br|
         boolean
      -
      -  Wether this item is checked or not
      -
   *  -  **isLeafItem** |br|
         boolean
      -
      -  Whether this item is leaf item or not
      -
   *  -  **expand** |br|
         boolean
      -
      -  Whether this item is expanded or not
      -
   *  -  **interacted** |br|
         boolean
      -
      -  Whether this item is interacted by user or not
      -
Inherited fields:

.. include:: HierarchyItem.rst