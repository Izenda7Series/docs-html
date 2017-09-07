===================================
ICacheProvider - Redis Sample
===================================

Izenda applies
`caching <https://en.wikipedia.org/wiki/Cache_(computing)>`__ to improve
user responsiveness and reduce resource usage. The built-in caching uses
`Memcached <http://www.memcached.org/>`__ which currently works best for
typical usage scenarios.

For specific needs, this feature can easily be integrated with other
caching systems, via the ``ICacheProvider`` interface.

In this sample, we will use `Redis <http://redis.io/>`__ as an
alternative cache server - there is no intentional comparison between
Memcached and Redis here, we just pick Redis as an example.

Summary of the Steps

#. :ref:`Reference the interface library Izenda.BI.CacheProvider.dll in our code base. <Reference_ICacheProvider_Interface_in_a_New_Project>`
#. :ref:`Provide our own implementation of the ICacheProvider interface. <Implement_the_ICacheProvider_Interface>`
#. :ref:`Unit test the implementation. <Implement_the_Tests>`
#. :ref:`Replace the built-in caching library file
   Izenda.BI.CacheProvider.Memcache.dll with our own library
   file. <Replace_the_Built-in_Caching_Library>`

Preparation
-----------
 

#. Redis test server setup

   #. Download, extract and compile the server from http://redis.io/download.

      For Windows, there are binary builds available at https://github.com/MSOpenTech/redis/releases. |br|

   #. Start the server using this command in terminal:

      .. code-block:: console

         src/redis-server

   #. Start the client in another terminal to check our server:

      .. code-block:: console

         $ src/redis-cli
         redis> set foo bar
         OK
         redis> get foo
         "bar"
#. Redis client library

   #. We will use the `StackExchange.Redis <https://github.com/StackExchange/StackExchange.Redis>`__ library.
   #. We will install it from within Visual Studio in the following :ref:`step <Reference_StackExchange.Redis_Client_Library>`.

ICacheProvider Implementation
----------------------------- 

.. _Reference_ICacheProvider_Interface_in_a_New_Project:

Reference ICacheProvider Interface in a New Project
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Create a new Class Library project in Visual
   Studio.
#. Name it Izenda.BI.CacheProvider.Redis.
#. Select a location (e.g. D:\\Projects).
#. Select to create new solution.
#. Give the solution name Izenda.BI.RedisCache.
#. Tick the Create directory for solution check-box.
#. Click OK to create the project and solution.

   .. figure:: /_static/images/CacheProvider.Redis_New_Project.png

      New Project
#. Copy the interface library file
   Izenda.BI.CacheProvider.dll from Izenda installation folder into the
   newly-created folder
   D:\\Projects\\Izenda.BI.RedisCache\\Izenda.BI.CacheProvider.Redis.
#. Open Solution Explorer, right-click References in project
   Izenda.BI.CacheProvider.Redis and select Add Reference.
#. In Reference Manager pop-up, click Browse and select the file
   Izenda.BI.CacheProvider.dll (in
   D:\\Projects\\Izenda.BI.RedisCache\\Izenda.BI.CacheProvider.Redis).
#. Click OK to close Reference Manager pop-up.
#. Verify the interface by double-clicking Izenda.BI.CacheProvider in
   References to open Object Browser.
#. Expand the nodes and select ICacheProvider to see this list of
   methods to implement.

   .. figure:: /_static/images/ICacheProvider_Interface.png

      ICacheProvider Interface

.. _Reference_StackExchange.Redis_Client_Library:

Reference StackExchange.Redis Client Library
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Open NuGet Package Manager pop-up from Tools > NuGet Package Manager
   > Manage NuGet Packages for Solution...
#. Click Browse tab and enter StackExchange.Redis in the text box to
   search.
#. Select StackExchange.Redis on the left and tick the
   Izenda.BI.CacheProvider.Redis project check-box on the right.
#. Select Latest stable 1.1.608 (at the time of writing) and click
   Install.
#. Verify that StackExchange.Redis is shown in the References list in
   Solution Explorer.

.. _Implement_the_ICacheProvider_Interface:

Implement the ICacheProvider Interface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Right-click the default Class1.cs file in Solution Explorer and
   rename it to RedisCacheProvider.cs, also agree to change the class
   name to RedisCacheProvider when asked.
#. Implement the methods of the interface using StackExchange.Redis
   APIs.
#. Reference the namespace System.ComponentModel.Composition if
   necessary (Add Reference and tick System.ComponentModel.Composition
   in Assemblies > Framework).

.. note::

   The Redis server address is assumed to be "localhost" in this sample. It should be read from the configuration file in an actual code.

