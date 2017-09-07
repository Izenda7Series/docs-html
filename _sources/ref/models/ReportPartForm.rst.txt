
=====================
ReportPartForm
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
      -  The type of the report part (1 = Form)
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
      -  A :doc:`ReportPartFormProperties` object
   *  -  **columns** |br|
         object
      -
      -  Data for Columns box |br|
         A :doc:`ReportPartContainer` object containing "columns" in **name** and the list of selected data source fields (:doc:`ReportPartElement` objects) in **elements**
   *  -  **separators** |br|
         object
      -
      -  Data for Separators box |br|
         A :doc:`ReportPartContainer` object containing "separators" in **name** and the list of selected data source fields (:doc:`ReportPartElement` objects) in **elements**
   *  -  **reportPartFormRepeater** |br|
         object
      -
      -  To be updated
   *  -  **reportPartFormEmbeddedReport** |br|
         object
      -
      -  To be updated
   *  -  **reportPartFormSmartTag** |br|
         object
      -
      -  To be updated
   *  -  **reportPartFormField** |br|
         object
      -
      -  To be updated
   *  -  **formState** |br|
         object
      -
      -  To be updated
   *  -  **htmlContent** |br|
         string
      -
      -  The HTML code built up for display, optionally edited by user
   *  -  **selectedFieldElement** |br|
         object
      -
      -  To be updated
   *  -  **activeTabKey** |br|
         string
      -
      -  To be updated
   *  -  **isSelectedCell** |br|
         boolean
      -
      -  Whether 
   *  -  **isActiveForEdit** |br|
         string
      -
      -  Whether 
