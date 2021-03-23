

=========================================
RolePagedRequest
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 60 10

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **roletId** |br|
         string (GUID)
      -  Y
      -  The id of the report if available
      -
   *  -  **userModeType** |br|
         integer
      -  
      -  The mode type |br|
         - 0 = All |br|
         - 1 = Access |br|
         - 2 = Schedule
      -
   *  -  **roleVirtualNode** |br|
         an array of object
      -  
      -  An array of :doc:`RoleVirtualNode` objects
      -


Inherited fields:

.. include:: PagedRequest.rst

.. container:: toggle

   .. container:: header

      **RolePagedRequest Sample**:

   .. code-block:: json

      {
         "roleId": "db8693f7-3d5a-41d7-a888-8a1dfaad31b4",
         "tenantId": null,
         "skipItems": 1,
         "pageSize": 6,
         "parentIds": ["5329b0cc-37a1-49c7-9271-a870a480db5c"],
         "criteria": [ { "key": "name", "value": "Anna" }]
      }

