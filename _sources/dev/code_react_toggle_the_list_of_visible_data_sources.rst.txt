======================================================
ReactJS to toggle the list of visible data sources
======================================================

In this sample we will write a simplistic web page utilizing ReactJS to
show two lists of available and visible data sources side by side and
toggle items between them.

-  We focus on applying ReactJS for a complex data structure.
-  We will use the :ref:`POST_connection/loadRemoteSchema`
   and :ref:`POST_connection` APIs.

Prerequisites
-------------

#. This sample is a continuation of :doc:`code_react_manage_the_list_of_categories`.
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
build the page to toggle visible data sources.

Start with a mock
-----------------

.. figure:: /_static/images/Connection_Move_Data_Source_to_Visible_List.jpg
   :width: 611px

   Move data sources between the two lists

For simplicity in this sample, we will skip the search boxes and the
Table, View, Stored Procedure and Function groups and only keep the
schema and data sources.

The response from the API is detailed in :ref:`POST_connection/loadRemoteSchema`.
Basically the ``response.dBSource.querySources`` is an array of schemas,
and each schema contains the ``querySources`` which is an array of query
sources.

Break the UI into a component hierarchy
---------------------------------------

We will have two side-by-side lists of schema items, and inside each
schema item is a list of query source items.

Following would be our component hierarchy:

-  App

   -  List of SchemaItems

      -  List of available QuerySourceItems

   -  List of SchemaItems

      -  List of visible QuerySourceItems

Available QuerySourceItem and visible QuerySourceItem differ only in the
checking condition for ``selected`` value, so we can use a single
component code and pass "Available" or "Visible" to each instance via
``props``.

Build a static version in React
-------------------------------

#. In "ui\_react\_examples" folder, create a blank text file and name it
   "ReactJS to toggle the list of visible data sources.html".
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
   
        var App = React.createClass({
         render: function() {
            return (
              <div>
                <p>Click an item to move between Available and Visible Data Sources.</p>
                <div style={{"width": "600px", "float": "left"}}>
                  <ul>
                    {this.props.schemaArray.map(function(result){
                      return <SchemaItem key={result.id} type="Available" schema={result} />
                    })}
                  </ul>
                </div>
                <div style={{"marginLeft": "620px"}}>
                  <ul>
                    {this.props.schemaArray.map(function(result){
                      return <SchemaItem key={result.id} type="Visible" schema={result} />
                    })}
                  </ul>
                </div>
              </div>
            )
         }
        });
   
        var SchemaItem = React.createClass({
         render: function() {
            return (
                <li>
                  <label>{this.props.schema.name}</label>
                  <ul>
                    {this.props.schema.querySources
                      .filter(function(querySource){
                        return ((this.props.type=="Visible") ? querySource.selected : !querySource.selected);
                      }.bind(this))
                      .map(function(result){
                        return <QuerySourceItem key={result.id} type={this.props.type} querySource={result} />
                      }.bind(this))
                    }
                  </ul>
                </li>
              )
         }
        });
        
        var QuerySourceItem = React.createClass({
         render: function() {
            return (
              <li style={{"cursor": "pointer"}}>
                {this.props.querySource.name}
              </li>
            )
         }
        });
        
        var schemas = [
         {id: '10', name: 'HumanResources', querySources: [
            {id: '11', name: 'Employee', selected: false},
            {id: '12', name: 'Department', selected: true}
         ]},
         {id: '20', name: 'Production', querySources: [
            {id: '21', name: 'Product', selected: true},
            {id: '22', name: 'WorkOrder', selected: true}
         ]},
         {id: '30', name: 'Sales', querySources: [
            {id: '31', name: 'Customer', selected: false},
            {id: '32', name: 'SalesOrderDetail', selected: false}
         ]}
        ];
     
        ReactDOM.render(<App schemaArray={schemas}/>, document.getElementById('app'));
      </script>
    </body>
   </html>

Identify the minimal UI state
-----------------------------

The pieces of data in our application:

-  The API url
-  The connection string
-  The server type id
-  The data returned from the API
-  The value of selected field

Our state would be the dBSource.querySources part of the response since
it contains the list of schemas and also the selected value. The API
url, connection string and server type id would be passed in via props.

.. code-block:: javascript

   ReactDOM.render(<App rootUrl={"http://127.0.0.1:8888/api/"} connectionString={"server=host01\\instance01;database=db01;User Id=user01;Password=secret;"} serverTypeId={"572bd576-8c92-4901-ab2a-b16e38144813"}/>, document.getElementById('app'));

