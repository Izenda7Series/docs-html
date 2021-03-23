.. _Cache_Config:


======================================
Cache
======================================


Introduction
------------------------------------------
* Izenda v3.3.0 and higher provides option to cache report  or dashboard data so that the performance can be mitigated.

Configuration
-----------------

Configure to store cache on memory
======================================

In the Web.config (.NET 4.6.1) or appsettings.json (.NET Core), Configure to use ``MemoryCacheStore`` by ``izenda.cache.data.cachestore`` and also limit the usage by ``izenda.cache.memcache.datacache.maxmemusage``

For example:

*  Web.config:

   .. code-block:: xml

      <add key="izenda.cache.data.cachestore" value="MemoryCacheStore"/>
      <add key="izenda.cache.memcache.datacache.maxmemusage" value="512"/> <!--Unit: MB, Minimum: 512-->


*  appsettings.json:

   .. code-block:: json
      
      {
         "izenda.cache.data.cachestore" : "MemoryCacheStore"/>
         "izenda.cache.memcache.datacache.maxmemusage" : "512"/> // Unit: MB, Minimum: 512
      }

Configure to store cache on disk
======================================

In the Web.config (.NET 4.6.1) or appsettings.json (.NET Core), Configure to use ``ExternalStorageCacheStore`` by ``izenda.cache.data.cachestore``

For example:

*  Web.config:

   .. code-block:: xml

      <add key="izenda.cache.data.cachestore" value="ExternalStorageCacheStore"/>


*  appsettings.json:

   .. code-block:: json
      
      {
         "izenda.cache.data.cachestore" : "ExternalStorageCacheStore"/>
      }