

===================
PerformanceSetting
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **queryTimeoutValue** |br|
         integer
      -
      -  An array of child ValueTreeNode objects.
      -
   *  -  **queryTimeoutDefaultValue** |br|
         integer
      -
      -  The default value for Query Timeout (``3600`` s)
      -
   *  -  **useNoLockValue** |br|
         boolean
      -
      -  Use :term:`NOLOCK` setting - whether the NOLOCK or equivalent clauses will be used in SQL queries.
      -
   *  -  **useNoLockDefaultValue** |br|
         boolean
      -
      -  The default value for Use NOLOCK (``true``)
      -
   *  -  **dataSourceLimitValue** |br|
         integer
      -
      -  Data Source Limit - the number of data sources allowed to be used in a single report.
      -
   *  -  **dataSourceLimitDefaultValue** |br|
         integer
      -
      -  The default value for Data Source Limit (``1000``)
      -
   *  -  **queryLimitValue** |br|
         integer
      -
      -  Query Limit - the number of data sources allowed to be used in a single report.
      -
   *  -  **queryLimitDefaultValue** |br|
         integer
      -
      -  The default value for Query Limit (``100000``)
      -
   *  -  **pivotColumnLimitValue** |br|
         integer
      -
      -  Pivot Column Limit - the number of data sources allowed to be used in a single report.
      -
   *  -  **pivotColumnDefaultValue** |br|
         integer
      -
      -  The default value for Pivot Column Limit (``100000``)
      -
   *  -  **fieldLimitValue** |br|
         integer
      -
      -  Field Limit - the number of data sources allowed to be used in a single report.
      -
   *  -  **fieldLimitDefaultValue** |br|
         integer
      -
      -  The default value for Field Limit (``1000``)
      -
   *  -  **filterLimitValue** |br|
         integer
      -
      -  Filter Limit - the number of data sources allowed to be used in a single report.
      -
   *  -  **filterLimitDefaultValue** |br|
         integer
      -
      -  The default value for Filter Limit (``1000``)
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant |br|
         null if the setting belongs to system
      -
   *  -  **modified** |br|
         datetime
      -  Y
      -  The modification datetime
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "queryTimeoutValue" : 3600,
        "queryTimeoutDefaultValue" : 3600,
        "useNoLockValue" : true,
        "useNoLockDefaultValue" : true,
        "dataSourceLimitValue" : 1000,
        "dataSourceLimitDefaultValue" : 1000,
        "tenantId" : null
      }
