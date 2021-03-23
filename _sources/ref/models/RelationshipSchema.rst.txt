==================
RelationshipSchema
==================


.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **joinQuerySourceId** |br|
         string (GUID)
      -
      -  The id of the query source containing the relationship
      -
   *  -  **foreignQuerySourceId** |br|
         string (GUID)
      -
      -  The id of the query source referenced by the relationship
      -
   *  -  **twoWays** |br|
         boolean
      -
      -  Is this a two-way relationship
      -  "Inner", "Full" and "Cross" join types are two-way while "Left" and "Right" are not
