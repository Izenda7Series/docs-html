=========================================================
JavaScript Manage UI Components, Libraries and Unit Tests
=========================================================

Unit testing raises the need to organize code into separate components.
Other reasons include code re-use and better management of various
JavaScript libraries.

In this sample we will re-write the :doc:`code_react_manage_the_list_of_categories` sample in
a commonly recommended way that allows for code re-use, unit test,
deployment and automatic management of third-party JavaScript packages
together with their specific versions.

Folders and Tools Preparation
-----------------------------

We will use `npm <https://www.npmjs.com/>`__ as the central place to
manage the libraries, run the web server and unit tests.

#. npm is packaged inside Node.js so firstly we need to download Node
   installer from https://nodejs.org.
#. .. figure:: /_static/images/Node.js_Setup_Including_npm.png
      :align: right
      :width: 306px

   Install npm

   Run the installer and include npm in the setup. |br|
#. Test that npm is installed successfully by running ``npm --version``
   in the command-line to see the version number.
#. Create a folder named "ui\_react\_samples\_2" anywhere available.
#. Inside it, create a folder named "src". This is where we will put our
   code, with each component in a separate file.

       Because of this structure, we now must use a web server even for
       testing. For details, please see `same-origin
       policy <https://en.wikipedia.org/wiki/Same-origin_policy>`__.

#. Inside "src" folder, create a folder named "\_\_tests\_\_". This is
   where we will put the unit tests.
#. In command-line, go to "ui\_react\_samples\_2" folder and run
   ``npm init`` to create npm configuration file "package.json".
#. Accept default values by pressing Enter.
#. The content of "ui\_react\_samples\_2/package.json" will be as
   following:

.. code-block:: json

   {
    "name": "ui_react_samples_2",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC"
   }

Install the Packages
--------------------

We need the following packages:

-  In both production and development:

   -  `react <https://www.npmjs.com/package/react>`__ and
      `react-dom <https://www.npmjs.com/package/react-dom>`__ for the
      UI.
   -  `babel-loader <https://www.npmjs.com/package/babel-loader>`__
      `babel-core <https://www.npmjs.com/package/babel-core>`__
      `babel-preset-es2015 <https://www.npmjs.com/package/babel-preset-es2015>`__
      `babel-preset-react <https://www.npmjs.com/package/babel-preset-react>`__
      to transpile JSX.
   -  `request <https://www.npmjs.com/package/request>`__ for REST API
      calls (to replace JQuery that `needs
      tweaking <https://www.npmjs.com/package/jquery>`__ to work in
      Node.js).
   -  `webpack <https://www.npmjs.com/package/webpack>`__ to bundle the
      source files together
   -  `json-loader <https://www.npmjs.com/package/json-loader>`__ for
      webpack.

-  In development only:

   -  `webpack-dev-server <https://www.npmjs.com/package/webpack-dev-server>`__
      to serve the bundle.
   -  `http-server <https://www.npmjs.com/package/http-server>`__ to
      serve HTML files.
   -  `react-addons-test-utils <https://www.npmjs.com/package/react-addons-test-utils>`__
      for unit testing.
   -  `mocha <https://www.npmjs.com/package/mocha>`__ for the test
      framework.
   -  `karma <https://www.npmjs.com/package/karma>`__
      `karma-cli <https://www.npmjs.com/package/karma-cli>`__,
      `karma-mocha <https://www.npmjs.com/package/karma-mocha>`__,
      `karma-webpack <https://www.npmjs.com/package/karma-webpack>`__,
      `karma-chrome-launcher <https://www.npmjs.com/package/karma-chrome-launcher>`__
      for the test runner.
   -  `karma-sinon <https://www.npmjs.com/package/karma-sinon>`__ to
      stub out API calls in unit tests.
   -  `expect <https://www.npmjs.com/package/expect>`__ to write
      assertions in unit tests.

Install the packages and save to "package.json":

#. In command-line, go to "ui\_react\_samples\_2" folder.
#. ``npm install react react-dom --save``
#. ``npm install babel-loader babel-core babel-preset-es2015 babel-preset-react --save``
#. ``npm install request@2.65.0 --save``

       (Use request at 2.65.0 because higher versions are having an
       issue with webpack.)

#. ``npm install webpack json-loader --save``
#. ``npm install webpack webpack-dev-server http-server react-addons-test-utils mocha`` |br| ``karma karma-cli karma-mocha karma-webpack karma-chrome-launcher karma-sinon expect --save-dev``

       (Packages only needed for development use ``--save-dev`` so that
       they are excluded when deployed for production)

Configure Unit Test
-------------------

#. Create a text file named "tests.webpack.js" in "ui\_react\_samples\_2" folder.

   .. code-block:: javascript

      var context = require.context('./src', true, /-test\.jsx$/);
      context.keys().forEach(context); 

   The code tells webpack to bundle all files ending in ``-test.jsx`` (test cases) below "ui\_react\_samples\_2/src" folder into this "tests.webpack.js" file.

