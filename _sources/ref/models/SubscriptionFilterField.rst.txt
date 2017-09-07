

=========================================
SubscriptionFilterField
=========================================

.. list-table::
   :header-rows: 1
   :widths: 25 5 65 5

   *  -  Field
      -  NULL
      -  Description
      -  Note
   *  -  **filterFieldId** |br|
         string (GUID)
      -
      -  The id of the filter field
      -
   *  -  **value** |br|
         string
      -
      -  The filter value
      -
   *  -  **operatorId** |br|
         string (GUID)
      -  Y
      -  The id of the operator
      -
   *  -  **operatorSetting** |br|
         string
      -
      -  The operator setting
      -
   *  -  **subscriptionId** |br|
         string (GUID)
      -  Y
      -  The id of the subscription
      -
   *  -  **position** |br|
         integer
      -
      -  The position in the list
      -
   *  -  **filterField** |br|
         object
      -
      -  A :doc:`FilterField` object
      -

Inherited fields:

.. include:: Entity.rst
