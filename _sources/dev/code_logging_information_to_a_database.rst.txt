=====================================
Logging Information Into a Database
=====================================

In order to adjust log4net to write to a particular database, as opposed
to the flat .log file there are a few steps that you need to take.

.. note::

   Depending on whether you are using the .NET Framework or .NET Core API resources, the configuration steps may vary. Please refer to the appropriate section below based on your setup.

-------------------------------------
Using .NET Framework API
-------------------------------------

-  Creating the Logging Database

   -  On your database sever, create an empty database with a meaningful
      name to easily identify its contents (ex. Izenda Logs)
   -  Within this table, create one table, entitled Log, with the query
      below:

      .. code-block:: sql

          CREATE TABLE [dbo].[Log] (
              [Id] [int] IDENTITY (1, 1) NOT NULL,
              [Date] [datetime] NOT NULL,
              [Thread] [varchar] (255) NOT NULL,
              [Level] [varchar] (50) NOT NULL,
              [Logger] [varchar] (255) NOT NULL,
              [Message] [varchar] (4000) NOT NULL,
              [Exception] [varchar] (2000) NULL 
          )

-  Open the web.config file in your API folder

   -  in ``<configSections>`` replace the current ``<section name="log4net">`` with the following:

      .. code-block:: xml

         <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net, Version=2.0.8.0, Culture=neutral, PublicKeyToken=669e0ddf0bb1aa2a" />

-  Lower on the same web.config file, there is a element (line 14).
   Remove this and all of its contents (Lines 14 through 52)

   -  Replace the removed section with the following, noting to add your
      connection string to the log database:

      .. code-block:: xml

         <log4net> <root> <level value="DEBUG" /> 
           <appender-ref ref="ADONetAppender" /> </root> 
           <appender name="ADONetAppender" type="log4net.Appender.ADONetAppender"> <bufferSize value="1" /> <connectionType value="System.Data.SqlClient.SqlConnection, System.Data, Version=2.0.8.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         
             <connectionString value="[YOUR CONNECTION STRING TO THE IZENDA LOGS DATABASE HERE]" /> 
             <commandText value="INSERT INTO Log ([Date],[Thread],[Level],[Logger],[Message],[Exception]) VALUES (@log_date, @thread, @log_level, @logger, @message, @exception)" />
         
             <parameter>
                  <parameterName value="@log_date"/> <dbType value="DateTime"/> <layout type="log4net.Layout.RawTimeStampLayout"/> 
             </parameter>
             <parameter>
                  <parameterName value="@thread"/> <dbType value="String"/> <size value="255"/> <layout type="log4net.Layout.PatternLayout"> <conversionPattern value="%thread"/> </layout> 
             </parameter>
             <parameter>
                  <parameterName value="@log_level"/> <dbType value="String"/> <size value="50"/> <layout type="log4net.Layout.PatternLayout"> <conversionPattern value="%level"/> </layout> 
             </parameter>
             <parameter>
                  <parameterName value="@logger"/> <dbType value="String"/> <size value="255"/> <layout type="log4net.Layout.PatternLayout"> <conversionPattern value="%logger"/> </layout> 
             </parameter>
             <parameter>
                  <parameterName value="@message"/> <dbType value="String"/> <size value="4000"/> <layout type="log4net.Layout.PatternLayout"> <conversionPattern value="%message"/> </layout> 
             </parameter>
             <parameter>
                  <parameterName value="@exception"/> <dbType value="String"/> <size value="2000"/> <layout type="log4net.Layout.ExceptionLayout"/> 
             </parameter> 
           </appender> 
         </log4net>

      .. note::
         
         The bufferSize value is currently set to 1. You can adjust
         this value to change the frequency with which the logs get pushed
         into the database.

-------------------------------------
Using .NET Core API
-------------------------------------

-  Creating the Logging Database

   -  On your database sever, create an empty database with a meaningful
      name to easily identify its contents (ex. Izenda Logs)
   -  Within this table, create one table, entitled Log, with the query
      below:

      .. code-block:: sql

          CREATE TABLE [dbo].[Log] (
              [Id] [int] IDENTITY (1, 1) NOT NULL,
              [Date] [datetime] NOT NULL,
              [Thread] [varchar] (255) NOT NULL,
              [Level] [varchar] (50) NOT NULL,
              [Logger] [varchar] (255) NOT NULL,
              [Message] [varchar] (4000) NOT NULL,
              [Exception] [varchar] (2000) NULL 
          )

