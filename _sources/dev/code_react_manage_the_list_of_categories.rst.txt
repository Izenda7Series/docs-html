===========================================
ReactJS to manage the list of categories
===========================================

In this sample we will write a simplistic web page utilizing ReactJS to
manage a list of items - the data source categories.

-  We will use the :ref:`GET_advancedSetting/category/(tenant_id)`,
   :ref:`POST_advancedSetting/category` and :ref:`DELETE_advancedSetting/category/{category_id}` APIs.
-  We will use ReactJS to create the UI.

Prerequisites
-------------

#. This sample is a continuation of :doc:`code_react_manage_a_scalar_value`.
#. This sample re-uses the folder structure created in :doc:`code_react_manage_a_scalar_value`.
#. The uncompressed, development version of react.js and react-dom.js
   has been put into "ui\_react\_examples/vendor" folder. (They are in
   the starter kit available at
   https://facebook.github.io/react/downloads.html)

Boilerplate code for an array
-----------------------------

With these APIs, we will be managing an array of objects, so:

-  We model the data in ``this.state`` in an array called categoryArray.
-  We modify render method to display a list of items
-  We render a new Add button to insert a new category
-  We modify reflectChangedData method to update categoryArray with user
   input.

We also make one code improvement to pass the API server IP and port via
the parameter rootUrl to the ReactJS component.

#. In "ui\_react\_examples" folder, create a blank text file and name it
   "ReactJS to manage the list of categories.html".
#. Edit the file with a text editor such as Notepad or Notepad++ and
   paste the following boilerplate HTML code:

.. comment: highlight as text since Pygments cannot parse jsx

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
        var CategoryList = React.createClass({
         getInitialState: function() {
            return {
              categoryArray: new Array()
            };
         },
         componentDidMount: function() {
            this.fetchData();
         },
         render: function() {
            var lines = this.state.categoryArray.map(function(category) {
              return (
                <li key={category.id}>
                <input type="text" id={category.id} value={category.name} onChange={this.reflectChangedData.bind(this,category.id)} />&nbsp;
                <button onClick={this.removeCategory.bind(this,category.id)}>Remove</button>
                </li>
              )
            }.bind(this));
            return (
              <div style={{"border": "1px solid black", "width": "400px"}}>
              <button onClick={this.addCategory}>Add</button>
              <ul> {lines} </ul>
              <button onClick={this.pushData}>Save</button>
              </div>
            )
         },
         fetchData: function() {
                 // TODO
              },
         reflectChangedData: function(id, event) {
            var categories = this.state.categoryArray;
            var pos = categories.map(function(x) {return x.id; }).indexOf(id);
            categories[pos].name = event.target.value;
            this.setState({categoryArray : categories});
         },
         pushData: function() {
            // TODO
         },
         addCategory: function(e) {
            // TODO
         },
         removeCategory: function(id, event) {
            // TODO
         }
        });
   
        ReactDOM.render(<CategoryList rootUrl={"http://127.0.0.1:8888/api/"} />, document.getElementById('app'));
      </script>
    </body>
   </html>

.. note::

   If using Notepad++, we can set the Language as JavaScript to see proper syntax highlighting.

-  We render the list of categories in an unordered list
   ``<ul>`` tag, with an ``<li>`` tag
   wrapping around the ``<input>`` tag for each
   category.
-  In ``onChange`` event of the input box, reflectChangedData is binded
   with category.id so that in the method we can know the change
   happended in which category and update that category only.
-  In ``reflectChangedData``, data in ``this.state`` is immutable so
   that is why we could not assign this.state.categoryArray.name
   directly.

Since this is a list of items, apart from fetchData and pushData we need
2 more custom methods:

-  addCategory to add a new category
-  removeCategory to remove a category

Implement fetchData
-------------------

From the API documentation :ref:`GET_advancedSetting/category/(tenant_id)`,
the ``// TODO`` in fetchData would be replaced by this ajax call:

.. code-block:: javascript

   $.ajax({
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
   })

Now open the page in web browser and we can see the list of existing
categories.

Implement pushData
------------------

From the API documentation :ref:`POST_advancedSetting/category`,
the ``// TODO`` in pushData would be replaced by this ajax call:

.. code-block:: javascript

   $.ajax({
     url: this.props.rootUrl + "advancedSetting/category/",
     type: "POST",
     contentType: "application/json",
     data: JSON.stringify(this.state.categoryArray),
     success: function(response) {
       if (!response.success) {
         console.log(JSON.stringify(response))
       }
       this.fetchData();
     }.bind(this),
     error: function(response) {
       console.log(JSON.stringify(response));
       this.fetchData();
     }
   })

Implement addCategory
---------------------

.. code-block:: javascript

   e.preventDefault();
   var categories = this.state.categoryArray;
   var newId = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
     var r = Math.random()*16|0, v = c == 'x' ? r : (r&0x3|0x8);
     return v.toString(16);
   });
   categories.push({id: newId, name: null});
   this.setState({categoryArray : categories});

