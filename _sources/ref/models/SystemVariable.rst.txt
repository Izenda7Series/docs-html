

=================
SystemVariable
=================

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
      -  The id of the system variable
      -
   *  -  **name** |br|
         string
      -
      -  The variable name
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type
      -
   *  -  **description** |br|
         string
      -
      -  The description
      -
   *  -  **scope** |br|
         integer
      -
      -  The scope
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "id" : "5cd4d4be-96d9-4c30-8680-04bd602bccd7",
         "name" : "{reportName}",
         "dataType" : "Text",
         "description" : "",
         "scope" : 0
      }