Identify where the state should live
------------------------------------

The state should be in the root App since all other components only need
a part of that state.

Now we can implement getInitialState, componentDidMount and fetchData
methods inside the root App.

.. code-block:: javascript

     getInitialState: function() {
      return {
        schemaArray: new Array()
        };
   },
   componentDidMount: function() {
      this.fetchData();
   },
   fetchData: function() {
      var postData = new Object();
      postData.connectionString = this.props.connectionString;
      postData.serverTypeId = this.props.serverTypeId;
      $.ajax({
        url: this.props.rootUrl + "connection/loadRemoteSchema/",
        type: "POST",
        data: JSON.stringify(postData),
        contentType: "application/json",
        success: function(response) {
          if (response.success) {
            this.setState({
              schemaArray: response.dBSource.querySources
            });
          }
          else {
            console.log(JSON.stringify(response));
          }
        }.bind(this),
        error: function(response) {
          console.log(JSON.stringify(response));
        }
      })
   },

Add inverse data flow
---------------------

Because the state is in the parent component App, a toggle action that
happens inside a QuerySourceItem cannot update it directly. Instead, App
needs to pass a callback to QuerySourceItem to update the state whenever
a toggle happens. For our hierarchy, the callback would be passed from
App to SchemaItem first, then from SchemaItem to QuerySourceItem.

We will name the callback ``reflectChangedData`` as normal:

.. comment: pygments code highlighting does not support React jsx yet

.. code-block:: text

     // .. in App
       return <SchemaItem key={result.id} type="Available" schema={result} reflectChangedData={this.reflectChangedData} />
     // .. in SchemaItem
       return <QuerySourceItem key={result.id} type={this.props.type} querySource={result} reflectChangedData={this.reflectChangedData}/>
     // .. in QuerySourceItem
     return (
       <li onClick={this.reflectChangedData.bind(this,this.props.querySource.id)} style={{"cursor": "pointer"}}>
         {this.props.querySource.name}
       </li>
     )
     // .. in QuerySourceItem
     reflectChangedData: function(querySourceId) {
       // the callback passed in by SchemaItem
       this.props.reflectChangedData(querySourceId);
     }
     // .. in SchemaItem
     reflectChangedData: function(querySourceId) {
       // the callback passed in by App
       this.props.reflectChangedData(this.props.schema.id, querySourceId);
     }
     // .. in App
     reflectChangedData: function(schemaId, querySourceId) {
       var schemas = this.state.schemaArray;
       var schemaPos = schemas.map(function(x) {return x.id; }).indexOf(schemaId);
       var querySources = schemas[schemaPos].querySources;
       var querySourcePos = querySources.map(function(x) {return x.id; }).indexOf(querySourceId);
       schemas[schemaPos].querySources[querySourcePos].selected = ! schemas[schemaPos].querySources[querySourcePos].selected;
       this.setState({schemaArray : schemas});
     }

#. The inverse flow begins in QuerySourceItem where we bind the id of
   the query source to the callback function in SchemaItem.
#. In SchemaItem we bind the id of the schema to the callback function
   in App.
#. In App we use the id of the schema and the id of the query source to
   find the updated item to toggle its selected value.
#. The setState call in App will render all the components.

Implement pushData
------------------

We will also add a Save button and implement pushData method to save the
connection together with visible data sources.

.. code-block:: javascript

   pushData: function() {
      var postData = {
        id: null,
        name: this.props.connectionName,
        serverTypeId: this.props.serverTypeId,
        connectionString: this.props.connectionString,
        visible: true,
        dBSource: {
          querySources: this.state.schemaArray.map(function(schema){
                          schema.querySources = schema.querySources.filter(function(querySource){
                           return querySource.selected;
                          });
                          return schema;
                        })
        }
      };
      $.ajax({
        url: this.props.rootUrl + "connection/",
        type: "POST",
        data: JSON.stringify(postData),
        contentType: "application/json",
        success: function(response) {
          if (!response.success) {
            console.log(JSON.stringify(response));
          } else {
            console.log("connectionId: "+response.connectionId);
          }
        },
        error: function(response) {
          console.log(JSON.stringify(response));
        }
      })
   }

Summary
-------

