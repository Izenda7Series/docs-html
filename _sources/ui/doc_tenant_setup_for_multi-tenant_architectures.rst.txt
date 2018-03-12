

===========================================
Tenant Setup for Multi-tenant Architectures
===========================================

.. versionadded:: 2.0.0

   Global Report feature can be used to share system reports among all tenants, see :doc:`/ui/doc_global_report_setup`.

In multi-tenant systems, tenant data is stored in similar database
structures placed in

-  different databases - Separate Database Architecture
-  different schemas in the same database - Separate Schema Architecture
-  same tables, schemas and databases - Shared Schema Architecture

Separate Database Architecture
------------------------------

.. _TicketDesk_-_Separate_Database_Architecture:

.. figure:: /_static/images/TicketDesk_-_Separate_Database_Architecture.png
   :align: right
   :width: 143px

   Sample Separate Database Architecture

Each tenant data is
stored in a separate database with identical structure. |br|

#. Add connections to each tenant database at that tenant level.

       In this sample, create 4 tenants each having one connection to
       its database.

#. Data model and other settings should be set up for one tenant, then
   copied to other tenants using a Copy Management setting similar to
   the following:

   .. _Copy_Management_-_Separate_Database_Architecture:

   .. figure:: /_static/images/Copy_Management_-_Separate_Database_Architecture.png
      :width: 900px

      Copy Management for Separate Database Architecture

Separate Schema Architecture
----------------------------

Each tenant data is stored in a separate schema in the same database.

#. Add
   connections to the shared database at that each tenant level.
#. Set up data model for one source tenant only.

   .. _MultiTenantCase2_T1_Data_Model:

   .. figure:: /_static/images/MultiTenantCase2_T1_Data_Model.png
      :width: 556px

      Connection and Data Model for one Source Tenant

#. Skip data model
   for other tenants (Just add the connection, test then save it).

   .. _MultiTenantCase2_T2_Connection:

   .. figure:: /_static/images/MultiTenantCase2_T2_Connection.png
      :width: 557px

      Connection for other Destination Tenants

#. Copy data model to other tenants using a Copy Management setting
   similar to the following:

   .. _Copy_Management_-_Separate_Schema_Architecture:

   .. figure:: /_static/images/Copy_Management_-_Separate_Schema_Architecture.png
      :width: 900px

      Copy Management for Separate Schema Architecture

#. The data model was successfully
   copied to other tenants.

   .. _MultiTenantCase2_T2_After_Copy:

   .. figure:: /_static/images/MultiTenantCase2_T2_After_Copy.png
      :width: 540px

      Copied Data Model

Shared Schema Architecture
--------------------------

Each tenant data is stored in the same tables, schema and database,
identified by different values in a "TenantID" field in every table.

#. Add
   connections to the shared database at that each tenant level.
#. Set up data model for one source tenant only.

   .. _MultiTenantCase3_T1_Data_Model:

   .. figure:: /_static/images/MultiTenantCase3_T1_Data_Model.png
      :width: 567px

      Connection and Data Model for one Source Tenant

#. Skip data model
   for other tenants (Just add the connection, test then save it).

   .. _MultiTenantCase3_T2_Connection:

   .. figure:: /_static/images/MultiTenantCase3_T2_Connection.png
      :width: 568px

      Connection for other Destination Tenants

#. Copy data model to other tenants using a Copy Management setting
   similar to the following:

   .. _Copy_Management_-_Shared_Schema_Architecture:

   .. figure:: /_static/images/Copy_Management_-_Shared_Schema_Architecture.png
      :width: 900px

      Copy Management for Shared Schema Architecture

#. Specify this specific
   "TenantID" field in the "Tenant Field" advanced setting to
   automatically restrict report data to that of the tenant of the
   current logged-in user.

       (This setting basically adds a filter condition "TenantID" = <value of the tenant id of the current logged-in user> to
       every query sources used in report)

   .. note::

      Please note that the field must be wrapped in brackets when set. For example: TenantID should be set as [TenantID]

   .. _Tenant_Field_advanced_setting:

   .. figure:: /_static/images/Tenant_Field_advanced_setting.png
      :width: 650px

      Tenant Field Advanced Setting

Reference
---------

-  `Multi-Tenant
   Architectures <https://msdn.microsoft.com/en-us/library/aa479086.aspx>`__
