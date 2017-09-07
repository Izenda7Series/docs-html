===========================================
ReactJS to manage a scalar value
===========================================

In this sample we will write a simplistic web page utilizing ReactJS to
manage a server scalar value setting.

-  We will test with the :ref:`GET_report/reportMode` and
   :ref:`POST_report/reportMode/{value}`
   APIs.
-  We will use ReactJS to create the UI.

Prerequisites
-------------

#. This sample is a continuation of :doc:`code_rest_api_test`.
#. This sample re-uses the folder structure created in :doc:`code_rest_api_test`.
#. The uncompressed, development version of react.js and react-dom.js
   has been put into "ui\_react\_examples/vendor" folder. (They are in
   the starter kit available at
   https://facebook.github.io/react/downloads.html)

Boilerplate code
----------------

#. In "ui\_react\_examples" folder, create a blank text file and name it
   "ReactJS to manage a scalar value.html".
#. Edit the file with a text editor such as Notepad or Notepad++ and
   paste the following boilerplate HTML code:

.. comment: highlight as text since Pygments cannot parse jsx

.. code-block:: text

   <!doctype html>
   <html>
    <head>
      <title>React Test</title>
      <script src="vendor/jquery-1.12.2.js" type="text/javascript"></script>
      <script src="vendor/react.js" type="text/javascript"></script>
      <script src="vendor/react-dom.js" type="text/javascript"></script>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js" type="text/javascript"></script>
    </head>
    <body>
   
      <section id="app"></section>
   
      <script type="text/babel">
        var ScalarValueComponent = React.createClass({
         getInitialState: function() {
            return {
              data: null
            };
         },
         componentDidMount: function() {
            this.fetchData();
         },
         render: function() {
            return (
              <div id="outerdiv">
                <input type="text" value={this.state.data} onChange={this.reflectChangedData} />&nbsp;
                <button onClick={this.pushData}>Save</button>
              </div>
            )
         },
         reflectChangedData: function(event) {
            this.setState({
              data: event.target.value
            });
         },
         fetchData: function() {
            // TODO
         },
         pushData: function() {
            // TODO
         }
        });
   
        ReactDOM.render(<ScalarValueComponent />, document.getElementById('app'));
      </script>
    </body>
   </html>

For production web site, we will replace the local libraries with
hosted, minified and compressed library links.

ReactJS basics
--------------

A ReactJS component maintains its data in ``this.state``, initialize the
data in ``getInitialState`` method, load the data from server in
``componentDidMount`` method, and creates its UI elements in the
``render`` method. The ``render`` method is called each time there is a
change in ``this.state``.

Above that we added 3 custom methods:

-  fetchData to get data from the server
-  reflectChangedData to update the state data according to user input
-  pushData to post data to the server

Just by implementing these 6 methods then we will have a working ReactJS
component. In this specific case, we only need to implement fetchData
and pushData, the other boilerplate methods are already working without
any change needed.

.. note::

   Note on the mixing of JavaScript and XML tags: we are using the JSX syntax to facilitate reading. This JSX will be translated to JavaScript by the included Babel library.

Implement fetchData
-------------------

From the API documentation :ref:`GET_report/reportMode`, the
``// TODO`` in fetchData would be replaced by this ajax call:

.. code-block:: javascript

    $.ajax({
     url: "http://127.0.0.1:8888/api/report/reportMode",
     type: "GET",
     contentType: "application/json",
     success: function(response) {
       this.setState({
         data: response
       });
     }.bind(this),
     error: function(response) {
       console.log(JSON.stringify(response));
     }
   })

Now open the page in web browser and we can see the value 0 or 1 for the reportMode setting.

.. note::

   We need to add ``.bind(this)`` for the call ``this.setState`` to correctly call the setState method of the ReactJS component.

Implement pushData
------------------

From the API documentation :ref:`POST_report/reportMode/{value}`,
the ``// TODO`` in pushData would be replaced by this ajax call:

.. code-block:: javascript

   $.ajax({
     url: "http://127.0.0.1:8888/api/report/reportMode/" + this.state.data,
     type: "POST",
     contentType: "application/json",
     success: function(response) {
       if (response == false) {
         this.fetchData();
         console.log('The response was "false"');
       }
     }.bind(this),
     error: function(response) {
       console.log(JSON.stringify(response));
     }
   })

Now we can enter the desired value 0 or 1 and click Save to update the
server setting. Any other value would receive a false response and an
notice line in JavaScript Console.

.. note::

   We need to add ``.bind(this)`` for the call ``this.fetchData`` to correctly call the fetchData method of the ReactJS component.

Summary
-------

In this sample, we went through these activities:

-  included the ReactJS and JQuery libraries.
-  created a boilerplate ReactJS component.
-  loaded initial data using ReactJS's componentDidMount event.
-  created UI components using ReactJS.
-  added event handlers to get data, post data and update the state data
   according to user input.

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
              var ScalarValueComponent = React.createClass({
               getInitialState: function() {
                  return {
                    data: null
                  };
               },
               componentDidMount: function() {
                  this.fetchData();
               },
               render: function() {
                  return (
                    <div id="outerdiv">
                      <input type="text" value={this.state.data} onChange={this.reflectChangedData} />&nbsp;
                      <button onClick={this.pushData}>Save</button>
                    </div>
                  )
               },
               fetchData: function() {
                       $.ajax({
                    url: "http://127.0.0.1:8888/api/report/reportMode",
                    type: "GET",
                    contentType: "application/json",
                    success: function(response) {
                      this.setState({
                        data: response
                      });
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  })
                    },
               reflectChangedData: function(event) {
                  this.setState({
                    data: event.target.value
                  });
               },
               pushData: function() {
                  $.ajax({
                    url: "http://127.0.0.1:8888/api/report/reportMode/" + this.state.data,
                    type: "POST",
                    contentType: "application/json",
                    success: function(response) {
                      if (response == false) {
                        this.fetchData();
                        console.log('The response was "false"');
                      }
                    }.bind(this),
                    error: function(response) {
                      console.log(JSON.stringify(response));
                    }
                  })
               }
              });
         
              ReactDOM.render(<ScalarValueComponent />, document.getElementById('app'));
            </script>
          </body>
         </html>