-  Open the log4net.config file in your API folder

   -  In ``<root>`` replace the current ``<appender-ref>`` elements with the ADONetAppender. Please refer the following as example:

      .. code-block:: xml

          <root>
               <appender-ref ref="ADONetAppender" />
          </root>

-  Lower on the same log4net.config file, there are two appender elements.
   Remove this and all of its contents (Lines 8 through 38)

   -  Replace the removed section with the following, noting the reference to appsetting.json for the connectionStringFile:

      .. code-block:: xml

          <appender name="ADONetAppender" type="MicroKnights.Logging.AdoNetAppender, MicroKnights.Log4NetAdoNetAppender">
               <bufferSize value="1" />
               <connectionType value="System.Data.SqlClient.SqlConnection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089" />
               <connectionStringName value="log4net" />
               <connectionStringFile value="appsettings.json" />
               <commandText value="INSERT INTO Log ([Date],[Thread],[Level],[Logger],[Message],[Exception]) VALUES (@log_date, @thread, @log_level, @logger, @message, @exception)" />
               <parameter>
                    <parameterName value="@log_date" />
                    <dbType value="DateTime" />
                    <layout type="log4net.Layout.RawTimeStampLayout" />
               </parameter>
               <parameter>
                    <parameterName value="@thread" />
                    <dbType value="String" />
                    <size value="255" />
                    <layout type="log4net.Layout.PatternLayout">
                    <conversionPattern value="%thread" />
                    </layout>
               </parameter>
               <parameter>
                    <parameterName value="@log_level" />
                    <dbType value="String" />
                    <size value="50" />
                    <layout type="log4net.Layout.PatternLayout">
                    <conversionPattern value="%level" />
                    </layout>
               </parameter>
               <parameter>
                    <parameterName value="@logger" />
                    <dbType value="String" />
                    <size value="255" />
                    <layout type="log4net.Layout.PatternLayout">
                    <conversionPattern value="%logger" />
                    </layout>
               </parameter>
               <parameter>
                    <parameterName value="@message" />
                    <dbType value="String" />
                    <size value="4000" />
                    <layout type="log4net.Layout.PatternLayout">
                    <conversionPattern value="%message" />
                    </layout>
               </parameter>
               <parameter>
                    <parameterName value="@exception" />
                    <dbType value="String" />
                    <size value="2000" />
                    <layout type="log4net.Layout.ExceptionLayout" />
               </parameter>
          </appender>

      .. note::
         
         The bufferSize value is currently set to 1. You can adjust
         this value to change the frequency with which the logs get pushed
         into the database.

-  Open the appsettings.json file in your API folder

   -  Add a "connectionStrings" parameter that points to your Log database similar to the below:

      .. code-block:: json
          :emphasize-lines: 26, 27, 28

          {
            "Logging": {
              "LogLevel": {
                "Default": "Warning"
              }
            },
            "httpHandlers": {

            },
            "AllowedHosts": "*",
            "AppSettings": {
              "Settings": {
                "defaultlandingpage": "Views/DefaultLandingPage.html",
                "izendaapiprefix": "api",
                "izendapassphrase": "vqL7SF+9c9FIQEKUOhSZapacQgUQh",
                "responseserverpath": "rs",
                "izenda.mssql.trimcharacters": "",
                "izenda.mysql.trimcharacters": "",
                "izenda.oracle.trimcharacters": "",
                "izenda.postgre.trimcharacters": ";",
                "izenda.redshift.trimcharacters": "",
                "izenda.elasticsearch.trimcharacters": "",
                "izenda.mongo.trimcharacters": ""
              }
            },
            "connectionStrings": {
              "log4net": "[YOUR CONNECTION STRING TO THE IZENDA LOGS DATABASE HERE]"
            }
          }

-  Download the MicroKnights.Log4NetAdoNetAppender.dll file from our Utilities page from the Upgrade tab in the `Customer Portal <https://app.izenda.com>`_.

   -  Add this assembly file to the root of your API directory.
