

=========================================
DataFormat
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **name** |br|
         string
      -
      -  The name of the format
      -
   *  -  **format** |br|
         string
      -
      -  The format
      -
   *  -  **description** |br|
         string
      -
      -  The description
      -
   *  -  **category** |br|
         string
      -
      -  The category
      -
   *  -  **subCategory** |br|
         string
      -
      -  The sub-category
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type
      -
   *  -  **groupBy** |br|
         string
      -
      -  The group by value
      -
   *  -  **formatDataType** |br|
         string
      -
      -  The format data type
      -
   *  -  **position** |br|
         string
      -
      -  The position in the list of data formats
      -
   *  -  **allowFilter** |br|
         boolean
      -
      -  Allow showing in filter field data format or not
      -
   *  -  **allowFieldProperty** |br|
         boolean
      -
      -  Allow showing in in field data format or not
      -
   *  -  **customId** |br|
         string
      -
      -  The id of customed data format (using the name value by default)
      -
   *  -  **jsFormatString** |br|
         string
      -
      -  The format string support to optimize chart labels
      
         .. versionadded:: 2.6.19
      -

Inherited:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
            "id": "104a55b9-70fb-429c-a9d9-78d99cc09f53",
            "name": "-(0,000.00)",
            "format": "-(0,000.00)",
            "description": "Positive: 15,000.25, Negative: -(15,000.25)",
            "category": "Number",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "formatDataType": null,
            "position": 93,
            "allowFilter": true,
            "allowFieldProperty": false,
            "customId": "104a55b9-70fb-429c-a9d9-78d99cc09f53",
            "jsFormatString": null
      }
