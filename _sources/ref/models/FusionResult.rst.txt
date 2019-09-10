

====================
FusionResult
====================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **records** |br|
         array of objects
      -
      -  An array of dynamic objects
      -
   *  -  **fieldsMapping** |br|
         array of objects
      -
      -  An array of dynamic objects
      -
   *  -  **grandTotalMapping** |br|
         array of objects
      -
      -  An array of dynamic objects
      -
   *  -  **subTotalMapping** |br|
         array of objects
      -
      -  An array of dynamic objects
      -
   *  -  **sideTotalMapping** |br|
         array of objects
      -
      -  An array of dynamic objects
      -
   *  -  **executionTrace** |br|
         array of strings
      -
      -  The execution trace
      -
   *  -  **paging** |br|
         object
      -
      -  A :doc:`PagingInfo` object
      -
   *  -  **pivotHeaderValues** |br|
         array of objects
      -
      -  The pivot header value |br|
         An array of dynamic objects
      -
   *  -  **cities** |br|
         array of objects
      -
      -  An array of :doc:`City` objects
      -
   *  -  **postalCodes** |br|
         array of objects
      -
      -  An array of :doc:`PostCode` objects
      -
   *  -  **stateCodes** |br|
         array of objects

         .. versionadded:: 3.5.0
      -
      -  An array of :doc:`StateCode` objects
      -
   *  -  **countyCodes** |br|
         array of objects

         .. versionadded:: 3.5.0
      -
      -  An array of :doc:`CountyCode` objects
      -
   *  -  **addressCodes** |br|
         array of objects

         .. versionadded:: 3.5.0
      -
      -  An array of :doc:`AddressCode` objects
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "grandTotalMapping" : [],
        "subTotalMapping" : [],
        "sideTotalMapping" : [],
        "records" : [{
              "freight_914e4fca_2d9e_" : 48.2900
           }, {
              "freight_914e4fca_2d9e_" : 4.5600
           }, {
              "freight_914e4fca_2d9e_" : 4.5400
           }, {
              "freight_914e4fca_2d9e_" : 98.0300
           }
        ],
        "fieldsMapping" : [{
              "fieldId" : "914e4fca-2d9e-4a9f-a224-8d4cc4133996",
              "fieldNameAlias" : "Freight",
              "columnName" : "freight_914e4fca_2d9e_"
           }
        ],
        "paging" : {
           "pageIndex" : 0,
           "pageSize" : 0,
           "total" : 0
        }
      }
