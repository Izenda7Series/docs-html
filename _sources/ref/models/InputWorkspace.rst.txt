
==============
InputWorkspace
==============

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **sourceTenantId** |br|
         string
      -
      -  The user-defined id of the source tenant
      -
   *  -  **reportIds** |br|
         array of strings
      -
      -  The list of report ids
      -
   *  -  **reportIdsLineNumber** |br|
         array of objects
      -
      -  An array of :doc:`CopiedItem` objects
      -
   *  -  **templateIds** |br|
         array of strings
      -
      -  The list of template ids
      -
   *  -  **templateIdsLineNumber** |br|
         array of objects
      -
      -  An array of :doc:`CopiedItem` objects
      -
   *  -  **dashboardIds** |br|
         array of strings
      -
      -  The list of dashboard ids
      -
   *  -  **dashboardIdsLineNumber** |br|
         array of objects
      -
      -  An array of :doc:`CopiedItem` objects
      -
   *  -  **destinationTenants** |br|
         array of objects
      -
      -  An array of :doc:`DestinationTenant` objects
      -
   *  -  **dataInSource** |br|
         object
      -
      -  A :doc:`DataInSource` object
      -
   *  -  **sourceLineNumber** |br|
         integer
      -
      -  The line number for source tag
      -
   *  -  **destinationLineNumber** |br|
         integer
      -
      -  The line number for destination tag
      -
   *  -  **sourceTenantLineNumber** |br|
         integer
      -
      -  The line number for source tenant tag
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "sourceTenantId": "78e5699a-6a67-471f-8374-529a80777754",
         "reportIds": [
            "4b6d592e-ad29-408d-a3f2-845776d555db"
         ]
      }