.. container:: toggle

   .. container:: header

      Full sample code:

   .. code-block:: csharp

      using System;
      using System.Collections.Generic;
      using System.ComponentModel.Composition;
      using System.Threading;
      using StackExchange.Redis;
      
      namespace Izenda.BI.CacheProvider.Redis
      {
         /// <summary>
         /// Redis cache provider
         /// </summary>
         [Export(typeof(ICacheProvider))]
         public class RedisCacheProvider : ICacheProvider, IDisposable
         {
            private bool disposed = false;
            private readonly ReaderWriterLockSlim lockCache = new ReaderWriterLockSlim();
            private static ConnectionMultiplexer redis;
            private static String serverAddress = "localhost";
      
            public RedisCacheProvider()
            {
                 redis = ConnectionMultiplexer.Connect(serverAddress);
            }
      
            /// <summary>
            ///     Adds an item to the underlying cache using the specified key.
            /// </summary>
            /// <param name="key"> The key. </param>
            /// <param name="value"> The value. </param>
            public void Add<T>(string key, T value)
            {
                 IDatabase db = redis.GetDatabase();
                 String stringValue = (String) Convert.ChangeType(value, System.TypeCode.String);
                 db.StringSet(key, stringValue);
            }
      
            /// <summary>
            ///     Adds an item to the underlying cache using the specified key with normal priority.
            /// </summary>
            /// <param name="key"> The key. </param>
            /// <param name="value"> The value. </param>
            /// <param name="expiration"> The expiration timeout as a timespan. This is a sliding value. </param>
            public void AddWithExactLifetime(string key, object value, TimeSpan expiration)
            {
                 IDatabase db = redis.GetDatabase();
                 String stringValue = (String)Convert.ChangeType(value, System.TypeCode.String);
                 // StackExchange.Redis client does not support exact datetime expiration, so sliding option is used.
                 db.StringSet(key, stringValue, expiration);
            }
      
            /// <summary>
            ///     Adds an item to the underlying cache using the specified key with normal priority.
            /// </summary>
            /// <param name="key"> The key. </param>
            /// <param name="value"> The value. </param>
            /// <param name="expiration"> The expiration timeout as a timespan. This is a sliding value. </param>
            public void AddWithSlidingLifetime(string key, object value, TimeSpan expiration)
            {
                 IDatabase db = redis.GetDatabase();
                 String stringValue = (String)Convert.ChangeType(value, System.TypeCode.String);
                 db.StringSet(key, stringValue, expiration);
            }
      
            /// <summary>
            ///     Determines whether the cache contains the specified key.
            /// </summary>
            /// <param name="key">The key.</param>
            /// <returns>
            ///     <c>true</c> if the underlying cache contains the key otherwise, <c>false</c>.
            /// </returns>
            public bool Contains(string key)
            {
                 IDatabase db = redis.GetDatabase();
                 return db.KeyExists(key);
            }
      
            /// <summary>
            /// Get object from cache. Build and add the cache if not exist.
            /// </summary>
            /// <typeparam name="T">The type to convert the object to.</typeparam>
            /// <param name="key">The key.</param>
            /// <param name="executor">The function call that returns the data.</param>
            public T Ensure<T>(string key, Func<T> executor)
            {
                 IDatabase db = redis.GetDatabase();
                 return EnsureCache(executor, key, TimeSpan.Zero, (caheKey, result, expiration) =>
                 {
                     Add(caheKey, result);
                 });
            }
      
            /// <summary>
            /// Get object from cache. Build and add the cache if not exist.
            /// </summary>
            /// <typeparam name="T">The type to convert the object to.</typeparam>
            /// <param name="key">The key.</param>
            /// <param name="expiration">The expiration timeout as a timespan. This is a sliding value.</param>
            /// <param name="executor">The function call that returns the data.</param>
            public T EnsureWithSlidingLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
            {
                 IDatabase db = redis.GetDatabase();
                 return EnsureCache(executor, key, expiration, (caheKey, result, expirationTime) =>
                 {
                     AddWithSlidingLifetime(caheKey, result, expirationTime);
                 });
            }
      
            /// <summary>
            /// Update and add the cache if not exist.
            /// </summary>
            /// <typeparam name="T">The type to convert the object to.</typeparam>
            /// <param name="key">The key.</param>
            /// <param name="expiration">The expiration timeout as a timespan. This is a sliding value.</param>
            /// <param name="executor">The function call that returns the data.</param>
            public T UpdateWithSlidingLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
            {
                 IDatabase db = redis.GetDatabase();
      
                 var updatingValue = executor();
                 lockCache.EnterWriteLock();
      
                 try
                 {
                     if (updatingValue != null)
                     {
                         String stringValue = (String)Convert.ChangeType(updatingValue, System.TypeCode.String);
                         db.StringSet(key, stringValue, expiration);
                     }
                 }
                 catch
                 {
                     System.Diagnostics.Trace.Write("**********----------Izenda: Fail set item to cache----------**********");
                 }
                 finally
                 {
                     lockCache.ExitWriteLock();
                 }
      
                 return updatingValue;
            }
      
            /// <summary>
            /// Get object from cache. Build and add the cache if not exist.
            /// </summary>
            /// <typeparam name="T">The type to convert the object to.</typeparam>
            /// <param name="key">The key.</param>
            /// <param name="expiration">The expiration timeout as a timespan. This is a exact value.</param>
            /// <param name="executor">The function call that returns the data.</param>
            public T EnsureWithExactLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
            {
                 IDatabase db = redis.GetDatabase();
                 return EnsureCache(executor, key, expiration, (caheKey, result, expirationTime) =>
                 {
                     AddWithExactLifetime(caheKey, result, expirationTime);
                 });
            }
      
            /// <summary>
            ///     Removes the specified item from the cache.
            /// </summary>
            /// <param name="key">The key</param>
            public void Remove(string key)
            {
                 IDatabase db = redis.GetDatabase();
                 db.KeyDelete(key);
            }
      
            /// <summary>
            /// Get object from cache. Build and add the cache if not exist.
            /// </summary>
            /// <typeparam name="T">The type to convert the object to.</typeparam>
            /// <param name="executor">The function call that returns the data.</param>
            /// <param name="key">The key.</param>
            /// <param name="expiration">The expiration timeout as a timespan.</param>
            private T EnsureCache<T>(Func<T> executor, string key, TimeSpan expiration, Action<string, T, TimeSpan> addItemToCache)
            {
                 var result = Get<T>(key);
      
                 if (EqualityComparer<T>.Default.Equals(result, default(T)))
                 {
                     var addingValue = executor();
                     lockCache.EnterWriteLock();
      
                     try
                     {
                         //Todo: remove log
                         System.Diagnostics.Trace.Write("**********----------Izenda: Adding item to cache----------**********");
                         result = addingValue;
      
                         if (result != null)
                         {
                             addItemToCache(key, result, expiration);
                         }
                     }
                     catch
                     {
                         System.Diagnostics.Trace.Write("**********----------Izenda: Fail add item to cache----------**********");
                     }
                     finally
                     {
                         lockCache.ExitWriteLock();
                     }
                 }
      
                 return result;
            }
      
            /// <summary>
            ///     Convenience method to retrieve and convert the object result from the cache.
            /// </summary>
            /// <typeparam name="T"> The type to convert the object to. </typeparam>
            /// <param name="key"> The key. </param>
            /// <returns> The instance of the object in the cache or the default value for the type if not found. </returns>
            public T Get<T>(string key)
            {
                 IDatabase db = redis.GetDatabase();
                 var result = db.StringGet(key);
      
                 if (result.IsNull)
                 {
                     return default(T);
                 }
      
                 return (T) Convert.ChangeType(result, typeof(T));
            }
      
            /// <summary>
            /// Dispose object
            /// </summary>
            public void Dispose()
            {
                 Dispose(true);
                 GC.SuppressFinalize(this);
            }
      
            /// <summary>
            /// Dispose object
            /// </summary>
            /// <param name="disposing"></param>
            protected virtual void Dispose(bool disposing)
            {
                 if (disposed)
                     return;
      
                 if (disposing)
                 {
                     lockCache.Dispose();
                 }
      
                 disposed = true;
            }
      
            /// <summary>
            /// Dispose object
            /// </summary>
            ~RedisCacheProvider()
            {
                 Dispose(false);
            }
         }
      }

