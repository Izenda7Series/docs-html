

=========================================
ValidationOperationResult
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **result** |br|
         object
      -
      -  An object with a string field **izendaDataType** containing the suggested data type
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "result" : {
           "izendaDataType" : "Money"
        },
        "success" : true,
        "messages" : []
      }
