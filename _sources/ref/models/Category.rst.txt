

==========================
Category
==========================

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
      -  The name of the category
      -
   *  -  **type** |br|
         string
      -
      -  The type of the category

         -  0 = Report
         -  1 = Template
         -  2 = Dashboard
         -  3 = Report/Template
      -
   *  -  **parentId** |br|
         string (GUID)
      -  Y
      -  The id of the parent category
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Whether this is a global category
      -
   *  -  **canDelete** |br|
         boolean
      -
      -  Can the category be deleted
      -
   *  -  **editable** |br|
         boolean
      -
      -  Can the category be edited
      -
   *  -  **savable** |br|
         boolean
      -
      -  Can the category be used to save reports or dashboards to
      -
   *  -  **subCategories** |br|
         array of objects
      -
      -  An array of child Category objects
      -
   *  -  **checked** |br|
         boolean
      -
      -  Is selected for copy in Copy Management
      -
   *  -  **reports** |br|
         array of objects
      -
      -  An array of child :doc:`Report` objects
      -
   *  -  **dashboards** |br|
         array of objects
      -
      -  An array of child :doc:`Dashboard` objects
      -
   *  -  **numOfChilds** |br|
         integer
      -
      -  The number of children
      -
   *  -  **numOfCheckedChilds** |br|
         integer
      -
      -  The number of selected children
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  *  true if 0 < numOfCheckedChilds < numOfChilds
         *  false if not
      -
   *  -  **status** |br|
         integer
      -
      -  The status

         - 0 = Empty
         - 1 = New
         - 2 = Exist
      -

Inherited fields:

.. include:: Entity.rst

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
        "name": "Uncategorized",
        "type": 2,
        "parentId": null,
        "tenantId": null,
        "canDelete": false,
        "editable": false,
        "savable": false,
        "subCategories": [],
        "checked": false,
        "reports": null,
        "dashboards": null,
        "id": null,
        "state": 0,
        "deleted": false,
        "inserted": true,
        "version": null,
        "created": null,
        "createdBy": "John Doe",
        "modified": null,
        "modifiedBy": null
      }
