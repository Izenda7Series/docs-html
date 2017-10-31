

=========================
Grand Total and Sub Total
=========================

Grand Total
=============

In report tables, the Grand Total for a field will provide either the sum (average, maximum, minimun) of all values or count (count distinct) values within that field across the entire data source.

For example, in a report for Northwind database's Orders table, the Grand Total for Freight field will tell the sum of all Freight costs until now.

   .. figure:: /_static/images/GrandTotal_For_Freight_Preview.png
      :align: center
      :width: 992px

      Grand Total Freight field.

   .. figure:: /_static/images/Grand_Total_Setting_For_Freight.png
      :align: center
      :width: 908px

      Grand Total setting for Freight field.

List of Grand Total Functions
-------------------------------

.. list-table::
   :widths: 35 65
   :header-rows: 1

   * - Function
     - Description
   * - Expression
     - User can combine the expression to collect data by using functions, operators and field names.
   * - Average
     - Return the avarage of all values within the field that set grand total across the entire data source.
   * - Count
     - Return the quantity of all values within the field that set grand total across the entire data source.
   * - Count Distinct
     - Return the count unique number of all values within the field that set grand total across the entire data source.
   * - Maximun
     - Return the maximun value of the field that set grand total across the entire data source.
   * - Minimun
     - Return the minimum value of the field that set grand total across the entire data source.
   * - Sum
     - Return the sum of all values within the field that set grand total across the entire data source.
   * - Count Distinct
     - Return the sum unique number of all values within the field that set grand total across the entire data source.



Sub Total
=============

In report tables, the Sub Total for a field will provide either the sum (average, maximum, minimun) of all values or count (count distinct) values within that field for each seperated group without having any sub-report.

For example, in a report for Northwind database's Orders table, to have the sum for all Freight costs to each country without having to create additional reports, Sub Total can be used.

   .. figure:: /_static/images/Sub_Total_Freight_Preview.png
      :align: center
      :width: 1008px

      Sub Total Freight field seperated by ShipCountry.

   .. figure:: /_static/images/Sub_Total_Freight_Setting.png
      :align: center
      :width: 904px

      Sub Total setting for Freight field.

List of Sub Total Functions
-------------------------------

.. list-table::
   :widths: 35 65
   :header-rows: 1

   * - Function
     - Description
   * - Expression
     - User can combine the expression to collect data for each group by using functions, operators and field names.
   * - Average
     - Return the avarage of all values within the field that set Sub Total across the entire group.
   * - Count
     - Return the quantity of all values within the field that set Sub Total across the entire group.
   * - Count Distinct
     - Return the count unique number of all values within the field that set Sub Total across the entire group.
   * - Maximun
     - Return the maximun value of the field that set Sub Total across the entire group.
   * - Minimun
     - Return the minimum value of the field that set  Sub Total across the entire group.
   * - Sum
     - Return the sum of all values within the field that set Sub Total across the entire group.
   * - Sum Distinct
     - Return the sum unique number of all values within the field that set Sub Total across the entire group.
