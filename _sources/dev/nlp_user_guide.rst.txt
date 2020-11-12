.. _NLQ_User_Guide:

==========================
Natural Language Query
==========================

- NLQ Data Connectors
- Syntax guided NLP search query
- NLP suggestions
- Grid improvements
- Multitenancy support

NLQ Data Connectors 
---------------------
Natural language processing functionality can be leveraged against a single **MSSQL** or a single **PGSQL** data source.

	.. figure:: /_static/images/nlq_connectors.png
		  :align: center
		  :width: 1404px
	  
Syntax guided NLP search query
-------------------------------
The search follows a mandatory syntax with a set of rules to follow. The following list of comparison words and signs will be automatically recognized by Izenda’s NLP and suggestions will appear.

.. list-table:: Syntax guide for NLP search query
   :class: apitable
   :header-rows: 1

	* - Words/ Signs
	  - Avg
	  - Sum
	  - Maximum
	  - Count
	  - Distinct sum
	  - Distinct count
	  - =
	  - >
	  - <
	  - Between
	  - Group
	  - Like
	  - Is
	* - Syntax
	  - **Avg** [Column Name] of [Table Name]
	  - **Sum** [Column Name] of [Table Name]
	  - **Maximum** [Column Name] of [Table Name>
	  - **Count** [Column Name] of [Table Name]
	  - **Distinct sum** [Column Name] of [Table Name]
	  - **Distinct count** [Column Name] of [Table Name]
      - [Column Name] of [Table Name]  **for** [Column Name] **=** [Value]
	  - [Column Name] of [Table Name]  **for** [Column Name] **>** [Value]
	  - [Column Name] of [Table Name]  **for** [Column Name] **<** [Value]
	  - [Column Name] of [Table Name]  **for** [Column Name] **between** [Value] and [Value]
	  - [Column Name] of [Table Name] **by** [Column Name]
	  - [Column Name] of [Table Name] **for** [Column Name] **like** [String value]
	  - [Column Name] of [Table Name] **for** [Column Name] **is** [String value
    * - Example
	  - **Avg** freight of orders
	  - **Sum** discount of order details ,
	  - **Maximum** unit price of products for categoryid = 1
	  - **Count** ship country of orders
	  - **Distinct Sum** Freight of orders
	  - **Distinct count** customer id of orders
	  - Count ship country of orders **for** freight **=** 100
	  - Ship country of orders **for** freight **>** 10
	  - Ship country of orders **for** freight **<** 10
	  - Product name of products **for** unit price **between** 10 **and** 50
	  - Avg freight of orders **by** ship city
	  - Avg freight of orders **for** ship city **like** AM
	  - Avg freight of orders **for** ship city **is** Brazil

NLP Suggestions
---------------------
As user types into the search box, Izenda will provide a list of suggestions to choose from. This list will be populated by the system after analyzing the data in DB/schemas. Users will need to select from the query suggestions and press ENTER to populate results in step 2. 

Izenda will provide query assistance based on the following:

- **Synonyms:**  Izenda’s NLQ engine will save hours of your effort to add tags and keywords to column names. When you type a keyword which is not a part of the data model, the synonyms of the column names will be automatically recognized by Izenda’s model. The engine will pick the matching columns from the data model and help you build your query. 

	.. figure:: /_static/images/nlq_synonyms.gif
		  :align: center
		  :width: 1404px
|

- **Relationships:**  Izenda’s NLQ engine identifies relationships in the DB and intelligently suggests columns from the related data sources. When you type a keyword which matches a column in another table with which relationship exists, the engine will suggest and help you build your query.

	.. figure:: /_static/images/nlq_relationships.gif
		  :align: center
		  :width: 1404px
|

- **Column Values**:  Izenda’s NLQ engine indexes the data connectors and helps in suggesting column values. When you type keywords ‘IS’ or ‘LIKE’, the engine will auto-populate values to easily select from. 

	.. figure:: /_static/images/nlq_value_suggestion.gif
		  :align: center
		  :width: 1404px

Grid Features
---------------------
For users who are unfamiliar with the data model, Grid improvements have been introduced in NLP step 2. This functionality will help in identifying, sorting and managing data very quickly. The ‘Add Column’ rail on the right side displays all the available columns that can be added to the grid. You can also find all applicable functions, formats and sorting options in the grid dropdown itself. 

	.. figure:: /_static/images/nlq_grid_Enhancements.gif
		  :align: center
		  :width: 1404px

Multitenancy support
---------------------
Izenda now has Multi-tenant capability in NLQ. A single instance of NLQ license can be served to multiple tenants. With this feature, every tenant can now configure NLQ separately with its own share of the data, configuration, user management and functionality.


Limitations
---------------------
- All column names in the search query have to be separated by a **comma** (,) for more suggestions to populate
- Users will be required to select from query suggestions for grids to populate in Step 2
- Synonyms of the values of column names will not be recognized by the model
- Natural language processing functionality can be leveraged against only MSSQL or PGSQL configuration database

   