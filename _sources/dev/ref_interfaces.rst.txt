===========================
Customizable Interfaces
===========================

.. versionchanged:: 0.22.12
   The namespace has been changed from Izenda.Synergy to **Izenda.BI**. The sample codes have been updated accordingly.


List of Interfaces
------------------

.. list-table::
   :widths: 20 30 50
   :header-rows: 1

   * - Interface
     - Purpose
     - Full Sample
   * - **ICache**
     - Caching
     - :doc:`code_icacheprovider_redis`
   * - **IDataSourceAdaptor**
     - Adapter for database systems
     - :doc:`code_idatasourceadaptor_db2`
   * - **ISystemRepository**
     - Access to Izenda System Database
     - To be updated

ICache
------

#. Create a class to implement interface ``ICache`` (in namespace
   Izenda.BI.CacheProvider)
#. Mark class attribute: ``[Export(typeof(ICache))]``

Samples

-  To be updated

IDataSourceAdaptor
------------------

#. Create a class to implement interface ``IDataSourceAdaptor`` (in
   namespace Izenda.BI.DataAdaptor)
#. Mark class attribute: ``[Export(typeof(IDataSourceAdaptor))]``
#. Create a Server Type value with this format
   ``<GUID>|<DbShortName>|[<DBShortName>] <DbFullName>``
#. Mark class attribute:
   ``[ExportMetadata("ServerType", "Server Type value")]``

Samples

-  To be updated

ISystemRepository
-----------------

#. Create a class to implement interface ``ISystemRepository`` (in
   namespace Izenda.BI.SystemRepository)
#. Mark class attribute: ``[Export(typeof(ISystemRepository))]``
#. Create a Server Type value with this format
   ``<GUID>|<DbShortName>|[<DBShortName>] <DbFullName>``
#. Mark class attribute:
   ``[ExportMetadata("ServerType", "Server Type value")]``

Samples

   .. code-block:: csharp

      [Export(typeof(ISystemRepository))]
      [ExportMetadata("ServerType", "572BD576-8C92-4901-AB2A-B16E38144813|MSSQL|[MSSQL] SQLServer")]
      public class SQLSystemRepository : ISystemRepository

.. deprecated:: 0.22.12
   The IHiddenFilter interface has been superseded by IAdhocExtension interface
