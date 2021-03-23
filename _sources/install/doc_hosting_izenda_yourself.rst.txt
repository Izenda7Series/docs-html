==========================
Hosting Izenda
==========================

.. note::

   It is recommended to install Izenda Front-end and Back-end on two separate servers to achieve maximum scalability. |br|
   For small data sources, however, a single server can be used.

Minimum Hardware Requirements
------------------------------

- Processor: 8 Core CPU (3.6Ghz)
- Free Hard Disk Space: 10 GB
- SSD drives are recommended for optimal database performance
- RAM: 16 GB

.. note::

    This is the minimum recommended for both the Database and the API servers. Your actual needs may vary based on the size of your database(s) and the number of concurrent users.

Software Requirements
------------------------------

* Operating System: Windows Server 20016 or newer , Ubuntu 18.04 or newer , Linux latest versions
* Web Server: IIS8 or newer with ASP Net Core 3.1 runtime for windows , Apache and Nginx latest versions for Linux
* .NET Core: .NET 3.1
* Supported Database servers, we recommend using a separate database for your Izenda configuration database as there are updates and changes which must be made during any upgrades for new features and performance:
   - Microsoft SQL Server 2012 or later
   - Microsoft Azure
   - PostgreSQL - 10.5 or later

