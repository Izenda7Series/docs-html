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
   
.. Note::

 Please refer to our GitHub repo for the latest code samples
 https://github.com/Izenda7Series/RedisCacheProvider

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

		using Izenda.BI.CacheProvider.RedisCache.Constants;
		using Izenda.BI.CacheProvider.RedisCache.Converters;
		using Izenda.BI.CacheProvider.RedisCache.Resolvers;
		using Izenda.BI.Framework.Models.ReportDesigner;
		using Newtonsoft.Json;
		using StackExchange.Redis;
		using System;
		using System.Collections.Generic;
		using System.ComponentModel.Composition;
		using System.Diagnostics;
		using System.Threading;
		using System.Linq;
		using Izenda.BI.Framework.CustomAttributes;
		using System.Collections.Concurrent;
		using Izenda.BI.Framework.Constants;

		namespace Izenda.BI.CacheProvider.RedisCache
		{
			/// <summary>
			/// Redis cache provider
			/// </summary>
			[Export(typeof(ICacheProvider))]
			public class RedisCacheProvider : ICacheProvider, IDisposable
			{
				private static ConcurrentDictionary<string, object> _mem = new ConcurrentDictionary<string, object>();
				private bool _disposed = false;
				private JsonSerializerSettings _serializerSettings = new JsonSerializerSettings();
				private readonly ReaderWriterLockSlim _lockCache = new ReaderWriterLockSlim(LockRecursionPolicy.SupportsRecursion);
				private readonly IDatabase _cache;
				private readonly IServer _server;

				public RedisCacheProvider()
				{
					_cache = RedisHelper.Database;
					_server = RedisHelper.Server;

					InitSerializer();
				}

				public RedisCacheProvider(IDatabase cache)
				{
					_cache = cache;
					InitSerializer();
				}

				/// <summary>
				/// Initializes the JSON serializer
				/// </summary>
				private void InitSerializer()
				{
					var resolver = new IzendaSerializerContractResolver();
					resolver.Ignore(typeof(ReportPartDefinition), "ReportPartContent");

					_serializerSettings.ReferenceLoopHandling = ReferenceLoopHandling.Ignore;
					_serializerSettings.TypeNameHandling = TypeNameHandling.Objects;
					_serializerSettings.TypeNameAssemblyFormat = System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple;

					_serializerSettings.Converters.Add(new DBServerTypeSupportingConverter());
					_serializerSettings.ContractResolver = resolver;
				}

				/// <summary>
				/// Serializes the obj to json
				/// </summary>
				/// <param name="obj"></param>
				/// <returns> A json string of the object</returns>
				private string Serialize(object obj)
				{
					return JsonConvert.SerializeObject(obj, _serializerSettings);
				}

				/// <summary>
				/// Deserializes the json string to the specified type
				/// </summary>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="serialized">The serialized object</param>
				/// <returns>THe deserialized object</returns>
				private T Deserialize<T>(string serialized)
				{
					return JsonConvert.DeserializeObject<T>(serialized, _serializerSettings);
				}

				/// <summary>
				/// Adds an item to the cache using the specified key.
				/// </summary>
				/// <param name="key"> The key </param>
				/// <param name="value"> The value </param>
				public void Add<T>(string key, T value)
				{
					try
					{
						_lockCache.EnterWriteLock();
						if(IsInMemoryCache(key, typeof(T)))
						{
							_mem.AddOrUpdate(key, value, (existingKey, oldValue) => value);
						}
						else
						{
							_cache.StringSet(key, Serialize(value));
						}
					}
					catch (Exception ex)
					{
						Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
					}
					finally
					{
						_lockCache.ExitWriteLock();
					}
				}

				private bool IsInMemoryCache(string key, Type type)
				{
					return key == IzendaKey.HashCodeMetadata
						|| (type.IsGenericType && type.GenericTypeArguments.Any(t => t == typeof(Object)))
						|| type.FullName.StartsWith("Izenda.BI.DataAdaptor.IDataSourceAdaptor")
						|| type.FullName.StartsWith("Izenda.BI.Logging.ILogManager")
						|| type.FullName.StartsWith("Izenda.BI.SystemRepository.ISystemRepository")
						|| type.FullName.StartsWith("Izenda.BI.Framework.Models.Contexts.UserContext");
				}

				/// <summary>
				/// Adds an item to the cache using the specified key and sets an expiration
				/// </summary>
				/// <param name="key"> The key </param>
				/// <param name="value"> The value</param>
				/// <param name="expiration"> The expiration </param>
				public void AddWithExactLifetime(string key, object value, TimeSpan expiration)
				{  
					try
					{
						_lockCache.EnterWriteLock();
						if (IsInMemoryCache(key, value.GetType()))
						{
							_mem.AddOrUpdate(key, value, (existingKey, oldValue) => value);
						}
						else
						{
							_cache.StringSet(key, Serialize(value), expiration);
						}
					}
					catch (Exception ex)
					{
						Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
					}
					finally
					{
						_lockCache.ExitWriteLock();
					}
				}

				/// <summary>
				/// Adds an item to the cache using the specified key and sets a sliding expiration
				/// </summary>
				/// <param name="key"> The key </param>
				/// <param name="value"> The value</param>
				/// <param name="expiration"> The expiration </param>
				public void AddWithSlidingLifetime(string key, object value, TimeSpan expiration)
				{
					AddWithExactLifetime(key, value, expiration);
				}

				/// <summary>
				/// Checks if the cache contains the given key
				/// </summary>
				/// <param name="key"> The key</param>
				/// <returns>true if the cache contains the key, false otherwise</returns>
				public bool Contains(string key)
				{
					return _mem.ContainsKey(key) ? true : _cache.KeyExists(key);
				}

				/// <summary>
				/// Retrieves the specified key from the cache
				/// </summary>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="key">The key</param>
				/// <returns></returns>
				public T Get<T>(string key)
				{
					
					if (IsInMemoryCache(key, typeof(T)))
					{
						object value;
						_mem.TryGetValue(key, out value);
						return (T)value;
					}
					else
					{
						var result = _cache.StringGet(key);
						if (result.IsNullOrEmpty)
							return default(T);

						return Deserialize<T>(result);
					}
				}

				/// <summary>
				/// Removes the specified item from the cache.
				/// </summary>
				/// <param name="key">The key</param>
				public void Remove(string key)
				{
					try
					{
						_lockCache.EnterWriteLock();
						object value;
						if(!_mem.TryRemove(key, out value))
						{
							_cache.KeyDelete(key);
						}
					}
					catch (Exception ex)
					{
						Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
					}
					finally
					{
						_lockCache.ExitWriteLock();
					}
				}

				/// <summary>
				/// Removes the keys matching the specified pattern.
				/// </summary>
				/// <param name="pattern">The pattern. </param>
				public void RemoveKeyWithPattern(string pattern)
				{
					var keysToRemove = _server.Keys(_cache.Database, pattern);

					try
					{
						_lockCache.EnterWriteLock();

						foreach (var key in keysToRemove)
						{
							object value;
							if (!_mem.TryRemove(key, out value))
							{
								_cache.KeyDelete(key);
							}
						}
					}
					catch (Exception ex)
					{
						Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
					}
					finally
					{
						_lockCache.ExitWriteLock();
					}
				}

				/// <summary>
				/// Retrieves the specified key from the cache. If no value exists, a cache entry is created. 
				/// </summary>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="key">The key</param>
				/// <param name="executor">The function call that returns the data.</param>
				/// <returns></returns>
				public T Ensure<T>(string key, Func<T> executor)
				{
					return EnsureCache(executor, key, TimeSpan.Zero, (cacheKey, result, expiration) =>
					{
						Add(cacheKey, result);
					});
				}

				/// <summary>
				/// Retrieves the specified key from the cache. If no value exists, a cache entry is created. 
				/// </summary>
				/// <typeparam name="T">The type to convert the object to.</typeparam>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="expiration"> The expiration </param>
				/// <param name="executor">The function call that returns the data.</param>
				public T EnsureWithExactLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
				{
					return EnsureCache(executor, key, expiration, (cacheKey, result, expirationTime) =>
					{
						AddWithExactLifetime(cacheKey, result, expirationTime);
					});
				}

				/// <summary>
				/// Retrieves the specified key from the cache. If no value exists, a cache entry is created. 
				/// </summary>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="expiration"> The sliding expiration </param>
				/// <param name="executor">The function call that returns the data.</param>
				public T EnsureWithSlidingLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
				{
					return EnsureWithExactLifetime<T>(key, expiration, executor);
				}

				/// <summary>
				/// Update the cache with the specified value, if the cache does not exist, it is created.
				/// </summary>
				/// <typeparam name="T">The object type</typeparam>
				/// <param name="key">The key.</param>
				/// <param name="expiration">The expiration timeout as a timespan. This is a sliding value.</param>
				/// <param name="executor">The function call that returns the data.</param>
				public T UpdateWithSlidingLifetime<T>(string key, TimeSpan expiration, Func<T> executor)
				{
					var newValue = executor();

					try
					{
						_lockCache.EnterWriteLock();
						if (newValue != null)
						{
							if (IsInMemoryCache(key, typeof(T)))
							{
								_mem.AddOrUpdate(key, newValue, (existingKey, oldValue) => newValue);
							}
							else
							{
								_cache.StringSet(key, Serialize(newValue), expiration);
							}
						}
					}
					catch (Exception ex)
					{
						Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
					}
					finally
					{
						_lockCache.ExitWriteLock();
					}

					return newValue;
				}

				/// <summary>
				/// Retrieves the specified key from the cache. If no value exists, a cache entry is created. 
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
						try
						{
							_lockCache.EnterWriteLock();

							result = Get<T>(key);

							if (EqualityComparer<T>.Default.Equals(result, default(T)))
							{
								var newValue = executor();

								result = newValue;
							}

							if (result != null)
							{
								addItemToCache(key, result, expiration);
							}
						}
						catch (Exception ex)
						{
							Trace.Write(string.Format(AppConstants.ExceptionTemplate, ex.ToString()));
						}
						finally
						{
							_lockCache.ExitWriteLock();
						}
					}

					return result;
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
					if (_disposed)
						return;

					if (disposing)
					{
						_lockCache.Dispose();
					}

					_disposed = true;
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
