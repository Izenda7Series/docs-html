.. _Breaking_Changes:

================
Breaking Changes
================
v4.0.0 (Beta) Major Release – March 24th, 2021
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. warning::
    - Front-end Updates: Izenda updated the following frontend libraries and dependencies customer who integrated izenda frontend need to modify their frontend if they are affected by the below library changes.	
        - React upgraded from 15.6 to 16.3
            - `React 15 to 16 migration guide <https://reactjs.org/blog/2017/09/26/react-v16.0.html>`_
            - React-dom upgraded from 15.6 to 16.3
        - Mobx upgraded from 2.4.2 to 5.15
            - `Mobx 3 to 4 migration guide <https://github.com/mobxjs/mobx/wiki/Migrating-from-mobx-3-to-mobx-4>`_
            - `Mobx 4 to 5 migration guide <https://mobx.js.org/migrating-from-4-or-5.html>`_    
        - Mobx-react upgraded from 3.5 to 5.2
        - Bootstrap upgraded from 3.3.7 to 3.4.1
        - Babel upgraded from 6 to 7
            - `Babel 7 migration guide <https://babeljs.io/docs/en/v7-migration>`_
  
    - .Net Core 3.1
        - If you currently use the IAdHocExtension/IzendaCustomBootstrapper classes you will need to rebuild these into a new assembly using our v4.x.x DLL's.
        - if your current deployment of izenda APIs are under the .net full framework then your deployment needs to migrate to .netcore 3.1
    - Exporting Engine
        - Izenda has updated the exporting process from WebKit to the Blink Engine
        - This could impact customers with Azure App Service deployments as the exporting service will not work directly due to the Blink engine. Please deploy the Izenda docker within a Linux container to resolve this.  
    - Map Provisioning Changes
        - The Izenda data structure for mapping data points has been updated for better performance, so map data must be re-provisioned within your Izenda instance
    - Encryption Changes
        - Izenda's encryption algorithm has been updated from 128 bit to 256 bit to support FIPS compliance
        - Updating your existing values into your izenda config database you need to log in as administrator and provision encryption jobs from the settings tab.
        - Izenda strongly recommends updating these encryption methods also it is strongly recommended to take backup of the izenda config database.  
    - Excel Driver
        - Izenda has internalized the Excel driver and as a result, some pre-existing reports may be impacted by this change

v3.0.0 April 2, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. warning::
  - If you currently have additional Azure resources configured for an EvoPDF exporting provider, this is no longer necessary. Syncfusion works in Azure environments without the need for a specific service. You will need to adjust your exporting configurations accordingly.
  - If you currently use the IAdHocExtension classes you will need to rebuild these into a new assembly using our v3.x dlls.

v2.18.1 March 19, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. warning::
   If you are currently leveraging LEFT or RIGHT joins in your reports, you should ensure that the changes in IZ-22764 have not impacted your reporting data.

v2.18.0 March 6, 2019
~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. warning::
   If you are leveraging the Quartz ADOJobStore database you will need to run an upgrade script on your Quartz database that can be found `here <https://github.com/quartznet/quartznet/blob/2.x/database/schema_25_to_26_upgrade.sql>`_.

v2.1.1 June 2, 2017
~~~~~~~~~~~~~~~~~~~~~
.. warning::
  For version 2.1.1 and above, there are code-level changes that will need to be made when using Izenda in embedded mode. The previous Encryption/Decryption logic has been refactored to use a new StringCipher class local to the kits. You can view the latest commits for more details.

v2.1.0 May 31, 2017
~~~~~~~~~~~~~~~~~~~~~
.. warning::
  -  File izenda-ui-blessed1.css was removed from the UI download it was merged with izenda-ui.css, please ensure when upgrading that it is removed from your local deployment

v2.0.0
~~~~~~~~~~~~~~~~~~~~~
.. warning::
  -  API Request - added additional header "Selected Tenant" for Global Reports. This change is already made in the webconfig in the build for download.
  -  Please ensure you are using the latest version of the Copy Console which is available with this download
  
.. warning::
   Global reports cannot be copied using the Copy Management UI. By definition, Global reports are meant to be shared across the tenant base to reduce the number of report definitions required for reports that all tenant can use. The copy console does not block copying Global reports to a tenant, and we are working on a patch to restrict this. Please note that doing this will cause unintended behavior and therefore should not be done. A feature is planned for a later release to add support for copying Global Reports from one System level to another for independent Izenda configuration databases, for now please do not copy Global reports using the Copy Console.
   Known issue: Tenant users with Full Report and Dashboard access can alter Global Category names.

v1.25.0
~~~~~~~
.. warning::
   -  For integrations using deployment mode 1 (Front End Integrated and Back End Standalone) you must update the Izenda System Settings table. The following Settings must contain the full URL including the base address AuthValidateAccessTokenUrl and AuthGetAccessTokenUrl. These would have been relative paths prior and now must be the full url including the base url.
