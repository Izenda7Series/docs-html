

=========================================
CommonFilterField
=========================================

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
      -  The common name
      -
   *  -  **displayName** |br|
         string
      -
      -  The display name
      -
   *  -  **value** |br|
         string
      -
      -  The value
      -
   *  -  **operatorId** |br|
         string (GUID)
      -  Y
      -  The id of the operator
      -
   *  -  **operatorSetting** |br|
         string
      -
      -  The operator setting
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **position** |br|
         integer
      -
      -  The position in the list of filters
      -
   *  -  **cascading** |br|
         boolean
      -
      -  Whether common filter field will be cascaded
      -
   *  -  **sortType** |br|
         string
      -
      -  The sort type
      -
   *  -  **filterFields** |br|
         array of objects
      -
      -  An array of dynamic objects
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "name": "042a04a3-dfe1-4ef9-bd27-1b657886f02e-ShipCountry",
        "displayName": "ShipCountry",
        "value": "",
        "operatorId": "042a04a3-dfe1-4ef9-bd27-1b657886f02e",
        "operatorSetting": "",
        "dataType": null,
        "dashboardId": "70193a58-5752-48b7-bd0b-018a430087ec",
        "position": 1,
        "cascading": false,
        "sortType": null,
        "filterFields": [
          {
           "filterFieldId": "e5698682-3118-41ba-94e4-985955fc2f2f",
           "dashboardPartId": "00000000-0000-0000-0000-000000000000"
          },
          {
           "filterFieldId": "9baaf9a0-5e65-45c2-b8e5-1cdb8ad5a021",
           "dashboardPartId": "00000000-0000-0000-0000-000000000000"
          }
        ],
        "id": "32bf178c-eeac-473a-bc0e-3d4c4096bb13",
        "state": 0,
        "deleted": false,
        "inserted": true,
        "version": 1,
        "created": "2017-01-10T03:35:23.803",
        "createdBy": "John Doe",
        "modified": "2017-01-10T03:35:23.803",
        "modifiedBy": "John Doe"
      }
