================================================
Supported Database Types
================================================

Supported Databases
~~~~~~~~~~~~~~~~~~~

Izenda fully supports the following database servers:

      -  Microsoft SQL Server 2008 or later
      -  Microsoft Azure
      -  Oracle 10.2 or later
      -  MySQL (For optimal performance MySQL 5.7+ is suggested. MySQL 5.7 includes major performance enhancements to derived tables/subqueries which are used throughout Izenda.)
      -  PostgreSQL 9.3+
      -  AWS Redshift (Izenda supports Redshift as a reporting database only (not a configuration database)) **New in version 2.7.0**
      -  :ref:`Elasticsearch` (Izenda supports Elastic as a reporting database only (not a configuration database)) **New in version 2.18.0**
      -  :ref:`MongoDB` (Izenda supports Mongo as a reporting database only (not a configuration database)) **New in version 3.1.0**

Cubes Support
~~~~~~~~~~~~~

    SSAS (SQL Server Analysis Services) cubes cannot be used directly as
    data sources; however, an MDX (Multidimensional Expression) query
    can be written to flatten the cube which Izenda can then report
    against.

Connection String Setup
~~~~~~~~~~~~~~~~~~~~~~~

Connection string setup is outlined in our Installation and Maintenance
Guide as well as our Administrator Guide.

-  Refer to the :doc:`System DB and License </ui/doc_system_db_and_license>`
   section and the :doc:`Connection String </ui/doc_connection_string>` section
   for more information.
