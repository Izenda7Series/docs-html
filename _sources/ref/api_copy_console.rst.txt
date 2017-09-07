

============================
Copy Console APIs
============================

The Izenda Copy Console Tool will allow you to copy templates, reports and dashboards from one Izenda Configuration database to another or within one configuration database.

The following APIs are used internally for the tool.

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `POST copyManagement/console/validate/sourcedata`_
     - Returns a distinct list of connections from selected tenant, reports, templates and dashboards.
   * - `POST copyManagement/console/validate/dataconsistent`_
     - Validates for consistency between source and destination, for example database server types, database mappings and data models.
   * - `POST copyManagement/console/validate/source`_
     - Validates that ids of source tenant, reports, templates and dashboards are correct.
   * - `POST copyManagement/console/validate/destination`_
     - Validates that destination tenants, database mappings and role mappings are correct.
   * - `POST copyManagement/console/loadreport`_
     - Returns all report/template and related data to be copied to another system.
   * - `POST copyManagement/console/copyreport`_
     - Copies report and related data to a system.
   * - `POST copyManagement/console/updatesubreport`_
     - Updates the content of copied reports to match destination state.
   * - `POST copyManagement/console/loaddashboard`_
     - Returns all dashboard and related data to be copied to another system.
   * - `POST copyManagement/console/copydashboard`_
     - Copies dashboard and related data to a system.
   * - `POST copyManagement/console/listreport`_
     - Returns a list of report definitions.

API Workflow
---------------

.. figure:: /_static/images/Copy_Console_API_Workflow.png
   :width: 428px

   Copy Console API Workflow

POST copyManagement/console/validate/sourcedata
--------------------------------------------------------------

Returns a distinct list of connections from selected tenant, reports, templates and dashboards.

**Request**

    Payload: an :doc:`models/InputWorkspace` object with **sourceTenantId**, **reportIds**, **templateIds** and **dashboardIds** fields populated

**Response**

    An :doc:`models/InputWorkspace` object with **dataInSource** field populated

**Samples**

   .. code-block:: http

      POST /api/copyManagement/console/validate/sourcedata HTTP/1.1

   Request payload::

      {
         "sourceTenantId": "78e5699a-6a67-471f-8374-529a80777754",
         "reportIds": [
            "4b6d592e-ad29-408d-a3f2-845776d555db"
         ]
      }


   Sample response::

      {
        "sourceTenantId": null,
        "reportIds": [],
        "reportIdsLineNumber": [],
        "templateIds": [],
        "templateIdsLineNumber": [],
        "dashboardIds": [],
        "dashboardIdsLineNumber": null,
        "destinationTenants": null,
        "dataInSource": {
          "dbSetupInfo": {
            "serverTypeId": "3d4916d1-5a41-4b94-874f-5bedacb89656",
            "serverTypeName": "[MYSQL] MySQL",
            "connectionString": "encrypted",
            "connectionId": "00000000-0000-0000-0000-000000000000"
          },
          "sourceConnections": "To be updated"
        },
        "sourceLineNumber": 0,
        "destinationLineNumber": 0,
        "sourceTenantLineNumber": 0
      }

POST copyManagement/console/validate/dataconsistent
--------------------------------------------------------------

Validates for consistency between source and destination, for example database server types, database mappings and data models.

**Request**

    Payload: an :doc:`models/InputWorkspace` object with **dataInSource** field populated

**Response**

    An array of strings containing the errors if available

**Samples**

   To be updated

POST copyManagement/console/validate/source
--------------------------------------------------------------

Validates that ids of source tenant, reports, templates and dashboards are correct.

**Request**

    Payload: an :doc:`models/InputWorkspace` object

**Response**

    An array of strings containing the errors if available

**Samples**

   To be updated

POST copyManagement/console/validate/destination
--------------------------------------------------------------

Validates that destination tenants, database mappings and role mappings are correct.

**Request**

    Payload: an array of :doc:`models/DestinationTenant` objects

**Response**

    An array of strings containing the errors if available

**Samples**

   To be updated

POST copyManagement/console/loadreport
--------------------------------------------------------------

Returns all report/template and related data to be copied to another system.

**Request**

    Payload: a :doc:`models/ReportParameter` object

**Response**

    A :doc:`models/WorkspaceDetailConsole` object with **reportDefinition**, **sourceTenantConnections**, **dataSourceConnections**, **sourceRoles** and **sourceUserPermissions** fields populated

**Samples**

   To be updated

POST copyManagement/console/copyreport
--------------------------------------------------------------

Copies report and related data to a system.

**Request**

    Payload: a :doc:`models/WorkspaceDetailConsole` object, which has been fully-populated from `POST copyManagement/console/loadreport`_

**Response**

    An array of :doc:`models/CopyStatus` objects

**Samples**

   Skipped because of too much data

POST copyManagement/console/updatesubreport
--------------------------------------------------------------

Updates the content of copied reports to match destination state.

**Request**

    Payload: an :doc:`models/UpdateSubReportInput` object, with **copyStatus** field populated from the result of `POST copyManagement/console/copyreport`_

**Response**

    An array of :doc:`models/UpdateSubReportStatus` objects

**Samples**

   To be updated

POST copyManagement/console/loaddashboard
--------------------------------------------------------------

Returns all dashboard and related data to be copied to another system.

**Request**

    Payload: a :doc:`models/LoadDashboard` object

**Response**

    A :doc:`models/WorkspaceDetailConsole` object with **dashBoardDefinition**, **sourceReports**, **reportDefinitions**, **sourceRoles** and **sourceUserPermissions** fields populated

**Samples**

   Skipped because of too much data

POST copyManagement/console/copydashboard
--------------------------------------------------------------

Copies dashboard and related data to a system.

**Request**

    Payload: a fully-populated  :doc:`models/WorkspaceDetailConsole` object

**Response**

    An array of :doc:`models/CopyStatus` objects

**Samples**

   Skipped because of too much data

POST copyManagement/console/listreport
--------------------------------------------------------------

Returns a list of report definitions.

**Request**

    Payload: an array of :doc:`models/ReportKey` objects

**Response**

    An array of :doc:`models/ReportDefinition` objects

**Samples**

   To be updated
