

DashboardParameter
---------------------

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **dashboard** |br|
         object
      -
      -  A :doc:`DashboardDefinition` object
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **section** |br|
         integer
      -
      - The dashboard section
      
         * 0 = All
         * 1 = Dashboard
         * 2 = Access
         * 3 = Subscription
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "dashboardId" : "a496ad94-fe92-48d5-a285-e45be738921f"
      }
