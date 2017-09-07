

=========================================
ReportSelectedQuerySource
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **querySourceId** |br|
         string (GUID)
      -
      -  The id of the query source
      -
   *  -  **isNew** |br|
         boolean
      -
      -  Whether the query source is new selection
      -
   *  -  **physicalChange** |br|
         integer
      -
      -  The change
      -
   *  -  **selected** |br|
         boolean
      -
      -  Is the query source selected
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "querySourceId": "39e2a9b9-3be3-4b8b-ae86-0823ecb3c533",
         "isNew": false,
         "physicalChange": 0,
         "selected": false
      }
