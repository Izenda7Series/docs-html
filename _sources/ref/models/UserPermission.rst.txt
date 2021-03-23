

=========================================
UserPermission
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  Null
      -  Description
      -  Note
   *  -  **reportId** |br|
         string (GUID)
      -  Y
      -  The id of the report
      -
   *  -  **dashboardId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard
      -
   *  -  **assignedType** |br|
         integer
      -
      -  The assign type

         -  1 = Everyone
         -  2 = Role
         -  3 = User
      -
   *  -  **accessRightId** |br|
         string (GUID)
      -  Y
      -  The id of the access right
      -
   *  -  **accessRight** |br|
         string
      -
      -  The access right
      -
   *  -  **shareWith** |br|
         string
      -
      -  The name of the user or role or "Everyone"
      -
   *  -  **position** |br|
         integer
      -
      -  The position
      -
   *  -  **accessors** |br|
         array of strings (GUID)
      -
      -  The ids of users or roles
      -
   *  -  **accessorNames** |br|
         array of strings
      -
      -  Names of the accessors
      -
   *  -  **tempId** |br|
         string (GUID)
      -
      -  The temp id
      -
   *  -  **reportAccessRightId** |br|
         string (GUID)
      -  Y
      -  Id of the report access right
      -
   *  -  **reportAccessRights** |br|
         string
      -
      -  The report access right names
      -
   *  -  **dashboardAccessRightId** |br|
         string (GUID)
      -  Y
      -  Id of the dashboard access right
      -
   *  -  **dashboardAccessRights** |br|
         string
      -
      -  The dashboard access right names
      -
   *  -  **assignedTypeName** |br|
         string
      -
      -  The assign type name
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "reportId" : null,
         "dashboardId" : "89dca314-f66f-489d-a14c-117aa3ec875d",
         "assignedType" : 1,
         "accessRightId" : "13698ebf-3e8e-43e1-9e2b-ad3f17d7d008",
         "accessRight" : "View Only",
         "shareWith" : "Everyone",
         "position" : 0,
         "accessors" : [],
         "tempId" : null,
         "reportAccessRightId" : null,
         "reportAccessRights" : "",
         "dashboardAccessRightId" : null,
         "dashboardAccessRights" : "",
         "id" : "193c7f1b-5fcd-40ee-be09-0d7b96736115",
         "state" : 0,
         "deleted" : false,
         "inserted" : true,
         "version" : 1,
         "created" : "2016-10-18T07:24:41.387",
         "createdBy" : null,
         "modified" : "2016-10-18T07:24:41.387",
         "modifiedBy" : null
      }
