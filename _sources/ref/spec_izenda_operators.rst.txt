==================================
Izenda Operators
==================================

List of Operators
-----------------

.. list-table::
   :widths: 20 45 15 20
   :header-rows: 1

   * - Operator
     - Description
     - Result Data Types
     - Examples
   * - **+ (Text Concatenation)** |br| |br|
       ``expression      +   expression`` |br| |br|
       Text + Text
     - Concatenates two text values in that exact order. |br| |br|   
       Not supported by Oracle and PostgreSQL. In cases where Oracle or PostgreSQL raises an error, please use the ``CONCAT function`` instead.
     - Text
     - To return employee's full name from [FirstName] and [LastName] columns: |br|
       ``[FirstName] + ' ' + [LastName]``
   * - **+ Add** |br| |br|
       ``expression      +   expression`` |br| |br|
       Numeric/Money + Numeric/Money |br| |br|
       Datetime + Numeric |br| |br|
       Numeric + Datetime |br| |br|
     - Adds two numbers or two currency amount, or adds a number of days to a date.
     - The data type with the higher prededence.
     - Two and a half days from hire date: |br|
       ``[HireDate] + 2.5``
   * - **- (Subtract)** |br| |br|
       ``expression      -   expression`` |br| |br|
       Numeric/Money - Numeric/Money |br| |br|
       Datetime - Numeric
     - Subtracts two numbers or two currency amount, or subtracts a number of days from a date.
     - The data type with the higher prededence.
     - The number of products in stock after 10 have been taken out: |br|
       ``UnitsInStock - 10``
   * - *** (Multiply)** |br| |br|
       ``expression      *   expression`` |br| |br|
       Numeric/Money * Numeric/Money
     - Multiplies two numbers, or a currency amount with a number.
     - Number
     - Price after 15% discount: |br|
       ``UnitPrice * 0.85``
   * - **/ (Divide)** |br| |br|
       ``expression      /   expression`` |br| |br|
       Numeric/Money / Numeric/Money
     - Divides one number or currency amount by another.
     - Number
     - Price after 50% discount: |br|
       ``UnitPrice / 2``
   * - **= (Equals)** |br| |br|
       ``expression      =   expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares the equality in value of two expressions.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different.
     - Boolean
     - Employees named 'John': |br|
       ``[FirstName] = 'John'``
   * - **> (Greater Than)** |br| |br|
       ``expression      >   expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares if the value of the first expression is higher than the second expression.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different.
     - Boolean
     - Products with more than 10 units in stock: |br|
       ``UnitsInStock > 10``
   * - **< (Less Than)** |br| |br|
       ``expression      <   expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares if the value of the first expression is lower than the second expression.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different.
     - Boolean
     - Products with less than 3 units in stock: |br|
       ``UnitsInStock < 3``
   * - **>= (Greater Than or Equal To)** |br| |br|
       ``expression      >=  expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares if the value of the first expression is higher than or equal to the second expression.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different.
     - Boolean
     -
   * - **<= (Less Than or Equal To)** |br| |br|
       ``expression      <=  expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares if the value of the first expression is lower than or equal to the second expression.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different.
     - Boolean
     -
   * - **<> (Not Equal To)** |br| |br|
       ``expression      <>  expression`` |br| |br|
       Any data type except Image and Lob.
     - Compares if the value of the first expression is not equal to the second expression.
       The expression of the lower precedence data type is converted to the higher precedence data type in case data types are different. types are different.
     - Boolean
     - Products still available in stock: |br|
       ``UnitsInStock <> 0``

Attention with Possibly NULL Fields
-----------------------------------

Special attention when checking if a field has value: the equal operator
cannot used with ``NULL``, ``IS NULL`` and ``IS NOT NULL`` should be
used instead.

To check if there is a photo for an employee in Northwind database:
``[Photo] IS NOT NULL``

Similarly, when using other comparison operators (e.g. "Greater Than >")
on a field that possibly has ``NULL`` value: the ``NULL`` case must be
tested separately.

To check if for employees with hire date later than 2010, including
unknown hire date: ``[HireDate] IS NULL OR [HireDate] > '01-01-2010'``
