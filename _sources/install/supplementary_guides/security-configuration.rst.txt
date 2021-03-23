======================================
Security Configuration
======================================
|

Introduction
------------------------------------------
Izenda v2.7.1 and higher allows application administrators to directly trim out the specified charaters per database server type when loading schemas. This option is applied globally and will affect the system and tenant users.


Configuration
----------------------------------------------------
This option is configured by the adding a key/value entry for the desired database and schemas in the API/Web.config file as shown below:

.. code-block:: xml
   :linenos:
   
   <!-- Please be sure that there are no leading or trailing spaces for each entry. -->
   <appSettings> 
      <add key="izenda.mssql.trimcharacters" value="" />
      <add key="izenda.mysql.trimcharacters" value="" />
      <add key="izenda.oracle.trimcharacters" value="" />
      <add key="izenda.postgre.trimcharacters" value="" />
      <add key="izenda.redshift.trimcharacters" value="" />
   </appSettings>


.. note::

   Depending on your IIS configuration, changes to the Web.config file may automatically trigger the application to be reloaded.


List of Supported Keys
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+--------------------------------------------+
| **izenda.mssql.trimcharacters**            |
+--------------------------------------------+
| **izenda.mysql.trimcharacters**            |
+--------------------------------------------+
| **izenda.oracle.trimcharacters**           |
+--------------------------------------------+
| **izenda.postgre.trimcharacters**          |
+--------------------------------------------+
| **izenda.redshift.trimcharacters**         |
+--------------------------------------------+