In this sample, we followed the recommended ReactJS design approach to
implement the list of visible data sources.

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
               getInitialState: function() {
                  return {
                    schemaArray: new Array()
                    };
               },
               componentDidMount: function() {
                  this.fetchData();
               },
               fetchData: function() {
                  var postData = new Object();
                  postData.connectionString = this.props.connectionString;
                  postData.serverTypeId = this.props.serverTypeId;
                       $.ajax({
                    url: this.props.rootUrl + "connection/loadRemoteSchema/",
                    type: "POST",
                    data: JSON.stringify(postData),
                    contentType: "application/json",
                    success: function(response) {
                      if (response.success) {
                        this.setState({
                          schemaArray: response.dBSource.querySources
                        });
                      }
                      else {
                        console.log(JSON.stringify(response));
                      }
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  })
               },
               render: function() {
                  return (
                    <div>
                      <button onClick={this.pushData}>Save</button>
                      <p>Click an item to move between Available and Visible Data Sources.</p>
                      <div style={{"width": "600px", "float": "left"}}>
                        <ul>
                          {this.state.schemaArray.map(function(result){
                            return <SchemaItem key={result.id} type="Available" schema={result} reflectChangedData={this.reflectChangedData} />
                          }.bind(this))}
                        </ul>
                      </div>
                      <div style={{"marginLeft": "620px"}}>
                        <ul>
                          {this.state.schemaArray.map(function(result){
                            return <SchemaItem key={result.id} type="Visible" schema={result} reflectChangedData={this.reflectChangedData} />
                          }.bind(this))}
                        </ul>
                      </div>
                    </div>
                  )
               },
               reflectChangedData: function(schemaId, querySourceId) {
                  var schemas = this.state.schemaArray;
                  var schemaPos = schemas.map(function(x) {return x.id; }).indexOf(schemaId);
                  var querySources = schemas[schemaPos].querySources;
                  var querySourcePos = querySources.map(function(x) {return x.id; }).indexOf(querySourceId);
                  schemas[schemaPos].querySources[querySourcePos].selected = ! schemas[schemaPos].querySources[querySourcePos].selected;
                  this.setState({schemaArray : schemas});
               },
               pushData: function() {
                  var postData = {
                    id: null,
                    name: this.props.connectionName,
                    serverTypeId: this.props.serverTypeId,
                    connectionString: this.props.connectionString,
                    visible: true,
                    dBSource: {
                      querySources: this.state.schemaArray.map(function(schema){
                                      schema.querySources = schema.querySources.filter(function(querySource){
                                       return querySource.selected;
                                      });
                                      return schema;
                                    })
                    }
                  };
                  $.ajax({
                    url: this.props.rootUrl + "connection/",
                    type: "POST",
                    data: JSON.stringify(postData),
                    contentType: "application/json",
                    success: function(response) {
                      if (!response.success) {
                        console.log(JSON.stringify(response));
                      } else {
                        console.log("connectionId: "+response.connectionId);
                      }
                    },
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  })
               }
              });
         
              var SchemaItem = React.createClass({
               render: function() {
                  return (
                      <li>
                        <label>{this.props.schema.name}</label>
                        <ul>
                          {this.props.schema.querySources
                            .filter(function(querySource){
                              return ((this.props.type=="Visible") ? querySource.selected : !querySource.selected);
                            }.bind(this))
                            .map(function(result){
                              return <QuerySourceItem key={result.id} type={this.props.type} querySource={result} reflectChangedData={this.reflectChangedData}/>
                            }.bind(this))
                          }
                        </ul>
                      </li>
                    )
                    },
               reflectChangedData: function(querySourceId) {
                  this.props.reflectChangedData(this.props.schema.id, querySourceId);
               }
              });
              
              var QuerySourceItem = React.createClass({
               render: function() {
                  return (
                    <li onClick={this.reflectChangedData.bind(this,this.props.querySource.id)} style={{"cursor": "pointer"}}>
                      {this.props.querySource.name}
                    </li>
                  )
               },
               reflectChangedData: function(querySourceId) {
                  this.props.reflectChangedData(querySourceId);
               }
              });
              
         
           
              ReactDOM.render(<App rootUrl={"http://127.0.0.1:8888/api/"} connectionString={"server=host01\\instance01;database=db01;User Id=user01;Password=secret;"} connectionName={"db01"} serverTypeId={"572bd576-8c92-4901-ab2a-b16e38144813"}/>, document.getElementById('app'));
            </script>
          </body>
         </html>
