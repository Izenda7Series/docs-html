

==========================
System DB and License
==========================

The **System DB and License** page allows user (admin) to

-  install to a target database
-  validate and store the license inside that database
-  renew the license or activate new modules.

Clean-install Preparations
--------------------------
 

-  A database server with an empty database already created - this would
   become the Izenda system database. Supported database servers
   include:

   .. hlist::
      :columns: 2

      -  Oracle
      -  MySQL
      -  Microsoft SQL Server
      -  PostgreSQL
      -  Microsoft Azure SQL Database

-  An Izenda license key - `email
   sales@izenda.com <mailto:sales@izenda.com?Subject=Izenda%20Trial>`__
   for a trial license.

Install the System Database
---------------------------

The first section is to input, verify and save the database connection
information.

#. .. _System_DB_&_License:

   .. figure:: /_static/images/System_DB_&_License.jpg
      :align: right
      :width: 483px

      System DB & License

   In browser, log in to Izenda as an Admin.
#. Click System DB & License in the left menu. (:numref:`System_DB_&_License`) |br|
#. .. _Select_Database_Server_Type:

   .. figure:: /_static/images/Select_Database_Server_Type.jpg
      :align: right
      :width: 379px

      Select Database Server Type

   Select database server type from the dropdown box. (:numref:`Select_Database_Server_Type`)

       All major database servers are already supported. |br|

#. Click the Connection Builder icon (⚡) to help build the connection string easily. (:numref:`Connection_Builder_link`)

   .. _Connection_Builder_link:

   .. figure:: /_static/images/Connection_Builder_link.jpg
      :width: 600px

      Click Connection Builder icon

   .. _Connection_Builder:

   .. figure:: /_static/images/Connection_Builder.jpg
      :align: right
      :width: 458px

      Connection Builder

   The Connection Builder. (:numref:`Connection_Builder`)

   This step can be bypassed when user already knows the connection
   string. In this case, it can be copied and pasted straight into the
   Connection String box. Some connection string examples are also
   provided below. |br|

   Example Connection Strings:

   - Oracle:
      - Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.45.37)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=MyOracleSID)));User Id=user;Password=password;
      - Data Source=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.45.37)(PORT=1521))(CONNECT_DATA=(SID=xe)));User Id=user;Password=password;
   
   - Microsoft SQL Server:
      - Server=192.168.45.37,1433;Database=izendaconfig;User ID=user;Password=password
      - Server=HOST-PC;Database=izendaconfig;User ID=user;Password=password

   - MySQL:
      - Server=MY-PC;Port=3306;Database=izendaconfig;User ID=user;Password=password
   
   - PostgreSQL:
      - Server=mydomainname;Port=5432;Database=izendaconfig;User ID=user;Password=password

#. Click the Connect button to test database connection and all
   necessary permissions for Izenda to work.

   The Connection String box will be highlighted while the database is being set up for first use.

   .. _Connection_String_highlighted:

   .. figure:: /_static/images/Connection_String_highlighted.jpg
      :width: 810px

      Connection String highlighted

#. After the connection string has been verified successfully, it will be saved and user can move next to the License section.

   .. note::

      Unless the Connection String has been verified successfully, user will not be able to perform any further action.

.. _Validate_and_Store_the_License:

Validate and Store the License
------------------------------

  In this section user will input, validate and save the license.

#. Click the Offline/Online switch to specify the license mode. (:numref:`Offline` and :numref:`Online`)

   .. _Offline:

   .. figure:: /_static/images/Offline.jpg

      Offline mode

   .. _Online:

   .. figure:: /_static/images/Online.jpg

      Online mode

#. Enter the license.

   -  For Offline mode user needs to enter the license key and token.
   -  For Online mode user needs to enter the license key.

#. Click Validate.

   .. note::

      In Online mode, another connection will be initiated to Izenda License Server for key validation.

#. Upon successful validation, the license will be automatically saved in the database. The license details will also be displayed in the License Information section for review. (:numref:`License_Information`)

   .. _License_Information:

   .. figure:: /_static/images/License_Information.jpg
      :width: 810px

      License Information section



System Mode Settings
--------------------

 

#. Select to use multi-tenant mode or not.

       This mode allows multiple clients on the same Izenda system.

       .. _System_Mode:

       .. figure:: /_static/images/System_Mode.png
          :width: 654px

          System Mode

