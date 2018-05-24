=============================================
Understanding The Three-tiered Architecture
=============================================

Overview
--------

Izenda is split into three levels: the Front End (UI), the Back End
(API),and the User Store (database layer). These three componenets can be
configured to support a fully standalone instance of Izenda as well as seamless,
fully-integrated instances.

.. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/Architecture.png
      :align: center

      High-level User & API Interaction

For more informaton about embedding Izenda, please refer to our `Developer Guide </dev/.developer_guide>`_.

*  Izenda offers a number of Integration Options.

   - 0 : All Stand Alone

   - 1 : Back End Stand Alone, Front End Integrated

   - 2 : Back End Integrated, Front End Stand Alone

   - 3 : Fully Integrated |br|

*  After deploying Izenda, ensure that the IzendaSystemSettings table in your Izenda Configuration Database contains the correct deployment mode value. For more about the SystemSetting table, click `here </ref/spec_izendasystemsetting_table>`_.

*  The table below groups our current kits available according to
   their deployment method. These kits are provided for demonstration purposes and should not be used as production-ready solutions.

   .. note::

      Click on an thumbnail or scroll down to see more detailed versions of each diagram

      
.. list-table::
   :header-rows: 1
   :widths: 100 100 100 100 100
   
   *  - Framework
      -  Deployment Mode 0
      -  Deployment Mode 1
      -  Deployment Mode 2
      -  Deployment Mode 3
   *  - Standalone Application
      -  .. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/thumbnails/Slide1.PNG
            :scale: 20 %
            :target: https://www.izenda.com/docs/intro/understanding_the_three-tiered_architecture.html#bi-platform-implementation
      -  
      -  
      -  
   *  - MVC
      -  
      -  .. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/thumbnails/Slide2.PNG
            :scale: 20 %
            :target: https://www.izenda.com/docs/intro/understanding_the_three-tiered_architecture.html#mvc-5-besa-implementation
      -  
      -  .. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/thumbnails/Slide4.PNG    
            :scale: 20 %
            :target: https://www.izenda.com/docs/intro/understanding_the_three-tiered_architecture.html#mvc-5-implementation
   *  - Web Forms
      -  
      -  
      -  
      -  .. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/thumbnails/Slide5.PNG
            :scale: 20 %
            :target:  https://www.izenda.com/docs/intro/understanding_the_three-tiered_architecture.html#webforms-implementation
   *  - Angular 2
      -  
      -  .. figure:: /_static/images/intro/understanding_the_three-tiered_architecture/thumbnails/Slide3.PNG
            :scale: 20 %
            :target: https://www.izenda.com/docs/intro/understanding_the_three-tiered_architecture.html#angular-2-implementation
      -  
      -  

Deployment Mode 0: Standalone Deployment
-----------------------------------------

-  The Standalone Deployment style features a standalone front end and
   back end. The goal for this deployment is to quickly disseminate the
   Izenda platform as outline throughout the documentation.

   -  Page layouts are immutable.
   -  CSS Stylesheets and basic logo replacement available.

.. figure::  /_static/images/Standalone.jpg

   A diagram of Izenda's standalone architecture.

BI Platform Implementation
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Requirements 
   
   - `API <http://downloads.izenda.com/latest/API.zip/>`_
   
   - `StandaloneUI <http://downloads.izenda.com/latest/StandaloneUI.zip>`_
   
   - An empty database
   
-  For installation steps, see the :doc:`/install/doc_installation_guide` and :doc:`/install/doc_upgrade_guide` for stand alone deployments.

.. figure::  /_static/images/intro/understanding_the_three-tiered_architecture/Slide1B.PNG

      A diagram of implementation

.. _Fully_Integrated_Deployment:


Deployment Mode 1: Back End Standalone, Front End Integrated
------------------------------------------------------------

*  The Back End Standalone Deployment syle features a seamless front end with a remote
   back end. This deployment is useful when you can devote a lightweight
   server to your integrated front end and a "meatier" server for all
   API calls which would include requesting queries from your reporting
   database(s).

MVC 5 BESA Implementation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Requirements:
   - API
   - Embedded UI
   - Empty database

- MVC Starter Kit Back End Standalone found `here <https://github.com/Izenda7Series/Mvc5StarterKit_BE_Standalone/>`_

.. figure::  /_static/images/intro/understanding_the_three-tiered_architecture/Slide2.PNG

      A diagram of implementation

Angular 2 Implementation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Requirements:
   - API
   - Embedded UI
   - Empty database
   - Angular 2 Starter Kit found `here <https://github.com/Izenda7Series/Angular2Starterkit/>`_


.. figure::  /_static/images/intro/understanding_the_three-tiered_architecture/Slide3.PNG
   
   A diagram of implementation
    
    
Deployment Mode 3: Fully Integrated
------------------------------------

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

MVC 5 Implementation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
- Requirements:
   - API
   - Embedded UI
   - Empty database
- MVC Starter Kit found `here <https://github.com/Izenda7Series/Mvc5StarterKit/>`_

.. figure::  /_static/images/intro/understanding_the_three-tiered_architecture/Slide4.PNG
   
   A diagram of implementation

Webforms Implementation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
- Requirements:
  - API
  - Embedded UI
  - Empty Database
- Webforms Starter Kit found `here <https://github.com/Izenda7Series/WebFormsStarterkit>`_ 


.. figure::  /_static/images/intro/understanding_the_three-tiered_architecture/Slide5.PNG
   
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