The Add button only needs to modify categoryArray, then the changed data
in ``this.state`` will trigger the render method. Also, the newly-added
category has its name as null so that ReactJS will render a new blank
editable input box.

Implement removeCategory
------------------------

From the API documentation :ref:`DELETE_advancedSetting/category/{category_id}`,
the ``// TODO`` in pushData would be replaced by this ajax call:

.. code-block:: javascript

   $.ajax({
     url: this.props.rootUrl + "advancedSetting/category/" + id,
     type: "DELETE",
     contentType: "application/json",
     success: function(response) {
       if (!response.success) {
         console.log(JSON.stringify(response))
       }
       this.fetchData();
     }.bind(this),
     error: function(response) {
       console.log(JSON.stringify(response));
       this.fetchData();
     }.bind(this)
   });

Summary
-------

In this sample, we went through a ReactJS structure to manage a list of
items.

.. container:: toggle

      .. container:: header

         Full source code in this sample:

      .. comment: highlight as text since Pygments cannot parse jsx

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
              var CategoryList = React.createClass({
               getInitialState: function() {
                  return {
                    categoryArray: new Array()
                  };
               },
               componentDidMount: function() {
                  this.fetchData();
               },
               render: function() {
                  var lines = this.state.categoryArray.map(function(category) {
                    return (
                      <li key={category.id}>
                      <input type="text" id={category.id} value={category.name} onChange={this.reflectChangedData.bind(this,category.id)} />&nbsp;
                      <button onClick={this.removeCategory.bind(this,category.id)}>Remove</button>
                      </li>
                    )
                  }.bind(this));
                  return (
                    <div style={{"border": "1px solid black", "width": "400px"}}>
                    <button onClick={this.addCategory}>Add</button>
                    <ul> {lines} </ul>
                    <button onClick={this.pushData}>Save</button>
                    </div>
                  )
               },
               fetchData: function() {
                  $.ajax({
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
                  })
               },
               reflectChangedData: function(id, event) {
                  var categories = this.state.categoryArray;
                  var pos = categories.map(function(x) {return x.id; }).indexOf(id);
                  categories[pos].name = event.target.value;
                  this.setState({categoryArray : categories});
               },
               pushData: function() {
                  $.ajax({
                    url: this.props.rootUrl + "advancedSetting/category/",
                    type: "POST",
                    contentType: "application/json",
                    data: JSON.stringify(this.state.categoryArray),
                    success: function(response) {
                      if (!response.success) {
                        console.log(JSON.stringify(response))
                      }
                      this.fetchData();
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                      this.fetchData();
                    }
                  })
               },
               addCategory: function(e) {
                  e.preventDefault();
                  var categories = this.state.categoryArray;
                  var newId = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
                    var r = Math.random()*16|0, v = c == 'x' ? r : (r&0x3|0x8);
                    return v.toString(16);
                  });
                  categories.push({id: newId, name: null});
                  this.setState({categoryArray : categories});
               },
               removeCategory: function(id, event) {
                  $.ajax({
                    url: this.props.rootUrl + "advancedSetting/category/" + id,
                    type: "DELETE",
                    contentType: "application/json",
                    success: function(response) {
                      if (!response.success) {
                        console.log(JSON.stringify(response))
                      }
                      this.fetchData();
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                      this.fetchData();
                    }.bind(this)
                  });
               }
              });
         
              ReactDOM.render(<CategoryList rootUrl={"http://127.0.0.1:8888/api/"} />, document.getElementById('app'));
            </script>
          </body>
         </html>