#. Create a text file named "karma.conf.js" in "ui\_react\_samples\_2" folder.

   .. code-block:: javascript

      var webpack = require('webpack');
      
      module.exports = function (config) {
        config.set({
            browsers: ['Chrome'],
            client: { captureConsole: true },
            singleRun: true,
            frameworks: ['mocha','sinon'],
            files: [
                'tests.webpack.js'
            ],
            preprocessors: {
                'tests.webpack.js': ['webpack']
            },
            reporters: ['dots'],
            webpack: {
                module: {
                    loaders: [
                      {test: /\.jsx$/, loader: 'babel-loader', query: {presets: ['react', 'es2015']}},
                      {test: /\.json$/, loader: 'json-loader'}
                    ]
                },
                watch: true,
                node: {
                  console: true,
                  fs: 'empty',
                  net: 'empty',
                  tls: 'empty'
                }
            },
            webpackServer: {
                noInfo: true
            }
        });
      }; 

   ``files`` section says that ``tests.webpack.js`` should be used to test, and ``preprocessors`` section tells webpack to process this file in advance (which bundles all test cases into the file).

   Also, the ``loaders`` section inside ``webpack`` tells webpack to use babel loader for JSX and json loader for json files.

#. Finally, edit "package.json" to change the npm test command to call karma:

.. comment: highlight as text since Pygments cannot parse partial json

.. code-block:: text

   "scripts": {
      "test": "karma start"
   },

Implement an Empty Component
----------------------------

Create a text file named "CategoryList.jsx" in
"ui\_react\_samples\_2/src".

.. comment: highlight as text since Pygments cannot parse jsx

.. code-block:: text

   var React = require('react');
   
   module.exports = React.createClass({
      render: function() {
         return <div></div>
      }
   });

Write the Unit Test
-------------------

#. Create a text file named "CategoryList-test.jsx" in
   "ui\_react\_samples\_2/src/\_\_tests\_\_".

   .. code-block:: javascript
      :linenos:
      :emphasize-lines: 24,25,29,30

      var React = require('react');
      var TestUtils = require('react-addons-test-utils');
      var expect = require('expect');
      var request = require('request');
      var CategoryList = require('../CategoryList.jsx');
      
      describe('CategoryList', function () {
      
         before(function(done){
            sinon
               .stub(request, 'get')
               .yields(  null,
                 {statusCode:200},
                 JSON.stringify([
                   {id:"192a433a-383e-4093-a21c-266b9a3031c2", name:"Category_1"},
                   {id:"3c55a8ac-5763-4dfd-9e1e-788e0e741400", name:"Category_2"},
                   {id:"3c55a8ac-5763-4dfd-9e1e-788e0e741401", name:"Category_3"}]));
            done();
         });
      
         it("renders an ul with lis", function () {
            var categoryList = TestUtils.renderIntoDocument(<CategoryList rootUrl={"foo"} />);
      
            var ul = TestUtils.findRenderedDOMComponentWithTag(
               categoryList, 'ul'
            );
            expect(ul).toExist();
      
            var lis = TestUtils.scryRenderedDOMComponentsWithTag(
               categoryList, 'li'
            );
            expect(lis.length).toBe(3);
         });
      
         after(function(done){
           request.get.restore();
           done();
         });
      
      }); 

#. In ``before``, we use sinon to stub any GET request to return successfully by statusCode 200 with a mock array of 3 categories as response. (See :ref:`GET_advancedSetting/category/(tenant\_id)` for sample of actual response.)
#. In ``"renders an ul with lis"``, we use React TestUtils to render the component with a dummy url, then use TestUtils functions to find and assert the UI elements.
#. In ``after``, we restore the original request.

Run the Unit Test
-----------------

#. In command-line, go to "ui\_react\_samples\_2" folder and run
   ``npm run --silent test``.
#. ``karma start`` should be called and after a while, open a Chrome
   browser window, then fail as expected with the messages
   ``CategoryList renders an ul with lis FAILED`` and
   ``Executed 1 of 1 (1 FAILED) ERROR``.

In next sections we will work on CategoryList code to make the unit test
succeed, as well as more tests to make use of React TestUtils'
``Simulate``.

Run the Component in Server
---------------------------

To run the component, we render it in a starting page, then use webpack
to bundle the page together with the libraries, then use
webpack-dev-server to serve the JavaScript bundle. This bundle will be
included in an HTML page served by the http-server.

#. Create the starting page named "index.jsx" in "ui\_react\_samples\_2"
   folder.

   .. code-block:: javascript

      var ReactDOM = require('react-dom');
      var CategoryList = require('./src/CategoryList');
      
      ReactDOM.render(<CategoryList rootUrl={"http://127.0.0.1:8888/api/"} />, document.getElementById('app')); 

