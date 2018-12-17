==========================
Hosting Izenda
==========================

.. note::

   It is recommended to install Izenda Front-end and Back-end on two separate servers to achieve maximum scalability. |br|
   For small data sources, however, a single server can be used.

Minimum Hardware Requirements
------------------------------

- Processor: 4 Core CPU (3.6Ghz)
- Free Hard Disk Space: 1 GB

  * SSD drives are recommended for optimal database performance

- RAM: 16 GB


.. note::

    This is the minimum recommended for both the Database and the API servers. Your actual needs may vary based on the size of your database(s) and the number of concurrent users.

Software Requirements
------------------------------

*  Operating System: Windows Server 2008R2 or newer
*  Web Server: IIS7 or newer with ASP.NET (see :ref:`Install_ASP.NET_4.5_and_URL_Rewrite_Components`)
*  .NET Application Pool (CLR): 4.0 Integrated
*  .NET Framework: .NET 4.0 or higher
*  Supported Database servers, we recommend using a separate database for your Izenda configuration database as there are updates and changes which must be made during any upgrades for new features and performance:

   -  Microsoft SQL Server 2008 or later
   -  Microsoft Azure
   -  Oracle 10.2 or later
   -  MySQL
   -  PostgreSQL

Required Software for Oracle Data Source
------------------------------------------

To access Oracle database, Izenda uses the Oracle Data Provider for .NET. This driver uses some DLLs that may be missing from some machines.

If having issues with **Oracle.ManagedDataAccessDTC.DLL**, please install the Microsoft Visual C++ 2010 Redistributable:

*  For Windows Server 2008 R2 x64, install the `Microsoft Visual C++ 2010 Redistributable Package <http://www.microsoft.com/en-us/download/details.aspx?id=14632>`_
*  For Windows Server 2012 x64, install the `Microsoft Visual C++ 2010 SP1 Redistributable Package <http://www.microsoft.com/en-us/download/details.aspx?id=13523>`_
