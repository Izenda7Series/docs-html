

===================
DataCacheSetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **isEnableDataCache** |br|
         boolean
      -  
      -  Whether data cache is enable or not
      -
   *  -  **timeToLive** |br|
         integer
      -  
      -  Define the lifespan in second for data caches
      -
   *  -  **evictionInterval** |br|
         integer
      -  
      -  Define the inteval to clear expired data caches
      -
   *  -  **refreshInterval** |br|
         integer
      -  
      -  Define the interval to load new data for data caches
      -
   *  -  **refreshDuration** |br|
         integer
      -  
      -  Limit the time to run refresh data cache job
      -
   *  -  **defaultIsEnableDataCache** |br|
         boolean
      -  Y
      -  Default value of ``isEnableDataCache``
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
   *  -  **defaultRefreshInterval** |br|
         integer
      -  Y
      -  Default value of ``refreshInterval``
      -
   *  -  **defaultRefreshDuration** |br|
         integer
      -  Y
      -  Default value of ``refreshDuration``
      -



.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "isEnableDataCache": true,
         "timeToLive": 600,
         "evictionInterval": 600,
         "refreshInterval": 200,
         "refreshDuration": 100,
         "defaultIsEnableDataCache": true,
         "defaultEvictionInterval": 600,
         "defaultTimeToLive": 600,
         "defaultRefreshInterval": 200,
         "defaultRefreshDuration": 100
      }
