=====================================
Logging Information Into a Database
=====================================

In order to adjust log4net to write to a particular database, as opposed
to the flat .log file there are a few steps that you need to take.

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

         <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net, Version=1.2.15.0, Culture=neutral, PublicKeyToken=669e0ddf0bb1aa2a" />

-  Lower on the same web.config file, there is a element (line 14).
   Remove this and all of its contents (Lines 14 through 52)

   -  Replace the removed section with the following, noting to add your
      connection string to the log database:

      .. code-block:: xml

         <log4net> <root> <level value="DEBUG" /> 
           <appender-ref ref="ADONetAppender" /> </root> 
           <appender name="ADONetAppender" type="log4net.Appender.ADONetAppender"> <bufferSize value="1" /> <connectionType value="System.Data.SqlClient.SqlConnection, System.Data, Version=1.2.15.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         
             <connectionString value="<YOUR CONNECTION STRING TO THE IZENDA LOGS DATABASE HERE" /> 
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
