
==============
CopyStatus
==============

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **status** |br|
         boolean
      -
      -  Is the copy successful
      -
   *  -  **isEdit** |br|
         boolean
      -
      -  True if overwriting destination report
      -
   *  -  **message** |br|
         array of objects
      -
      -  An array of error messages
      -
   *  -  **newId** |br|
         string (GUID)
      -
      -  The id of the new report
      -
   *  -  **sourceId** |br|
         string (GUID)
      -
      -  The id of source report
      -
   *  -  **tenantId** |br|
         string (GUID)
      -
      -  The id of the tenant
      -
   *  -  **copyMessage** |br|
         string
      -
      -  The display message for the status
      -
   *  -  **hasSubReport** |br|
         boolean
      -
      -  Whether there were sub-reports copied
      -
   *  -  **destinationName** |br|
         string
      -
      -  The destination name
      -
   *  -  **type** |br|
         string
      -
      -  Either "Report", "Template" or "Dashboard"
      -
