=========================================================
ReactJS to manage data sources and data source fields
=========================================================

In this sample we will write a simplistic web page utilizing ReactJS to
manage data sources and data source fields in Data Model.

-  We focus on applying ReactJS for a parent-child data structure.
-  We will use the :ref:`POST_dataModel/loadQuerySources`, :ref:`POST_dataModel/loadQuerySourceFields` and :ref:`POST_dataModel` APIs.

Prerequisites
-------------

#. This sample continues from :doc:`code_react_manage_the_list_of_categories`.
#. This sample re-uses the folder structure created in :doc:`code_react_manage_the_list_of_categories`.
#. The uncompressed, development version of react.js and react-dom.js
   has been put into "ui\_react\_examples/vendor" folder. (They are in
   the starter kit available at
   https://facebook.github.io/react/downloads.html)

Thinking in React
-----------------

That is the name of a `ReactJS
guide <https://facebook.github.io/react/docs/thinking-in-react.html>`__
about building apps. In this sample we will follow the same process to
build the page to manage data sources and data source fields.

Start with a mock
-----------------

.. figure:: /_static/images/Data_Model_Tables_and_Views_Column_Grid.png

   Data Model - Data Source Grid and Column Grid

For simplicity in this sample, we will skip the search box, sorting
and paging controls.

The response from the API is detailed in :ref:`POST_dataModel/loadQuerySources` and :ref:`POST_dataModel/loadQuerySourceFields`.
Basically the ``response.result`` is an array of query sources, or query
source fields.

Break the UI into a component hierarchy
---------------------------------------

We will have a table of query sources, and a table of query source
fields that shows the content of the selected query source. In each row
in table of query sources, we have a select box to display and select
the category.

Following would be our component hierarchy:

-  App

   -  Table of QuerySourceItems

      -  Exactly one CategoryItem in each QuerySourceItem

   -  Table of QuerySourceFieldItems of the currently selected
      QuerySourceItem

Build a static version in React
-------------------------------

#. In "ui\_react\_examples" folder, create a blank text file and name it
   "ReactJS to manage data sources and data source fields.html".
#. Edit the file with a text editor such as Notepad or Notepad++ and
   paste the following HTML code:

.. comment: pygments code highlighting does not support React jsx yet

.. code-block:: text

   <!doctype html>
   <html>
    <head>
      <script src="vendor/react.js" type="text/javascript"></script>
      <script src="vendor/react-dom.js" type="text/javascript"></script>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js" type="text/javascript"></script>
    </head>
    <body>
      
      <section id="app"></section>
      
      <script type="text/babel">
   
        var categoryArray = [
         {id: '1', name: 'Category_1'},
         {id: '2', name: 'Category_2'},
         {id: '3', name: 'Category_3'},
         {id: '4', name: 'Category_4'}
        ];
   
        var querySourceArray = [
         {id: '10', name: 'dbo.Products', type: 'Table', selected: true, connectionName: 'Northwind', dataSourceCategoryId: 2, alias: null},
         {id: '20', name: 'dbo.Employees', type: 'Table', selected: true, connectionName: 'Northwind', dataSourceCategoryId: 2, alias: 'e'},
         {id: '30', name: 'dbo.Suppliers', type: 'Table', selected: false, connectionName: 'Northwind', dataSourceCategoryId: null, alias: null},
         {id: '40', name: 'dbo.Customers', type: 'Table', selected: true, connectionName: 'Northwind', dataSourceCategoryId: 1, alias: 'c'}
        ];
        
        var selectedQuerySourceId = '20';
        
        var querySourceFieldArray = [
         {id: '11', name: 'EmployeeID', dataType: 'int', alias: null, visible: true, filterable: true},
         {id: '12', name: 'FirstName', dataType: 'nvarchar', alias: 'FN', visible: true, filterable: true},
         {id: '13', name: 'LastName', dataType: 'nvarchar', alias: 'LN', visible: true, filterable: false},
         {id: '14', name: 'BirthDate', dataType: 'datetime', alias: 'DoB', visible: false, filterable: false}
        ];
   
        var App = React.createClass({
         render: function() {
            var selectedQuerySourceName = this.props.querySourceArray[0].name;
            return (
              <div>
                <button onClick={this.pushData}>Save</button>
                <p></p>
                <table style={{"border": "1px solid black"}}>
                  <thead>
                    <tr>
                      <th>Category</th>
                      <th>Database Name</th>
                      <th>Data Source Name</th>
                      <th>Data Source Alias</th>
                    </tr>
                  </thead>
                  <tbody>
                    {this.props.querySourceArray.map(function(result){
                      var color = (result.id==this.props.selectedQuerySourceId) ? "lightgrey" : "white";
                      return <QuerySourceItem key={result.id} color={color} querySource={result} categories={this.props.categoryArray} />;
                    }.bind(this))}
                  </tbody>
                </table>
                <p></p>
                <label>{selectedQuerySourceName}</label>
                <table style={{"border": "1px solid black"}}>
                  <thead>
                    <tr>
                      <th>Column Name</th>
                      <th>Data Type</th>
                      <th>Column Alias</th>
                      <th>Visible</th>
                      <th>Filterable</th>
                    </tr>
                  </thead>
                  <tbody>
                    {
                      this.props.querySourceFieldArray.map(function(result){
                        return <QuerySourceFieldItem key={result.id} querySourceField={result} />
                    })}
                  </tbody>
                </table>
              </div>
            )
         }
        });
   
        var QuerySourceItem = React.createClass({
         render: function() {
            return (
              <tr style={{backgroundColor: this.props.color}}>
                <td><CategoryItem selectedCategoryId={this.props.querySource.dataSourceCategoryId} categories={this.props.categories} /></td>
                <td>{this.props.querySource.connectionName}</td>
                <td>{this.props.querySource.name}</td>
                <td><input type="text" value={(this.props.querySource.alias==null)?"":this.props.querySource.alias} /></td>
              </tr>
            )
         }
        });
   
        var QuerySourceFieldItem = React.createClass({
         render: function() {
            return (
              <tr>
                <td>{this.props.querySourceField.name}</td>
                <td>{this.props.querySourceField.dataType}</td>
                <td><input type="text" value={(this.props.querySourceField.alias==null)?"":this.props.querySourceField.alias} /></td>
                <td><input type="checkbox" checked={this.props.querySourceField.visible} /></td>
                <td><input type="checkbox" checked={this.props.querySourceField.filterable} /></td>
              </tr>
            )
         }
        });
        
        var CategoryItem = React.createClass({
         render: function() {
            var options = this.props.categories.map(function(category) {
              return (
                <option key={category.id} value={category.id}>{category.name}</option>
              )
              
            });
            return (
              <select value={(this.props.selectedCategoryId==null)?"":this.props.selectedCategoryId}>
                <option value=""></option>
                {options}
              </select>
            )
         }
        });
   
        ReactDOM.render(<App querySourceArray={querySourceArray} selectedQuerySourceId={selectedQuerySourceId} querySourceFieldArray={querySourceFieldArray} categoryArray={categoryArray} />, document.getElementById('app'));
      </script>
    </body>
   </html>

Identify the minimal UI state
-----------------------------

The pieces of data in our application:

-  The API url
-  The array of data sources returned from the API
-  The array of categories returned from the API
-  The currently selected data source
-  The array of data source fields returned from the API

Our state would be all of the above data except for the API url, which
would be passed in via props.

.. code-block:: javascript

   ReactDOM.render(<App rootUrl={"http://127.0.0.1:8888/api/"} />, document.getElementById('app'));

Identify where the state should live
------------------------------------

The state should be in the root App since all other components only need
a part of that state.

Now we can implement getInitialState, componentDidMount and fetchData
methods inside the root App.

.. code-block:: javascript

   getInitialState: function() {
      return {
        querySourceArray: new Array(),
        querySourceFieldArray: new Array(),
        selectedQuerySourceId: null,
        categoryArray: new Array()
        };
   },
   componentDidMount: function() {
      this.fetchData();
   },
   fetchData: function() {
      this.fetchCategories();
      this.fetchQuerySources().success(this.fetchQuerySourceFields());
   },
   fetchCategories: function() {
      return $.ajax({
        url: this.props.rootUrl + "advancedSetting/category/",
        type: "GET",
        contentType: "application/json",
        success: function(response) {
          this.setState({
            categoryArray: response
          });
        }.bind(this),
        error: function(response) {
          console.log(JSON.stringify(response));
        }
      });
   },
   fetchQuerySources: function() {
      var postData = {querySourceType: "Table", criteria: [{key: "All", "value":"", "operation":1}], pageIndex: 1, pageSize: 10, sortOrders: []};
      return $.ajax({
        url: this.props.rootUrl + "dataModel/loadQuerySources/",
        type: "POST",
        data: JSON.stringify(postData),
        contentType: "application/json",
        success: function(response) {
          this.setState({
            querySourceArray: response.result,
            selectedQuerySourceId: (response.result.length > 0) ? response.result[0].id : null
          });
        }.bind(this),
        error: function(response) {
          console.log(JSON.stringify(response));
        }
      });
   },
   fetchQuerySourceFields: function() {
      var postData = {querySource: {id: this.state.selectedQuerySourceId, type: "Table"}, criteria: [], pageIndex: 1, pageSize: 10, sortOrders: []};
      return $.ajax({
        url: this.props.rootUrl + "dataModel/loadQuerySourceFields/",
        type: "POST",
        data: JSON.stringify(postData),
        contentType: "application/json",
        success: function(response) {
          this.setState({
            querySourceFieldArray: response.result
          });
        }.bind(this),
        error: function(response) {
          console.log(JSON.stringify(response));
        }
      });
   }

In this fetchData method we need to get the list of categories, the list
of query sources, then sequently the list of query source fields for the
selected/first query source. Since ajax calls are asynchronous, we need
to queue the second call in success method of the first call
``this.fetchQuerySources().success(this.fetchQuerySourceFields());``
(see "success" section in http://api.jquery.com/jquery.ajax/).

Add inverse data flow
---------------------

We need to handle the following events:

-  A QuerySourceItem is selected: to fetch the corresponding list of
   query source fields, then update the state.
-  A CategoryItem inside a QuerySourceItem is selected: to update the
   dataSourceCategoryId property for that QuerySourceItem in the state.
-  An alias input inside a QuerySourceItem is updated: to update the
   alias property for that QuerySourceItem in the state.
-  An alias input inside a QuerySourceFieldItem is updated: to update
   the alias property for that QuerySourceFieldItem in the state.
-  A visible checkbox inside a QuerySourceItem is updated: to update the
   visible property for that QuerySourceItem in the state.
-  A filterable checkbox inside a QuerySourceItem is updated: to update
   the filterable property for that QuerySourceItem in the state.

All these events need to be passed to the root App for processing, via
callbacks.

reflectSelectedQuerySource
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

     // in App
     return <QuerySourceItem .. reflectSelectedQuerySource={this.reflectSelectedQuerySource} />;
     // .. in QuerySourceItem
     <tr style={{backgroundColor: this.props.color}} onClick={this.reflectSelectedQuerySource}>
     // .. in QuerySourceItem
     reflectSelectedQuerySource: function() {
       this.props.reflectSelectedQuerySource(this.props.querySource.id);
     }
     // .. in App
     reflectSelectedQuerySource: function(querySourceId) {
       if (querySourceId != this.state.selectedQuerySourceId) {
         this.setState(
           {selectedQuerySourceId: querySourceId},
           this.fetchQuerySourceFields
         );
       }
     }

.. note::

   fetchQuerySourceFields needs to use the result of selectedQuerySourceId in the asynchronous setState method. That is why we need to queue fetchQuerySourceFields in callback of setState ``this.setState({selectedQuerySourceId: querySourceId}, this.fetchQuerySourceFields);`` |br|
   (see "setState" section in https://facebook.github.io/react/docs/component-api.html).

reflectChangedCategory
~~~~~~~~~~~~~~~~~~~~~~

.. comment: pygments code highlighting does not support React jsx yet

.. code-block:: text

     // in App
     return <QuerySourceItem .. reflectChangedCategory={this.reflectChangedCategory} />;
     // .. in QuerySourceItem
     <td><CategoryItem .. reflectChangedCategory={this.reflectChangedCategory} /></td>
     // .. in CategoryItem
     <select .. onChange={this.reflectChangedCategory} >
     // .. in CategoryItem
     reflectChangedCategory: function(event) {
       this.props.reflectChangedCategory(event.target.value);          
     }
     // .. in QuerySourceItem
     reflectChangedCategory: function(selectedCategoryId) {
       this.props.reflectChangedCategory(this.props.querySource.id, selectedCategoryId);
     }
     // .. in App
     reflectChangedCategory: function(querySourceId, selectedCategoryId) {
       var querySources = this.state.querySourceArray;
       var querySourcePos = querySources.map(function(x){return x.id;}).indexOf(querySourceId);
       querySources[querySourcePos].dataSourceCategoryId = selectedCategoryId;
       this.setState({
         querySourceArray: querySources
       });
     }

reflectChangedQuerySourceAlias
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. comment: pygments code highlighting does not support React jsx yet

.. code-block:: text

     // in App
     return <QuerySourceItem .. reflectChangedAlias={this.reflectChangedQuerySourceAlias} />;
     // .. in QuerySourceItem
     <td><input .. onChange={this.reflectChangedAlias} /></td>
     // .. in QuerySourceItem
     reflectChangedAlias: function(event) {
       this.props.reflectChangedAlias(this.props.querySource.id, event.target.value);
     }
     // .. in App
     reflectChangedQuerySourceAlias: function(querySourceId, alias) {
       var querySources = this.state.querySourceArray;
       var querySourcePos = querySources.map(function(x){return x.id;}).indexOf(querySourceId);
       querySources[querySourcePos].alias = alias;
       this.setState({
         querySourceArray: querySources
       });
     }

reflectChangedQuerySourceFieldAlias
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. comment: pygments code highlighting does not support React jsx yet

.. code-block:: text

     // in App
     return <QuerySourceFieldItem .. reflectChangedAlias={this.reflectChangedQuerySourceFieldAlias} />;
     // .. in QuerySourceFieldItem
     <td><input .. onChange={this.reflectChangedAlias} /></td>
     // .. in QuerySourceFieldItem
     reflectChangedAlias: function(event) {
       this.props.reflectChangedAlias(this.props.querySourceField.id, event.target.value);
     }
     // .. in App
     reflectChangedQuerySourceFieldAlias: function(querySourceFieldId, alias) {
       var querySourceFields = this.state.querySourceFieldArray;
       var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
       querySourceFields[querySourceFieldPos].alias = alias;
       this.setState({
         querySourceFieldArray: querySourceFields
       });
     }

reflectVisibleField and reflectFilterableField
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: javascript

     // in App
     return <QuerySourceFieldItem .. reflectVisibleField={this.reflectVisibleField} />
     // .. in QuerySourceFieldItem
     <input type="checkbox" checked={this.props.querySourceField.visible} onChange={this.reflectVisibleField} />
     // .. in QuerySourceFieldItem
     reflectVisibleField: function() {
       this.props.reflectVisibleField(this.props.querySourceField.id);
     }
     // .. in App
     reflectVisibleField: function(querySourceFieldId) {
       var querySourceFields = this.state.querySourceFieldArray;
       var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
       querySourceFields[querySourceFieldPos].visible = !querySourceFields[querySourceFieldPos].visible;
       this.setState({
         querySourceFieldArray: querySourceFields
       });
     }

We use similar code for reflectFilterableField.

Implement pushData
------------------

The API for saving is :ref:`POST_dataModel`.
It saves an array of query sources, each with an optional array of query
source fields.

We will try to save only items that have been changed since page load or
last save. These include an array of changed query sources in the data
source grid and a single querySourceId if any changes in the column grid
(they are plain object properties, neither state nor props).

.. code-block:: javascript

   componentDidMount: function() {
      this.fetchData();
      this.changedQuerySources = new Array();
      this.querySourceWithChangedQuerySourceFields = null;
   }

Each time we handle a change event in a component, we will log that id
for later processing.

.. code-block:: javascript

   reflectChangedCategory: function(querySourceId, selectedCategoryId) {
      ..
      this.registerChangedQuerySource(querySourceId);
   },
   reflectChangedQuerySourceAlias: function(querySourceId, alias) {
      ..
      this.registerChangedQuerySource(querySourceId);
   },
   registerChangedQuerySource: function(querySourceId) {
      this.changedQuerySources.push(querySourceId);
   },
   reflectChangedQuerySourceFieldAlias: function(querySourceFieldId, alias) {
      ..
      this.registerChangedQuerySourceField(querySourceFieldId);
   },
   reflectVisibleField: function(querySourceFieldId) {
      ..
      this.registerChangedQuerySourceField(querySourceFieldId);
   },
   reflectFilterableField: function(querySourceFieldId) {
      ..
      this.registerChangedQuerySourceField(querySourceFieldId);
   },
   registerChangedQuerySourceField: function(querySourceFieldId) {
      var querySourceFields = this.state.querySourceFieldArray;
      var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
      this.querySourceWithChangedQuerySourceFields = querySourceFields[querySourceFieldPos].querySourceId;
   }

In pushData method we will extract a unique array of changed query
sources, compose the post data then call the API.

.. code-block:: javascript

   function uniqueOnly(value, index, self) {
     return self.indexOf(value) === index;
   }
   
   var allChangedQuerySources = (this.querySourceWithChangedQuerySourceFields!=null)
     ? this.changedQuerySources.concat(this.querySourceWithChangedQuerySourceFields)
     : this.changedQuerySources;
   var uniqueChangedQuerySources = allChangedQuerySources.filter(uniqueOnly);
   
   postData.querySources = this.state.querySourceArray.filter(function(querySource){
     return uniqueChangedQuerySources.indexOf(querySource.id) >= 0;
   });
   
   if (this.querySourceWithChangedQuerySourceFields!=null) {
     var querySourceWithChangedQuerySourceFieldsPos = postData.querySources.map(function(x){return x.id;}).indexOf(this.querySourceWithChangedQuerySourceFields);
     postData.querySources[querySourceWithChangedQuerySourceFieldsPos].querySourceFields = this.state.querySourceFieldArray;
   }

Summary
-------

In this sample, we followed the recommended ReactJS design approach to
manage data sources and data source fields.



.. container:: toggle

      .. container:: header

         Full source code in this sample:

      .. comment: pygments code highlighting does not support React jsx yet

      .. code-block:: text

         <!doctype html>
         <html>
          <head>
            <script src="vendor/jquery-1.12.2.js" type="text/javascript"></script>
            <script src="vendor/react.js" type="text/javascript"></script>
            <script src="vendor/react-dom.js" type="text/javascript"></script>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js" type="text/javascript"></script>
          </head>
          <body>
            
            <section id="app"></section>
            
            <script type="text/babel">
         
              var App = React.createClass({
               render: function() {
                  var selectedQuerySourceName = (this.state.querySourceArray.length > 0)
                    ? this.state.querySourceArray[this.state.querySourceArray.map(function(x){return x.id;}).indexOf(this.state.selectedQuerySourceId)].name
                    : '';
                  return (
                    <div>
                      <button onClick={this.pushData}>Save</button>
                      <p></p>
                      <table style={{"border": "1px solid black"}}>
                        <thead>
                          <tr>
                            <th>Category</th>
                            <th>Database Name</th>
                            <th>Data Source Name</th>
                            <th>Data Source Alias</th>
                          </tr>
                        </thead>
                        <tbody>
                          {this.state.querySourceArray.map(function(querySource){
                            var color = (querySource.id==this.state.selectedQuerySourceId) ? "lightgrey" : "white";
                            return <QuerySourceItem key={querySource.id} color={color} querySource={querySource} categories={this.state.categoryArray} reflectSelectedQuerySource={this.reflectSelectedQuerySource} reflectChangedCategory={this.reflectChangedCategory} reflectChangedAlias={this.reflectChangedQuerySourceAlias} />;
                          }.bind(this))}
                        </tbody>
                      </table>
                      <p></p>
                      <label>{selectedQuerySourceName}</label>
                      <table style={{"border": "1px solid black"}}>
                        <thead>
                          <tr>
                            <th>Column Name</th>
                            <th>Data Type</th>
                            <th>Column Alias</th>
                            <th>Visible</th>
                            <th>Filterable</th>
                          </tr>
                        </thead>
                        <tbody>
                          {this.state.querySourceFieldArray.map(function(querySourceField){
                              return <QuerySourceFieldItem key={querySourceField.id} querySourceField={querySourceField} reflectChangedAlias={this.reflectChangedQuerySourceFieldAlias} reflectVisibleField={this.reflectVisibleField} reflectFilterableField={this.reflectFilterableField} />
                          }.bind(this))}
                        </tbody>
                      </table>
                    </div>
                  )
               },
               getInitialState: function() {
                  return {
                    querySourceArray: new Array(),
                    querySourceFieldArray: new Array(),
                    selectedQuerySourceId: null,
                    categoryArray: new Array()
                    };
               },        
               componentDidMount: function() {
                  this.fetchData();
                  this.changedQuerySources = new Array();
                  this.querySourceWithChangedQuerySourceFields = null;
               },
               fetchData: function() {
                  this.fetchCategories();
                  this.fetchQuerySources().success(this.fetchQuerySourceFields());
               },
               fetchCategories: function() {
                  return $.ajax({
                    url: this.props.rootUrl + "advancedSetting/category/",
                    type: "GET",
                    contentType: "application/json",
                    success: function(response) {
                      this.setState({
                        categoryArray: response
                      });
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  });
               },
               fetchQuerySources: function() {
                  var postData = {querySourceType: "Table", criteria: [{key: "All", "value":"", "operation":1}], pageIndex: 1, pageSize: 10, sortOrders: []};
                  return $.ajax({
                    url: this.props.rootUrl + "dataModel/loadQuerySources/",
                    type: "POST",
                    data: JSON.stringify(postData),
                    contentType: "application/json",
                    success: function(response) {
                      this.setState({
                        querySourceArray: response.result,
                        selectedQuerySourceId: (response.result.length > 0) ? response.result[0].id : null
                      });
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  });
               },
               fetchQuerySourceFields: function() {
                  var postData = {querySource: {id: this.state.selectedQuerySourceId, type: "Table"}, criteria: [], pageIndex: 1, pageSize: 10, sortOrders: []};
                  return $.ajax({
                    url: this.props.rootUrl + "dataModel/loadQuerySourceFields/",
                    type: "POST",
                    data: JSON.stringify(postData),
                    contentType: "application/json",
                    success: function(response) {
                      this.setState({
                        querySourceFieldArray: response.result
                      });
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  });
               },
               reflectSelectedQuerySource: function(querySourceId) {
                  if (querySourceId != this.state.selectedQuerySourceId) {
                    this.setState(
                      {selectedQuerySourceId: querySourceId},
                      this.fetchQuerySourceFields
                    );
                  }
               },
               reflectChangedCategory: function(querySourceId, selectedCategoryId) {
                  var querySources = this.state.querySourceArray;
                  var querySourcePos = querySources.map(function(x){return x.id;}).indexOf(querySourceId);
                  querySources[querySourcePos].dataSourceCategoryId = selectedCategoryId;
                  this.setState({
                    querySourceArray: querySources
                  });
                  this.registerChangedQuerySource(querySourceId);
               },
               reflectChangedQuerySourceAlias: function(querySourceId, alias) {
                  var querySources = this.state.querySourceArray;
                  var querySourcePos = querySources.map(function(x){return x.id;}).indexOf(querySourceId);
                  querySources[querySourcePos].alias = alias;
                  this.setState({
                    querySourceArray: querySources
                  });
                  this.registerChangedQuerySource(querySourceId);
               },
               reflectChangedQuerySourceFieldAlias: function(querySourceFieldId, alias) {
                  var querySourceFields = this.state.querySourceFieldArray;
                  var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
                  querySourceFields[querySourceFieldPos].alias = alias;
                  this.setState({
                    querySourceFieldArray: querySourceFields
                  });
                  this.registerChangedQuerySourceField(querySourceFieldId);
               },
               reflectVisibleField: function(querySourceFieldId) {
                  var querySourceFields = this.state.querySourceFieldArray;
                  var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
                  querySourceFields[querySourceFieldPos].visible = !querySourceFields[querySourceFieldPos].visible;
                  this.setState({
                    querySourceFieldArray: querySourceFields
                  });
                  this.registerChangedQuerySourceField(querySourceFieldId);
               },
               reflectFilterableField: function(querySourceFieldId) {
                  var querySourceFields = this.state.querySourceFieldArray;
                  var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
                  querySourceFields[querySourceFieldPos].filterable = !querySourceFields[querySourceFieldPos].filterable;
                  this.setState({
                    querySourceFieldArray: querySourceFields
                  });
                  this.registerChangedQuerySourceField(querySourceFieldId);
               },
               registerChangedQuerySource: function(querySourceId) {
                  this.changedQuerySources.push(querySourceId);
               },
               registerChangedQuerySourceField: function(querySourceFieldId) {
                  var querySourceFields = this.state.querySourceFieldArray;
                  var querySourceFieldPos = querySourceFields.map(function(x){return x.id;}).indexOf(querySourceFieldId);
                  this.querySourceWithChangedQuerySourceFields = querySourceFields[querySourceFieldPos].querySourceId;
               },
               pushData: function() {
                  
                  var postData = new Object();
                  
                  function uniqueOnly(value, index, self) {
                    return self.indexOf(value) === index;
                  }
                  
                  var allChangedQuerySources = (this.querySourceWithChangedQuerySourceFields!=null)
                    ? this.changedQuerySources.concat(this.querySourceWithChangedQuerySourceFields)
                    : this.changedQuerySources;
                  var uniqueChangedQuerySources = allChangedQuerySources.filter(uniqueOnly);
                  
                  postData.querySources = this.state.querySourceArray.filter(function(querySource){
                    return uniqueChangedQuerySources.indexOf(querySource.id) >= 0;
                  });
                  
                  if (this.querySourceWithChangedQuerySourceFields!=null) {
                    var querySourceWithChangedQuerySourceFieldsPos = postData.querySources.map(function(x){return x.id;}).indexOf(this.querySourceWithChangedQuerySourceFields);
                    postData.querySources[querySourceWithChangedQuerySourceFieldsPos].querySourceFields = this.state.querySourceFieldArray;
                  }
                  
                  return $.ajax({
                    url: this.props.rootUrl + "dataModel/",
                    type: "POST",
                    data: JSON.stringify(postData),
                    contentType: "application/json",
                    success: function(response) {
                      if (response.success) {
                        this.fetchData();
                        this.changedQuerySources = new Array();
                        this.querySourceWithChangedQuerySourceFields = null;
                      } else {
                        console.log(JSON.stringify(response));
                      }
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  });
               }
              });
         
              var QuerySourceItem = React.createClass({
               render: function() {
                  return (
                    <tr style={{backgroundColor: this.props.color}} onClick={this.reflectSelectedQuerySource}>
                      <td><CategoryItem selectedCategoryId={this.props.querySource.dataSourceCategoryId} categories={this.props.categories} reflectChangedCategory={this.reflectChangedCategory} /></td>
                      <td>{this.props.querySource.connectionName}</td>
                      <td>{this.props.querySource.name}</td>
                      <td><input type="text" value={(this.props.querySource.alias==null)?"":this.props.querySource.alias} onChange={this.reflectChangedAlias} /></td>
                    </tr>
                  )
               },
               reflectSelectedQuerySource: function() {
                  this.props.reflectSelectedQuerySource(this.props.querySource.id);
               },
               reflectChangedCategory: function(selectedCategoryId) {
                  this.props.reflectChangedCategory(this.props.querySource.id, selectedCategoryId);
               },
               reflectChangedAlias: function(event) {
                  this.props.reflectChangedAlias(this.props.querySource.id, event.target.value);
               }
              });
         
              var QuerySourceFieldItem = React.createClass({
               render: function() {
                  return (
                    <tr>
                      <td>{this.props.querySourceField.name}</td>
                      <td>{this.props.querySourceField.dataType}</td>
                      <td><input type="text" value={(this.props.querySourceField.alias==null)?"":this.props.querySourceField.alias} onChange={this.reflectChangedAlias} /></td>
                      <td><input type="checkbox" checked={this.props.querySourceField.visible} onChange={this.reflectVisibleField} /></td>
                      <td><input type="checkbox" checked={this.props.querySourceField.filterable} onChange={this.reflectFilterableField} /></td>
                    </tr>
                  )
               },
               reflectChangedAlias: function(event) {
                  this.props.reflectChangedAlias(this.props.querySourceField.id, event.target.value);
               },
               reflectVisibleField: function() {
                  this.props.reflectVisibleField(this.props.querySourceField.id);
               },
               reflectFilterableField: function() {
                  this.props.reflectFilterableField(this.props.querySourceField.id);
               }
              });
              
              var CategoryItem = React.createClass({
               render: function() {          
                  var options = this.props.categories.map(function(category) {
                    return (
                      <option key={category.id} value={category.id}>{category.name}</option>
                    )
                    
                  });
                  return (
                    <select value={(this.props.selectedCategoryId==null)?"":this.props.selectedCategoryId} onChange={this.reflectChangedCategory} >
                      <option value=""></option>
                      {options}
                    </select>
                  )
               },
               reflectChangedCategory: function(event) {
                  this.props.reflectChangedCategory(event.target.value);          
               }
              });
         
              ReactDOM.render(<App rootUrl={"http://127.0.0.1:8888/api/"} />, document.getElementById('app'));
            </script>
          </body>
         </html>
