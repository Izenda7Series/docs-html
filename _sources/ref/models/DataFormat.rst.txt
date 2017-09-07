

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
   *  -  **customId** |br|
         string
      -
      -  The id of customed data format (using the name value by default)
      -

Inherited:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "name": "MM/dd/yyyy",
         "format": "MM/dd/yyyy",
         "description": "01/01/2016",
         "category": "Short Date",
         "subCategory": "",
         "dataType": "Date & Time",
         "groupBy": "date",
         "position": "1",
         "id": "8074c8aa-55c7-4326-b6cd-0d4b0f7300cb",
         "state": 0,
         "version": null,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
      }
