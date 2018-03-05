===================
IAdHocExtension
===================

**IAdHocExtension** interface in Izenda.BI.Framework.CustomConfiguration defines the extension APIs that allows customization code to hook in the report life cycle.

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - Customized Behavior
     - Method & Sample
     - Description
   * - Filter data tree lookup
     - `OnPreLoadFilterDataTree`_
     - Allows customizing the tree of filter values displayed for selection under Report Designer filter fields, Equals (Tree) dropdown menu. This has extra report filter settings, which contains the other filter values selected by the user in the report. This allows for easy set up of cascading behavior in your custom code. If this is implemented OnLoadFilterDataTree will be ignored.  
   * - Filter data tree lookup (To be deprecated in 3.0.0)
     - `OnLoadFilterDataTree`_
     - Allows customizing the tree of filter values displayed for selection under Report Designer filter fields, Equals (Tree) dropdown menu. This will be deprecated in favor of OnPreLoadFilterDataTree, please make plans to convert to this implementation prior to release of 3.0.0 
   * - Customize filter data tree lookup results
     - `OnPostLoadFilterDataTree`_
     - Allows override of the filter tree just before the results are returned to the user.
   * - Filter data
     - `OnPreLoadFilterData`_
     - Allows injecting report filter data instead of querying the database
   * - Filter data display
     - `OnPostLoadFilterData`_
     - Allows overriding filter values displayed for selection under Report Designer filter fields
   * - ReportDefinition object
     - `OnPreExecute`_
     - Allows on-the-fly customization of the report content
   * - Data source query tree
     - `OnExecuting`_
     - Allows customizing the data source query tree
   * - Data source query results
     - `OnPostExecute`_
     - Allows customizing the execution result of data source queries
   * - Hidden report filters
     - `SetHiddenFilters`_
     - Adds customized filters to reports while hiding them from UI users
   * - Custom In Time Period Filters
     - `CustomTimePeriod`_
     - Adds custom In Time Period Filter Values
   * - Load Custom Data Format
     - `LoadCustomDataFormat`_
     - Adds custom data formats for specified data types
   * - WebUrlResolver
     - `IWebUrlResolver`_
     - Allow overriding the DefaultWebUrlResolver and customizing the way the application generates the Front End URL.	 


The companion wrapper class **DefaultAdHocExtension** in  Izenda.BI.Framework.CustomConfiguration should be used as the base class for customization.

.. figure:: /_static/images/DefaultAdHocExtension_class.png

   DefaultAdHocExtension class

.. seealso::

   :doc:`Full-code Samples for all IAdHocExtension Methods <code_iadhocextension_samples>`

OnPreLoadFilterDataTree
-----------------------------------

``List<ValueTreeNode> OnPreLoadFilterDataTree(ReportFilterField filterField, ReportFilterSetting filterSetting, out bool handled)``

This method customizes the behavior of :ref:`POST_report/loadFilterFieldDataAsTree` and :ref:`POST_dashboard/loadFilterFieldDataAsTree` APIs.

   .. code-block:: csharp

       public override List<ValueTreeNode> OnPreLoadFilterDataTree(ReportFilterField filterField, ReportFilterSetting filterSetting, out bool handled)
       {
         handled = false; 
         var result = new List<ValueTreeNode>(); 
         var shipCountry = filterSetting.FilterFields.FirstOrDefault(f => f.SourceFieldName == "ShipCountry"); 
         if (filterField.SourceFieldName == "ShipCity" && shipCountry != null) 
         { 
             if(shipCountry.Value == "Argentina") 
             { 
                 handled = true; 
                 var rootNode = new ValueTreeNode { Text = "[All]", Value = "[All]" }; 
                 rootNode.Nodes = new List<ValueTreeNode>(); 
                 rootNode.Nodes.Add(new ValueTreeNode { Text = "Buenos Aires", Value = "Buenos Aires" }); 
                 rootNode.Nodes.Add(new ValueTreeNode { Text = "Mendoza", Value = "Mendoza" }); 
                 rootNode.Nodes.Add(new ValueTreeNode { Text = "Salta", Value = "Salta" }); 
                 result.Add(rootNode); 
             } 
         } 
         return result; 
       }

OnLoadFilterDataTree
-----------------------------------

