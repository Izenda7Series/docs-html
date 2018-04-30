================================
IzendaSystemSetting table
================================

Some configurable system settings are stored in IzendaSystemSetting table. These settings can also be changed directly inside this table without going through the UI.


.. list-table::
   :widths: 20 65 15
   :header-rows: 1

   * - Name
     - Description
     - Default Value
   * - **WebAPIUrl**
     - The url for Izenda Back-end
     - Blank - use setting from web server
   * - **FiscalYear**
     - The start of fiscal year, in mm/dd format
     - 10/01
   * - **LicenseExpiredWarningTrial**
     - The number of days before trial license expires to notify user
     - 4
   * - **DeploymentMode**
     - .. container:: 

          Integration modes |br| |br|

       * 0 = AllStandAlone
       * 1 = BEStandAloneFEIntegrated
       * 2 = BEIntegratedFEStandAlone
       * 3 = AllIntegrated
     - 0
   * - **AuthenticationBaseAddress**
     - Deprecated 1.25.0 release
     - Blank
   * - **AuthValidateAccessTokenUrl**
     - Access token validation path (prefixed by AuthenticationBaseAddress)
     - api/validateAccessToken
   * - **AuthGetAccessTokenUrl**
     - Access token retrieval path (prefixed by AuthenticationBaseAddress)
     - api/getAccessToken
   * - **LicenseExpiredWarningPeriod**
     - The number of days before trial license expires to notify user
     - 14
   * - **CommonFilterSetting**
     - .. container:: 

          How to decide if two fields are the "same" to become common filters |br| |br|

       * 0 = QuerySourceFieldId - same id value
       * 1 = QuerySourceFieldName - same name
       * 2 = QuerySourceFieldAlias - same alias
     - 0
   * - **TracingType**
     - .. container:: 

          Which information to log, using bitmask check: |br| |br|

       * 000 = None
       * xx1 = LogRequestInfo
       * x1x = LogProcessTime
       * 1xx = LogPerformanceInfo
     - .. container:: 

          3 (011): |br| |br|

       * LogRequestInfo
       * LogProcessTime
   * - **LicenseWebAPIUrl**
     - The license checker url
     - Site-specific
   * - **ExportConversionDelay**
     - Delay time in seconds to wait for asynchronous items to be completely loaded or for a web page redirect to finish before exporting
     - 5
   * - **WebUrl**
     - The Front-end url, used for Exporting
     - Site-specific
   * - **SubscriptionJobInterval**
     - Check subscriptions every x minutes
     - 1
   * - **ApiSecretToken**
     - The secret token to communicate with hosting API, in Integrated Front-end modes
     - Site-specific
   * - **ExportFileLocation**
     - The location for exported files
     - C:\
   * - **AllowDuplicateUser**
     - Allow duplicated user names in multi-tenant mode or not
     - 1
   * - **PageSize**
     - The default print page size
     - A4
   * - **SystemMode**
     - .. container:: 

          Tenant mode |br| |br|

       * 0 = Multi-tenant
       * 1 = Single-tenant
     - 0
   * - **LostConnectionAllowPeriod**
     - License checker maximum lost connection period, in minutes
     - 96
   * - **CustomFunctionFilePath**
     - Path to user custom functions json file
     - Blank
   * - **RefreshTokenPeriod**
     - Refresh token every x minutes
     - 60
   * - **ReportAdvancedMode**
     - .. container:: 

          Report mode |br| |br|

       * 0 = Simple
       * 1 = Advanced
     - 1
   * - **EvoLicenseKey**
     - License key for third-party EvoPDF
     - Site-specific
   * - **HasCreatePermission** |br| **OnReportingDatabase**
     - .. container:: 

          Do accounts in connection strings have permission to create tables? |br| |br|

       * If yes, Izenda will create temp tables as physical ones.
       * If not, it will use memory tables.
     - 1
   * - **Margin**
     - Place-holder
     -
   * - **ExportNavigationTimeout**
     - Navigation timeout for third-party EvoPDF, in seconds
     - 300
   * - **LayoutSize**
     - The number of report tiles per screen width, used for calculating export size
     - 12
   * - **AuthRSAPublicKey**
     - The Public key from the RSA key pair used for encrypting export requests on Integrated Front-end modes
     - Site-specific
   * - **Token Timeout**
     - The number of minutes before inactive user's token expires in standalone versions
     - 20
   * - **StoredProcParamDelimiter**
     - The delimiter which will be used to separate values for stored procedure input parameters which accept multiple values
     - ,
   * - **CommandTimeout**
     - Timeout used for all queries to the Izenda Configuration Database, in seconds
     - 500
   * - **HelpSystemUrl**
     - The URL link which is used when users click the Help Sysetm "?" icon on the Izenda header bar
     - http://www.izenda.com
   * - **InsertBatchSize**
     - Limits large insert statements to smaller batches for the Izenda database  
     - 10000
   * - **ProvisionStaticDataStatus**
     - .. container:: 

          Status of provisioning map data |br| |br|

       * 0 = NotStarted
       * 1 = Provisioning
       * 2 = ProvisionSuccess
       * 3 = ProvisionError
     - Should be 2
   * - **ImportFileSystemPath**
     - .. container:: 

          The directory to store uploaded file when importing report/dashboard definitions. |br|
          Izenda supports 3 types of directory: |br|

       * Absolute path.
       * Relative path.
       * UNC path.

     - IzendaImport
