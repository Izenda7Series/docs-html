==========================
Permissions Setup
==========================

.. contents:: Table of Contents
      :depth: 2

|br|

What are Permissions? 
--------------------------------
Permissions are how you grant functionality to users in your instance of Izenda. These include several areas like:

    - Controlling what types of report parts they can create
    - Setting who they can share their reports with
    - Determining if they can access and manipulate their tenant's data model

In a multi-tenant instance you can set permission at both the tenant and role level. In this scenario, the tenant will act like a ceiling for a role's permissions.

    - If a tenant object does not have access to a particular permission, then no roles within that tenant can have access to that permission
    - Tenant permissions will generally be inherited down into the role permissions when you are creating new roles within that tenant

----------------------------------------------------------------

.. Permissions_Overview:

Permissions Overview
--------------------------------
A permissions object is comprised of several areas

    .. container:: toggle

        .. container:: header 

                **System Configuration**

        * Scheduled Instances
            * This permission determines if a tenant/role has access to a master search dialogue to audit all scheduled/subscribed instances
                * The search dialogue is located in the Settings > System Configuration > Scheduling tab
                

    .. container:: toggle

        .. container:: header 

                **Data Setup**:

        * Data Model
            * This permission grants access for the tenant/role to edit and interact with the data model
                * Note that this permission is all or nothing. There is no way to limit if they can add relationships or not, alias data sources, etc.
            * Custom Views
                * Create
                    * This permission grants access for the tenant/role to create custom views within their data model
                * Edit
                    * This permission grants access for the tenant/role to edit any existing custom views within their data model
                * Delete
                    * This permission grants access for the tenant/role to delete any existing custom views within their data model
        * Advanced Settings
            * Category
                * This permission grants access to the Data Model > Advanced Settings > Category tab for the tenant/role
                    * This tab is used to create, edit, or delete any data source categories used in the data model
            * Others
                * This permission grants access to the Data Model > Advanced Settings > Others tab for the tenant/role
                    * This tab is used to set various behavior for the tenant such as sorting column names, determining common filter criteria for dashboards, etc.


    .. container:: toggle

        .. container:: header 

                **User Setup**:

        * Actions
            * Create
                * This permission grants access for the tenant/role to create new users
                    * NOTE: Users cannot be added through the UI in an integrated instance
            * Edit 
                * This permission grants access for the tenant/role to edit existing users
            * Delete
                * This permission grants access for the tenant/role to delete existing users
                    * NOTE: Users cannot be deleted through the UI in an integrated instance
            * Configure Password Option
                * This permission grants acces for the tenant/role to set up/reset passwords for new and existing users
        * User Role Association

    .. container:: toggle

        .. container:: header 

                **Role Setup**:

        * Actions
            * Create 
                * This permission grants access for the tenant/role to create new roles
            * Edit
                * This permission grants access for the tenant/role to edit existing roles
            * Delete 
                * This permission grants access for the tenant/role to delete existing roles
        * Data Model Access
            * This permission grants the tenant/role the ability to interact with a role's data model access on the Role Setup page
        * Permissions
            * This permission grants the tenant/role the ability to interact with a role's permission set on the Role Setup page
        * Grant Role with Full Report and Dashboard Access
            * This permission grants the tenant/role the ability to set the 'Full Report and Dashboard Access' permission in the Permission tab of the Role Setup page

    .. container:: toggle

        .. container:: header 

                **Reports**:

        * Can create new report?
            * This permission allows a tenant/role to create new reports
        * Data Sources
            * Simple Data Sources
                * This setting will prevent a user from seeing and editing joins on the Data Sources tab of the report designer
                    * NOTE: Roles with Simple Data Sources can only choose datasources with relationships between them that are defined in the data model. If a relationship does not exist between these data sources, they cannot choose those to build a report off of. 
                * This setting will also collapse the right-hand properties panel in the designer tab 
            * Advanced Data Sources
                * This setting will allow a user to edit and create joins in the Data Sources tab of the report designer
                * This setting will auto-expand the right-hand properties panel in the designer tab
        * Report Part Types 
            * Chart
                * This permission will allow a user to build Chart type report parts in the report designer
            * Form
                * This permission will allow a user to build Form type report parts in the report designer
            * Gauge
                * This permission will allow a user to build Gauge type report parts in the report designer
            * Maps
                * This permission will allow a user to build Map type report parts in the report designer
        * Report Categories/Subcategories
            * Can Create New Category?
                * This permission will determine if a user is able to type in a new category during the save/copy/move actions on a report
        * Filter Properties
            * Filter Logic 
                * This permission will determine if a user is able to create their own filter logic in the filter panel of the report designer
            * Cross Filtering
                * This permission will determine if a user is able to set cross filtering behavior in their report
        * Field Properties
            * Custom URL
                * This permission will determine if the Custom URL option is visible in the field properties panel of the report designer
            * Embedded Javascript
                * This permission will determine if the Embedded Javascript option is visible in the field properties panel of the report designer
            * Subreport
                * This permission will determine if the Subreport option is visible in the field properties panel of the report designer
        *Actions
            * Schedule
                * This permission will allow a user to create scheduled instances in the Schedule tab of of the report designer
            * Register to Alerts
                * This permission will allow a user to create alerted instances against a report
            * Subscribe
                * This permission will allow a user to create subscribed instances against reports they have access to
            * Configure Access Rights
                * This permission will allow a user to share the report by creating Access Rights in the Access tab of the report designer
            * Email
                * This permission will allow a user to email the contents of a report that they have access to 
            * Print
                * This permission will allow a user to print the contents of a report that they have access to
            * Export
                * This permission will allow a user to export the contents of a report to any file types they have access to
            * View Report History
                * This permission will allow a user to see the version history of a report on their report list
            * Unarchive Report Version
                * This permission will allow a user to unarchive older version of reports into their own report objects
            * Delete
                * This permission will allow a user to delete existing reports that they have sufficient access to
            * Overwrite Existing Report 
                * This permission will allow a user to overwrite existing reports that they have been given sufficient access to


    .. container:: toggle

        .. container:: header 

                **Dashboards**:

        * Can create new dashboard?
            * This permission allows a tenant/role to create new dashboards

        * Dashboard Categories/Subcategories
            * Can create new category?                
                * This permission will determine if a user is able to type in a new category during the save/copy/move actions on a dashboard

        *Actions    
            * Schedule
                * This permission will allow a user to create scheduled instances in the Schedule tab of of the dashboard designer
            * Subscribe
                * This permission will allow a user to create subscribed instances against dashboards they have access to
            * Configure Access Rights
                * This permission will allow a user to share the dashboard by creating Access Rights in the Access tab of the dashboard designer
            * Email
                * This permission will allow a user to email the contents of a dashboard that they have access to 
            * Print
                * This permission will allow a user to print the contents of a dashboard that they have access to
            * Export
                * This permission will allow a user to export the contents of a dashboard to any file types they have access to
            * Delete
                * This permission will allow a user to delete existing dashboards that they have sufficient access to 
            * Overwrite Existing Report
                * This permission will allow a user to overwrite existing dashboards that they have been given sufficient access to

    .. container:: toggle

        .. container:: header 

                **Access**:

        * Access Limits
            * Roles/Users allowed to share with
                * This dialogue will determine the list of roles and their users that a user can grant report level access to
        * Access Defaults
            * This dialogue will allow you to create default access rights that will get set on every report/dashboard members of this role create
            * NOTE: These are only default values applied. If that same user has Configure Access Rights set, they can remove these Defaults
                * These default values are also limited by what roles and users are set in the Access Limits portion above


    .. container:: toggle

        .. container:: header 

                **Scheduling**:

        * Scheduling Limits
            * Roles/Users allowed to share with
                * This dialogue will determine the list of roles and their users that can be added as valid recipients when e-mailing or scheduling a report/dashboard
        * Scheduling Scope
            * System Users
                * This permission will limit the valid recipients of an e-mail/schedule to only users in the system set in the above Scheduling Limits section
            * External Users
                * This permission will allow a user to manually enter an e-mail address as a valid recipient even if it does not match a user account in the system


    .. container:: toggle

        .. container:: header 

                **Emailing**:

        * Delivery Method
            * Link
                * This permission will allow a user to send a link to a report in the e-mail body
                * NOTE: This is a link to the viewer of the report, which means the recipient will have to be authorized by the system in order to access it.
            * Embedded HTML
                * This permission will allow a user to send the report contents embedded within the e-mail body
                * NOTE: The report content is generated from the account of the user sending the e-mail, not the user receiving the content
            * Attachment
                * This permission will allow a user to send the report contents in a file attached to the e-mail
                * NOTE: The report content is generated from the account of the user sending the e-mail, not the user receiving the content

        * Attachment Type 
            * Word
            * Excel
            * PDF
            * CSV
            * XML
            * JSON


    .. container:: toggle

        .. container:: header 

                **Exporting**:  

        * Exporting Format
            * Word
            * Excel
            * PDF
            * CSV
            * XML
            * JSON
            * Query Execution
          

    .. container:: toggle

        .. container:: header 

                **System-wide**:

        * Can see system messages?
            * This permission will determine if a tenant/role can see system wide messages that are otherwise only at the system level



