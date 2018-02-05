======================================
Data/Tenant Setup via the API
======================================



Adding a Connection String to the System Level
---------------------------------------------------------------
To add any connection string for reporting data, we will utilize the  `POST /api/connection <https://www.izenda.com/docs/ref/api_connection.html#post-connection>`__   endpoint.
The below sample request body adds a connection string to the system level:
This will emulate the same behavior as if you went to the Settings > Data Setup > Connection String page and input a connection string manually. Setting ‘selected’ to true will move the data sources from the Available Data Sources to the Visible Data Sources Column
			
		.. container:: toggle

			 .. container:: header

			 	**Sample**:
			
			 .. code-block:: json

				{
				   "id":null,
				   "name":"northwind",
				   "serverTypeId":"572bd576-8c92-4901-ab2a-b16e38144813",                       <-- This is the GUID of the database type (See Glossary)
				   "connectionString":"[YOUR CONNECTION STRING]",                               <-- This will be the connection string to the reporting database
				   "visible":true,                                                              <-- This value lets you set a connection as visible/non-visible
				   "dBSource":{
					  "querySources":[
						 {
							"id":null,
							"connectionId":null,
							"name":"dbo",                                                       <-- This is the name of the schema
							"querySources":[
							   {
								  "id":null,
								  "name":"Orders",
								  "type":"Table",
								  "selected":true,                                              <-- Selected will move the data source from Available to Visible if set to true
								  "physicalChange":0,                                           <-- Sets the physical state of the data source (See Glossary)
								  "approval":0,                                                 <-- Sets the approval value of the data source (See Glossary)
								  "categoryId":null                                             <-- The ID of a Category you have created for organizing data sources
							   },
							   {
								  "id":null,
								  "name":"GetContact",
								  "type":"Stored Procedure",
								  "selected":true,
								  "physicalChange":0,
								  "approval":0,
								  "categoryId":null
							   },
							   {
								  "id":null,
								  "name":"Invoices",
								  "type":"View",
								  "selected":true,
								  "physicalChange":0,
								  "approval":0,
								  "categoryId":null
							   }
							]
						 }
					  ]
				   },
				   "tenantId":null
				}





Updating an Existing Connection String
----------------------------------------------------
Updating an existing connection string is a two-part process. First, you need to make a call to  `POST api/connection/reloadRemoteSchema <https://www.izenda.com/docs/ref/api_connection.html#post-connection-reloadremoteschema>`__

The below sample request body adds a connection string to the system level:

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
					  "connectionId" : "E1DDD0AA-3074-41B2-AE5B-9E2262EB71B6",                      <-- This is the GUID found as under the Id column in the IzendaConnection table
					  "connectionString" : "PV/NvF4lI7zpTJx/U5VBPQqWJ3j3Bm1fHla2LRKUOMSNLDe9nul",   <-- This will be the encrypted connection string found in the IzendaConnection table 
					  "serverTypeId" : "572bd576-8c92-4901-ab2a-b16e38144813"                       <-- This is the GUID of the database type (See Glossary)
				}


The response body will contain the information you need in order to push an update to an existing connection. You can then re-use the POST /api/connection endpoint and update which data sources are selected, or which connection strings are set to visible/non-visible.
The below sample request body shows the update to the existing connection string.

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

					{
					   "id":null,
					   "name":"northwind",
					   "serverTypeId":"572bd576-8c92-4901-ab2a-b16e38144813",                       <-- This is the GUID of the database type (See Glossary)
					   "connectionString":"[YOUR CONNECTION STRING]",                               <-- This will be the connection string to the reporting database
					   "visible":true,                                                              <-- This value lets you set a connection as visible/non-visible
					   "dBSource":{
						  "querySources":[
							 {
								"id":null,
								"connectionId":null,
								"name":"dbo",                                                       <-- This is the name of the schema
								"querySources":[
								   {
									  "id":null,
									  "name":"Orders",
									  "type":"Table",
									  "selected":true,                                              <-- Selected will move the data source from Available to Visible if set to true
									  "physicalChange":0,                                           <-- Sets the physical state of the data source (See Glossary)
									  "approval":0,                                                 <-- Sets the approval value of the data source (See Glossary)
									  "categoryId":null                                             <-- The ID of a Category you have created for organizing data sources
								   },
								   {
									  "id":null,
									  "name":"GetContact",
									  "type":"Stored Procedure",
									  "selected":true,
									  "physicalChange":0,
									  "approval":0,
									  "categoryId":null
								   },
								   {
									  "id":null,
									  "name":"Invoices",
									  "type":"View",
									  "selected":true,
									  "physicalChange":0,
									  "approval":0,
									  "categoryId":null
								   }
								]
							 }
						  ]
					   },
					   "tenantId":null
					}

Configuring the Data Model
-------------------------------------
To update or modify the data model you will make a call to the `POST api/dataModel <https://www.izenda.com/docs/ref/api_data_model.html#id3>`__ endpoint.

When making these updates, please note that not every field is necessary to make a successful post. For more information on what all of these fields are and what they pertain to you can follow our Object Model documentation below:
	* `QuerySourceCategory <https://www.izenda.com/docs/ref/models/QuerySourceCategory.html>`__ 
	* `QuerySource  <https://www.izenda.com/docs/ref/models/QuerySource.html>`__  
	*  `QuerySourceField <https://www.izenda.com/docs/ref/models/QuerySourceField.html>`__   