``List<ValueTreeNode> OnLoadFilterDataTree(QuerySourceFieldInfo fieldInfo)``

This method customizes the behavior of :ref:`POST_report/loadFilterFieldDataAsTree` and :ref:`POST_dashboard/loadFilterFieldDataAsTree` APIs.

For example, the API can be customized to return a list of cities per country in a hierarchy like this::

   All
     +--Argentina
        +--Buenos Aires
     +--France
        +--Lille
        +--Lyon
        +--Marseille

Sample code to display All > South America and North America for Manager role:

   .. code-block:: csharp

       [Export(typeof(IAdHocExtension))]
       public class AdHocExtensionSample : DefaultAdHocExtension
       {
         public override List<ValueTreeNode> OnLoadFilterDataTree(QuerySourceFieldInfo fieldInfo)
         {
              var result = new List<ValueTreeNode>();
      
              if (fieldInfo.QuerySourceName == "OrderDetailsByRegion" && fieldInfo.Name == "CountryRegionName"
                  && HttpContext.Current.User.IsInRole("Manager"))
              {
                  // Node [All] is required for UI to render.
                  var rootNode = new ValueTreeNode { Text = "[All]", Value = "[All]" };
                  rootNode.Nodes = new List<ValueTreeNode>();
                  rootNode.Nodes.Add(new ValueTreeNode { Text = "South America", Value = "South America" });
                  rootNode.Nodes.Add(new ValueTreeNode { Text = "North America", Value = "North America" });
      
                  result.Add(rootNode);
              }
      
              return result;
         }
       }
      
OnPostLoadFilterDataTree
-----------------------------------

``List<ValueTreeNode> OnPostLoadFilterDataTree(ReportFilterField filterField, List<ValueTreeNode> data, ReportFilterSetting filterSetting)``

This method customizes the behavior of :ref:`POST_report/loadFilterFieldDataAsTree` and :ref:`POST_dashboard/loadFilterFieldDataAsTree` APIs.

   .. code-block:: csharp

       public override List<ValueTreeNode> OnPostLoadFilterDataTree(ReportFilterField filterField, List<ValueTreeNode> data, ReportFilterSetting filterSetting)
       {
         var shipCountry = filterSetting.FilterFields.FirstOrDefault(f => f.SourceFieldName == "ShipCountry"); 
         if (filterField.SourceFieldName == "ShipCity" && shipCountry != null) 
         { 
             if (shipCountry.Value == "Argentina") 
             { 
                 var rootNode = data[0]; 
                 rootNode.Nodes.Add(new ValueTreeNode { Text = "La Plata - After", Value = "La Plata" }); 
             } 
         } 

         return data; 
       }
       
OnPreLoadFilterData
-------------------

``List<string> OnPreLoadFilterData(ReportFilterSetting filterSetting, out bool handled)``

This method allows injecting report filter data instead of querying the database.

* if ``handled`` is false (not set), system will ignore the output and query the database for filter values.
* if ``handled`` is set to true, system will take the output as filter values and skip the database query.


For example, it can be used to:

* skip time-consuming database queries when the list of values is predictable: true and false, list of regions (although there is no warranty that the injected values actually have data in the database)
* disable filtering by returning null in some conditions


Sample code to use a pre-defined list for filters on OrdersByRegion.CountryRegionName:

.. code-block:: csharp

    [Export(typeof(IAdHocExtension))]
    public class AdHocExtensionSample : DefaultAdHocExtension
    {
      public override List<string> OnPreLoadFilterData(ReportFilterSetting filterSetting, out bool handled)
      {
           handled = false;
           List<String> result = null;
   
           if (filterSetting.FilterFields.Count == 1
               && filterSetting.FilterFields.Any(
                   x   =>  x.SourceDataObjectName.Equals("OrdersByRegion")
                           && x.SourceFieldName.Equals("CountryRegionName")))
           {
               handled = true;
               result = new List<string>()
               {
                   "Europe",
                   "North America",
                   "South America"
               };
           }
   
           return result;
      }
    }

OnPostLoadFilterData
---------------------

``List<string> OnPostLoadFilterData(ReportFilterField filterField, List<string> data)``

This method allows overriding filter values displayed for selection under Report Designer filter fields.


For example, it can be used to:
* do a secondary lookup on filter values returned from system to add more information such as appending population to city names
* format values returned from system for example to proper case or title case
* add or remove values from the list


