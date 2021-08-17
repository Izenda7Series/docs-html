

=========================================
ReportDataSourceParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The tenant id
      -
   *  -  **querySourceId** |br|
         string (GUID)
      -  Y
      -  The id of the query source
      -
   *  -  **relationships** |br|
         array of objects
      -
      -  An array of :doc:`Relationship` objects
      -

Inherited fields:

.. include:: ReportParameter.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "criteria": [{
            "key": "Name",
            "value": ""
         }],
         "pageSize": 50,
         "parentIds": [],
         "querySourceId": null,
         "reportKey" : {
            "key" : "f53b65ba-4d27-45c9-930e-156538f30531",
            "tenantId" : null
         },
         "relationships": [],
         "skipItems": 0,
         "tenantId" : null
      }