Add UnitTest Project
~~~~~~~~~~~~~~~~~~~~

#. Rick click Solution 'Izenda.BI.RedisCache' in Solution Explorer and
   select Add > New Project.
#. Add a Class Library project named Izenda.BI.CacheProvider.Redis.Test.
#. Reference the project Izenda.BI.CacheProvider.Redis (Add Reference
   and tick Izenda.BI.CacheProvider.Redis in Projects > Solution).
#. Reference xUnit Library.

   #. Open NuGet Package Manager pop-up from Tools > NuGet Package
      Manager > Manage NuGet Packages for Solution...
   #. Click Browse tab and enter xunit in the text box to search.
   #. Select xunit on the left and tick the
      Izenda.BI.CacheProvider.Redis.Test project check-box on the right.
   #. Select version 1.9.1 (working at the time of writing) and click
      Install.
   #. Similarly install xunit.runner.visualstudio version 2.1.0 to
      Izenda.BI.CacheProvider.Redis.Test project.

.. _Implement_the_Tests:

Implement the Tests
~~~~~~~~~~~~~~~~~~~

#. Right-click the default Class1.cs file in Solution Explorer and
   rename it to RedisCacheProviderTest.cs, also agree to change the
   class name to RedisCacheProviderTest when asked.
#. Implement the tests in xUnit.

