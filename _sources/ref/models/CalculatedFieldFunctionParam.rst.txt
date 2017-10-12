
=============================
CalculatedFieldFunctionParam
=============================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -
      -  The id of the tenant
      -
   *  -  **querySourceIds** |br|
         a list of string (GUID)
      -
      -  The ids of the Query Sources
      -
   *  -  **includeCustomJsonFunction** |br|
         boolean
      -
      -  Whether this is include custom json function or not
      -

.. container:: toggle

   .. container:: header

      **CalculatedFieldFunctionParam Sample**:

   .. code-block:: json

      {
         "tenantId" : "b5b3a5cc-9e55-424c-ae85-ba92ec3b934e",
         "querySourceIds" : [
            "273badf8-d210-494f-a458-25e8f462891f",
            "5cc9e1dd-239c-43ac-8098-6b1c4b9e4478",
            "25ac2696-cabb-41df-a9aa-1b46f46c42f1",
            "f7ae5b5d-628e-4eaf-b8b2-fd823a484a35"		
         ],
         "includeCustomJsonFunction" : false
      }