----------------------------------------------------------------

Difference Between Tenant Permissions and Role Permissions
--------------------------------

Permissions can be set in two place: at the tenant level and at the role level. While a majority of the permission objects are the same, there are some difference between them.


    * Tenant Level Differences
        - Tenant Access Checkboxes
            * This column of checkboxes along the right-hand side of the permissions tab determines if these permission are visible during the Role Setup process
                * If Tenant Access is not set, then you will not see that permission during role setup, but the role will still inherit what is set behind the scenes
                * If Tenant Access is set, then you will see that permission during role seutp and can choose to remove that permission from that particular role
            * If this checkbox is set AND the corresponding permission is set, then you will be able to disable or enable this option on a per-role basis during role setup.

    * Role Level Differences
        - Full Report and Dashboard Access
            * This permission will make this role a reporting power user. They will be able to access every report and dahsboard regardless of this role's data access or Access Rights that are set on a report 
        - Report Category Accessibility
            * This dialogue will determine the visiblity/access this role has to the corresponding report category
            * It is dividied into three containers:
                * Available Categories
                    * This container will show all report categories that exist in the tenant
                * Visible Categories 
                    * This container will show any report categories that users in this role can see reports within
                * Categories Allowed for Saving Reports 
                    * This container will show any report categories that users in this role can save reports within
            * NOTE: This dialogue is changed automatically by the Access Rights that get set on certain reports
        - Dashboard Category Accessibility
            * This dialogue will determine the visiblity/access this role has to the corresponding report category. It is dividied into three containers:         
                * Available Categories
                    * This container will show all dashboard categories that exist in the tenant
                * Visible Categories 
                    * This container will show any report dashboard that users in this role can see reports within
                * Categories Allowed for Saving Reports 
                    * This container will show any report dashboard that users in this role can save reports within
            * NOTE: This dialogue is changed automatically by the Access Rights that get set on certain reports