#. Create the default webpack configuration file named "webpack.config.js" in "ui\_react\_samples\_2" folder.

   .. code-block:: javascript

      module.exports = {
          entry: './index.jsx',
          output: {
              filename: 'bundle.js',
              publicPath: 'http://localhost:8090/assets'
              // url to include the bundle in HTML page will be http://localhost:8090/assets/bundle.js
          },
          module: {
              loaders: [
                  {test: /\.jsx$/, loader: 'babel-loader', query: {presets: ['react', 'es2015']}},
                  {test: /\.json$/, loader: 'json'}
              ]
          },
          externals: {
              //don't bundle the 'react' npm package with our bundle.js
              //but get it from a global 'React' variable
              'react': 'React'
          },
          resolve: {
              extensions: ['', '.js', '.jsx']
          },
          node: {
            console: true,
            fs: 'empty',
            net: 'empty',
            tls: 'empty'
          }
      } 

#. Create the HTML page named "index.html" in "ui\_react\_samples\_2" folder.

   .. code-block:: html

      <!DOCTYPE html>
      <html>
      <head>
          <!-- include react -->
          <script src="./node_modules/react/dist/react-with-addons.js"></script>
      </head>
      <body>
          <div id="app">
              <!-- id="app" is where the react component will be rendered -->
          </div>
          <!-- include the webpack-dev-server script so changes are automatically reloaded -->
          <script src="http://localhost:8090/webpack-dev-server.js"></script>
          <!-- include the bundle from webpack -->
          <script type="text/javascript" src="http://localhost:8090/assets/bundle.js"></script>
      </body>
      </html> 

#. Add commands to "package.json" to start the server

   .. comment: highlight as text since Pygments cannot parse partial json

   .. code-block:: text

      "scripts": {
       "test": "karma start",
       "start": "npm run serve | npm run dev",
       "serve": "./node_modules/.bin/http-server -p 8080",
       "dev": "webpack-dev-server --progress --colors --port 8090"
      },

#. Start the server by running ``npm run start``.
#. Open browser and go to http://localhost:8080/ to see a blank page.

Implement CategoryList Component
--------------------------------

The JavaScript code is nearly the same as :doc:`code_react_manage_the_list_of_categories`, but without the HTML code.

.. comment: highlight as text since Pygments cannot parse jsx

.. code-block:: text

   var React = require('react');
   var request = require('request');
   
   module.exports = React.createClass({
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
         // TODO
       }
   });
   
The fetchData, pushData and removeCategory functions are now implemented using `request <https://www.npmjs.com/package/request>`__ library:

.. code-block:: javascript

    fetchData: function() {    
      request.get(
        {
         url: this.props.rootUrl + "advancedSetting/category/",
         headers: {"Content-Type": "application/json"},
         withCredentials: false
         },
        function (err, res, body) {
         if (!err && res.statusCode === 200) {
            this.setState({
              categoryArray: JSON.parse(body)
            });
         } else {
            console.log("Error in fetchData: " + JSON.stringify(res));
         }
        }.bind(this)
      );
    },
    pushData: function() {
      request.post(
        {
         url: this.props.rootUrl + "advancedSetting/category/",
         headers: {"Content-Type": "application/json"},
         withCredentials: false,
         body: JSON.stringify(this.state.categoryArray)
         },
        function (err, res, body) {
         var parsed_body = JSON.parse(body);
         if (!err && res.statusCode === 200) {
            if (!parsed_body.success) {
              console.log(JSON.stringify(res));
            }
            this.fetchData();
         } else {
            console.log(JSON.stringify(res));
            this.fetchData();
         }
        }.bind(this)
      );
    },
    removeCategory: function(id, event) {
      request.delete(
        {
         url: this.props.rootUrl + "advancedSetting/category/" + id,
         headers: {"Content-Type": "application/json"},
         withCredentials: false
         },
        function (err, res, body) {
         var parsed_body = JSON.parse(body);
         if (!err && res.statusCode === 200) {
            if (!parsed_body.success) {
              console.log(JSON.stringify(res));
            }
            this.fetchData();
         } else {
            console.log(JSON.stringify(res));
            this.fetchData();
         }
        }.bind(this)
      );
    }

The page at http://localhost:8080/ will automatically be refreshed each
time the code is updated.

Test Behaviors with React TestUtils
-----------------------------------

React TestUtils allow us to simulate mouse and keyboard events,
therefore provides a way to test the event handler code. Here we will
test that a new <li> tag is inserted when the Add button is clicked.

Between the functions ``"renders an ul with lis"`` and ``after``, add
the following function:

.. code-block:: javascript
   :linenos:
   :emphasize-lines: 16

   it("renders one more li when Add button is clicked", function () {
     var categoryList = TestUtils.renderIntoDocument(<CategoryList rootUrl={"foo"} />);
     
     var ul = TestUtils.findRenderedDOMComponentWithTag(
       categoryList, 'ul'
     );
   
     expect(ul).toExist();
     
     var buttons = TestUtils.scryRenderedDOMComponentsWithTag(
       categoryList, 'button'
     );
     
     var addButton = buttons[0];
     
     TestUtils.Simulate.click(addButton);
     
     var lis = TestUtils.scryRenderedDOMComponentsWithTag(
       categoryList, 'li'
     );
   
     expect(lis.length).toBe(4);
   }); 
