

===================
SecurityQuestion
===================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **question** |br|
         string
      -
      -  The question
      -
   *  -  **orderNumber** |br|
         integer
      -
      -  The order of the question
      -


Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "tenantId": null,
        "question": "What is the first and last name of your first boyfriend or girlfriend?",
        "orderNumber": 1,
        "id": "5784ece5-d2e7-42b1-89bb-859737b7b2a9",
        "state": 0,
        "deleted": false,
        "inserted": true,
        "version": 1,
        "created": null,
        "createdBy": null,
        "modified": null,
        "modifiedBy": null
      }