The request body for this endpoint is comprised of an array of QuerySource objects and each of those contains an array of QuerySourceField objects. Essentially this translate to a list of data sources and the columns within each one.
The below sample request body is a simplified version that updates one table without altering it’s underlying fields:

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "tenantId":null,
				   "querySources":[
					  {
						 "realName":"Orders",
						 "id":"22D8B24C-F840-4779-8F14-53DDCB698D13",
						 "name":"dbo.Orders",
						 "type":"Table",
						 "categoryId":"ED2D2401-8408-44D8-822D-1982F8F0732E",
						 "connectionId":"E1DDD0AA-3074-41B2-AE5B-9E2262EB71B6",
						 "dataSourceCategoryName":null,                                         <-- This is where you can input an organizational category name (It does not have to exist)
						 "alias":null,                                                          <-- This is where you can specifiy an alias for the data source
						 "originalAlias":null,
						 "modified":"2017-07-18T19:40:13",                                      <-- This value is the timestamp of the change. This will always need to be incremented
						 "physicalChange":0,                                                    <-- This will note any chance in the data source (See Glossary)
						 "numOfCheckedChilds":0,
						 "extendedProperties":"{}",
						 "querySourceFields":[  ]
					  }
				   ]
				}

You can input values into the ‘alias’ values to alias these data source to use a more user-friendly name. You can also use the ‘dataSourceCategoryName’ value to assign a category to this data source to organize it along other data sources that may share similar trends or information.

The below sample is a more detailed request body updates the data model (note: not every field is necessary):

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "tenantId":null,
				   "querySources":[
					  {
						 "realName":"Orders",
						 "id":"22D8B24C-F840-4779-8F14-53DDCB698D13",
						 "name":"dbo.Orders",
						 "type":"Table",
						 "parentQuerySourceId":null,
						 "categoryId":"ED2D2401-8408-44D8-822D-1982F8F0732E",
						 "selected":false,
						 "deleted":false,
						 "connectionId":"E1DDD0AA-3074-41B2-AE5B-9E2262EB71B6",
						 "connectionName":"northwind",
						 "childs":null,
						 "dataSourceCategoryId":null,                                           <-- If an organizational category exists, you can add it by the GUID
						 "dataSourceCategoryName":null,                                         <-- This is where you can input an organizational category name (It does not have to exist)
						 "alias":null,                                                          <-- This is where you can specifiy an alias for the data source
						 "originalAlias":null,
						 "querySourceCategoryName":null,
						 "querySourceCategory":null,
						 "modified":"2017-08-14T14:30:33",                                      <-- This value is the timestamp of the change. This will always need to be incremented
						 "physicalChange":0,                                                    <-- This will note any chance in the data source (See Glossary)
						 "approval":0,
						 "existed":false,
						 "checked":false,
						 "belongToCopiedReport":false,
						 "viewDefinition":null,
						 "isCustomQuerySource":false,
						 "fullPath":null,
						 "indeterminate":false,
						 "numOfChilds":0,
						 "numOfCheckedChilds":0,
						 "isNewCategory":true,
						 "extendedProperties":"{}",
						 "querySourceFields":[                                                  <-- This will be an arry of QuerySourceField objects (you don't have to provide all fields)
							{
							   "name":"OrderID",
							   "alias":"",
							   "dataType":"int",
							   "izendaDataType":"Numeric",
							   "allowDistinct":true,
							   "visible":true,                                                  <-- This determines if a field will be available when building a report
							   "filterable":true,                                               <-- This determines if a user can filter on this field when building a report
							   "querySourceId":"22D8B24C-F840-4779-8F14-53DDCB698D13",
							   "parentId":null,
							   "expressionFields":[

							   ],
							   "type":0,
							   "groupPosition":0,
							   "position":1,
							   "extendedProperties":"{\"PrimaryKey\":true}",
							   "physicalChange":0,
							   "approval":0,
							   "existed":false,
							   "matchedTenant":false,
							   "functionName":null,
							   "expression":null,
							   "fullName":null,
							   "calculatedTree":null,
							   "reportId":null,
							   "originalName":null,
							   "originalId":"00000000-0000-0000-0000-000000000000",
							   "isParameter":false,
							   "isCalculated":false,
							   "hasAggregatedFunction":false,
							   "querySource":null,
							   "querySourceName":null,
							   "categoryName":null,
							   "inaccessible":false,
							   "originalAlias":null,
							   "fullPath":null,
							   "id":"593bb917-0c5d-4ebf-b589-894d1a7922f2",
							   "state":0,
							   "deleted":false,
							   "inserted":true,
							   "version":null,
							   "created":null,
							   "createdBy":"System Admin",
							   "modified":"2017-08-14T14:07:51.653",
							   "modifiedBy":null,
							   "filteredValue":"{}"
							}
						 ]
					  }
				   ]
				}


Adding Calculated Fields to the Data Model
----------------------------------------------------------
To add a calculated field to the data model you can utilize the *POST api/fusion/validateDataModelExpression* endpoint. In this you’ll be able to provide the expression you wish to add to a data source.
The below sample request body shows the initial request:

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "querySourceId":"91f9da8d-7c2b-4b5d-ae93-a77084295cf9",                      <-- This is the GUID for the data source where you're adding the calculation
				   "expression":"COUNT(DISTINCT([OrderID]))",                                   <-- This is the expression for your calculated field
				   "izendaDataType": "null"
				   "querySourceFieldId":null,
				   "tenantId":null
				}

