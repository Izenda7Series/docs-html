

=======================
QuerySourceSchema
=======================

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
      -  The id of the query source schema
      -
   *  -  **name** |br|
         string
      -
      -  The name
      -
   *  -  **type** |br|
         string
      -
      -  Either "Table", "View", "Stored Procedure" or "Function"
      -
   *  -  **color** |br|
         string
      -
      -  The color for display
      -
   *  -  **connectionId** |br|
         string (GUID)
      -
      -  The id of the connection containing the query source
      -
   *  -  **modified** |br|
         datetime
      -
      -  The modify datetime
      -
   *  -  **fields** |br|
         array of objects
      -
      -  An array of child :doc:`QuerySourceFieldSchema` objects
      -
