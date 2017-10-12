

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
      -  An object with |br|
         \- a string field **izendaDataType** containing the suggested data type |br|
         \- a boolean field **isRunningField** whether expression in request payload contains running field
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **ValidationOperationResult Sample**:

   .. code-block:: json

      {
         "result": {
            "izendaDataType": "Numeric",
            "isRunningField": true
         },
         "success": true,
         "messages": [],
         "data": null
      }
