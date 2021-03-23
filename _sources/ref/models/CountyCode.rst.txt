CountyCode
====================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **countryCode** |br|
         string
      -
      -  The country code
      -
   *  -  **countryCode3** |br|
         string
      -
      -  The ISO Alpha-3 country code
      -
   *  -  **countryName** |br|
         string
      -
      -  The name of the country
      -
   *  -  **stateCode** |br|
         string
      -
      -  The code of the state
      -
   *  -  **stateName** |br|
         string
      -
      -  The name of the state
      -
   *  -  **code** |br|
         string
      -
      -  The code of the county
      -
   *  -  **name** |br|
         string
      -
      -  The name of the county
      -
   *  -  **latitude** |br|
         string
      -
      -  The latitude
      -
   *  -  **longitude** |br|
         string
      -
      -  The longitude
      -
   *  -  **coordinates** |br|
         string
      -
      -  The array of coordinates to define the boundary of county |br|
      -


.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "countryCode": "us",
         "countryCode3": "USA",
         "countryName": "United States",
         "stateCode": "in",
         "stateName": "Inagua",
         "code": "OR",
         "name": "Orange",
         "latitude": "",
         "longitude": "",
         "coordinates": "[[{\"lng\":\"-86.6816\",\"lat\":\"38.3949\"},{\"lng\":\"-86.6819\",\"lat\":\"38.4488\"},{\"lng\":\"-86.6826\",\"lat\":\"38.5264\"},{\"lng\":\"-86.6826\",\"lat\":\"38.5930\"},{\"lng\":\"-86.6830\",\"lat\":\"38.6867\"},{\"lng\":\"-86.4602\",\"lat\":\"38.6888\"},{\"lng\":\"-86.3088\",\"lat\":\"38.6883\"},{\"lng\":\"-86.3080\",\"lat\":\"38.6443\"},{\"lng\":\"-86.3088\",\"lat\":\"38.4228\"},{\"lng\":\"-86.3090\",\"lat\":\"38.3939\"},{\"lng\":\"-86.4519\",\"lat\":\"38.3963\"},{\"lng\":\"-86.6816\",\"lat\":\"38.3949\"}]]"
      }