If the above is successful, you may then use the POST api/fusion/calculatedFieldValue endpoint to push an updated version of the calculated field that contains the data type.
The below sample request body shows the updated request:

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "querySourceId":"91f9da8d-7c2b-4b5d-ae93-a77084295cf9",                      <-- This is the GUID for the data source where you're adding the calculation
				   "expression":"COUNT(DISTINCT([OrderID]))",                                   <-- This is the expression for your calculated field
				   "izendaDataType": "Numeric",                                                 <-- This is the data type you want the calculation to return
				   "querySourceFieldId":null,
				   "tenantId":null
				}

Once you have done the above, you will need to save the data model to commit the addition of the calculated field. You will use the same *POST api/dataModel* from before, but this time include your calculated field as a QuerySourceField value in the array.
The below sample request body is just the QuerySourceField value for the calculated field without the rest of the request body. You will need to add this to the prior request body under the appropriate datasource.

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
						 "querySourceFields":[
							{
							   "alias":"",
							   "visible":true,
							   "filterable":true,
							   "isCalculated":true,
							   "izendaDataType":"Numeric",                                      <-- This is the data type you would want for the calculated field
							   "name":"Test Calculated Field",                                  <-- This is the name you want for the calculated field
							   "expression":"COUNT(DISTINCT([OrderID]))",                       <-- This is the expression you wrote for the calculated field
							   "id":null,
							   "tempId":"32",
							   "state":1,
							   "position":17,
							   "filteredValue":"{}"
							}
						 ]
				}

Creating a New Tenant
-------------------------------
To add a new tenant into your environment you will utilize the `POST api/tenant  <https://www.izenda.com/docs/ref/api_tenant.html#id1>`__ endpoint.

The below sample request body shows the basic information for tenant creation. Note that this example does not contain values for the ‘permission’ and ‘permissionAccessModel’ arrays.

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "isDirty":true,
				   "tenantID":"001",                                                            <-- This is the Tenant ID value (This is not user-facing)
				   "name":"First Tenant",                                                       <-- This is the value users will use when logging in
				   "active":true,                                                               <-- Sets if a Tenant is in use or not
				   "tenantModules":[                                                            <-- Enables only the modules present in this array
					  "Alerting",
					  "Form",
					  "Dashboard",
					  "Report Templates",
					  "Scheduling",
					  "Exporting",
					  "Report Designer",
					  "Charting",
					  "Maps"
				   ],
				   "isSelected":false,
				   "permission":{  },                                                           <-- This will contain the permission object for the tenant
				   "version":0,
				   "permissionAccessModel":{  }                                                 <-- This will contains a list of access rights that can be set (See Glossary)
				}

To see what is involved in both condensed arrays, please see the Glossary for Permissions and Access Rights.

Adding a Connection String to a Tenant
----------------------------------------------------
To add a connection string to a newly created tenant you will reuse the *POST api/connection* endpoint.
The only difference between adding a connection string for a tenant and adding it at the system level is the ‘tenantId’ value in the JSON. Any time this value is set to null it references the system level. To push any request to a tenant, set the ‘tenantId’ value equal to the GUID for that tenant. This value can be found in the IzendaTenant table.
The below sample request body shows adding the same connection string we provided at the system level, but this time adjusted to be added to the tenant we just created.

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "id":null,
				   "name":"northwind",
				   "serverTypeId":"572bd576-8c92-4901-ab2a-b16e38144813",                       <-- This is the GUID of the database type (See Glossary)
				   "connectionString":"[YOUR CONNECTION STRING]",                               <-- This will be the connection string to the reporting database
				   "visible":true,                                                              <-- This value lets you set a connection as visible/non-visible
				   "dBSource":{
					  "querySources":[
						 {
							"id":null,
							"connectionId":null,
							"name":"dbo",                                                       <-- This is the name of the schema
							"querySources":[
							   {
								  "id":null,
								  "name":"Orders",
								  "type":"Table",
								  "selected":true,                                              <-- Selected will move the data source from Available to Visible if set to true
								  "physicalChange":0,                                           <-- Sets the physical state of the data source (See Glossary)
								  "approval":0,                                                 <-- Sets the approval value of the data source (See Glossary)
								  "categoryId":null                                             <-- The ID of a Category you have created for organizing data sources
							   },
							   {
								  "id":null,
								  "name":"GetContact",
								  "type":"Stored Procedure",
								  "selected":true,
								  "physicalChange":0,
								  "approval":0,
								  "categoryId":null
							   },
							   {
								  "id":null,
								  "name":"Invoices",
								  "type":"View",
								  "selected":true,
								  "physicalChange":0,
								  "approval":0,
								  "categoryId":null
							   }
							]
						 }
					  ]
				   },
				   "tenantId":null
				}

The Tenant’s GUID value on line 45 will add this connection information for the First Tenant we made with the api/tenant/ endpoint.

Creating/Updating the Tenant’s Data Model
----------------------------------------------------------
To update and alter the data model at a tenant level, it will follow the same process as the logic as the System level. The only difference, much like adding a connection string at the tenant level, is providing the tenantId value in the request body.
The Tenant’s GUID value on line 2 will update the data model in the tenant that corresponds with this GUID, which will be the First Tenant that we have previously created

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json
			 
				{
				   "isDirty":true,
				   "tenantID":"001",                                                            <-- This is the Tenant ID value (This is not user-facing)
				   "name":"First Tenant",                                                       <-- This is the value users will use when logging in
				   "active":true,                                                               <-- Sets if a Tenant is in use or not
				   "tenantModules":[                                                            <-- Enables only the modules present in this array
					  "Alerting",
					  "Form",
					  "Dashboard",
					  "Report Templates",
					  "Scheduling",
					  "Exporting",
					  "Report Designer",
					  "Charting",
					  "Maps"
				   ],
				   "isSelected":false,
				   "permission":{  },                                                           <-- This will contain the permission object for the tenant
				   "version":0,
				   "permissionAccessModel":{  }                                                 <-- This will contains a list of access rights that can be set (See Glossary)
				}



