================================================
Understanding the User Store
================================================

The User Store is one of the three tiers of Izenda's Architecture and is
designed to manage all data interactions within Izenda. Within the User
Store, the Configuration Database stores all relevant reporting data.
The Configuration Database is set up during the :doc:`installation
process </install/doc_installation_guide>` and can be hosted on various :doc:`types
of databases. </intro/supported_database_types>`.

.. figure::  /_static/images/UserStore.jpg
    :align: center
    :scale: 75 %

    UserStore

What The Configuration Database Contains (High Level)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Encrypted Database Connection Strings
-  User identifier information
-  Report Definitions
-  Report Metadata (e.g. revision history previously saved versions)

What The Configuration Database Does Not Contain (High Level)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  A backdoor to your data
-  A backdoor to your user identities (Social Security numbers, spouse
   names, favorite colors)

Connection to Izenda Servers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  In online mode, the User Store is used routinely to verify the
   license.
-  Reports Definitions, User Definitions, and Connection Strings are not
   backed up on Izenda servers.