Sample code to change Europe to EU for Employee role:

.. code-block:: csharp

    [Export(typeof(IAdHocExtension))]
    public class AdHocExtensionSample : DefaultAdHocExtension
    {
      public override List<string> OnPostLoadFilterData(ReportFilterField filterField, List<string> data)
      {
           // override dropdown value based on user role for filter on view "OrderDetailsByRegion" and field "CountryRegionName"
           if (filterField.SourceDataObjectName == "OrderDetailsByRegion" && filterField.SourceFieldName == "CountryRegionName"
               && HttpContext.Current.User.IsInRole("Employee"))
           {
             var indexEU = data.IndexOf("Europe");
             if (indexEU != -1)
               data[indexEU] = "EU";
           }
           return base.OnPostLoadFilterData(filterField, data);
      }
    }

OnPreExecute
-------------------

``ReportDefinition OnPreExecute(ReportDefinition reportDefinition)``

This method allows customizing the report content on the fly before it is run.

For example, it can be used to:

* customize the data sources, relationships, filters and calculated fields
* customize the report parts settings

Sample code to remove all Map report parts on-the-fly:

.. code-block:: csharp

    [Export(typeof(IAdHocExtension))]
    public class AdHocExtensionSample : DefaultAdHocExtension
    {
      public override ReportDefinition OnPreExecute(ReportDefinition report)
      {
           if (report.ReportPart.Any(x => x.ReportPartContent.Type == ReportPartContentType.Map))
           {
               var filteredReportPart = report.ReportPart.Where(x => x.ReportPartContent.Type != ReportPartContentType.Map).ToList();
               report.ReportPart = filteredReportPart;
           }
   
           return report;
      }
    }

OnExecuting
-------------

``QueryTree OnExecuting(QueryTree queryTree)``

This method allows customizing the data source queries on the fly before it is run.

For example, it can be used to:

* inspect the query steps
* customize the operations such as adding a limit operator or re-ordering the sequence

.. figure:: /_static/images/QueryTree_Sample.png

   QueryTree Sample


Sample code to log all operations without a result limit operator:

.. code-block:: csharp

    [Export(typeof(IAdHocExtension))]
    public class AdHocExtensionSample : DefaultAdHocExtension
    {
      public override QueryTree OnExecuting(QueryTree queryTree)
      {
           var nodeVisitor = new QueryTreePathAnalyzeVisitor(new ExtensibilityFactory(), queryTree.ContextData);
           nodeVisitor.ContextData = queryTree.ContextData;
           queryTree.Root.Accept(nodeVisitor);
   
           var resultLimitOperator = new ResultLimitOperator()
           {
               ChildOperand = new Operand()
               {
                   QuerySource = new QuerySource()
               }
           };
   
           try
           {
               nodeVisitor.Visit(resultLimitOperator);
           }
           catch (Exception)
           {
               Console.WriteLine("LOG: Query with no limit");
           }
   
           return queryTree;
      }
    }

OnPostExecute
-----------------

``List<IDictionary<string, object>> OnPostExecute(QueryTree executedQueryTree, List<IDictionary<string, object>> result)``

This method allows customizing the execution result of data source queries.

For example, it can be used to:
* inspect the execution result
* alter the execution result such as adding and removing rows or changing data values

Sample code to limit the execution result to the first 1000 rows only (although the database may return more than that):

.. code-block:: csharp

    [Export(typeof(IAdHocExtension))]
    public class AdHocExtensionSample : DefaultAdHocExtension
    {
      public override List<IDictionary<string, object>> OnPostExecute(QueryTree executedQueryTree, List<IDictionary<string, object>> result)
      {
           return result.Take(1000).ToList();
      }
    }

.. _SetHiddenFilters:

SetHiddenFilters
--------------------

``ReportFilterSetting SetHiddenFilters(SetHiddenFilterParam param)``

This method adds customized filters to every reports while hiding them from UI users.

For example, it can be used to:

* filter data to rows with ShipRegion = 'WA' or BLANK only.
* automatically filter all tables to non-deleted data (IsDeleted = FALSE).
* in a Shared Schema Multi-Tenant Architecture, filter every table to only data of the tenant of current logged in user.

