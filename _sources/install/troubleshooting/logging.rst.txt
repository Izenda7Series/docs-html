=================================
Logging
=================================
|

Log files are not being created
--------------------------------------
This issue is due to the API site/instance not having enough permissions to create the logs folder and the actual log files. Please ensure that you have given 'WRITE' permissions to the API. When the API has sufficient permissions, it will create the logs folder, you do not have to do this manually.


Common Error Log Messages
--------------------------------------
The following error log messages may have multiple causes, so the solution to each error is not exhaustive. These are the most common causes/solutions we have encountered.

.. list-table::
    :widths: 50 50
    :header-rows: 1

    * - Error Log Message
      - Common Cause/Solution
    * - The access token is not valid |br|

        .. container:: toggle
        
            .. container:: header

                Sample Log (timeout):

            .. code-block:: text

                2018-03-16 13:12:26,317 [30   ][ERROR][IzendaBootstraper                   ] The access token is not valid 
                Izenda.BI.Framework.Exceptions.UnAuthorizeException: The access token is not valid
                at Izenda.BI.Logic.Users.StandAloneAuthenticationLogic.(String , Nullable`1 )
                at Izenda.BI.Logic.Users.StandAloneAuthenticationLogic.ValidateAccessToken(String accessToken, Nullable`1 selectedTenantId)
                at Izenda.BI.Logic.Users.UserLogic.ValidateAccessToken(String accessToken, Nullable`1 selectedTenantId)
                at Izenda.BI.API.IzendaModule.GetCurrentUserAccessTokenInfo(String currentAccessToken, String currentAccessTenant)
                at Izenda.BI.API.IzendaModule.SetupContext(Boolean runAsAdministrator, String accessToken, String currentTenant)
                at Izenda.BI.API.IzendaModule.ExecuteInMornitoringContext(Boolean wrapingExceptionIntoOperationResult, Object paramtersToLog, Func`1 function, Boolean runAsAdministrator, String userAction, String accessToken, String currentTenant)
                at Izenda.BI.API.ReportDesigner.ReportModule.<.ctor>b__2_126(Object parameters)
                at Nancy.Routing.Route.<>c__DisplayClass4.<Wrap>b__3(Object parameters, CancellationToken context)

        .. container:: toggle
        
            .. container:: header

                Sample Log (wrong credentials):

            .. code-block:: text

                2018-03-16 13:20:20,414 [12   ][ERROR][IzendaBootstraper                   ] Izenda exception:  
                Izenda.BI.Framework.Exceptions.IzendaModelException
                at Izenda.BI.Logic.Users.AllStandAloneAuthenticationLogic.(Credential , Func`3 )
                at Izenda.BI.Logic.Users.AllStandAloneAuthenticationLogic.Login(Credential userCredential, Func`3 func)
                at Izenda.BI.Logic.Users.UserLogic.Login(Credential userCredential)
                at Izenda.BI.API.Connection.UserModule.<>c__DisplayClass0_4.<.ctor>b__9()
                at Izenda.BI.API.IzendaModule.ExecuteInMornitoringContext(Boolean wrapingExceptionIntoOperationResult, Object paramtersToLog, Func`1 function, Boolean runAsAdministrator, String userAction, String accessToken, String currentTenant)

      - * Session timeout due to inactivity |br|
        * Incorrect username or password

    * - Invalid column name:
    
        * 'CreatedById'
        * 'CustomDefinition'
        * 'IsRunningField'

        .. container:: toggle
        
            .. container:: header

                Sample Logs:

            .. code-block:: text

                System.Data.SqlClient.SqlException (0x80131904): Invalid column name 'CreatedById'.
                System.Data.SqlClient.SqlException (0x80131904): Invalid column name 'CustomDefinition'.
                System.Data.SqlClient.SqlException (0x80131904): Invalid column name 'IsRunningField'.

      - Missing upgrade scripts for config database, please find Schema Migration Assistant `here <https://tools.izenda.com/>`_ 

        * If invalid column 'CreatedById', apply upgrade script v2.0.1 - 2.1.2
        * If invalid column 'CustomDefinition' and 'IsRunningField', apply upgrade script v2.4.0 - 2.5.0

    * - Subscription failure

        .. container:: toggle
        
            .. container:: header

                Sample Log:

            .. code-block:: text

                 2018-03-07 16:51:32,081 [DefaultQuartzScheduler_Worker-2][INFO ][SubscriptionJob                     ] Start scheduling 0 subscription jobs 
                 2018-03-07 16:51:32,097 [30   ][INFO ][PingJob                             ] Ping system status failure: The remote server returned an error: (404) Not Found.

      - "WebAPIUrl" value in the "IzendaSystemSetting" table not set or incorrect. |br|
        Documentation to set this value can be found `here <https://www.izenda.com/docs/install/troubleshooting/scheduling.html#scheduled-items-are-not-being-sent-on-time>`_.

    * - Cannot load fields of remote table

        .. container:: toggle
        
            .. container:: header

                Sample Log:

            .. code-block:: text

                2018-01-11 09:10:28,701 [23  ][ERROR][DataModelLogic                      ] Cannot load fields of remote table
                System.Data.SqlClient.SqlException (0x80131904): The operation could not be performed because OLE DB provider "SQLNCLI10" for linked server "Demo" was unable to begin a distributed transaction.
                at System.Data.SqlClient.SqlConnection.OnError(SqlException exception, Boolean breakConnection, Action`1 wrapCloseInAction)
                at System.Data.SqlClient.TdsParser.ThrowExceptionAndWarning(TdsParserStateObject stateObj, Boolean callerHasConnectionLock, Boolean asyncClose)
                at System.Data.SqlClient.TdsParser.TryRun(RunBehavior runBehavior, SqlCommand cmdHandler, SqlDataReader dataStream, BulkCopySimpleResultSet bulkCopyHandler, TdsParserStateObject stateObj, Boolean& dataReady)
                at System.Data.SqlClient.SqlDataReader.TryConsumeMetaData()
                at System.Data.SqlClient.SqlDataReader.get_MetaData()
                at System.Data.SqlClient.SqlCommand.FinishExecuteReader(SqlDataReader ds, RunBehavior runBehavior, String resetOptionsString, Boolean isInternal, Boolean forDescribeParameterEncryption)
                at System.Data.SqlClient.SqlCommand.RunExecuteReaderTds(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, Boolean async, Int32 timeout, Task& task, Boolean asyncWrite, Boolean inRetry, SqlDataReader ds, Boolean describeParameterEncryptionRequest)
                at System.Data.SqlClient.SqlCommand.RunExecuteReader(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, String method, TaskCompletionSource`1 completion, Int32 timeout, Task& task, Boolean& usedCache, Boolean asyncWrite, Boolean inRetry)
                at System.Data.SqlClient.SqlCommand.RunExecuteReader(CommandBehavior cmdBehavior, RunBehavior runBehavior, Boolean returnStream, String method)
                at System.Data.SqlClient.SqlCommand.ExecuteReader(CommandBehavior behavior, String method)
                at System.Data.SqlClient.SqlCommand.ExecuteReader()
                at Izenda.BI.DataAdaptor.RDBMS.SQL.SQLSchemaLoader.

      - Defect `#17033 <https://www.izenda.com/docs/release_notes.html?highlight=17033#v2-1-5-june-22-2017>`_ in our release notes page.

        Resolved by new setting added as of version 2.1.5. In the "IzendaSystemSetting" table of the config DB, set the "RollbackSPWhenLoadSchema" value to 0 to avoid distributed transaction errors when system attempts to fetch stored procedure schema data (if using Linked Server and cannot setup DTC).

    * - Export failure

        .. container:: toggle
        
            .. container:: header

                Sample Log (value not set):

            .. code-block:: text

                2018-03-20 10:22:30,868 [12   ][ERROR][ExportingLogic                      ] Failed to convert to image: ReportId=8f74023a-4cbd-4f35-92ba-e3c04fa041d9, ReportPartId=29a15ab9-221a-430f-977f-6cf4e125726e 
                System.ArgumentNullException: Base web url cannot be null or empty
                Parameter name: baseUrl
                at Izenda.BI.Framework.Contracts.DefaultWebUrlResolver.ResolveUrl(String baseUrl, WebUrlActionLink action, Nullable`1 id, Dictionary`2 parameters)
                at Izenda.BI.Exporting.ExportHelper.ConvertToImage(ExportSetting setting, ExportData data, Int32 width, Int32 height, Object separatorValue)
                ...
                2018-03-20 10:22:30,967 [12   ][ERROR][IzendaBootstraper                   ] Izenda exception:  
                Izenda.BI.Framework.Exceptions.IzendaModelException ---> System.ArgumentNullException: Base web url cannot be null or empty
                Parameter name: baseUrl
                at Izenda.BI.Framework.Contracts.DefaultWebUrlResolver.ResolveUrl(String baseUrl, WebUrlActionLink action, Nullable`1 id, Dictionary`2 parameters)
                at Izenda.BI.Exporting.Html.Builder.HtmlBuilder.Build(ExportContext context)
                at Izenda.BI.Exporting.Pdf.PdfExportProvider.Export(ExportContext context)
                at Izenda.BI.Logic.Exporting.ExportingLogic.Export(ExportRequest request, ExportType type)
                --- End of inner exception stack trace ---
                at Izenda.BI.Logic.Exporting.ExportingLogic.Export(ExportRequest request, ExportType type)
                at Izenda.BI.API.Export.ExportModule.<>c__DisplayClass0_0.<.ctor>b__1()
                at Izenda.BI.API.IzendaModule.ExecuteInMornitoringContext(Boolean wrapingExceptionIntoOperationResult, Object paramtersToLog, Func`1 function, Boolean runAsAdministrator, String userAction, String accessToken, String currentTenant)
                at Izenda.BI.API.Export.ExportModule.<>c__DisplayClass0_1.<.ctor>b__0(Object parameters)
                at Nancy.Routing.Route.<>c__DisplayClass4.<Wrap>b__3(Object parameters, CancellationToken context)

        .. container:: toggle
        
            .. container:: header

                Sample Log (incorrect value):

            .. code-block:: text

                2018-03-20 10:44:55,228 [30   ][INFO ][ExportingLogic                      ] Attempt to convert to image by url: <URL to page with rendered report part>
                2018-03-20 10:44:55,464 [30   ][ERROR][ExportingLogic                      ] Failed to convert to image: ReportId=30db0d8b-1b4b-4b43-8366-ccb04b72fcaa, ReportPartId=29a15ab9-221a-430f-977f-6cf4e125726e 
                System.Exception: HTML load error. The remote content was not found at the server - HTTP error 404
                at EvoPdf.HtmlToImageConverter.?(String A_0, Boolean A_1, ?& A_2, Boolean A_3, Boolean A_4, Boolean A_5)
                at EvoPdf.HtmlToImageConverter.ConvertUrlToImageObject(String url)
                at EvoPdf.HtmlToImageConverter.ConvertUrl(String url, ImageFormat format)
                at Izenda.BI.Exporting.ExportHelper.ConvertToImage(ExportSetting setting, ExportData data, Int32 width, Int32 height, Object separatorValue)

      - "WebUrl" value in the "IzendaSystemSetting" table not set or incorrect. |br|
        Documentation to set this value can be found `here <https://www.izenda.com/docs/install/troubleshooting/exporting.html#charts-and-other-visualizations-are-not-rendered-in-exports>`_.

    * - Send email failed, [object Object]

        .. container:: toggle
        
            .. container:: header

                Sample Log:

            .. code-block:: text

                2018-04-02 14:57:42,679 [55   ][ERROR][IzendaBootstraper                   ] You don't have permission to perform this action 
                Izenda.BI.Framework.Exceptions.IzendaException: You don't have permission to perform this action
                at Izenda.BI.Logic.Authorization.Validators.TenantAccessAuthorizeHandler.Execute(TenantAccessHandlerContext context)
                at Izenda.BI.Logic.Authorization.AuthorizationService.Authorize[TContext,THanlder](TContext context)
                at Izenda.BI.Logic.Exporting.ExportingLogic.
                (ExportRequest , ExportType )
                at Izenda.BI.Logic.Exporting.ExportingLogic.Export(ExportRequest request, ExportType type)
                at Izenda.BI.Logic.Exporting.ExportingLogic.ExportSubscription(Subscription subscription)
                at Izenda.BI.API.Export.ExportModule.<>c__DisplayClass0_3.<.ctor>b__4()
                at Izenda.BI.API.IzendaModule.ExecuteInMornitoringContext(Boolean wrapingExceptionIntoOperationResult, Object paramtersToLog, Func`1 function, Boolean runAsAdministrator, String userAction, String accessToken, String currentTenant)

      - Emailing global report as embedded HTML or Attachment at the tenant-level, Defect `#19293 <https://www.izenda.com/docs/release_notes.html?highlight=17033#v2-6-21-march-12-2018>`_ in our release notes page.

        Resolved as of version 2.6.21, please `upgrade <https://www.izenda.com/docs/install/doc_upgrade_guide.html>`_ to that version or greater.

    * - Cannot get LicenseSetting

        .. container:: toggle
        
            .. container:: header

                Sample Log:

            .. code-block:: text

                2017-11-27 16:03:40,319 [10   ][ERROR][DatabaseSettingLogic                ] Cannot get LicenseSetting 
                System.InvalidOperationException: OracleConnection.ConnectionString is invalid
                at Oracle.ManagedDataAccess.Client.OracleConnection.Open()
                at Izenda.BI.Oracle.OracleConnection.OpenConnection(String connectionString)
                at Izenda.BI.SystemRepository.RDBMS.RDBMSSystemRepository.Query[T](String sql, Object param, IDbTransaction transaction, Boolean buffered, Nullable`1 commandTimeout)
                at Izenda.BI.SystemRepository.RDBMS.Oracle.OracleSystemRepository.Query[T](String sql, Object param, IDbTransaction transaction, Boolean buffered, Nullable`1 commandTimeout)
                at Izenda.BI.SystemRepository.RDBMS.RDBMSSystemRepository.GetLicenseSetting()
                at Izenda.BI.Logic.DatabaseSetup.DatabaseSettingLogic.VerifyConnection(Guid serverType, String connectionString)

      - Issue with Oracle schema in Izenda.

        Resolved as of version 2.6.7, please `upgrade <https://www.izenda.com/docs/install/doc_upgrade_guide.html>`_ to that version or greater.

    * - Html conversion failed

        .. container:: toggle
        
            .. container:: header

                Sample Log:

            .. code-block:: text

                2019-04-17 03:00:50,561 [17   ][ERROR][IzendaBootstraper                   ] Izenda exception:  
                Izenda.BI.Framework.Exceptions.IzendaModelException ---> Syncfusion.Pdf.PdfException: Html conversion failed
                at Syncfusion.HtmlConverter.HtmlConverter.CheckConversionDone(String tempFilePath)
                at Syncfusion.HtmlConverter.HtmlConverter.ConvertHtmlToPdf(String url, Int32 width, Int32 height)
                at Syncfusion.HtmlConverter.HtmlToPdfConverter.Convert(String url)
                at Syncfusion.HtmlConverter.HtmlToPdfConverter.Convert(String html, String baseurl)
                at Izenda.BI.Exporting.HtmlConverterTool.ConvertHtmlToPdf(ExportSetting setting, HtmlDocument htmlDocument)
                at Izenda.BI.Exporting.Pdf.PdfExportProvider.Export(ExportContext context)
                at Izenda.BI.Logic.Exporting.ExportingLogic.Export(ExportRequest request, ExportType type, Boolean enableWriteStat)

      - Missing assemblies on the server where API is hosted.

        Download and install the Microsoft Visual C++ 2010 Redistributable Package on the server. For this, please refer to the steps `here <https://www.izenda.com/docs/install/troubleshooting/exporting.html#exporting-to-pdf-not-working-on-server-hosting-izenda-api-v3-0>`_.