Creating Roles
--------------------
There are two endpoints that you can use to create a role via the API.
* For standalone environments, you will use `POST api/role  <https://www.izenda.com/docs/ref/api_role.html#id3>`__ 
* For integrated environments, you will use  `POST api/role/intergration/saveRole  <https://www.izenda.com/docs/ref/api_role.html#post-role-intergration-saverole>`__ 

Both endpoints will expect a `RoleDetail object  <https://www.izenda.com/docs/ref/models/RoleDetail.html>`__  as the request body.

The below sample request body creates a simple role in a standalone environment:

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "isDirty":true,
				   "users":[  ],                                                                <-- This is an array of UserDetail objects
				   "permission":{  },                                                           <-- This is a permission object (See Glossary)
				   "visibleQuerySources":[  ],                                                  <-- This is an array of all the QuerySources a role has access to
				   "name":"First Role",                                                         <-- This is the name you assign to the role
				   "tenantId":null,                                                             <-- This will create the role under a Tenant if the GUID is provided
				   "active":true,
				   "deleted":false,
				   "state":0,
				   "inserted":false,
				   "version":0,
				   "created":null,
				   "createdBy":null,
				   "modified":null,
				   "modifiedBy":null
				}

Note that this request does not contain the permission object. Please see the Glossary for more information on the permission components of these request bodies.

Setting Data Source Availability for Roles
------------------------------------------------------
To set specific data sources for a role, you can do this as part of the initial role creation, or as an update to an existing role. In either scenario, you will use the same endpoints as before. This means you will use either the *POST api/role* or *POST api/role/integration/saveRole* endpoints. This time, you will provide an array of QuerySource objects in the ‘visibleQuerySources’ portion of the request body.
The below sample request body creates a simple role in a standalone environment but grants access to the Orders table and every field within it. The contents of these are limited to just the GUIDs for each data source and the columns with in and you do not need to provide additional information.
During this process, you can control the data access a role has on a per-field basis, and you do not have to grant them access to an entire data source. In this example, we are only granting the ‘Second Role’ access to four fields from the Orders table.

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				{
				   "isDirty":true,
				   "users":[  ],
				   "permission":{  },
				   "visibleQuerySources":[
					  {
						 "id":"91f9da8d-7c2b-4b5d-ae93-a77084295cf9",                           <-- The GUID for the QuerySource
						 "querySourceFields":[
							{
							   "id":"793fcbcb-a22c-4dc5-a00f-cadc894fd569"                      <-- The GUID for the QuerySourceField
							},
							{
							   "id":"593bb917-0c5d-4ebf-b589-894d1a7922f2"
							},
							{
							   "id":"40c1594a-f751-4d0c-8aaf-11ee74d48c57"
							},
							{
							   "id":"c8de82f7-742a-4c13-88aa-5b35ea27f7bb"
							}
						 ]
					  }
				   ],
				   "name":"Second Role",
				   "tenantId":null,
				   "active":true,
				   "deleted":false,
				   "state":0,
				   "inserted":false,
				   "version":0,
				   "created":null,
				   "createdBy":null,
				   "modified":null,
				   "modifiedBy":null
				}


Glossary and Reference
-----------------------
*ServerTypeID* : The serverTypeId value refers to the underlying database type that you are attempting to connect to. This will refer to one of five possible values: 
	* *MSSQL* : “572bd576-8c92-4901-ab2a-b16e38144813” 
	* *MySQL* : “3d4916d1-5a41-4b94-874f-5bedacb89656” 
	* *Oracle* : “f2638ed5-70e5-47da-a052-4da0c1888fcf” 
	* *PGSQL* : “93942448-c715-4f98-85e2-9292ed7ca4bc” 
	* *AzureSQL* : “d968e96f-91dc-414d-9fd8-aef2926c9a18”

*PhysicalChange* : The physicalChange value in our API requests/responses can contain one of five possible values. These values pertain to the physical states of the values/objects being passed.
	* -1: Not Set
	* 0: None
	* 1: Added
	* 2: Modified
	* 3: Deleted

*Approval*
	* 0: No Pending Changes
	* 1: Pending Changes to the Object (added field/removed field/etc.)

Permission Objects
-------------------

