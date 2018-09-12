==================================
Izenda Functions
==================================

List of Built-in Functions
--------------------------

.. list-table::
   :widths: 20 45 15 20
   :header-rows: 1

   * - Function
     - Description
     - Result Data Types
     - Examples
   * - **AVG** |br| |br|
       ``AVG(expression)`` |br| |br|
       Numeric, Money
     - Returns the average of the values in a group. Null values are ignored.
     - Numeric, Money
     - ``AVG([Retail].[dbo].[Orders].[Freight])``
   * - **COUNT** |br| |br|
       ``COUNT(expression)`` |br| |br|
       Any data type except Image and Lob.
     - Returns the number of items in a group.
     - Numeric.
     - ``COUNT([Retail].[dbo].[Orders].[OrderID])``
   * - **MAX** |br| |br|
       ``MAX(expression)`` |br| |br|
       Any data type except Image and Lob.
     - Returns the maximum value in a group.
     - The same data type as expression.
     - ``MAX([Retail].[dbo].[Orders].[Freight])``
   * - **MIN** |br| |br|
       ``MIN(expression)`` |br| |br|
       Any data type except Image and Lob.
     - Returns the minimum value in a group.
     - The same data type as expression.
     - ``MIN([Retail].[dbo].[Orders].[Freight])``
   * - **SUM** |br| |br|
       ``SUM(expression)`` |br| |br|
       Numeric, Money.
     - Returns the sum of all the values in a group. Null values are ignored.
     - The same data type as expression.
     - ``SUM([Retail].[dbo].[Orders].[Freight])``
   * - **LEN** |br| |br|
       ``LEN(expression)`` |br| |br|
       Text.
     - Returns the number of characters of the given text expression, excluding trailing blanks.
     - Numeric.
     - ``LEN([Retail].[dbo].[Orders].[ShipAddress])``
   * - **ROUND** |br| |br|
       ``ROUND(expression)`` |br| |br|
       Numeric, Money.
     - Returns the expression rounded to the specified length or precision.
     - The same data type as expression.
     - ``ROUND([Retail].[dbo].[Orders].[Freight],0)``
   * - **CONCAT** |br| |br|
       ``CONCAT(expression, expression [, ...])`` |br| |br|
       Text.
     - Returns the concatenation of all the parameters in that exact order.
     - Text.
     - ``CONCAT('ab','cd',[SHIPCOUNTRY])``
   * - **GETDATE** |br| |br|
       ``GETDATE()`` |br| |br|
       N/A.
     - Returns the current system date and time.
     - Datetime.
     - ``GETDATE()``
   * - **DATEADD** |br| |br|
       ``DATEADD(datepart, number, date)`` |br| |br|
       **datepart**: the part of the date. (See table `List of Dateparts and Abbreviations`_) |br| |br|
       **number**: the value used to increment datepart. |br| |br|
       **date**: an expression that returns a datetime value.
     - Returns a new datetime value based on adding an interval to the specified date.
     - Datetime.
     - ``DATEADD(day,3,[DueDate])``
   * - **DATEDIFF** |br| |br|
       ``DATEDIFF(datepart, startdate, enddate)`` |br| |br|
       **datepart**: the part of the date. (See table `List of Dateparts and Abbreviations`_) |br| |br|
       **startdate**, **enddate**: expressions that return datetime values.
     - Returns the number of date and time boundaries crossed between two specified dates.
     - Numeric.
     - ``DATEDIFF(day,[OrderDate],[ShipDate])`` |br| |br|
   * - **DATEPART** |br| |br|
       ``DATEPART(datepart, date)`` |br| |br|
       **datepart**: the part of the date. (See table `List of Dateparts and Abbreviations`_) |br| |br|
       **date**: an expression that returns a datetime value.
     - Returns a number representing the specified datepart of the specified date.
     - Numeric.
     - ``DATEPART(DAY,[Retail].[dbo].[Orders].[OrderDate])``
   * - **CONVERT** |br| |br|
       ``CONVERT(data_type, expression)`` |br| |br|
       **data_type**: any data type. |br| |br|
       **expression**: any expression.
     - Explicitly converts an expression of one data type to another, similar to ``CAST..AS``.
     - The same data type as data_type.
     - ``CONVERT(TEXT,[Retail].[dbo].[Orders].[OrderDate])``
   * - **CAST..AS** |br| |br|
       ``CAST(expression AS data_type)`` |br| |br|
       **data_type**: any data type. |br| |br|
       **expression**: any expression.
     - Explicitly converts an expression of one data type to another, similar to ``CONVERT``.
     - The same data type as data_type.
     - ``CAST([Retail].[dbo].[Orders].[OrderID] AS TEXT)``
   * - **ISNULL** |br| |br|
       ``ISNULL(check_expression, replacement_expression)`` |br| |br|
       **check_expression** and **replacement_expression**: any data type.
     - Returns the value of check_expression if it is not NULL; otherwise, returns the value of replacement_expression.
     - The same data type as expression.
     - ``ISNULL([Retail].[dbo].[Orders].[ShipRegion] , 'No Region')``
   * - **BETWEEN..AND** |br| |br|
       ``BETWEEN(expression, begin_expression, end_expression)`` |br| |br|
       Any data type except Image and Lob.
     - Returns TRUE if the value of test_expression is greater than or equal to the value of begin_expression and less than or equal to the value of end_expression, otherwise returns FALSE.
     - Boolean.
     - ``CASE WHEN (BETWEEN ([Retail].[dbo].[Orders].[EmployeeID],1 , 3)) THEN 1000 else [Retail].[dbo].[Orders].[EmployeeID] END``
   * - **AND** |br| |br|
       ``boolean_expression AND boolean_expression`` |br| |br|
       Boolean.
     - Returns TRUE when both expressions are TRUE, otherwise returns FALSE.
     - Boolean.
     - ``CASE WHEN ([Retail].[dbo].[Orders].[EmployeeID] = 1 AND [Retail].[dbo].[Orders].[CustomerID] = 'DELDG') THEN 1000 else [Retail].[dbo].[Orders].[EmployeeID] end``
   * - **OR** |br| |br|
       ``boolean_expression AND boolean_expression`` |br| |br|
       Boolean.
     - Returns TRUE when either expression is TRUE, otherwise returns FALSE.
     - Boolean.
     - ``CASE WHEN ([Retail].[dbo].[Orders].[EmployeeID] = 1 OR [Retail].[dbo].[Orders].[EmployeeID] = 2) THEN 1000 else [Retail].[dbo].[Orders].[EmployeeID] end``
   * - **DISTINCT** |br| |br|
       ``DISTINCT (expression)`` or ``DISTINCT expression`` |br| |br|
       Any data type except Image and Lob.
     - Returns unique values.
     - The same data type as expression.
     - ``COUNT(DISTINCT([Northwind].[dbo].[Orders].[ShipCity]))``
   * - **IFF** |br| |br|
       ``IFF (boolean_expression, true_expression[, false_expression])`` |br| |br|
       **boolean_expression**: Boolean. |br| |br|
       **true_expression**, **false_expression**: any data type except Image and Lob.
     - Returns the value of true_expression when boolean_expression is TRUE, otherwise returns the value of false_expression.
     - The highest precedence data type from data types of true_expression and false_expression.
     - ``IIF([Retail].[dbo].[Orders].[EmployeeID] = 2, 200, [Retail].[dbo].[Orders].[EmployeeID])``
   * - **IF..THEN..ELSE..END** |br| |br|
       ``IF (boolean_expression) THEN (true_expression) [ELSE (false_expression)] END`` |br| |br|
       **boolean_expression**: Boolean. |br| |br|
       **true_expression**, **false_expression**: any data type except Image and Lob.
     - Returns the value of true_expression when boolean_expression is TRUE, otherwise returns the value of false_expression.
     - The highest precedence data type from data types of true_expression and false_expression.
     - ``IF ([northwind].[dbo].[Orders].[EmployeeID] < 3) then 'Less' else ( IF (BETWEEN ([northwind].[dbo].[Orders].[EmployeeID] , 3, 6)) then  'More' else 'Most' END) END``
   * - **CASE WHEN...THEN...ELSE...END** |br| |br|
       ``CASE WHEN (when_expression) THEN (result_expression) […n] [ELSE (else_result_expression)] END`` |br| |br|
       Any data type except Image and Lob.
     - Returns the value of result_expression matching the first when_expression with the value equal to input_expression, otherwise return the value of else_result_expression.
     - The highest precedence data type from data types of all ``result_expression`` s and else_result_expression.
     - ``Case when ([northwind].[dbo].[Orders].[EmployeeID] = 1) then 'less' when ([northwind].[dbo].[Orders].[EmployeeID] = 3 ) then 'mid' when ([northwind].[dbo].[Orders].[EmployeeID] = 4)  then 'high' else 'not evaluated' end``
   * - **CASE..WHEN..THEN..ELSE..END** |br| |br|
       ``CASE (input_expression) WHEN (when_expression) THEN (result_expression) […n] [ELSE (else_result_expression)] END`` |br| |br|
       Any data type except Image and Lob.
     - Returns the value of result_expression matching the first when_expression with the value equal to input_expression, otherwise return the value of else_result_expression.
     - The highest precedence data type from data types of all ``result_expression`` s and else_result_expression.
     -
   * - **CASE WHEN...THEN...ELSE...END |br| |br|
       ``CASE WHEN (when_expression) THEN (result_expression) […n] [ELSE (else_result_expression)] END`` |br| |br|
       Any data type except Image and Lob.
     - Returns the value of result_expression matching the first when_expression with the value equal to input_expression, otherwise return the value of else_result_expression.
     - The highest precedence data type from data types of all ``result_expression`` s and else_result_expression.
     - ``Case when ([northwind].[dbo].[Orders].[EmployeeID] = 1) then 'less' when ([northwind].[dbo].[Orders].[EmployeeID] = 3 ) then 'mid' when ([northwind].[dbo].[Orders].[EmployeeID] = 4)  then 'high' else 'not evaluated' end``
   * - **RUNNINGSUM** |br| |br|
       ``RUNNINGSUM(expression)`` |br| |br|
       Numeric, Money.
     - Returns the sum of all the values of expression from the first row up to the current row.
     - The same data type as expression.
     - ``RUNNINGSUM([Retail].[dbo].[Orders].[Freight])``
   * - **RUNNINGAVG** |br| |br|
       ``RUNNINGAVG(expression)`` |br| |br|
       Numeric, Money.
     - Returns the average of all the values of expression from the first row up to the current row.
     - The same data type as expression.
     - ``RUNNINGAVG([Retail].[dbo].[Orders].[Freight])``
   * - **RUNNINGCOUNT** |br| |br|
       ``RUNNINGCOUNT(expression)`` |br| |br|
       Any data type except Image and Lob.
     - Returns the number of unique values of expression from the first row up to the current row.
     - Numeric.
     - ``RUNNINGCOUNT([Retail].[dbo].[Orders].[OrderID])``

List of Dateparts and Abbreviations
-----------------------------------


+--------------------------------------------+--------------------+
| Datepart                                   | Abbreviations      |
+--------------------------------------------+--------------------+
| **year**                                   | **yy**, **yyyy**   |
+--------------------------------------------+--------------------+
| **quarter**                                | **qq**, **q**      |
+--------------------------------------------+--------------------+
| **month**                                  | **mm**, **m**      |
+--------------------------------------------+--------------------+
| **dayofyear**                              | **dy**, **y**      |
+--------------------------------------------+--------------------+
| **day**                                    | **dd**, **d**      |
+--------------------------------------------+--------------------+
| **week**                                   | **ww**, **wk**     |
+--------------------------------------------+--------------------+
| **weekday**                                | **dw**             |
+--------------------------------------------+--------------------+
| **hour**                                   | **hh**             |
+--------------------------------------------+--------------------+
| **minute**                                 | **mi**, **n**      |
+--------------------------------------------+--------------------+
| **second**                                 | **ss**, **s**      |
+--------------------------------------------+--------------------+
| **millisecond**                            | **ms**             |
+--------------------------------------------+--------------------+
