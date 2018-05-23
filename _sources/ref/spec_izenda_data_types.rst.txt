==================================
Izenda Data Types
==================================

.. topic:: Data Types

   All DBMS (Database Management System) enforce classifying data into data types, for data integrity and performance (disk reading and writing). However, each DBMS uses a data type terminology different from standard SQL, and even the standard terminology may be too technical for end-users to understand.

   For example: the case with `Boolean data types <https://en.wikipedia.org/wiki/SQL:1999#Boolean_data_types>`_.


   Izenda presents end-users with a generic data type system using familiar names.

|br|

List of Data Types
------------------

.. list-table::
   :widths: 9 13 13 13 13 13 13 13
   :header-rows: 1
   :stub-columns: 1

   * - Name
     - Description
     - ISO
     - Microsoft SQL Server
     - MySQL
     - Oracle
     - PostgreSQL
     - AWS Redshift
   * - Numeric
     - Numbers, including negative values, integers or real numbers (having decimal points).
     - integer, dec, float, double precision
     - tinyint, smallint, int, bigint, decimal, float, real
     - tinyint, smallint, mediumint, int, integer, bigint, decimal, numeric, fixed, float, double, double precision, real
     - number, binary_float, binary_double, binary_integer
     - smallint, bigint, integer, double precision, real, numeric
     - numeric, int, smallint,  integer, real, int2, int4, int8, bigint, float4, float8, double precision, smallserial, serial, bigserial
   * - Text
     - Text, maximum 4,000 chars.
     - character, char varying, character varying, national char, national character, national char varying, nation character varying, nation text
     - char, varchar, nchar, nvarchar, text, ntext
     - char, varchar
     - char, varchar2, nchar, nvarchar2
     - character, char, character varying, varchar, text
     - character varying, character, bpchar, varchar, nvarchar, text, uuid, bit, bit varying, cidr, inet, macaddr, interval
   * - Datetime
     - Date combined with time of day.
     - timestamp, date
     - smaldatetime, datetime, date, datetime2
     - date, datetime, timestamp
     - date, timestamp
     - date, timestamp, timestamp without time zone, timestamp with time zone
     - timestamp,timestamp with time zone, datetime, date, timestamp without time zone
   * - Money
     - Currency amount.
     - numeric
     - money, smallmoney
     - N/A
     - N/A
     - money
     - N/A
   * - Boolean
     - TRUE and FALSE values.
     - boolean
     - bit
     - bool, boolean, tinyint(1)
     - number(1)
     - boolean
     - boolean
   * - Image
     - The binary format of an image.
     - N/A
     - image
     - N/A
     - N/A
     - N/A
     - N/A
   * - Lob
     - Binary data.
     - binary large object
     - text, ntext, binary, varbinary
     - binary, varbinary, tinyblob, blob, mediumblob, longblob, tinytext, text, mediumtext, longtext
     - clob, nlob, long, blob, bfile, raw, long raw
     - bytea
     - bytea
   * - Time
     - Time data only (hour, minute, and second values)
     - Time
     - Time
     - Time
     - N/A
     - time, time without time zone, time with time zone
     - time with time zone, time without time zone, time
   * - XML
     - Extensible Markup Language (XML) data type
     - N/A
     - XML
     - N/A
     - XMLType
     - XML
     - XML
   * - JSON
     - JavaScript Object Notation (JSON) data type
     - N/A
     - XML
     - JSON
     - N/A
     - JSON
     - JSON

Default Data Type Mapping
---------------------------

.. list-table::
   :widths:  9 13 13 13 13 13 13 13
   :header-rows: 1
   :stub-columns: 1

   * - Name
     - Description
     - ISO
     - Microsoft SQL Server
     - MySQL
     - Oracle
     - PostgreSQL
     - AWS Redshift
   * - Numeric
     -  Numbers, including negative values, integers or real numbers (having decimal points).
     - dec
     - decimal
     - decimal
     - number
     - numeric
     - numeric
   * - Text
     - Text, maximum 4,000 chars.
     - nation character varying
     - nvarchar
     - varchar
     - nvarchar2
     - character varying
     - character varying
   * - Datetime
     - Date combined with time of day.
     - timestamp
     - datetime2
     - datetime
     - date
     - timestamp
     - timestamp
   * - Money
     - Currency amount.
     - numeric
     - money
     - decimal
     - number
     - money
     - numeric
   * - Boolean
     - TRUE and FALSE values.
     - boolean
     - bit
     - tinyint(1)
     - number(1)
     - boolean
     - boolean
   * - Image
     - The binary format of an image.
     - binary large object
     - image
     - longblob
     - blob
     - bytea
     - bytea
   * - Lob
     - Binary data.
     - binary large object
     - varbinary
     - longblob
     - blob
     - bytea
     - bytea
   * - Time
     - Time data only (hour, minute, and second values)
     - Time
     - Time
     - Time
     - N/A
     - time with time zone
     - time with time zone
   * - XML
     - Extensible Markup Language (XML) data type
     - N/A
     - XML
     - N/A
     - XMLType
     - XML
     - XML
   * - JSON
     - JavaScript Object Notation (JSON) data type
     - N/A
     - nvarchar (JSON functions will be supported)
     - JSON
     - N/A
     - JSON
     - JSON

Data Type Precedence
--------------------

When an operator combines two expressions of different data types, the
expression of the lower precedence data type is converted to the higher
precedence data type. If the conversion is not available, an error is
returned.

#. Datetime (highest)
#. Numeric
#. Money
#. Boolean
#. Text
#. Image
#. Lob
#. Time
#. XML
#. JSON (lowest)