Sample code to add hidden filter ShipRegion = "WA" or "[Blank]" for all:

.. comment: Not highlighted: Pygments does not support interpolated string in C# 6 yet https://bitbucket.org/birkenfeld/pygments-main/issues/1138/supporting-c-60

.. code-block:: csharp

     [Export(typeof(IAdHocExtension))]

        public override ReportFilterSetting SetHiddenFilters(SetHiddenFilterParam param)
        {
            var filterFieldName = "ShipRegion";

            Func<ReportFilterSetting, int, QuerySource, QuerySourceField, Guid, Relationship, int> addHiddenFilters = (result, filterPosition, querySource, field, equalOperator, rel) =>
            {
                var firstFilter = new ReportFilterField
                {
                    Alias = $"ShipRegion{filterPosition}",
                    QuerySourceId = querySource.Id,
                    SourceDataObjectName = querySource.Name,
                    QuerySourceType = querySource.Type,
                    QuerySourceFieldId = field.Id,
                    SourceFieldName = field.Name,
                    DataType = field.DataType,
                    Position = ++filterPosition,
                    OperatorId = equalOperator,
                    Value = "WA",
                    RelationshipId = rel?.Id,
                    IsParameter = false,
                    ReportFieldAlias = null
                };

                var secondFilter = new ReportFilterField
                {
                    Alias = $"ShipRegion{filterPosition}",
                    QuerySourceId = querySource.Id,
                    SourceDataObjectName = querySource.Name,
                    QuerySourceType = querySource.Type,
                    QuerySourceFieldId = field.Id,
                    SourceFieldName = field.Name,
                    DataType = field.DataType,
                    Position = ++filterPosition,
                    OperatorId = equalOperator,
                    Value = "[Blank]",
                    RelationshipId = rel?.Id,
                    IsParameter = false,
                    ReportFieldAlias = null
                };
                result.FilterFields.Add(firstFilter);
                result.FilterFields.Add(secondFilter);

                var logic = $"({filterPosition - 1} OR {filterPosition})";
                if (string.IsNullOrEmpty(result.Logic))
                {
                    result.Logic = logic;
                }
                else
                {
                    result.Logic += $" AND {logic}";
                }

                return filterPosition;
            };

            var filterSetting = new ReportFilterSetting()
            {
                FilterFields = new List<ReportFilterField>()
            };
            var position = 0;

            var ds = param.ReportDefinition.ReportDataSource;

            // Build the hidden filters for ship country fields
            foreach (var querySource in param.QuerySources // Scan thru the query sources that are involved in the report
                .Where(x => x.QuerySourceFields.Any(y => y.Name.Equals(filterFieldName, StringComparison.OrdinalIgnoreCase)))) // Take only query sources that have filter field name
            {
                // Pick the relationships that joins the query source as primary source
                // Setting the join ensure the proper table is assigned when using join alias in the UI
                var rels = param.ReportDefinition.ReportRelationship.
                    Where(x => x.JoinQuerySourceId == querySource.Id)
                    .ToList();

                // Count the relationships that the filter query source is foreign query source
                var foreignRelCounts = param.ReportDefinition.ReportRelationship
                    .Where(x => x.ForeignQuerySourceId == querySource.Id)
                    .Count();

                // Find actual filter field in query source
                var field = querySource.QuerySourceFields.FirstOrDefault(x => x.Name.Equals(filterFieldName, StringComparison.OrdinalIgnoreCase));

                // Pick the equal operator
                var equalOperator = Izenda.BI.Framework.Enums.FilterOperator.FilterOperator.EqualsManualEntry.GetUid();

                // In case there is no relationship that the query source is joined as primary
                if (rels.Count() == 0)
                {
                    // Just add hidden filter with null relationship
                    position = addHiddenFilters(filterSetting, position, querySource, field, equalOperator, null);
                }
                else
                {
                    // Add another hidden filter for query source that appears in both alias primary and foreign query source of relationships.
                    // This step is mandatory because when aliasing a primary query source, it becomes another instance of query source in the query. 
                    // So if we only add filter for alias, the original query source instance will not be impacted by the filter. That's why we need
                    // to add another filter for original instance when it appears in both side of alias and foreign.
                    // For example:
                    //          [Order] LEFT JOIN [Employee]
                    //      [Aliased Employee] LEFT JOIN [Department]
                    // If the system needs to add a hidden filter to [Employee], for example: [CompanyId] = 'ALKA'
                    // It needs to add
                    //          [Employee].[CompanyId] = 'ALKA' AND [Aliased Employee].[CompanyId] = 'ALKA'
                    // By this way, it ensures all [Employee] instances are filtered by ALKA company id.
                    if (foreignRelCounts > 0)
                    {
                        position = addHiddenFilters(filterSetting, position, querySource, field, equalOperator, null);
                    }
                    
                    foreach (var rel in rels)
                    {
                        // Loop thru all relationships that the query source is joined as primary and add the hidden field associated with each relationship
                        position = addHiddenFilters(filterSetting, position, querySource, field, equalOperator, rel);
                    }
                }
            }

            return filterSetting;
        }