----------------------------------------------------------------

Difference Between System Level Roles and Tenant Level Roles
--------------------------------

Roles can exist at both the system level and the tenant level. While a majority of both roles are the same, roles at the system level have a unique Tenant Setup category of their permissions object. 

    * Tenant Setup  
        * Actions
            * Create
                * This permission grants access for the role to create new tenants
            * Edit
                * This permission grants access for the role to edit existing tenants
            * Delete
                * This permission grants access for the role to delete existing tenants
        * Permissions
            * This permission will determine if this role has access to the Tenant Setup tab of the Settings page


----------------------------------------------------------------


Permission Settings that Impact UI Elements
--------------------------------

Some of the permissions, when not granted to a tenant/role, will cause some of Izenda's UI elements to not render on certain pages. Below are a list of the elements, by page, that can be configured by certain permissions

    .. container:: toggle

        .. container:: header 

                **Report List**:

        .. figure::  /_static/images/Permissions_Report_List_Elements.png
            :align: center
            :width: 1100px

        #. Report Tab +
            * This is controlled by the Report > Can Create New Report? permission
        #. Print Button
            * This is controlled by the Report > Actions > Print permission
        #. Export Dropdown
            * This is controlled by the Report > Actions > Export permission
                * Note that the dropdown options are controlled in the Exporting section of permissions
        #. Email Button
            * This is controlled by the Report > Actions > Email permission
        #. Subscribe Button
            * This is controlled by the Report > Actions > Subscribe permission
        #. Version Dialogue
            * This is controlled by the Report > Actions > View Report History permission


    .. container:: toggle

        .. container:: header 

                **Report Viewer**:

        .. figure::  /_static/images/Permissions_Report_Viewer_Elements.png
            :align: center
            :width: 1100px

        #. Subscribe Button
            * This is controlled by the Report > Actions > Subscribe permission
        #. Print Button
            * This is controlled by the Report > Actions > Print permission
        #. Email Button
            * This is controlled by the Report > Actions > Email permission
                * Note that the email dialogue is controlled in the Emailing section of permissions
        #. Export Button
            * This is controlled by the Report > Actions > Export permission
                * Note that the dropdown options are controlled in the Exporting section of permissions
        #. Edit Dropdown > View History Dialogue
            * This is controlled by the Report > Actions > View Report History permission


    .. container:: toggle

        .. container:: header 

                **Report Designer**: 

        .. figure::  /_static/images/Permissions_Report_Designer_Elements.png
            :align: center
            :width: 1100px

        #. Report Part Selection
            * The list of report parts a user can build is controlled by the Report > Report Part Types permissions
        #. Filter Logic
            * This is controlled by the Reports > Filter Properties > Filter Logic permission
        #. Cross Filtering
            * This is controlled by the Reports > Filter Properties > Cross Filtering permission
        #. Custom URL
            * This is controlled by the Reports > Field Properties > Custom URL permission
        #. Embedded Javascript
            * This is controlled by the Reports > Field Properties > Embedded Javascript permission            
        #. Subreports
            * This is controlled by the Reports > Field Properties > Subreport permission
        #. Scheduling Tab
            * This is controlled by the Report > Actions > Schedule permission
        #. Access Tab
            * This is controlled by the Report > Actions > Configure Access Rights permission
    
    .. container:: toggle

        .. container:: header 

                **Dashboard List**: 
                
        .. figure::  /_static/images/Permissions_Dashboard_List_Elements.png
            :align: center
            :width: 1100px

        #. Dashboard Tab +
            * This is controlled by the Report > Can Create New Dashboard? permission
        #. Print Button
            * This is controlled by the Report > Actions > Print permission
        #. Export Button
            * This is controlled by the Report > Actions > Export permission
        #. Email Button
            * This is controlled by the Report > Actions > Email permission
        #. Subscribe Button
            * This is controlled by the Report > Actions > Subscribe permission

    .. container:: toggle

        .. container:: header 

                **Dashboard Viewer/Designer**: 

        .. figure::  /_static/images/Permissions_Dashboard_ViewDesign_Elements.png
            :align: center
            :width: 1100px

        #. Access Button
            * This is controlled by the Report > Actions > Configure Access Rights permission
        #. Schedule Button
            This is controlled by the Report > Actions > Schedule permission
        #. Print Button
            * This is controlled by the Report > Actions > Print permission
        #. Export Button
            * This is controlled by the Report > Actions > Export permission
                * Note that the dropdown options are controlled in the Exporting section of permissions
        #. Email button
            * This is controlled by the Report > Actions > Email permission
                * Note that the email dialogue is controlled in the Emailing section of permissions

    .. container:: toggle

        .. container:: header 

                **Settings Page**: 
                
        .. container:: toggle

            .. container:: header 

                    **Data Setup**: 

            .. figure::  /_static/images/Permissions_Settings_DataSetup_Elements.png
                :align: center
                :width: 1100px

            #. Data Model Tab
                * This is controlled by the Data Setup > Data Model permission
            #. Advanced Settings Tab
                2a. Category Tab
                    * This is controlled by the Data Setup > Advanced Settings > Category permission
                2b. Others Tab
                    * This is controlled by the Data Setup > Advanced Settings > Others permissions

        .. container:: toggle

            .. container:: header 

                    **Role Setup**:

            .. figure::  /_static/images/Permissions_Settings_RoleSetup_Elements.png
                :align: center
                :width: 1100px

            #. Data Model Access Tab
                * This is controlled by the Role Setup > Data Model Access permission
            #. Permissions Tab
                * This is controlled by the Role Setup > Permissions permission
                2a. Grant Full Report and Dashboard Access Permission 
                    * This is controlled by the Role Setup > Grant Role with Full Report and Dashboard Access permission

        .. container:: toggle

            .. container:: header 

                    **User Setup**:

            .. figure::  /_static/images/Permissions_Settings_UserSetup_Elements.png
                :align: center
                :width: 1100px

            #. Configure Password Button
                * This is controlled by the User Setup > Actions > Configure Password Options permission
            #. User Role Association Dialogue
                * This is controlled by the User Setup > User Role Association Permission

        .. container:: toggle

            .. container:: header 

                    **System Configuration**: 
                    
            .. figure::  /_static/images/Permissions_Settings_SystemConfiguration_Elements.png
                :align: center
                :width: 1100px

            #. Scheduling Tab
                * This is configured by the System Configuration > Scheduled Instances permission