*Tenant Permissions*

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				"permission":{
					 "isClickedSection":false,
					 "propsCloned":{
						"fullReportAndDashboardAccess":false,
						"systemConfiguration":{
						   "scheduledInstances":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"tenantSetup":{
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "tenantAccess":0
						   },
						   "permissions":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"dataSetup":{
						   "dataModel":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "advancedSettings":{
							  "category":false,
							  "others":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"userSetup":{
						   "userRoleAssociation":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "configureSecurityOptions":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"roleSetup":{
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "tenantAccess":0
						   },
						   "dataModelAccess":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "permissions":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "grantRoleWithFullReportAndDashboardAccess":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"reports":{
						   "canCreateNewReport":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "dataSources":{
							  "simpleDataSources":false,
							  "advancedDataSources":false,
							  "tenantAccess":0
						   },
						   "reportPartTypes":{
							  "chart":false,
							  "form":false,
							  "gauge":false,
							  "map":false,
							  "tenantAccess":0
						   },
						   "reportCategoriesSubcategories":{
							  "canCreateNewCategory":{
								 "value":false,
								 "tenantAccess":0
							  },
							  "categoryAccessibility":{
								 "categories":[

								 ],
								 "tenantAccess":0
							  }
						   },
						   "filterProperties":{
							  "filterLogic":false,
							  "crossFiltering":false,
							  "tenantAccess":0
						   },
						   "fieldProperties":{
							  "customURL":false,
							  "embeddedJavaScript":false,
							  "subreport":false,
							  "tenantAccess":0
						   },
						   "actions":{
							  "schedule":false,
							  "email":false,
							  "viewReportHistory":false,
							  "del":false,
							  "registerForAlerts":false,
							  "print":false,
							  "unarchiveReportVersions":false,
							  "overwriteExistingReport":false,
							  "subscribe":false,
							  "exporting":false,
							  "configureAccessRights":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"dashboards":{
						   "canCreateNewDashboard":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "dashboardCategoriesSubcategories":{
							  "canCreateNewCategory":{
								 "value":false,
								 "tenantAccess":0
							  },
							  "categoryAccessibility":{
								 "categories":[

								 ],
								 "tenantAccess":0
							  }
						   },
						   "actions":{
							  "schedule":false,
							  "email":false,
							  "del":false,
							  "subscribe":false,
							  "print":false,
							  "overwriteExistingDashboard":false,
							  "configureAccessRights":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"access":{
						   "accessLimits":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "accessDefaults":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"scheduling":{
						   "schedulingLimits":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "schedulingScope":{
							  "systemUsers":false,
							  "externalUsers":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"emailing":{
						   "deliveryMethod":{
							  "link":false,
							  "embeddedHTML":false,
							  "attachment":false,
							  "tenantAccess":0
						   },
						   "attachmentType":{
							  "word":false,
							  "excel":false,
							  "pdf":false,
							  "csv":false,
							  "xml":false,
							  "json":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"exporting":{
						   "exportingFormat":{
							  "word":false,
							  "excel":false,
							  "pdf":false,
							  "csv":false,
							  "xml":false,
							  "json":false,
							  "queryExecution":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"systemwide":{
						   "canSeeSystemMessages":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"section":null,
						"isTenantSetup":false
					 },
					 "isDirty":true,
					 "fullReportAndDashboardAccess":true,
					 "systemConfiguration":{
						"scheduledInstances":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "tenantSetup":{
						"actions":{
						   "create":false,
						   "edit":false,
						   "del":false,
						   "tenantAccess":1
						},
						"permissions":{
						   "value":false,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "dataSetup":{
						"dataModel":{
						   "value":true,
						   "tenantAccess":1
						},
						"advancedSettings":{
						   "category":true,
						   "others":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "userSetup":{
						"userRoleAssociation":{
						   "value":true,
						   "tenantAccess":1
						},
						"actions":{
						   "create":true,
						   "edit":true,
						   "del":true,
						   "configureSecurityOptions":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "roleSetup":{
						"actions":{
						   "create":true,
						   "edit":true,
						   "del":true,
						   "tenantAccess":1
						},
						"dataModelAccess":{
						   "value":true,
						   "tenantAccess":1
						},
						"permissions":{
						   "value":true,
						   "tenantAccess":1
						},
						"grantRoleWithFullReportAndDashboardAccess":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "reports":{
						"canCreateNewReport":{
						   "value":true,
						   "tenantAccess":1
						},
						"dataSources":{
						   "simpleDataSources":true,
						   "advancedDataSources":false,
						   "tenantAccess":1
						},
						"reportPartTypes":{
						   "chart":true,
						   "form":true,
						   "gauge":true,
						   "map":true,
						   "tenantAccess":1
						},
						"reportCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":true,
							  "tenantAccess":1
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":1
						   }
						},
						"filterProperties":{
						   "filterLogic":true,
						   "crossFiltering":true,
						   "tenantAccess":1
						},
						"fieldProperties":{
						   "customURL":true,
						   "embeddedJavaScript":true,
						   "subreport":true,
						   "tenantAccess":1
						},
						"actions":{
						   "schedule":true,
						   "email":true,
						   "viewReportHistory":true,
						   "del":true,
						   "registerForAlerts":true,
						   "print":true,
						   "unarchiveReportVersions":true,
						   "overwriteExistingReport":true,
						   "subscribe":true,
						   "exporting":true,
						   "configureAccessRights":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "dashboards":{
						"canCreateNewDashboard":{
						   "value":true,
						   "tenantAccess":1
						},
						"dashboardCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":true,
							  "tenantAccess":1
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":1
						   }
						},
						"actions":{
						   "schedule":true,
						   "email":true,
						   "del":true,
						   "subscribe":true,
						   "print":true,
						   "overwriteExistingDashboard":true,
						   "configureAccessRights":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "access":{
						"accessLimits":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"accessDefaults":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "scheduling":{
						"schedulingLimits":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"schedulingScope":{
						   "systemUsers":true,
						   "externalUsers":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "emailing":{
						"deliveryMethod":{
						   "link":true,
						   "embeddedHTML":true,
						   "attachment":true,
						   "tenantAccess":1
						},
						"attachmentType":{
						   "word":true,
						   "excel":true,
						   "pdf":true,
						   "csv":true,
						   "xml":true,
						   "json":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "exporting":{
						"exportingFormat":{
						   "word":true,
						   "excel":true,
						   "pdf":true,
						   "csv":true,
						   "xml":true,
						   "json":true,
						   "queryExecution":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "systemwide":{
						"canSeeSystemMessages":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "section":"systemConfiguration",
					 "isTenantSetup":false
				  }

*System Role Permissions*

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

				  "isClickedSection":false,
				  "propsCloned":{
					 "fullReportAndDashboardAccess":false,
					 "systemConfiguration":{
						"scheduledInstances":{
						   "value":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "tenantSetup":{
						"actions":{
						   "create":false,
						   "edit":false,
						   "del":false,
						   "tenantAccess":0
						},
						"permissions":{
						   "value":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "dataSetup":{
						"dataModel":{
						   "value":false,
						   "tenantAccess":0
						},
						"advancedSettings":{
						   "category":false,
						   "others":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "userSetup":{
						"userRoleAssociation":{
						   "value":false,
						   "tenantAccess":0
						},
						"actions":{
						   "create":false,
						   "edit":false,
						   "del":false,
						   "configureSecurityOptions":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "roleSetup":{
						"actions":{
						   "create":false,
						   "edit":false,
						   "del":false,
						   "tenantAccess":0
						},
						"dataModelAccess":{
						   "value":false,
						   "tenantAccess":0
						},
						"permissions":{
						   "value":false,
						   "tenantAccess":0
						},
						"grantRoleWithFullReportAndDashboardAccess":{
						   "value":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "reports":{
						"canCreateNewReport":{
						   "value":false,
						   "tenantAccess":0
						},
						"dataSources":{
						   "simpleDataSources":false,
						   "advancedDataSources":false,
						   "tenantAccess":0
						},
						"reportPartTypes":{
						   "chart":false,
						   "form":false,
						   "gauge":false,
						   "map":false,
						   "tenantAccess":0
						},
						"reportCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":0
						   }
						},
						"filterProperties":{
						   "filterLogic":false,
						   "crossFiltering":false,
						   "tenantAccess":0
						},
						"fieldProperties":{
						   "customURL":false,
						   "embeddedJavaScript":false,
						   "subreport":false,
						   "tenantAccess":0
						},
						"actions":{
						   "schedule":false,
						   "email":false,
						   "viewReportHistory":false,
						   "del":false,
						   "registerForAlerts":false,
						   "print":false,
						   "unarchiveReportVersions":false,
						   "overwriteExistingReport":false,
						   "subscribe":false,
						   "exporting":false,
						   "configureAccessRights":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "dashboards":{
						"canCreateNewDashboard":{
						   "value":false,
						   "tenantAccess":0
						},
						"dashboardCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":0
						   }
						},
						"actions":{
						   "schedule":false,
						   "email":false,
						   "del":false,
						   "subscribe":false,
						   "print":false,
						   "overwriteExistingDashboard":false,
						   "configureAccessRights":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "access":{
						"accessLimits":{
						   "value":[

						   ],
						   "tenantAccess":0
						},
						"accessDefaults":{
						   "value":[

						   ],
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "scheduling":{
						"schedulingLimits":{
						   "value":[

						   ],
						   "tenantAccess":0
						},
						"schedulingScope":{
						   "systemUsers":false,
						   "externalUsers":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "emailing":{
						"deliveryMethod":{
						   "link":false,
						   "embeddedHTML":false,
						   "attachment":false,
						   "tenantAccess":0
						},
						"attachmentType":{
						   "word":false,
						   "excel":false,
						   "pdf":false,
						   "csv":false,
						   "xml":false,
						   "json":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "exporting":{
						"exportingFormat":{
						   "word":false,
						   "excel":false,
						   "pdf":false,
						   "csv":false,
						   "xml":false,
						   "json":false,
						   "queryExecution":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "systemwide":{
						"canSeeSystemMessages":{
						   "value":false,
						   "tenantAccess":0
						},
						"tenantAccess":0
					 },
					 "section":null,
					 "isTenantSetup":false
				  },
				  "isDirty":true,
				  "fullReportAndDashboardAccess":true,
				  "systemConfiguration":{
					 "scheduledInstances":{
						"value":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "tenantSetup":{
					 "actions":{
						"create":true,
						"edit":true,
						"del":true,
						"tenantAccess":0
					 },
					 "permissions":{
						"value":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "dataSetup":{
					 "dataModel":{
						"value":true,
						"tenantAccess":0
					 },
					 "advancedSettings":{
						"category":true,
						"others":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "userSetup":{
					 "userRoleAssociation":{
						"value":true,
						"tenantAccess":0
					 },
					 "actions":{
						"create":true,
						"edit":true,
						"del":true,
						"configureSecurityOptions":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "roleSetup":{
					 "actions":{
						"create":true,
						"edit":true,
						"del":true,
						"tenantAccess":0
					 },
					 "dataModelAccess":{
						"value":true,
						"tenantAccess":0
					 },
					 "permissions":{
						"value":true,
						"tenantAccess":0
					 },
					 "grantRoleWithFullReportAndDashboardAccess":{
						"value":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "reports":{
					 "canCreateNewReport":{
						"value":true,
						"tenantAccess":0
					 },
					 "dataSources":{
						"simpleDataSources":false,
						"advancedDataSources":false,
						"tenantAccess":0
					 },
					 "reportPartTypes":{
						"chart":true,
						"form":true,
						"gauge":true,
						"map":true,
						"tenantAccess":0
					 },
					 "reportCategoriesSubcategories":{
						"canCreateNewCategory":{
						   "value":true,
						   "tenantAccess":0
						},
						"categoryAccessibility":{
						   "categories":[

						   ],
						   "tenantAccess":0
						}
					 },
					 "filterProperties":{
						"filterLogic":true,
						"crossFiltering":true,
						"tenantAccess":0
					 },
					 "fieldProperties":{
						"customURL":true,
						"embeddedJavaScript":true,
						"subreport":true,
						"tenantAccess":0
					 },
					 "actions":{
						"schedule":true,
						"email":true,
						"viewReportHistory":true,
						"del":true,
						"registerForAlerts":true,
						"print":true,
						"unarchiveReportVersions":true,
						"overwriteExistingReport":true,
						"subscribe":true,
						"exporting":true,
						"configureAccessRights":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "dashboards":{
					 "canCreateNewDashboard":{
						"value":true,
						"tenantAccess":0
					 },
					 "dashboardCategoriesSubcategories":{
						"canCreateNewCategory":{
						   "value":true,
						   "tenantAccess":0
						},
						"categoryAccessibility":{
						   "categories":[

						   ],
						   "tenantAccess":0
						}
					 },
					 "actions":{
						"schedule":true,
						"email":true,
						"del":true,
						"subscribe":true,
						"print":true,
						"overwriteExistingDashboard":true,
						"configureAccessRights":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "access":{
					 "accessLimits":{
						"value":[

						],
						"tenantAccess":0
					 },
					 "accessDefaults":{
						"value":[

						],
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "scheduling":{
					 "schedulingLimits":{
						"value":[

						],
						"tenantAccess":0
					 },
					 "schedulingScope":{
						"systemUsers":true,
						"externalUsers":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "emailing":{
					 "deliveryMethod":{
						"link":true,
						"embeddedHTML":true,
						"attachment":true,
						"tenantAccess":0
					 },
					 "attachmentType":{
						"word":true,
						"excel":true,
						"pdf":true,
						"csv":true,
						"xml":true,
						"json":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "exporting":{
					 "exportingFormat":{
						"word":true,
						"excel":true,
						"pdf":true,
						"csv":true,
						"xml":true,
						"json":true,
						"queryExecution":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "systemwide":{
					 "canSeeSystemMessages":{
						"value":true,
						"tenantAccess":0
					 },
					 "tenantAccess":0
				  },
				  "section":"systemConfiguration",
				  "isTenantSetup":false
			   }


*Tenant Role Permissions*

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json
			 
				"permission":{
					 "isClickedSection":false,
					 "propsCloned":{
						"fullReportAndDashboardAccess":false,
						"systemConfiguration":{
						   "scheduledInstances":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"tenantSetup":{
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "tenantAccess":0
						   },
						   "permissions":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"dataSetup":{
						   "dataModel":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "advancedSettings":{
							  "category":false,
							  "others":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"userSetup":{
						   "userRoleAssociation":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "configureSecurityOptions":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"roleSetup":{
						   "actions":{
							  "create":false,
							  "edit":false,
							  "del":false,
							  "tenantAccess":0
						   },
						   "dataModelAccess":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "permissions":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "grantRoleWithFullReportAndDashboardAccess":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"reports":{
						   "canCreateNewReport":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "dataSources":{
							  "simpleDataSources":false,
							  "advancedDataSources":false,
							  "tenantAccess":0
						   },
						   "reportPartTypes":{
							  "chart":false,
							  "form":false,
							  "gauge":false,
							  "map":false,
							  "tenantAccess":0
						   },
						   "reportCategoriesSubcategories":{
							  "canCreateNewCategory":{
								 "value":false,
								 "tenantAccess":0
							  },
							  "categoryAccessibility":{
								 "categories":[

								 ],
								 "tenantAccess":0
							  }
						   },
						   "filterProperties":{
							  "filterLogic":false,
							  "crossFiltering":false,
							  "tenantAccess":0
						   },
						   "fieldProperties":{
							  "customURL":false,
							  "embeddedJavaScript":false,
							  "subreport":false,
							  "tenantAccess":0
						   },
						   "actions":{
							  "schedule":false,
							  "email":false,
							  "viewReportHistory":false,
							  "del":false,
							  "registerForAlerts":false,
							  "print":false,
							  "unarchiveReportVersions":false,
							  "overwriteExistingReport":false,
							  "subscribe":false,
							  "exporting":false,
							  "configureAccessRights":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"dashboards":{
						   "canCreateNewDashboard":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "dashboardCategoriesSubcategories":{
							  "canCreateNewCategory":{
								 "value":false,
								 "tenantAccess":0
							  },
							  "categoryAccessibility":{
								 "categories":[

								 ],
								 "tenantAccess":0
							  }
						   },
						   "actions":{
							  "schedule":false,
							  "email":false,
							  "del":false,
							  "subscribe":false,
							  "print":false,
							  "overwriteExistingDashboard":false,
							  "configureAccessRights":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"access":{
						   "accessLimits":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "accessDefaults":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"scheduling":{
						   "schedulingLimits":{
							  "value":[

							  ],
							  "tenantAccess":0
						   },
						   "schedulingScope":{
							  "systemUsers":false,
							  "externalUsers":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"emailing":{
						   "deliveryMethod":{
							  "link":false,
							  "embeddedHTML":false,
							  "attachment":false,
							  "tenantAccess":0
						   },
						   "attachmentType":{
							  "word":false,
							  "excel":false,
							  "pdf":false,
							  "csv":false,
							  "xml":false,
							  "json":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"exporting":{
						   "exportingFormat":{
							  "word":false,
							  "excel":false,
							  "pdf":false,
							  "csv":false,
							  "xml":false,
							  "json":false,
							  "queryExecution":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"systemwide":{
						   "canSeeSystemMessages":{
							  "value":false,
							  "tenantAccess":0
						   },
						   "tenantAccess":0
						},
						"section":null,
						"isTenantSetup":false
					 },
					 "isDirty":true,
					 "fullReportAndDashboardAccess":true,
					 "systemConfiguration":{
						"scheduledInstances":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "tenantSetup":{
						"actions":{
						   "create":false,
						   "edit":false,
						   "del":false,
						   "tenantAccess":1
						},
						"permissions":{
						   "value":false,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "dataSetup":{
						"dataModel":{
						   "value":true,
						   "tenantAccess":1
						},
						"advancedSettings":{
						   "category":true,
						   "others":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "userSetup":{
						"userRoleAssociation":{
						   "value":true,
						   "tenantAccess":1
						},
						"actions":{
						   "create":true,
						   "edit":true,
						   "del":true,
						   "configureSecurityOptions":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "roleSetup":{
						"actions":{
						   "create":true,
						   "edit":true,
						   "del":true,
						   "tenantAccess":1
						},
						"dataModelAccess":{
						   "value":true,
						   "tenantAccess":1
						},
						"permissions":{
						   "value":true,
						   "tenantAccess":1
						},
						"grantRoleWithFullReportAndDashboardAccess":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "reports":{
						"canCreateNewReport":{
						   "value":true,
						   "tenantAccess":1
						},
						"dataSources":{
						   "simpleDataSources":true,
						   "advancedDataSources":false,
						   "tenantAccess":1
						},
						"reportPartTypes":{
						   "chart":true,
						   "form":true,
						   "gauge":true,
						   "map":true,
						   "tenantAccess":1
						},
						"reportCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":true,
							  "tenantAccess":1
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":1
						   }
						},
						"filterProperties":{
						   "filterLogic":true,
						   "crossFiltering":true,
						   "tenantAccess":1
						},
						"fieldProperties":{
						   "customURL":true,
						   "embeddedJavaScript":true,
						   "subreport":true,
						   "tenantAccess":1
						},
						"actions":{
						   "schedule":true,
						   "email":true,
						   "viewReportHistory":true,
						   "del":true,
						   "registerForAlerts":true,
						   "print":true,
						   "unarchiveReportVersions":true,
						   "overwriteExistingReport":true,
						   "subscribe":true,
						   "exporting":true,
						   "configureAccessRights":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "dashboards":{
						"canCreateNewDashboard":{
						   "value":true,
						   "tenantAccess":1
						},
						"dashboardCategoriesSubcategories":{
						   "canCreateNewCategory":{
							  "value":true,
							  "tenantAccess":1
						   },
						   "categoryAccessibility":{
							  "categories":[

							  ],
							  "tenantAccess":1
						   }
						},
						"actions":{
						   "schedule":true,
						   "email":true,
						   "del":true,
						   "subscribe":true,
						   "print":true,
						   "overwriteExistingDashboard":true,
						   "configureAccessRights":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "access":{
						"accessLimits":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"accessDefaults":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "scheduling":{
						"schedulingLimits":{
						   "value":[

						   ],
						   "tenantAccess":1
						},
						"schedulingScope":{
						   "systemUsers":true,
						   "externalUsers":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "emailing":{
						"deliveryMethod":{
						   "link":true,
						   "embeddedHTML":true,
						   "attachment":true,
						   "tenantAccess":1
						},
						"attachmentType":{
						   "word":true,
						   "excel":true,
						   "pdf":true,
						   "csv":true,
						   "xml":true,
						   "json":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "exporting":{
						"exportingFormat":{
						   "word":true,
						   "excel":true,
						   "pdf":true,
						   "csv":true,
						   "xml":true,
						   "json":true,
						   "queryExecution":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "systemwide":{
						"canSeeSystemMessages":{
						   "value":true,
						   "tenantAccess":1
						},
						"tenantAccess":1
					 },
					 "section":"systemConfiguration",
					 "isTenantSetup":false
				  }


*PermissionAccessModel*

This section of the tenant creation request body provides information on all of the access rights that can be set within the tenant on the its roles and dashboards. Detailed breakdowns of these values can be found here:
https://www.izenda.com/docs/ui/doc_report_designer_access.html

		.. container:: toggle

			 .. container:: header

			 	**Sample**:

			 .. code-block:: json

					{
						  "reportAccessRight":[
							 {
								"name":"Full Access",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d010",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"Locked",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d003",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"No Access",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d005",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"Quick Edit",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d001",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"Save As",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d002",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"View Only",
								"type":0,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d004",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 }
						  ],
						  "dashboardAccessRight":[
							 {
								"name":"Full Access",
								"type":1,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d011",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"Locked",
								"type":1,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d007",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"No Access",
								"type":1,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d009",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"Save As",
								"type":1,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d006",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 },
							 {
								"name":"View Only",
								"type":1,
								"id":"13698ebf-3e8e-43e1-9e2b-ad3f17d7d008",
								"state":0,
								"deleted":false,
								"inserted":true,
								"version":1,
								"created":null,
								"createdBy":null,
								"modified":null,
								"modifiedBy":null
							 }
						  ]
					   }
					}
