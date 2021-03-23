

=========================================
ReportConnectionParam
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note

   *  -  **categories** |br|
         array of objects
      -
      -  An array of :doc:`ReportCategoryParam` objects.
      -


Inherited fields:

.. include:: ReportParam.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

        {
            "categories": [
                {
                    "querySourceNames": [
                        "Employees"
                    ],
                    "id": "860cab58-d90a-4d6d-9251-ec45c067f6b9",
                    "name": "dbo"
                }
            ],
            "id": "5963219c-5243-4b6f-9042-b27ca9cbc5ec",
            "name": "Retail"
        }