StateCode
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
   *  -  **code** |br|
         string
      -
      -  The code of the state
      -
   *  -  **name** |br|
         string
      -
      -  The name of the state
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
      -  The array of coordinates to define the boundary of state |br|
      -


.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "countryCode": "ad",
         "countryCode3": "AND",
         "countryName": "Andorra",
         "code": "CA",
         "name": "Canillo",
         "latitude": "42.5842",
         "longitude": "1.6054",
         "coordinates": "[[{\"lng\":\"1.5556\",\"lat\":\"42.5626\"},{\"lng\":\"1.5578\",\"lat\":\"42.5746\"},{\"lng\":\"1.5645\",\"lat\":\"42.5842\"},{\"lng\":\"1.5750\",\"lat\":\"42.5917\"},{\"lng\":\"1.5883\",\"lat\":\"42.5946\"},{\"lng\":\"1.5988\",\"lat\":\"42.5976\"},{\"lng\":\"1.5988\",\"lat\":\"42.6065\"},{\"lng\":\"1.5973\",\"lat\":\"42.6219\"},{\"lng\":\"1.6083\",\"lat\":\"42.6181\"},{\"lng\":\"1.7220\",\"lat\":\"42.6099\"},{\"lng\":\"1.7133\",\"lat\":\"42.5896\"},{\"lng\":\"1.7294\",\"lat\":\"42.5820\"},{\"lng\":\"1.7527\",\"lat\":\"42.5767\"},{\"lng\":\"1.7611\",\"lat\":\"42.5676\"},{\"lng\":\"1.7611\",\"lat\":\"42.5676\"},{\"lng\":\"1.7651\",\"lat\":\"42.5634\"},{\"lng\":\"1.7400\",\"lat\":\"42.5616\"},{\"lng\":\"1.7217\",\"lat\":\"42.5485\"},{\"lng\":\"1.7171\",\"lat\":\"42.5399\"},{\"lng\":\"1.7103\",\"lat\":\"42.5448\"},{\"lng\":\"1.7006\",\"lat\":\"42.5493\"},{\"lng\":\"1.6902\",\"lat\":\"42.5530\"},{\"lng\":\"1.6865\",\"lat\":\"42.5656\"},{\"lng\":\"1.6828\",\"lat\":\"42.5746\"},{\"lng\":\"1.6686\",\"lat\":\"42.5701\"},{\"lng\":\"1.6493\",\"lat\":\"42.5701\"},{\"lng\":\"1.6285\",\"lat\":\"42.5678\"},{\"lng\":\"1.6047\",\"lat\":\"42.5641\"},{\"lng\":\"1.5712\",\"lat\":\"42.5641\"},{\"lng\":\"1.5556\",\"lat\":\"42.5626\"}]]"
      }