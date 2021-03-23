

=========================================
ReportFunction
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **id** |br|
         string (GUID)
      -  Y
      -  The id of the function
      -
   *  -  **name** |br|
         string
      -
      -  The function/operator
      -
   *  -  **expression** |br|
         string
      -
      -  The expression
      -
   *  -  **dataType** |br|
         string
      -
      -  The data type
      -
   *  -  **formatDataType** |br|
         string
      -
      -  The output data type
      -
   *  -  **syntax** |br|
         string
      -
      -  The syntax displayed to user
      -  For example: |br|
         ``expression + expression``
   *  -  **expressionSyntax** |br|
         string
      -
      -  The syntax of the function/operator
      -  For example: |br|
         ``+``
   *  -  **isOperator** |br|
         boolean
      -
      -  Is this an operator (or a function)
      -
   *  -  **userDefined** |br|
         boolean
      -
      -  Is this a user-defined function
      -
   *  -  **extendedProperties** |br|
         object
      -
      -  A dynamic object to store the extended properties
      -

.. container:: toggle

   .. container:: header

      **Sample**:

   .. code-block:: json

      {
         "id": null,
         "name": "*",
         "expression": null,
         "dataType": null,
         "formatDataType": null,
         "syntax": "expression * expression",
         "expressionSyntax": "*",
         "isOperator": false
      }
