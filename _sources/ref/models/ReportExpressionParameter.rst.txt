

=========================================
ReportExpressionParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **expression** |br|
         string
      -
      -  The expression
      -
   *  -  **izendaDataType** |br|
         string
      -
      -  The Izenda data type
      -
   *  -  **querySourceFieldId** |br|
         string (GUID)
      -  Y
      -  The id of the query source field
      -


Inherited fields:

.. include:: ReportParameter.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "reportKey" : {
           "key" : "e40d635c-c90f-45f7-bf7a-5750db7ef9cf"
        },
        "expression" : "[Northwind].[dbo].[Products].[UnitsInStock] * [Northwind].[dbo].[Products].[UnitPrice]"
      }
