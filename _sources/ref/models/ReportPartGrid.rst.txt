
=====================
ReportPartGrid
=====================

.. comment: this is the Object Model in Front-end

.. list-table::
   :header-rows: 1
   :widths: 25 5 70

   *  -  Field
      -  NULL
      -  Description
   *  -  **type** |br|
         integer
      -
      -  The type of the report part (3 = Grid)
   *  -  **title** |br|
         object
      -
      -  To be updated
   *  -  **description** |br|
         object
      -
      -  To be updated
   *  -  **properties** |br|
         object
      -
      -  A :doc:`ReportPartGridProperties` object
   *  -  **settings** |br|
         object
      -
      -  A dynamic object to keep the settings in Report Part Configuration, can be user-defined.
   *  -  **columns** |br|
         object
      -
      -  Data for the Columns box |br|
         A :doc:`ReportPartContainer` object containing "columns" in **name** and the list of selected data source fields in **elements**
   *  -  **values** |br|
         object
      -
      -  To be updated
   *  -  **rows** |br|
         object
      -
      -  To be updated
   *  -  **separators** |br|
         object
      -
      -  Data for the Separators box |br|
         A :doc:`ReportPartContainer` object containing "separators" in **name** and the list of selected data source fields in **elements**
