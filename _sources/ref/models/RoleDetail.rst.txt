
=================
RoleDetail
=================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **users** |br|
         array of objects
      -
      -  An array of :doc:`UserDetail` objects
      -
   *  -  **tenantUniqueName** |br|
         string
      -
      -  Used for integration only
      -
   *  -  **permission** |br|
         object
      -
      -  A :doc:`Permission` object
      -
   *  -  **visibleQuerySources** |br|
         array of objects
      -
      -  An array of :doc:`QuerySource` objects
      -

Inherited fields:

.. include:: Role.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "users": [],
         "permission": null,
         "visibleQuerySources": null,
         "name": "Analyst",
         "tenantId": null,
         "active": true,
         "deleted": false,
         "id": "0d030b1a-9568-4c98-8b1e-5dcc94dbd281",
         "state": 0,
         "inserted": true,
         "version": 1,
         "created": null,
         "createdBy": null,
         "modified": null,
         "modifiedBy": null
      }
