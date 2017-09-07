

=================
ValueTreeNode
=================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **nodes** |br|
         array of objects
      -
      -  An array of child ValueTreeNode objects.
      -
   *  -  **parent** |br|
         object
      -
      -  The parent :doc:`ValueTreeNode` object.
      -
   *  -  **id** |br|
         string (GUID)
      -
      -  The id of the object.
      -
   *  -  **text** |br|
         string
      -
      -  The display text of the object
      -
   *  -  **value** |br|
         string
      -
      -  The value of the object
      -
   *  -  **numOfChilds** |br|
         integer
      -
      -  The number of children
      -
   *  -  **numOfCheckedChilds** |br|
         integer
      -
      -  The number of selected children
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  *  true if 0 < numOfCheckedChilds < numOfChilds
         *  false if not
      -
   *  -  **isCheck** |br|
         boolean
      -
      -  Whether this instance is selected
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "nodes" : [{
              "nodes" : [],
              "text" : "[Blank]",
              "value" : "[Blank]"
           }, {
              "nodes" : [],
              "text" : "Finland",
              "value" : "Finland"
           }, {
              "nodes" : [],
              "text" : "USA",
              "value" : "USA"
           }
        ],
        "text" : "[All]",
        "value" : "[All]"
      }
