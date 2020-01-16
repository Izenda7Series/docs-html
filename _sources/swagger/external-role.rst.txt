.. _External_Role:

============================
External Role
============================

.. _RoleExternal:

.. raw:: html
   :file: ./external-role.html


Permission and string value mapping
-----------------------------------

.. list-table::
   :header-rows: 1
   :widths: 30 40 30

   *  -  Permission
      -  String Value
      -  Note
   *  -  **Full Report And Dashboard Access**
      -  FullReportAndDashboardAccess
      -
   *  -  **System Configuration**
      -
      -
   *  -  .. container:: lpad2
   
            **Scheduled Instances**
      -  systemConfig.schedule
      - 
   *  -  **Tenant Setup**
      -
      -
   *  -  .. container:: lpad2
   
            **Actions**
      -
      -
   *  -  .. container:: lpad4
   
            **Create**
      -  tenantSetup.create
      -
   *  -  .. container:: lpad4
   
            **Edit**
      -  tenantSetup.edit
      -
   *  -  .. container:: lpad4
   
            **Delete**
      -  tenantSetup.delete
      -
   *  -  .. container:: lpad2
   
            **Permissions**
      -  tenantSetup.permissions
      -
   *  -  **Data Setup**
      -
      -
   *  -  .. container:: lpad2
   
            **Data Connectors**
      -  dataSetup.dataConnectors
      -
   *  -  .. container:: lpad2
   
            **Data Model**
      -  dataSetup.dataModel
      -
   *  -  .. container:: lpad4

            **customView**
      -
      -
   *  -  .. container:: lpad6

            **Create**
      -  dataSetup.dataModel.customView.create
      -
   *  -  .. container:: lpad6

            **Edit**
      -  dataSetup.dataModel.customView.edit
      -
   *  -  .. container:: lpad6

            **Delete**
      -  dataSetup.dataModel.customView.delete
      -
   *  -  .. container:: lpad2
   
            **Advanced Settings**
      - 
      -
   *  -  .. container:: lpad4
   
            **Category**
      -  dataSetup.advancedSettings.category
      -
   *  -  .. container:: lpad4
   
            **Others**
      -  dataSetup.advancedSettings.others
      -
   *  -  **User Setup**
      -
      -
   *  -  .. container:: lpad2
   
            **User Role Association**
      -  userSetup.userRoleAssociation
      -
   *  -  .. container:: lpad2
   
            **Actions**
      -
      -
   *  -  .. container:: lpad4
   
            **Create**
      -  userSetup.create
      -
   *  -  .. container:: lpad4
   
            **Edit**
      -  userSetup.edit
      -
   *  -  .. container:: lpad4
   
            **Delete**
      -  userSetup.delete
      -
   *  -  .. container:: lpad4
   
            **Configure Password Option**
      -  userSetup.configSercurity
      -
   *  -  **Role Setup**
      -
      -
   *  -  .. container:: lpad2
   
            **Actions**
      -
      -
   *  -  .. container:: lpad4
   
            **Create**
      -  roleSetup.create
      -
   *  -  .. container:: lpad4
   
            **Edit**
      -  roleSetup.edit
      -
   *  -  .. container:: lpad4
   
            **Delete**
      -  roleSetup.delete
      -
   *  -  .. container:: lpad2
   
            **Data Model Access**
      -  roleSetup.dataModelAccess
      -
   *  -  .. container:: lpad2
   
            **Permissions**
      -  roleSetup.Permissions
      -
   *  -  .. container:: lpad2
   
            **Grant Role with Full Report and Dashboard Access**
      -  roleSetup.grantRoleWithFullReportAndDashboardAccess
      -
   *  -  **Reports**
      -
      -
   *  -  .. container:: lpad2
   
            **Can create new report?**
      -  reports.create
      -
   *  -  .. container:: lpad2
   
            **Data Sources**
      -
      -
   *  -  .. container:: lpad4
   
            **Simple Data Sourcess**
      -  reports.dataSources.simple
      -  
   *  -  .. container:: lpad4
   
            **Advanced Data Sourcess**
      -  reports.dataSources.advanced
      -
   *  -  .. container:: lpad2
   
            **Report Part Types**
      -
      -
   *  -  .. container:: lpad4
   
            **Chart**
      -  reports.partTypes.chart
      -  
   *  -  .. container:: lpad4
   
            **Form**
      -  reports.partTypes.form
      -
   *  -  .. container:: lpad4
   
            **Gauge**
      -  reports.partTypes.gauge
      -  
   *  -  .. container:: lpad4
   
            **Map**
      -  reports.partTypes.map
      -
   *  -  .. container:: lpad2
   
            **Report Categories/Subcategories**
      -
      -
   *  -  .. container:: lpad4
   
            **Can create new category?**
      -  reports.categories.create
      -  
   *  -  .. container:: lpad4
   
            **Category Accessibility**
      -  reports.categoryAccess.visible.global[<Category Name 1>][<SubCate1>] |br|
         reports.categoryAccess.visible.local[<Category Name 1>][<SubCate1>] |br|
         reports.categoryAccess.savable.local[<Category Name 1>][<SubCate1>] |br|
      -  If Category name contains special charater (``"\" , "[" , "]"``), it must be follow after a ``"\"`` character
   *  -  .. container:: lpad4
   
            **Filter Properties**
      -  
      -  
   *  -  .. container:: lpad6
   
            **Filter Logic**
      -  reports.filter.logic
      -  
   *  -  .. container:: lpad6
   
            **Cross Filtering**
      -  reports.filter.crossFiltering
      -  
   *  -  .. container:: lpad4
   
            **Field Properties**
      -  
      -  
   *  -  .. container:: lpad6
   
            **Custom URL**
      -  reports.field.customURL
      -  
   *  -  .. container:: lpad6
   
            **Embedded Javascript**
      -  reports.field.embeddedJS
      -  
   *  -  .. container:: lpad6
   
            **Subreport**
      -  reports.field.subReport
      -  
   *  -  .. container:: lpad4
   
            **Actions**
      -  
      -  
   *  -  .. container:: lpad6
   
            **Schedule**
      -  reports.schedule
      -  
   *  -  .. container:: lpad6
   
            **Email**
      -  reports.email
      -  
   *  -  .. container:: lpad6
   
            **View Report History**
      -  reports.viewHistory
      -  
   *  -  .. container:: lpad6
   
            **Delete**
      -  reports.delete
      -  
   *  -  .. container:: lpad6
   
            **Register to alerts**
      -  reports.alert
      -  
   *  -  .. container:: lpad6
   
            **Print**
      -  reports.print
      -  
   *  -  .. container:: lpad6
   
            **Unarchive Report Versions**
      -  reports.unarchiveReportVersion
      -  
   *  -  .. container:: lpad6
   
            **Overwrite Existing Report**
      -  reports.overwrite
      -  
   *  -  .. container:: lpad6
   
            **Subscribe**
      -  reports.subscribe
      -  
   *  -  .. container:: lpad6
   
            **Export**
      -  reports.exporting
      -  
   *  -  .. container:: lpad6
   
            **Configure Access Rights**
      -  reports.accessRights
      -  
   *  -  **Dashboard**
      -
      -
   *  -  .. container:: lpad2
   
            **Can create new dashboard?**
      -  dashboards.create
      -
   *  -  .. container:: lpad2
   
            **Display tile header in uneditable dashboard**
      -  dashboards.displayTileHeader
      -
   *  -  .. container:: lpad2
   
            **Dashboard Categories/Subcategories**
      -
      -
   *  -  .. container:: lpad4
   
            **Can create new category?**
      -  dashboards.categories.create
      -  
   *  -  .. container:: lpad4
   
            **Category Accessibility**
      -  dashboards.categoryAccess.visible.global[<Category Name 1>][<SubCate1>] |br|
         dashboards.categoryAccess.visible.local[<Category Name 1>][<SubCate1>] |br|
         dashboards.categoryAccess.savable.local[<Category Name 1>][<SubCate1>] |br|
      -  If Category name contains special charater (``"\" , "[" , "]"``), it must be follow after a ``"\"`` character
   *  -  .. container:: lpad4
   
            **Actions**
      -  
      -  
   *  -  .. container:: lpad6
   
            **Schedule**
      -  dashboards.schedule
      -  
   *  -  .. container:: lpad6
   
            **Email**
      -  dashboards.email
      -  
   *  -  .. container:: lpad6
   
            **Delete**
      -  dashboards.delete
      -  
   *  -  .. container:: lpad6
   
            **Subscribe**
      -  dashboards.subscribe
      -  
   *  -  .. container:: lpad6
   
            **Print**
      -  dashboards.print
      -  
   *  -  .. container:: lpad6
   
            **Overwrite Existing Dashboard**
      -  dashboards.overwrite
      -  
   *  -  .. container:: lpad6
   
            **Configure Access Rights**
      -  dashboards.accessRights
      -  
   *  -  .. container:: lpad6
   
            **Export**
      -  dashboards.exporting
      -  
   *  -  **Access**
      -
      -
   *  -  .. container:: lpad2
   
            **Access Limits**
      -  accessLimits[<roleName>][<userName>]
      -  If roleName/Username contains special charater (``"\" , "[" , "]"``), it must be follow after a ``"\"`` character
   *  -  .. container:: lpad2
   
            **Access Defaults**
      -  accessDefaults.everyone.report.<accessRight>
         accessDefaults.<shareWith>.[<Rolename/userName>].report.<accessRight>
         accessDefaults.everyone.dashboard.<accessRight>
         accessDefaults.<shareWith>.[<Rolename/userName>].dashboard.<accessRight>
      -  If roleName/Username contains special charater (``"\" , "[" , "]"``), it must be follow after a ``"\"`` character
   *  -  **Scheduling**
      -
      -
   *  -  .. container:: lpad2
   
            **Scheduling Limits**
      -  schedulingLimits[<roleName>][<userName>]
      -  If roleName/Username contains special charater (``"\" , "[" , "]"``), it must be follow after a ``"\"`` character
   *  -  .. container:: lpad2
   
            **External Users**
      -  
      -  
   *  -  .. container:: lpad4
   
            **System Users**
      -  schedulingScope.systemUsers
      -  
   *  -  .. container:: lpad4
   
            **External Users**
      -  schedulingScope.externalUsers
      -  
   *  -  **Emailing**
      -
      -
   *  -  .. container:: lpad2
   
            **Delivery Method**
      -
      -
   *  -  .. container:: lpad4
   
            **Link**
      -  email.deliveryMethod.link
      -  
   *  -  .. container:: lpad4
   
            **Embedded HTML**
      - email.deliveryMethod.embedded
      -  
   *  -  .. container:: lpad4
   
            **Attachment**
      -  email.deliveryMethod.attachment
      -  
   *  -  .. container:: lpad2
   
            **Attachment Type**
      -  
      -  
   *  -  .. container:: lpad4
   
            **Word**
      -  email.attachmentType.word
      -  
   *  -  .. container:: lpad4
   
            **Excel**
      -  email.attachmentType.excel
      -  
   *  -  .. container:: lpad4
   
            **PDF**
      -  email.attachmentType.pdf
      -  
   *  -  .. container:: lpad4
   
            **CSV**
      -  email.attachmentType.csv
      -  
   *  -  .. container:: lpad4
   
            **XML**
      -  email.attachmentType.xml
      -  
   *  -  .. container:: lpad4
   
            **JSON**
      -  email.attachmentType.json
      -  
   *  -  .. container:: lpad4
   
            **Definition**
      -  email.attachmentType.definition
      -  
   *  -  **System-wide**
      -
      -
   *  -  .. container:: lpad2
   
            **Can see system messages?**
      -  canSeeSystemMessages
      -


