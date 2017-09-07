================================================
Query Performance
================================================

There are several factors related to optimal query performance.

Optimized Data Model
~~~~~~~~~~~~~~~~~~~~

Izenda moves as fast as your data allows.

-  Izenda leverages directly off reporting databases. Izenda does not
   store any data and is, therefore, a query executor and performs as
   efficiently as the databases that it sits on top of.
-  Provide views and stored procedures at the database layer whenever
   possible to streamline complex queries and data setup. Izenda allows
   for similar functionality to be built on-the-fly but this will ensure
   that the performance is specifically tailored to your data.

.. _Izenda_Fusion:

Izenda Fusion
~~~~~~~~~~~~~

Izenda allows users to connect to multiple databases and create
relationships between them through a method known as Izenda Fusion.

-  Databases are not required to be on the same machine since each
   database has it's own unique connection string
-  Databases do \*not\* have to be of the same type. For instance, you
   can "fuse" a MySQL Database with an Microsoft SQL Database.
-  Izenda’s Fusion engine leverages asynchronous querying in tandem with
   in memory query tree and map reduce technologies. This enables fast
   cross database querying and multi-step calculations.
-  Izenda does not cache data in memory or copy any data from your
   database.
-  Izenda can connect to and query multiple databases asynchronously,
   and then aggregate returned data in memory before sending to client
   for rendering.
