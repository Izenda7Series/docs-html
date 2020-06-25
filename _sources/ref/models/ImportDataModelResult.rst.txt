
=========================================
ImportDataModelResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **success** |br|
         boolean
      -
      -  
         * true if the import was successful
         * false if not
      -
   *  -  **messages** |br|
         array of objects
      -  Y
      -  An array of :doc:`ModelError` objects
      -
   *  -  **inconsistentDataSources** |br|
         object
      -  Y
      -  A dynamic object to list inconsistent data sources
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "success": true,
         "messages": null,
         "inconsistentDataSources": null
      }