.. container:: toggle

   .. container:: header

      Full sample code:

   .. code-block:: csharp

      using System;
      using System.Collections.Generic;
      using System.Linq;
      using System.Text;
      using System.Threading.Tasks;
      using Xunit;
      
      namespace Izenda.BI.CacheProvider.Redis.Test
      {
         public class RedisCacheProviderTest
         {
            private const string Key = "test_key";
            private const string Value = "test value";
      
            /// <summary>
            /// Test function Add()
            /// </summary>
            [Fact]
            public void AddValueToCache_NoExpiration()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.Add(Key, Value);
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
      
            /// <summary>
            /// Test function AddWithExactLifeTime()
            /// </summary>
            [Fact]
            public void AddWithExactLifeTime_ExpireIn20Seconds()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.AddWithExactLifetime(Key, Value, new TimeSpan(0, 0, 20));
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
            /// <summary>
            /// Test function AddWithSlidingLifetime()
            /// </summary>
            [Fact]
            public void AddWithSlidingLifetime_ExpireAfter20Seconds()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.AddWithSlidingLifetime(Key, Value, new TimeSpan(0, 0, 20));
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
            /// <summary>
            /// Test function Contain()
            /// </summary>
            [Fact]
            public void ContainKey_ReturnTrueAfterAddItem()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.Add(Key, Value);
                 var containKeyInCache = redisCacheProvider.Contains(Key);
      
                 Assert.True(containKeyInCache);
            }
      
            /// <summary>
            /// Test function Ensure()
            /// </summary>
            [Fact]
            public void EnsureCache_ReturnCorrectObject()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.Ensure(Key, () => { return Value; });
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
            /// <summary>
            /// Test function EnsureCacheWithExactLifeTime()
            /// </summary>
            [Fact]
            public void EnsureCacheWithExactLifeTime_ReturnCorrectObject()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.EnsureWithExactLifetime(Key, new TimeSpan(0, 0, 20), () => { return Value; });
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
            /// <summary>
            /// Test function TestEnsureCacheWidthSlidingLifetime()
            /// </summary>
            [Fact]
            public void EnsureCacheWidthSlidingLifetime_ReturnCorrectObject()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.EnsureWithSlidingLifetime(Key, new TimeSpan(0, 0, 20), () => { return Value; });
                 var valueFromCache = redisCacheProvider.Get<string>(Key);
      
                 Assert.Equal(Value, valueFromCache);
            }
      
            /// <summary>
            /// Test function Remove()
            /// </summary>
            [Fact]
            public void RemoveCache_ObjectIsRemoved()
            {
                 var redisCacheProvider = new RedisCacheProvider();
                 redisCacheProvider.Add(Key, Value);
                 redisCacheProvider.Remove(Key);
      
                 var containCacheKey = redisCacheProvider.Contains(Key);
                 Assert.False(containCacheKey);
            }
         }
      }

Run the UnitTests
~~~~~~~~~~~~~~~~~

#. Open Test Explorer from Menu > Test > Windows.
#. Click Run All in Test Explorer.

       (Remember to start the Redis server before testing)

#. All the tests should be passed.

.. figure:: /_static/images/RedisCacheProviderTest_TestExplorer.png

   Test Explorer Result

.. _Replace_the_Built-in_Caching_Library:

Replace the Built-in Caching Library
------------------------------------

#. In the installation folder, find the built-in caching library file
   Izenda.BI.CacheProvider.Memcache.dll and rename to
   Izenda.BI.CacheProvider.Memcache.dll.unused.
#. Copy the new caching library file Izenda.BI.CacheProvider.Redis.dll
   and StackExchange.Redis.dll to the folder (they can be found at
   D:\\Projects\\Izenda.BI.RedisCache\\Izenda.BI.CacheProvider.Redis\\bin\\Debug\\).
#. Restart the system for the DLL to be loaded.
#. Use the system for a while then open the Redis client in terminal to check our cache:

   .. code-block:: console

      $ src/redis-cli
      redis> keys *
