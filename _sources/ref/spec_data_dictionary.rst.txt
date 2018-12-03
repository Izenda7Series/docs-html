================================
Data Dictionary
================================

.. note::

   The following data types are documented for a Microsoft SQL Server database.

.. list-table::
   :widths: 30 30 5 15 20
   :header-rows: 1

   * - Table / Field Name
     - Data Type
     - Length
     - Constraints
     - Note
   * - **IzendaAccessRight** |br|
       Pre-defined sharing rights on each report or dashboard
     - 
     - 
     - 
     - 
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - 
     - 
       * 0 = Report/Template
       * 1 = Dashboard
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaAdvancedSetting** |br|
       Advanced system settings
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - 2048
     - 
     - 
   * - .. container:: lpad2

          **DefaultValue**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Type**
     - nvarchar
     - 50
     - 
     - Performance, Security or Others
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaCity** |br|
       Data of cities used for Map report part
     -
     -
     -
     -
   * - .. container:: lpad2

          **GeonameId**
     - varchar
     - 10
     - not null
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **AsciiName**
     - nvarchar
     - 255
     - 
     - The name in Latin alphabets
   * - .. container:: lpad2

          **AlternateNames**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Latitude**
     - varchar
     - 15
     - 
     - 
   * - .. container:: lpad2

          **Longitude**
     - varchar
     - 15
     - 
     - 
   * - .. container:: lpad2

          **FeatureClasss**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **FeatureCode**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **CountryCode**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Cc2**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Admin1Code**
     - varchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **Admin2Code**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Admin3Code**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Admin4Code**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Population**
     - varchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **Elevation**
     - varchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **Dem**
     - varchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **Timezone**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **ModificationDate**
     - datetime
     - 
     - 
     - 
   * - **IzendaCommonFilterField** |br|
       Filter fields that are common among different report parts in the same dashboard
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - varchar
     - 1000
     - 
     - Auto-generated name, e.g. ce0fda8a-4515-409c-9d00-0bf56c2b4c4d-OrderDate
   * - .. container:: lpad2

          **DisplayName**
     - varchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Value**
     - varchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - FK to IzendaFilterOperator
     - 
   * - .. container:: lpad2

          **OperatorSetting**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **DataType**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **DashboardId**
     - uniqueidentifier
     - 
     - FK to IzendaDashboard
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **FilterFieldContent**
     - varchar
     - max
     - 
     - data in json format
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaConnection** |br|
       Connection strings to source databases
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - Database name
   * - .. container:: lpad2

          **ServerTypeId**
     - uniqueidentifier
     - 
     - not null
     - 
   * - .. container:: lpad2

          **ConnectionString**
     - nvarchar
     - 500
     - 
     - Encrypted connection string
   * - .. container:: lpad2

          **Visible**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **RelateToConnectionId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Color**
     - nvarchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaDashboard** |br|
       Dashboards
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **CategoryId**
     - uniqueidentifier
     - 
     - FK to IzendaReportCategory
     - 
   * - .. container:: lpad2

          **SubCategoryId**
     - uniqueidentifier
     - 
     - FK to IzendaReportCategory
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **ImageUrl**
     - nvarchar
     - 2048
     - 
     - 
   * - .. container:: lpad2

          **StretchImage**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **BackgroundColor**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **ShowFilterDescription**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **Owner**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **LastViewed**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfView**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **RenderingTime**
     - float
     - 
     - 
     - Unit: second
   * - .. container:: lpad2

          **OwnerId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **CreatedById**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **ModifiedById**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **SourceId**
     - uniqueidentifier
     - 
     - 
     - 
   * - **IzendaDashboardPart** |br|
       Dashboard parts
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **DashboardId**
     - uniqueidentifier
     - 
     - FK to IzendaDashboard
     - 
   * - .. container:: lpad2

          **Type**
     - nvarchar
     - 50
     - 
     - Either reportPart or text
   * - .. container:: lpad2

          **Title**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport
     - 
   * - .. container:: lpad2

          **ReportPartId**
     - uniqueidentifier
     - 
     - FK to IzendaReportPart
     - 
   * - .. container:: lpad2

          **NumberOfRecord**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **FilterDescription**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **Content**
     - nvarchar
     - max
     - 
     - Data in json format
   * - .. container:: lpad2

          **PositionX**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **PositionY**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Width**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Height**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **SourceId**
     - uniqueidentifier
     - 
     - 
     - 
   * - **IzendaDashboardPartFilterField** |br|
       Filter fields in a dashboard part
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **FilterFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaFilterField
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - FK to IzendaFilterOperator
     - 
   * - .. container:: lpad2

          **OperatorSetting**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **DashboardPartId**
     - uniqueidentifier
     - 
     - FK to IzendaDashboardPart
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaDataFormat** |br|
       Data formats, e.g. 'mm/dd/yyyy'
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Format**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - 256
     - 
     - Sample values 
   * - .. container:: lpad2

          **Category**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **SubCategory**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **DataType**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **AllowFilter**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **AllowFieldProperty**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **GroupBy**
     - nvarchar
     - 50
     - 
     - Values to be grouped by
   * - .. container:: lpad2

          **FormatDataType**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaDataSourceCategory** |br|
       Categories for source tables, views and stored procedures
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaDataTypeFunctionMapping** |br|
       Mappings between data types and supported functions
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **DataType**
     - nvarchar
     - 50
     - not null
     - 
   * - .. container:: lpad2

          **FunctionId**
     - uniqueidentifier
     - 
     - FK to IzendaFunction |br|
       not null
     - 
   * - .. container:: lpad2

          **FormatDataType**
     - nvarchar
     - 50
     - 
     - Data type of the result
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaDBVersion** |br|
       Current version of Izenda database schema
     -
     -
     -
     -
   * - .. container:: lpad2

          **Version**
     - nvarchar
     - 16
     - not null
     - Current version of Izenda database schema
   * - **IzendaEmailSetting** |br|
       	[Expand] Email sending options
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **DisplayName**
     - nvarchar
     - 256
     - 
     - Value of the name in From field, e.g. John Doe in "From: John Doe <jdoe@acme.com>"
   * - .. container:: lpad2

          **EmailFromAddress**
     - nvarchar
     - 256
     - 
     - Value of the email in From field, e.g. jdoe@acme.com in "From: John Doe <jdoe@acme.com>"
   * - .. container:: lpad2

          **UseSystemConfiguration**
     - bit
     - 
     - 
     - Re-use setting from system level or not
   * - .. container:: lpad2

          **Server**
     - nvarchar
     - 256
     - 
     - E.g. smtp.gmail.com
   * - .. container:: lpad2

          **Port**
     - int
     - 
     - 
     - E.g. 587
   * - .. container:: lpad2

          **SecureConnection**
     - bit
     - 
     - 
     - Use SSL/TLS or not
   * - .. container:: lpad2

          **Login**
     - nvarchar
     - 256
     - 
     - User name for the email server
   * - .. container:: lpad2

          **Password**
     - nvarchar
     - 500
     - 
     - Encrypted password
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaExportMarginDefaultValue** |br|
       Default values for the margin in Export function
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - not null
     -
       * 0 = Normal
       * 1 = Narrow
       * 2 = Wide
       * 3 = Custom
       * 4 = MinCustom
       * 5 = MaxCustom
   * - .. container:: lpad2

          **TopValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **BottomValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **LeftValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **RightValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **HeaderValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **FooterValue**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaFilterField** |br|
       Filter fields in a report part
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **FilterId**
     - uniqueidentifier
     - 
     - FK to IzendaFilter
     - 
   * - .. container:: lpad2

          **QuerySourceFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySourceField
     - 
   * - .. container:: lpad2

          **QuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource
     - 
   * - .. container:: lpad2

          **QuerySourceType**
     - nvarchar
     - 50
     - 
     - Table, Aggregated Field, Calculated Fields or Stored Procedure
   * - .. container:: lpad2

          **RelationshipId**
     - uniqueidentifier
     - 
     - FK to IzendaRelationship
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Alias**
     - nvarchar
     - 256
     - 
     - Display alias, e.g. Sum(Freight), Freight*1.1
   * - .. container:: lpad2

          **ReportFieldAlias**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **ReportPartTitle**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Visible**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Required**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Cascading**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - FK to IzendaOperator
     - 
   * - .. container:: lpad2

          **OperatorSetting**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - max
     - 
     - Values for the operator, separated by semi-colon
   * - .. container:: lpad2

          **DataFormatId**
     - uniqueidentifier
     - 
     - FK to IzendaDataFormat
     - 
   * - .. container:: lpad2

          **FontFamily**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **FontSize**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **TextColor**
     - nvarchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **BackgroundColor**
     - nvarchar
     - 10
     - 
     - 
   * - .. container:: lpad2

          **FontBold**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **FontItalic**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **FontUnderline**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **SortType**
     - nvarchar
     - 10
     - 
     - ASC, DESC or Unsorted
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaFilterOperator** |br|
       Operators used in filters
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Label**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **OperatorGroupId**
     - uniqueidentifier
     - 
     - FK to IzendaOperatorGroup
     - 
   * - .. container:: lpad2

          **AllowParameter**
     - bit
     - 
     - 
     - Needs additional parameter value (in IzendaFilterField.Value) or not
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaFilterOperatorGroup** |br|
       Groups of filter operators
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaFilterOperatorRule** |br|
       Rules for filter operators
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - FK to IzendaOperator
     - 
   * - .. container:: lpad2

          **AllowNull**
     - bit
     - 
     - 
     - Accepts null values or not
   * - .. container:: lpad2

          **IsPairedValues**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaFunction** |br|
       Built-in functions
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - varchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Expression**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **SubTotal**
     - bit
     - 
     - 
     - Is usable in Sub Total or not
   * - .. container:: lpad2

          **GrandTotal**
     - bit
     - 
     - 
     - Is usable in Grand Total or not
   * - .. container:: lpad2

          **FieldProperty**
     - bit
     - 
     - 
     - Is usable on a data source field or not
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaLanguage** |br|
       Supported languages and cultures
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Language**
     - nvarchar
     - 150
     - 
     - 
   * - .. container:: lpad2

          **CultureName**
     - nvarchar
     - 20
     - 
     - E.g. en-US
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 150
     - 
     - 
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 150
     - 
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - **IzendaLicenseSetting** |br|
       License data
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Online**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **LicenseKey**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **Token**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **LastRefresh**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaPasswordHistory** |br|
       Password hash history to prevent reuse
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **UserId**
     - uniqueidentifier
     - 
     - FK to IzendaUser
     - 
   * - .. container:: lpad2

          **PasswordHash**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **PasswordSalt**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaPerformanceStatsTrend** |br|
       Collected performance statistics
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **NumberOfCore**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfServer**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfReport**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfReportCreator**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfDashboard**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfDashboardCreator**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfReportView**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfDashboardView**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfActiveTenant**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfInactiveTenant**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfActiveUser**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfInactiveUser**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **DeploymentMode** 

          .. versionadded:: 2.15.0
     - int
     - 
     - 
     -
       * 0 = All Standalone
       * 1 = BE Standalone - FE Integrated
       * 2 = BE Integrated - FE Standalone
       * 3 = All Integrated
   * - .. container:: lpad2

          **NumberOfCreateReportUser**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfCreateDashboardUser**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **IzendaVersion**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **IzendaConfigurationDatabase**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **DatabaseTypesInUse**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **ClientLicenseKey**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaPostalCode** |br|
       Postal code data used for Map
     -
     -
     -
     -
   * - .. container:: lpad2

          **PostalCode**
     - varchar
     - 10
     - not null
     - 
   * - .. container:: lpad2

          **PlaceName**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Province**
     - nvarchar
     - 255
     - 
     - 
   * - .. container:: lpad2

          **Latitude**
     - varchar
     - 15
     - 
     - 
   * - .. container:: lpad2

          **Longitude**
     - varchar
     - 15
     - 
     - 
   * - **IzendaQuerySource** |br|
       Data sources
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Type**
     - nvarchar
     - 50
     - 
     - Table, View or Stored Procedure
   * - .. container:: lpad2

          **Selected**
     - bit
     - 
     - 
     - Is selected to be visible or not
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **ParentQuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource
     - 
   * - .. container:: lpad2

          **CategoryId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **DataSourceCategoryId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **Alias**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **ExtendedProperties**
     - nvarchar
     - 4000
     - 
     - Properties for functions and stored procedures, in json format
   * - .. container:: lpad2

          **PhysicalChange**
     - int
     - 
     - 
     - 
       * -1 = Not set
       *  0 = None
       *  1 = Added
       *  2 = Modified
       *  3 = Deleted
   * - .. container:: lpad2

          **Approval**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaQuerySourceCategory** |br|
       Database schemas
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **ParentCategoryId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **ConnectionId**
     - uniqueidentifier
     - 
     - FK to IzendaConnection |br|
       not null
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaQuerySourceField** |br|
       Database fields and calculated fields
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **DataType**
     - nvarchar
     - 50
     - 
     - Original data type
   * - .. container:: lpad2

          **IzendaDataType**
     - nvarchar
     - 50
     - 
     - Converted data type
   * - .. container:: lpad2

          **AllowDistinct**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Alias**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Visible**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Filterable**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **QuerySourceId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **ParentId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource
     - 
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - 
     - 
       * 0 = Field
       * 1 = Parameter
   * - .. container:: lpad2

          **GroupPosition**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **FilteredValue**
     - nvarchar
     - max
     - 
     - Filter values for stored procedures parameters
   * - .. container:: lpad2

          **ExtendedProperties**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **MatchedTenant**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **PhysicalChange**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Approval**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **FunctionName**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Expression**
     - nvarchar
     - 500
     - 
     - Expression for calculated fields
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport
     - 
   * - .. container:: lpad2

          **IsCalculated**
     - bit
     - 
     - 
     - Is calculated field or not
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaRelationship** |br|
       Database relationships
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **JoinQuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource |br|
       not null
     - 
   * - .. container:: lpad2

          **ForeignQuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource |br|
       not null
     - 
   * - .. container:: lpad2

          **JoinFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySourceField
     - 
   * - .. container:: lpad2

          **ForeignFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySourceField
     - 
   * - .. container:: lpad2

          **Alias**
     - nvarchar
     - 256
     - 
     - Alias of join query source
   * - .. container:: lpad2

          **SystemRelationship**
     - bit
     - 
     - 
     - Is this a physical relationship (or defined in Data Model)
   * - .. container:: lpad2

          **JoinType**
     - nvarchar
     - 50
     - 
     - Inner, Right, Left or Outer
   * - .. container:: lpad2

          **ParentRelationshipId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport
     - 
   * - .. container:: lpad2

          **ForeignAlias**
     - nvarchar
     - 256
     - 
     - Alias of foreign query source
   * - .. container:: lpad2

          **RelationshipPosition**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaRelationshipKeyJoin** |br|
       Additional fields in a multi-column relationship
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **RelationshipId**
     - uniqueidentifier
     - 
     - FK to IzendaRelationship |br|
       not null
     - 
   * - .. container:: lpad2

          **JoinQuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource |br|
       not null
     - 
   * - .. container:: lpad2

          **ForeignQuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource |br|
       not null
     - 
   * - .. container:: lpad2

          **JoinFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySourceField |br|
       not null
     - 
   * - .. container:: lpad2

          **ForeignFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySourceField |br|
       not null
     - 
   * - .. container:: lpad2

          **Operator**
     - nvarchar
     - 50
     - 
     - Join operator
   * - .. container:: lpad2

          **JoinSourceAlias**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **ForeignSourceAlias**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaReport** |br|
       Reports
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - not null
     - 
       * 0 = Report
       * 1 = Template
   * - .. container:: lpad2

          **PreviewRecord**
     - int
     - 
     - not null
     - 
   * - .. container:: lpad2

          **AdvancedMode**
     - bit
     - 
     - not null
     - 
   * - .. container:: lpad2

          **AllowNulls**
     - bit
     - 
     - not null
     - 
   * - .. container:: lpad2

          **IsDistinct**
     - bit
     - 
     - not null
     - 
   * - .. container:: lpad2

          **CategoryId**
     - uniqueidentifier
     - 
     - FK to IzendaReportCategory
     - 
   * - .. container:: lpad2

          **SubCategoryId**
     - uniqueidentifier
     - 
     - FK to IzendaReportCategory
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **HeaderContent**
     - nvarchar
     - max
     - 
     - Content of header box, in json format
   * - .. container:: lpad2

          **FooterContent**
     - nvarchar
     - max
     - 
     - Content of footer box, in json format
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **LastViewed**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **Owner**
     - nvarchar
     - 256
     - 
     - Firstname and lastname of owner for display
   * - .. container:: lpad2

          **OwnerId**
     - uniqueidentifier
     - 
     - FK to IzendaUser
     - The owner
   * - .. container:: lpad2

          **Title**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **TitleDescriptionContent**
     - nvarchar
     - max
     - 
     - Content of title box, in json format
   * - .. container:: lpad2

          **ExcludedRelationships**
     - nvarchar
     - max
     - 
     - Relationships that were manually removed
   * - .. container:: lpad2

          **NumberOfView**
     - bigint
     - 
     - 
     - 
   * - .. container:: lpad2

          **RenderingTime**
     - float
     - 
     - 
     - 
   * - .. container:: lpad2

          **CreatedById**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **ModifiedById**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **ExportFormatSettingData**
     - nvarchar
     - max
     - 
     - Remembered export settings, in json format
   * - .. container:: lpad2

          **SnapToGrid**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **UsingFields**
     - nvarchar
     - max
     - 
     - List of ids of query source fields used by this report, comma-separated
   * - .. container:: lpad2

          **SourceId**
     - uniqueidentifier
     - 
     - 
     - 
   * - **IzendaReportCategory** |br|
       Categories for report/dashboard
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - not null
     - 
       * 0 = Report
       * 1 = Template
       * 2 = Dashboard
   * - .. container:: lpad2

          **ParentId**
     - uniqueidentifier
     - 
     - FK to IzendaReportCategory
     - Id of the parent category, for sub-categories
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaReportDataSource** |br|
       Data sources used in reports
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **QuerySourceId**
     - uniqueidentifier
     - 
     - FK to IzendaQuerySource |br|
       not null
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport |br|
       not null
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaReportFilter** |br|
       Data of filters in report
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Logic**
     - nvarchar
     - 2000
     - 
     - The logic, e.g. 1 AND 2 OR 3
   * - .. container:: lpad2

          **Visible**
     - bit
     - 
     - 
     - Shown under report description or not
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaReportHistory** |br|
       Report history
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport |br|
       not null
     - 
   * - .. container:: lpad2

          **ReportName**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - max
     - not null
     - 
   * - .. container:: lpad2

          **Definition**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaReportPart** |br|
       Report parts
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Title**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **PositionX**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **PositionY**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Width**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Height**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Content**
     - nvarchar
     - max
     - 
     - The :doc:`models/ReportPartContent` in json format
   * - .. container:: lpad2

          **NumberOfRecord**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport |br|
       not null
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **SourceId**
     - uniqueidentifier
     - 
     - 
     - 
   * - **IzendaReportSetting** |br|
       Report Settings
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **EnforceVersionHistory**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumOfArchivedVersionToKeep**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **RemoveArchivedVersions**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **RecurrentReportSettingData**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **IsScheduled**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaRole** |br|
       Roles
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **PermissionData**
     - nvarchar
     - max
     - 
     - Permissions in json format
   * - .. container:: lpad2

          **QuerySources**
     - nvarchar
     - max
     - 
     - Array of tenant query sources, in json format
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Active**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSecurityPolicy** |br|
       Security policies
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **MinNumberOfPasswordLenght**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfPasswordLenght**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MinNumberOfSpecialCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfSpecialCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MinNumberOfUppercaseCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfUppercaseCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MinNumberOfLowercaseCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfLowercaseCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MinNumberOfNumericCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfNumericCharacter**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfRepeatSequential**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MinNumberOfPasswordAge**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **MaxNumberOfPasswordAge**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NotifyUseDuring**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfPasswordToKeep**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **PasswordLinkValidity**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfQuestionProfile**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfQuestionResetPassword**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfFailedLogonAllowed**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfFailedAnswerAllowed**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **LockoutPeriod**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSecurityQuestion** |br|
       Security questions
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Question**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **OrderNumber**
     - int
     - 
     - 
     - 
   * - **IzendaServer** |br|
       The web server information used in performance statistics
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **ServerName**
     - nvarchar
     - 1000
     - 
     - 
   * - .. container:: lpad2

          **ServerCore**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSubsCommonFilterField** |br|
       Common filter fields used in subscriptions
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **CommonFilterFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaCommonFilterField
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - max
     - 
     - Selected values for this filter
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - FK to IzendaOperator
     - 
   * - .. container:: lpad2

          **OperatorSetting**
     - nvarchar
     - 100
     - 
     - 
   * - .. container:: lpad2

          **SubscriptionId**
     - uniqueidentifier
     - 
     - FK to IzendaSubscription
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSubscription** |br|
       Report and dashboard subscriptions and sheduled deliveries
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Schedule**
     - nvarchar
     - max
     - 
     - Description of the schedule for display
   * - .. container:: lpad2

          **FilterValueSelection**
     - nvarchar
     - max
     - 
     - Description of the filter for display
   * - .. container:: lpad2

          **Type**
     - nvarchar
     - 100
     - 
     - Subscribed Reporting Item or Subscribed Alert
   * - .. container:: lpad2

          **TimeZoneName**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **TimeZoneValue**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **StartDate**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **StartDateUtc**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **StartTime**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **RecurrenceType**
     - int
     - 
     - 
     - 
       * 0 = AlertHourly
       * 1 = AlertDaily
       * 2 = EveryDay
       * 3 = EveryWeekday
       * 4 = EveryWeek
       * 5 = EveryTwoWeeks
       * 6 = EveryMonth
       * 7 = EveryQuarter
       * 8 = CustomRecurrence
   * - .. container:: lpad2

          **RecurrencePattern**
     - int
     - 
     - 
     - 
       * 0 = Daily
       * 1 = Weekly
       * 2 = Monthly
       * 3 = Yearly
   * - .. container:: lpad2

          **RecurrencePatternValue**
     - nvarchar
     - max
     - 
     - Details of the recurrence pattern, in json format, e.g. {"recurrenceWeek":1,"selectedDayValue":"2"}
   * - .. container:: lpad2

          **IsEndless**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **IsScheduled**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Occurrence**
     - int
     - 
     - 
     - Actual number of past occurences
   * - .. container:: lpad2

          **EndDate**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **EndDateUtc**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **DeliveryType**
     - nvarchar
     - 100
     - 
     - Email or File Location
   * - .. container:: lpad2

          **DeliveryMethod**
     - nvarchar
     - 100
     - 
     - Link, Attachment, Embedded HTML or Send to disk
   * - .. container:: lpad2

          **ExportFileType**
     - nvarchar
     - 50
     - 
     - PDF, Word, Excel, or CSV
   * - .. container:: lpad2

          **ExportAttachmentType**
     - nvarchar
     - 50
     - 
     - 
   * - .. container:: lpad2

          **EmailSubject**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **EmailBody**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **DashboardId**
     - uniqueidentifier
     - 
     - FK to IzendaDashboard
     - 
   * - .. container:: lpad2

          **Recipients**
     - nvarchar
     - max
     - 
     - Comma-separated list of email addresses
   * - .. container:: lpad2

          **LastSuccessfulRun**
     - nvarchar
     - 500
     - 
     - Display value for LastSuccessfulRunDate
   * - .. container:: lpad2

          **NextScheduledRun**
     - nvarchar
     - 500
     - 
     - Display value for NextScheduledRunDate
   * - .. container:: lpad2

          **LastSuccessfulRunDate**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **NextScheduledRunDate**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **IsSubscription**
     - bit
     - 
     - 
     - Is this a subscription (or scheduled delivery)
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **CreatedById**
     - uniqueidentifier
     - 
     - 
     - Redundant, to be removed
   * - **IzendaSubscriptionFilterField** |br|
       Filter fields used in subscriptions
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **FilterFieldId**
     - uniqueidentifier
     - 
     - FK to IzendaFilterField
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - max
     - 
     - Selected values for this filter
   * - .. container:: lpad2

          **OperatorId**
     - uniqueidentifier
     - 
     - 
     - 
   * - .. container:: lpad2

          **OperatorSetting**
     - nvarchar
     - 100
     - FK to IzendaFilterOperator
     - Selected operator for this filter
   * - .. container:: lpad2

          **SubscriptionId**
     - uniqueidentifier
     - 
     - FK to IzendaSubscription
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSystemSetting** |br|
       System settings
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - varchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaSystemVariable** |br|
       System variables
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
       * Everywhere: {currentDateTime}, {currentUserName}, {tenantName}
       * Report/Dashboard: {recipientName}
       * Report: {reportName}, {reportLink}, {embedReportHTML}
       * Dashboard: {dashboardLink}, {dashboardName}, {embedDashboardHTML}
       * Export: {pageNumber}, {horizontalRule}, {verticalRule}
   * - .. container:: lpad2

          **DataType**
     - nvarchar
     - 50
     - 
     - Output data type of the system variable
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - 2000
     - 
     - 
   * - .. container:: lpad2

          **Scope**
     - int
     - 
     - 
     - 
       * 0 = Everywhere
       * 1 = Report/Dashboard
       * 2 = Report
       * 3 = Dashboard
       * 4 = Export
   * - **IzendaTemporaryData** |br|
       Data for un-saved objects
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **ObjectId**
     - uniqueidentifier
     - 
     - 
     - Id of the temporary object
   * - .. container:: lpad2

          **ObjectData**
     - nvarchar
     - max
     - 
     - Data of the object, in json format
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **UserId**
     - uniqueidentifier
     - 
     - 
     - User who owns this temporary data
   * - **IzendaTenant** |br|
       Tenant data in multi-tenant mode
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **TenantID**
     - varchar
     - 256
     - not null
     - The user-defined "Tenant Id" field
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Active**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Modules**
     - nvarchar
     - 500
     - 
     - Encrypted list of assigned modules
   * - .. container:: lpad2

          **PermissionData**
     - nvarchar
     - max
     - 
     - Data of permissions, in json format
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaTimePeriod** |br|
       Pre-defined time periods, e.g. current and next month
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Type**
     - nvarchar
     - 100
     - 
     - Classification for the period, e.g. Day, Calendar Quarter, Fiscal Quarter
   * - .. container:: lpad2

          **Value**
     - nvarchar
     - 256
     - 
     - Internal value of the period
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaUser** |br|
       Users
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **UserName**
     - nvarchar
     - 256
     - not null
     - 
   * - .. container:: lpad2

          **FirstName**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **LastName**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **PasswordHash**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **PasswordSalt**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - .. container:: lpad2

          **EmailAddress**
     - varchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **CurrentTokenHash**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Active**
     - bit
     - 
     - 
     - Inactive users cannot login
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **DataOffset**
     - numeric(10,2)
     - 
     - s
     - For versions 2.9.4 and prior, the data type was *int*
   * - .. container:: lpad2

          **TimestampOffset**
     - numeric(10,2)
     - 
     - 
     -  For versions 2.9.4 and prior, the data type was *int*
   * - .. container:: lpad2

          **InitPassword**
     - bit
     - 
     - 
     - Has password been initiated
   * - .. container:: lpad2

          **RetryLoginTime**
     - smallint
     - 
     - 
     - The number of failed login attempts
   * - .. container:: lpad2

          **LastTimeAccessed**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **PasswordLastChanged**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **Locked**
     - bit
     - 
     - 
     - Is locked out because of max failed login attempts or not
   * - .. container:: lpad2

          **LockedDate**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **CultureName**
     - nvarchar
     - 20
     - 
     - 
   * - .. container:: lpad2

          **DateFormat**
     - nvarchar
     - 20
     - 
     - 
   * - .. container:: lpad2

          **SystemAdmin**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **SecurityQuestionLastChanged**
     - datetime
     - 
     - 
     - 
   * - .. container:: lpad2

          **NumberOfFailedSecurityQuestion**
     - int
     - 
     - 
     - The aggregated number of times that user fails security questions, it will be reset when user is unlocked
   * - **IzendaUserPermission** |br|
       Sharing rights on each report or dashboard
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **ReportId**
     - uniqueidentifier
     - 
     - FK to IzendaReport
     - 
   * - .. container:: lpad2

          **DashboardId**
     - uniqueidentifier
     - 
     - FK to IzendaDashboard
     - 
   * - .. container:: lpad2

          **AssignedTo**
     - nvarchar
     - 4000
     - 
     - Array of ids of assigned roles or users depending on AssignedType, in json format
   * - .. container:: lpad2

          **AssignedType**
     - int
     - 
     - 
     - 
       * 1 = Everyone
       * 2 = Role
       * 3 = User
   * - .. container:: lpad2

          **AccessRightId**
     - uniqueidentifier
     - 
     - FK to IzendaAccessRight
     - 
   * - .. container:: lpad2

          **Position**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaUserRole** |br|
       Assignment of users and roles
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **UserId**
     - uniqueidentifier
     - 
     - FK to IzendaUser
     - 
   * - .. container:: lpad2

          **RoleId**
     - uniqueidentifier
     - 
     - FK to IzendaRole
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaUserSecurityQuestion** |br|
       Security questions for each user
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **UserId**
     - uniqueidentifier
     - 
     - FK to IzendaUser |br|
       not null
     - 
   * - .. container:: lpad2

          **SecurityQuestionId**
     - uniqueidentifier
     - 
     - FK to IzendaSecurityQuestion |br|
       not null
     - 
   * - .. container:: lpad2

          **Answer**
     - nvarchar
     - max
     - not null
     - 
   * - .. container:: lpad2

          **Version**
     - int
     - 
     - 
     - Current version of the data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **ModifiedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who last modified this data
   * - **IzendaWorkspace** |br|
       Copy management workspaces
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **Name**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **Description**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - 
     - Not used |br|
       The target ternant is in IzendaWorkspaceTenant
   * - .. container:: lpad2

          **OwnerId**
     - uniqueidentifier
     - 
     - FK to IzendaUser
     - 
   * - .. container:: lpad2

          **CreatedBy**
     - nvarchar
     - 256
     - FK to IzendaUser
     - User who created this data
   * - .. container:: lpad2

          **Deleted**
     - bit
     - 
     - 
     - Is this data deleted
   * - .. container:: lpad2

          **Created**
     - datetime
     - 
     - 
     - The created datetime
   * - .. container:: lpad2

          **Modified**
     - datetime
     - 
     - 
     - The modification datetime
   * - .. container:: lpad2

          **CopyRoles**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyReport**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyDashboard**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyRolePermission**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyAdvancedSettings**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyDataModel**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **CopyTenantPermissions**
     - bit
     - 
     - 
     - 
   * - .. container:: lpad2

          **SourceId**
     - uniqueidentifier
     - 
     - 
     - Id of the source tenant, null or empty if source is system
   * - .. container:: lpad2

          **SelectAllTenants**
     - bit
     - 
     - 
     - Copies to all tenants or not
   * - .. container:: lpad2

          **SourceDataModel**
     - nvarchar
     - max
     - 
     - Source data model in json format
   * - .. container:: lpad2

          **SourceHashCode**
     - nvarchar
     - 500
     - 
     - Hash code of all connection strings of source
   * - .. container:: lpad2

          **CopiedRolesData**
     - nvarchar
     - max
     - 
     - Array of ids of copied roles at modification time, in json format
   * - .. container:: lpad2

          **CopiedRolePermissionData**
     - nvarchar
     - max
     - 
     - Array of ids of copied permissions at modification time, in json format
   * - .. container:: lpad2

          **TotalHashCode**
     - nvarchar
     - 500
     - 
     - Array of hash codes of advancedSettings, tenantPermission, roles and rolePermissions, in json format
   * - .. container:: lpad2

          **SourceReportModel**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **SourceTemplateModel**
     - nvarchar
     - max
     - 
     - 
   * - .. container:: lpad2

          **SourceDashboardModel**
     - nvarchar
     - max
     - 
     - 
   * - **IzendaWorkspaceMapping** |br|
       Mapping from source to destination in copy management workspace
     -
     -
     -
     -
   * - .. container:: lpad2

          **Id**
     - uniqueidentifier
     - 
     - PK
     - 
   * - .. container:: lpad2

          **WorkspaceId**
     - uniqueidentifier
     - 
     - FK to IzendaWorkspace
     - 
   * - .. container:: lpad2

          **FromDatabaseName**
     - nvarchar
     - 256
     - 
     - Source database in mappings with "Database" type
   * - .. container:: lpad2

          **Type**
     - int
     - 
     - 
     - 
   * - .. container:: lpad2

          **FromObject**
     - nvarchar
     - 256
     - 
     - Source schema in mappings with "Schema" type
   * - .. container:: lpad2

          **ToDatabaseName**
     - nvarchar
     - 256
     - 
     - Target database in mappings with "Database" type
   * - .. container:: lpad2

          **ToObject**
     - nvarchar
     - 256
     - 
     - Target schema in mappings with "Schema" type
   * - .. container:: lpad2

          **IsGlobal**
     - bit
     - 
     - 
     - Place-holder
   * - .. container:: lpad2

          **FromServer**
     - nvarchar
     - 256
     - 
     - 
   * - .. container:: lpad2

          **ToServer**
     - nvarchar
     - 256
     - 
     - 
   * - **IzendaWorkspaceMappingTenant** |br|
       Selected tenants for each copy management mapping
     - 
     - 
     - 
     -
   * - .. container:: lpad2

          **WorkspaceMappingId**
     - uniqueidentifier
     - 
     - FK to IzendaWorkspaceMapping
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - **IzendaWorkspaceTenant** |br|
       Selected tenants for each copy management workspace
     - 
     - 
     - 
     -
   * - .. container:: lpad2

          **WorkspaceId**
     - uniqueidentifier
     - 
     - FK to IzendaWorkspace |br|
       not null
     - 
   * - .. container:: lpad2

          **TenantId**
     - uniqueidentifier
     - 
     - FK to IzendaTenant
     - The id of the tenant if not null
   * - .. container:: lpad2

          **Status**
     - int
     - 
     - 
     - 
       * 0 = NeedValidated
       * 1 = ReadyToCopy
       * 2 = AuthenticationMissing
       * 3 = ValidationError
   * - .. container:: lpad2

          **SourceDataModel**
     - nvarchar
     - max
     - 
     - Place-holder
   * - .. container:: lpad2

          **PhysicalDataModel**
     - nvarchar
     - max
     - 
     - Place-holder
   * - .. container:: lpad2

          **DestinationHashCode**
     - nvarchar
     - 500
     - 
     - Hascode of all connection strings of the tenant


.. helper sql code:
   select table_name , '* - .. container:: lpad2'+char(13)+char(10)+char(13)+char(10)+'       **' + column_name + '**' + char(13)+char(10)+'  - '+DATA_TYPE + char(13)+char(10)+'  - '+coalesce(cast(character_maximum_length as varchar(20)),'') + char(13)+char(10)+'  - ' + char(13)+char(10)+'  - ' from information_schema.columns where table_name like 'Izenda%' order by table_name,ORDINAL_POSITION 