#. If using multi-tenant mode, select to allow duplicated user id among
   different tenants or not.

Import Map Data
---------------

Optionally provision Map data. This is only needed if the report part
type :doc:`Map <doc_report_designer_map>` is to be used in reports and dashboards.

US zip codes match on first 5 number, and Canadian zip codes will match on the first 3 characters of the zip code.

.. note::

   Izenda Map data contains all countries and all US and Canada cities and will take several minutes to be fully set up.
   
To upgrade map data when any changes are made by Izenda please follow the instructions below. We do not automatically run these types of upgrades as map report parts will not work until the process is complete:

1. Update IzendaSystemSetting Table in your Izenda Configuration Database as below: |br|

.. code-block:: sql
	:linenos:
	
	Update IzendaSystemSetting
	Set Value = 0
	Where Name = 'ProvisionStaticDataStatus'
	
.. Warning::

   As general best practice, we recommend backing up your database before making any manual updates.

2. After making these changes, all API instances should be restarted. 
 
3. Next you will need to log into the Izenda Application as a System Administrator and Run "Provision Map Data" on the Izenda DB & License Page to insert the new data. |br|

Once this is complete, map report parts will be available again. 

Modify the License
------------------

  The Database Connection and License Entry page allows modifying the
license to either renew it or activate new modules.

#. In browser, log in to Izenda as an Admin.
#. Click System DB & License in the left menu.
#. Note the current license details in License Information section.
#. Click the Offline/Online switch to specify the license mode.
#. Enter the license.

   -  For Offline mode user needs to enter the new license key and
      token.
   -  For Online mode user needs to enter the new license key.

#. Click Validate.

   .. note::

      In Online mode, another connection will be initiated to Izenda License Server for key validation.

#. Upon successful validation, the new license will be automatically saved in the database.
#. Please review the new license details in License Information section. (:numref:`License_Next`)

   .. _License_Next:

   .. figure:: /_static/images/License_Next.jpg
      :width: 796px

      New License Information

Select new System Database
--------------------------

Only select new system database if needed, since all current settings
are not copied to the new database.

#. In browser, log in to Izenda as an Admin.
#. Click System DB & License in the left menu.
#. Use the Connection Builder to build the new connection string.
#. Click Connect.
#. Click OK in the confirmation pop-up to acknowledge that the license
   needs to be re-validated afterwards. (:numref:`SystemDB_Change_System_DB_Confirmation`)

   .. _SystemDB_Change_System_DB_Confirmation:

   .. figure:: /_static/images/SystemDB_Change_System_DB_Confirmation.jpg
      :width: 457px

      New system database confirmation

   If there is an error with the new database connection, the current connection continues to be used. (:numref:`SystemDB_Change_NonExistent_System_DB_Confirmation`)

   .. _SystemDB_Change_NonExistent_System_DB_Confirmation:

   .. figure:: /_static/images/SystemDB_Change_NonExistent_System_DB_Confirmation.jpg
      :width: 713px

      Invalid new connection confirmation

#. System will be installed to the new database.
#. `Validate and store the license`_ again.

Notifications
-------------

Nearly-expired License Reminder
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _Expired_License:

.. figure:: /_static/images/Expired_License.jpg
   :align: right
   :width: 308px

   Near Expired License Reminder

User will get this reminder when the license is near expiration. (:numref:`Expired_License`) |br|

User will need to request a new license, then enter and validate it in the system.

Changing License to Online/Offline Confirmation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When switching the license mode, there will be a pop-up confirmation.

-  .. _Online_confirmation:

   .. figure:: /_static/images/Online_confirmation.jpg
      :align: right
      :width: 473px

      Offline to Online Confirmation

   To Online mode (:numref:`Online_confirmation`) |br|
-  .. _Offline_confirmation:

   .. figure:: /_static/images/Offline_confirmation.jpg
      :align: right
      :width: 476px

      Online to Offline Confirmation

   To Offline mode (:numref:`Offline_confirmation`) |br|

Click OK to confirm or Cancel to keep current license mode.

Email Support
-------------

Should user has any further question, he/she can quickly ask for
assistance via email by clicking the envelope icons (✉) in Database
Connection and License sections respectively.
