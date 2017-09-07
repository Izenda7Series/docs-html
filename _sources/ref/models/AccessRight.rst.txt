
==============
AccessRight
==============

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
      -  The name of the access right
      -
   *  -  **type** |br|
         integer
      -  Y
      -  The type of the access right
      
         * 0 = Report/Template
         * 1 = Dashboard
      -


Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
           "name" : "Full Access",
           "type" : 0,
           "id" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d010",
           "state" : 0,
           "deleted" : false,
           "inserted" : true,
           "version" : 1,
           "created" : null,
           "createdBy" : null,
           "modified" : null,
           "modifiedBy" : null
      }
