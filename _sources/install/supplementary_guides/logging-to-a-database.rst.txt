===========================================
Logging to a Database
===========================================
|

Log Contents
-------------------------------------------

Izenda 7 allows users to configure different levels of logging. By default, the logging level is set to "INFO" which can be in the API Web.config file by the line ``<levelMin value="INFO" />``.


Recorded Logs
###########################################

    * Who ran a report/dashboard
        - Our logs for reports/dashboards contain username and tenantname information.

    * What report/dashboard was ran
        - Our logs for reports/dashboards contain GUIDs in the requests whens someone loads a report/dashboard.

    * When it was ran
        - Every API log contains a timestamp.

    * The parameters/filters and values used to generate a report
        - The filters are in the executed queries for the above calls.


List of Logging levels
###########################################

+--------------------------------------------+
| **ALL**                                    |
+--------------------------------------------+
| **DEBUG**                                  |
+--------------------------------------------+
| **INFO**                                   |
+--------------------------------------------+
| **WARN**                                   |
+--------------------------------------------+
| **ERROR**                                  |
+--------------------------------------------+
| **FATAL**                                  |
+--------------------------------------------+
| **OFF**                                    |
+--------------------------------------------+


Storing Logs in a Database
-------------------------------------------

In order to write the recorded logs into a database, please see our setup guide `here <https://www.izenda.com/docs/dev/code_logging_information_to_a_database.html>`_.


Potential Caveats
###########################################

    * Depending on how frequent the logs are writing to the database, there may be some extra overhead when querying the database.
