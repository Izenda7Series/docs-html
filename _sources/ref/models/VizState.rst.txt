===================
VizState
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **zoomLevel** |br|
         integer
      -
      -  The zoom level of the map
      -
   *  -  **centerPoint** |br|
         object
      -
      -  The center point of the map. This object contains 2 propeties as below: |br|

         \- *lat*: the latitude of the center point |br|
         \- *long*: the longitude of the center point
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "zoomLevel": 1,
         "centerPoint": {
            "lat": 0,
            "lng": 0
         }
      }