


Dashboard
----------

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
      -  The name of the dashboard
      -
   *  -  **description** |br|
         string
      -
      -  The description of the dashboard
      -
   *  -  **categoryId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard category
      -
   *  -  **categoryName** |br|
         string
      -
      -  The name of the dashboard category
      -
   *  -  **subCategoryId** |br|
         string (GUID)
      -  Y
      -  The id of the dashboard sub-category
      -
   *  -  **subCategoryName** |br|
         string
      -
      -  The name of the dashboard sub-category
      -
   *  -  **tenantId** |br|
         string (GUID)
      -  Y
      -  The id of the tenant if available
      -
   *  -  **imageUrl** |br|
         string
      -
      -  The url of the image
      -
   *  -  **stretchImage** |br|
         boolean
      -
      -  Is the image stretched
      -
   *  -  **backgroundColor** |br|
         string
      -
      -  The background color
      -
   *  -  **showFilterDescription** |br|
         boolean
      -
      -  Whether to show filter descriptions
      -
   *  -  **lastViewed** |br|
         datetime
      -  Y
      -  The last viewed date time
      -
   *  -  **owner** |br|
         string
      -
      -  The owner name
      -
   *  -  **ownerId** |br|
         string (GUID)
      -  Y
      -  The id of the owner
      -
   *  -  **createdById** |br|
         string (GUID)
      -  Y
      -  Id of user who created this dashboard
      -
   *  -  **modifiedById** |br|
         string (GUID)
      -  Y
      -  Id of user who last modified this dashboard
      -
   *  -  **checked** |br|
         boolean
      -
      -  Is selected for copy in Copy Management
      -
   *  -  **numberOfView** |br|
         integer
      -
      -  The number of view
      -
   *  -  **renderingTime** |br|
         real number
      -
      -  The rendering time
      -
   *  -  **sourceId** |br|
         string (GUID)
      -  Y
      -  The id of the source dashboard in case this dashboard has been copied
      -
   *  -  **isGlobal** |br|
         boolean
      -
      -  Whether this is global dashboard
      -
   *  -  **deletable** |br|
         boolean
      -
      -  Is deletable
      -
   *  -  **editable** |br|
         boolean
      -
      -  Is editable
      -
   *  -  **movable** |br|
         boolean
      -
      -  Is movable
      -
   *  -  **copyable** |br|
         boolean
      -
      -  Is copyable
      -
   *  -  **accessPriority** |br|
         integer
      -
      -  The access priority
      -
   *  -  **dashboardParts** |br|
         array of objects
      -
      -  An array of :doc:`DashboardPart` objects
      -
   *  -  **indeterminate** |br|
         boolean
      -
      -  Place-holder, returns false
      -

   *  -  **isCheck** |br|
         boolean
      -
      -  Whether this is selected
      -
   *  -  **displayDashboardTileHeader** |br|
         boolean
          .. versionadded:: 3.1.0
      -
      -  Whether display dashboard tile or not
      -
      
Inherited fields:

.. include:: Entity.rst
