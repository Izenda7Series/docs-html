


WorkspaceTenant
-----------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **workspaceId** |br|
         string (GUID)
      -  Y
      -  The id of the workspace
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **status** |br|
         integer
      -
      -  The status of the workspace tenant

         * 0 = Need Validated
         * 1 = Ready to Copy
         * 2 = Authentication Missing
         * 3 = Validation Error
      -
   *  -  **physicalDataModel** |br|
         string
      -
      -  The physical data structure in json format
      -
   *  -  **sourceDataModel** |br|
         string
      -
      -  The source data model in json format
      -
   *  -  **destinationHashCode** |br|
         string
      -
      -  The hashcode of the tenant data model
      -


Inherited fields:

.. include:: Entity.rst