Application Scenarios
-----------------------

Hidden filters can be applied based on several values. For example,

User Name::

   var currentUser = UserContext.Current;
   var currentUserName = currentUser.CurrentUser.UserName;

   if (String.Compare(currentUserName, "userName") == 0)
   {
      //Filter Logic Goes Here
   }

Tenant Name::

   var currentUser = UserContext.Current;
   var currentTenantName = currentUser.CurrentTenant.Name;

   if (String.Compare(currentTenantName, "TestTenant") == 0)
   {
          //Filter Logic Goes Here
   }

Role Name::

   var currentUser = UserContext.Current;
   var currentUserRoles = currentUser.Roles.Select(x => x.Name).ToList();

   if (String.Compare(currentUserRoles[0], “Administrator”) == 0)
   {
          //Filter Logic Goes Here
   }

Role Name (Alternative Method)::

   var currentUser = UserContext.Current;

   if (currentUser.IsInRole("Administrator")
   {
          //Filter Logic Goes Here
   }

Schema Notation::

   public override ReportFilterSetting SetHiddenFilters(SetHiddenFilterParam param)
   {
        var queryCategory = param.QuerySources.First(x => x.Name.Equals("Orders")).QuerySourceCategoryName;

        if (String.Compare(queryCategory, "dbo") == 0)
        {
             //Filter Logic Goes Here
        }
   }


Query Source::

   public override ReportFilterSetting SetHiddenFilters(SetHiddenFilterParam param)
   {
        var querySouce = param.QuerySources.First(x => x.Name.Equals("TableName"));

        if (String.Compare(querySource.Type, "Table") == 0)
        {
             //Filter Logic Goes Here
        }
   }


Applying Filter with Compounded Values
-----------------------------------------

In some scenarios, you will require several values passed into the same filter, which get applied according to the logic you provide.

.. code-block:: csharp

   if (String.Compare(currentUserName, "userName") == 0)
   {
        result.Logic = "(1 or 2 or 3)"; //The logic, something like "1 AND 2 OR 3"

        //Equal operator
        var equalOperator = param.FilterOperatorGroups.First(x => x.Name.Equals("Equivalence")).FilterOperators
             .First(x => x.Name.Equals("Equals (Selection)"));

        //Filter Order.ShipContry = USA
        string[] valArray = { "USA", "Argentina", "Germany" };
        var querySouce = param.QuerySources.First(x => x.Name.Equals("Orders"));
        var field = querySouce.QuerySourceFields.First(x => x.Name.Equals("ShipCountry"));

        for (int i = 0; i < valArray.Length; i++)
        {
             var reportFilterField = new ReportFilterField
             {
                  QuerySourceId = querySouce.Id,
                  SourceDataObjectName = querySouce.Name,
                  QuerySourceType = querySouce.Type,
                  QuerySourceFieldId = field.Id,
                  SourceFieldName = field.Name,
                  DataType = field.DataType,
                  Position = i+1,
                  OperatorId = equalOperator.Id,
                  Value = valStr[i],
                  RelationshipId = null,
                  IsParameter = false,
                  ReportFieldAlias = null
             };

             filterFields.Add(reportFilterField);
        }
   }

.. _CustomTimePeriod:

CustomTimePeriod
-----------------------------------

``public override List<CustomTimePeriod> LoadCustomTimePeriod()``

NOTE: This method is only available in v1.24.0 or higher

You can create custom time period filters for various datatypes by overriding the LoadCustomTimePeriod in your DefaultAdHocExtension implementation.

.. code-block:: csharp

    using Operator = Izenda.BI.Framework.Enums.DateTimeOperator;

    [Export(typeof(IAdHocExtension))]
    public class CustomAdhocReport : DefaultAdHocExtension
    {
        public override List<CustomTimePeriod> LoadCustomTimePeriod()
        {
            var result = new List<CustomTimePeriod>
            {
                new CustomTimePeriod("Tomorrow",
                    DateTime.Now, DateTime.Now.AddDays(1), Operator.BetweenDateTime),
                new CustomTimePeriod("Previous Date -> DateTime Now",
                   () => DateTime.Now.AddDays(-1), () => DateTime.Now, Operator.BetweenDateTime),
                new CustomTimePeriod("Less Than 2 Days Old",
                    2, Operator.LessThanDaysOld),
                new CustomTimePeriod("Greater Than 2 Days Old",
                   () => 2, Operator.GreaterThanDaysOld),
                new CustomTimePeriod(">= Date Time Now + 2 Days",    
                    DateTime.Now.AddDays(2), Operator.GreaterThanOrEqualsCalender),
                new CustomTimePeriod("<= Date Time Now - 2 Days",
                   () => DateTime.Now.AddDays(-2), Operator.LessThanOrEqualsCalendar)
            };

            return result;
        }
    }

.. _LoadCustomDataFormat:

LoadCustomDataFormat
-----------------------------------

``public override List<DataFormat> LoadCustomDataFormat()``

.. note:: 
   * This method is only available in v1.24.0 or higher. |br| |br|

   * You can create custom formats for various datatypes by overriding the LoadCustomDataFormat in your DefaultAdHocExtension implementation. |br| |br|

   * From v2.6.19, :doc:`../ref/models/DataFormat` object has 1 new field: JsFormatString

     - JsFormatString is used for optimizing chart axes lables

     - If DataFormat contains both FormatFunc and JsFormatString, the JsFormatString will be more precede. |br| |br|

   * New in v2.6.20, if JsFormatString does not contain braces {} that means the value of jsFormatString is the name of the funtion will be obtained in the FE to apply in the chart. |br|
     User must ensure  to register the format function by using :ref:`Front-end integration API: addJsFormat(formatName, formatFunction) <addJsFormat>`.

.. code-block:: csharp

        /// <summary>
        /// Loads the defined custom formats into the Izenda application
        /// 
        /// <see href="https://msdn.microsoft.com/en-us/library/dwhawy9k(v=vs.110).aspx">Standard Numeric Format Strings</see>
        /// </summary>
        /// <returns>A list of custom formats. </returns>
         public override List<DataFormat> LoadCustomDataFormat()

        {

            var result = new List<DataFormat>

            {

                new DataFormat
                {
                    Name = "By Hour",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        return ((DateTime)x).ToString("M/d/yyyy h:00 tt");
                    }
                },
       
                new DataFormat
                {
                    Name = "dd MM:mm",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        var date = Convert.ToDateTime(x);
                        return date.ToString("dd HH:mm");
                    }
                },
                new DataFormat
                {
                    Name = "dd HH:mm:ss",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        var date = Convert.ToDateTime(x);
                        return date.ToString("dd HH:mm:ss");
                    }
                },
                new DataFormat
                {
                    Name = "dd mm:ss",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        var date = Convert.ToDateTime(x);
                        return date.ToString("dd mm:ss");
                    }
                },
                new DataFormat
                {
                    Name = "£0,000",
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        return ((decimal)x).ToString("C0", CultureInfo.CreateSpecificCulture("en-GB"));
                    }
                },
                new DataFormat
                {
                    Name = "¥0,000",
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        return ((decimal)x).ToString("C0", CultureInfo.CreateSpecificCulture("ja-JP"));
                    }

                },
                new DataFormat
                {
                    Name = "0,000",
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        return String.Format(CultureInfo.InvariantCulture, "{0:0,0}", x);
                    }

                },
                new DataFormat
                {
                    Name = "$0,000",
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        return String.Format(CultureInfo.InvariantCulture, "${0:0,0}", x);
                     }
                },

                new DataFormat
                {
                    Name = "HH:MM:SS",
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    FormatFunc = (x) =>
                    {
                        var newValue = Convert.ToDouble(x);
                        TimeSpan time = TimeSpan.FromSeconds(newValue);

                        return time.ToString(@"dd\.hh\:mm\:ss");
                    }

                }

                // Note: new in version 2.6.19
                // Custom DataFormat use JsFormatString

                new DataFormat
                {
                    Name = "2f km", //example: 2.00 km.
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "{value:.2f} km."
                },

                new DataFormat
                {
                    Name = "millisecond",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "{value:%A, %b %e, %H:%M:%S.%L}",
                        //A: Day of week
                        //B: Month 
                        //b: Abbreviations of Month
                        //e: Day
                        //H: Hour
                        //M: Minute
                        //S: Second
                        //L: Millisecond
                    FormatDataType = DataType.DateTime
                },
                
                new DataFormat
                {
                    Name = "second",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "{value:%H:%M:%S}",
                        //H: Hour
                        //M: Minute
                        //S: Second
                    FormatDataType = DataType.DateTime
                },

                new DataFormat
                {
                    Name = "minute",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "{value:%M}",
                    FormatDataType = DataType.DateTime
                },

                new DataFormat
                {
                    Name = "hour",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "{value:%H:%M}",
                },

                new DataFormat
                {
                    Name = "day",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString ="{value:%A, %B %e, %Y}",
                        //A: Day of week
                        //B: Month 
                        //Y: Year
                    FormatDataType = DataType.DateTime
                },

                new DataFormat
                {
                    Name = "week",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString ="Week from {value:%A, %B %e, %Y}",
                        //A: Day of week
                        //B: Month 
                        //Y: Year
                    FormatDataType = DataType.DateTime
                },

                new DataFormat
                {
                    Name = "month",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString ="{value:%B %Y}",
                    FormatDataType = DataType.DateTime
                },

                new DataFormat
                {
                    Name = "year",
                    DataType = DataType.DateTime,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString ="Year {value:%Y}",
                    FormatDataType = DataType.DateTime
                }

                //new in version 2.6.20
                new DataFormat
                {
                    Name = "2f km", //example: 2.00 km.
                    DataType = DataType.Numeric,
                    Category = IzendaKey.CustomFormat,
                    JsFormatString = "1k" //The name of the js format function
                }

            };

            return result;

        }
		

