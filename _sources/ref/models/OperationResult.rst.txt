

OperationResult
------------------

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
      -  Is the operation successful
      -
   *  -  **messages** |br|
         array of objects
      -
      -  An array of :doc:`ModelError` objects
      -
   *  -  **data** |br|
         object
      -
      -  A dynamic object to store additional data
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "success": true,
         "data": "4e2d54c8-20e7-437f-a5ce-43e963c763a2"
      }
