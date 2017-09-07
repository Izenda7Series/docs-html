

=========================================
SaveConnectionStatus
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **connectionId** |br|
         string (GUID)
      -  Y
      -  The id of the connection
      -

Inherited fields:

.. include:: OperationResult.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "success" : true,
        "connectionId" : "f5180bc0-7c07-48db-b672-e66a5adde027",
        "connectionErrors" : []
      }
