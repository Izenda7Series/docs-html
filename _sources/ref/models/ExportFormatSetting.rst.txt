

=========================================
ExportFormatSetting
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **orientation** |br|
         integer
      -
      -

         -  0 = Portrait
         -  1 = Landscape
      -
   *  -  **margins** |br|
         integer
      -
      -

         -  0 = Normal
         -  1 = Narrow
         -  2 = Wide
         -  3 = Custom
         -  4 = MinCustom
         -  5 = MaxCustom
      -
   *  -  **centerOnPage** |br|
         object
      -
      -  A :doc:`CenterOnPageStyle` object
      -
   *  -  **pageBreakAfterReportPart** |br|
         boolean
      -
      -  True if "page break after each report part" is set
      -
   *  -  **marginSettings** |br|
         array of objects
      -
      -  An array of :doc:`ExportMarginTypeSetting` objects
      -
