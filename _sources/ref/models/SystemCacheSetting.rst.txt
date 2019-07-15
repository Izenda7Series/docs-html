

===================
SystemCacheSetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **timeToLive** |br|
         integer
      -  
      -  Define the lifespan in second for system caches
      -
   *  -  **evictionInterval** |br|
         integer
      -  
      -  Define the inteval to clear expired system caches
      -
   *  -  **defaultEvictionInterval** |br|
         integer
      -  Y
      -  Default value of ``EvictionInterval``
      -
   *  -  **defaultTimeToLive** |br|
         integer
      -  Y
      -  Default value of ``timeToLive``
      -




.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "timeToLive": 60,
         "evictionInterval": 3600,
         "defaultEvictionInterval": 3600,
         "defaultTimeToLive": 60
      }
