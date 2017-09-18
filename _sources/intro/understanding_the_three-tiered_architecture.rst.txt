=============================================
Understanding The Three-tiered Architecture
=============================================

Overview
--------

Izenda is split into three levels: the Front End (UI), the Back End
(API),and the User Store (database layer). The three levels can be
configured to support standalone models of Izenda as well as seamless,
fully integrated versions.

*  Izenda offers a number of Integration Options.

   - 0 : All Stand Alone

   - 1 : Back End Stand Alone Front End Integrated

   - 2 : Back End Integrated Front End Stand Alone

   - 3 : All Integrated |br|

*  The diagram below groups our current kits available according to
   their deployment method.

   .. note::

      Click on the image to zoom or scroll down to see more detailed versions of each diagram

   .. figure:: /_static/images/Overview4.png

      Overview

*  Once Izenda is deployed, the SystemSettings table must be updated with the correct deployment value. For more about the SystemSetting table, click :doc:`here </ref/spec_izendasystemsetting_table>`.

Standalone Deployment
---------------------

-  The Standalone Deployment style features a standalone front end and
   back end. The goal for this deployment is to quickly disseminate the
   Izenda platform as outline throughout the documentation.

   -  Page layouts are immutable.
   -  CSS Stylesheets and basic logo replacement available.

.. figure::  /_static/images/Standalone.jpg

   A diagram of Izenda's standalone architecture.

-  **BI Platform Implementation**

   -  *Requires the `API <http://downloads.izenda.com/latest/API.zip/>`_, `StandaloneUI <http://downloads.izenda.com/latest/StandaloneUI.zip>`_, and an empty database*

   -  For installation steps, see the :doc:`/install/doc_installation_guide` and :doc:`/install/doc_upgrade_guide` for stand alone deployments.

   .. figure::  /_static/images/StandaloneArchDiagram2.png

      A diagram of implementation

.. _Fully_Integrated_Deployment:

Fully Integrated Deployment
---------------------------

*  The Fully Integrated Deployment style features an integrated front
   end and back end. The goal for this deployment is to create a
   seamless experience for your user while making the code intuitive and
   maintainable.

   -  Allows for Single Sign-On Authentication through your application.
   -  Allows for full-page renders of Izenda as well as granular element
      renders to allow unique page configurations within your
      application.
   -  Allows for tenant-level white labeling of colors, graphics, and
      page schemes.

   .. figure::  /_static/images/Fully_Embedded.jpg

      A diagram of Izenda's fully integrated architecture

*  **MVC Implementation**

   - *Requires the API, the Embedded UI, `MVC Back End Standalone Kit <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone>`_, and an empty database.*

   .. figure::  /_static/images/MVC3ArchDiagram.png

      A diagram of implementation

Backend End Standalone Deployment: Standalone API, Embedded UI
---------------------------------------------

*  The Mixed Deployment syle features a seamless front end with a remote
   back end. This deployment is useful when you can devote a lightweight
   server to your integrated front end and a "meatier" server for all
   API calls which would include requesting queries from your reporting
   database(s).

*  **MVC Implementation**

   - *Requires the API, the Embedded UI, the `MVC Kit <https://github.com/Izenda7Series/Mvc5StarterKit>`_, and an empty database.*

   .. figure::  /_static/images/MVC1ArchDiagram.png

      A diagram of implementation

*  **Angular 2 Implementation**
      - *Requires the API, the Embedded UI, the `test <https://github.com/Izenda7Series/Angular2Starterkit/>`_, and an empty database.*


   .. figure::  /_static/images/Angular1ArchDiagram2.png

      A diagram of implementation
    
    

Switching Between Deployment Styles
-----------------------------------

While it is possible to switch between deployment styles, it is
discouraged for a long-term deployment strategy.

-  The database layer is accessed differently in different modes and
   some values within the configuration database are unique to a
   particular deployment style. To switch a deployment from one style to
   another, a database administrator must update these values.
-  Izenda has a Console Application that will allow you to copy reports
   from one Configuration Database to another. This can help remedy
   potential data corruption and can be modified to schedule migrations.
   Nevertheless, the results may be extremely server intensive depending
   on your server resources and your data size. Please refer to the
   :doc:`/ui/doc_copy_console` for more information.

Alternative:

-  If you like the setup of the standalone style for report/dashboard
   designers but would like the seamless nature of the embedded style
   for end users, you can create a "designer" tenant in an embedded
   deployment with access to a fully rendered Izenda BI Portal. Reports
   and dashboards can then be copied from one tenant to another via
   :doc:`/ui/doc_copy_management` page.
