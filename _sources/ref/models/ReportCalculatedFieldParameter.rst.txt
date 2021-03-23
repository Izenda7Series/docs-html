

=========================================
ReportCalculatedFieldParameter
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **calculatedField** |br|
         object
      -
      -  A :doc:`QuerySourceField` object
      -




Inherited fields:

.. include:: ReportParameter.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "reportKey" : {
           "key" : "681dc08e-4355-441f-a438-370d5c1a7a99"
        },
        "calculatedField" : {
           "id" : null,
           "name" : "MoneyInStock",
           "functionName" : "[None]",
           "expression" : "[Northwind].[dbo].[Products].[UnitPrice] * [Northwind].[dbo].[Products].[UnitsInStock]",
           "izendaDataType" : "Money"
        }
      }