IWebUrlResolver
-----------------------------------

``public override IWebUrlResolver WebUrlResolver => new CustomWebUrlResolver();``

NOTE: This method is only available in v2.6.9 or higher

This property will allow you to override the DefaultWebUrlResolver and customize the way the application generates the Front End URL. This can be used when sending report and dashboard links via emails, schedules and subscriptions. Additionally you can now customize the URLS for ViewReport, ViewDashboard, ViewReportPart, etc.

Step 1: Implement IWebUrlResolver or inherit from DefaultWebUrlResolver


.. code-block:: csharp

	public class CustomWebUrlResolver : DefaultWebUrlResolver
	{
		private readonly ILog logger;

		public CustomWebUrlResolver()
		{
			this.logger = (new LogManager()).GetLogger<CustomWebUrlResolver>();
		}

		public override string ResolveUrl(string baseUrl, WebUrlActionLink action, Guid? id, Dictionary<string, object> parameters = null)
		{
			logger.Info($"Resolving the url of {action} on base url {baseUrl}");
			// Put logic to custom the web url here
			return base.ResolveUrl(baseUrl, action, id, parameters);
		}
	}
	
	
Step 2: Override WebUrlResolver property of DefaultAdhocExtension

.. code-block:: csharp

	[Export(typeof(IAdHocExtension))]
	public class CustomAdhocReport : DefaultAdHocExtension
	{
		public override IWebUrlResolver WebUrlResolver => new CustomWebUrlResolver();
	}
    
See Also
-----------

The :doc:`UserContext.Current </ref/models/UserContext>` object contains data of the current logged in user, which can be leveraged in filters:

*  to check if user has "Report Designer" role: |br| ``UserContext.Current.IsInRole("Report Designer")``
*  to check if user belongs to "ACME" tenant: |br| ``UserContext.Current.CurrentTenant.TenantID == "acme"``
*  to check if user has permission to create new reports: |br| ``UserContext.Current.Permissions.Reports.CanCreateNewReport.Value == TRUE``
