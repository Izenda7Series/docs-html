

=================
TimePeriod
=================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **name** |br|
         string
      -
      -  The name of the time period
      -
   *  -  **type** |br|
         string
      -
      -  Either "Long-term Period", "Fiscal Quarter", "Fiscal Year", "Calendar Quarter", "Calendar Year", "Calendar Month", "Calendar Week", or "Day"
      -
   *  -  **value** |br|
         string
      -
      -  The internal value of the time period
      -
   *  -  **isCustomFilter** |br|
         boolean
      -
      -  Whether this is user-defined filter
      -
   *  -  **customId** |br|
         string
      -
      -  The id of customed time period (using the name value by default)
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "name": "In the Future",
         "type": "Long-term Period",
         "value": "",
         "id": "b8ef8ad0-7a90-4f70-b3f3-52cbaf518335",
         "state": 0,
         "version": null,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
      }
