

============================
Export APIs
============================


Summary
------------

.. list-table::
   :class: apitable
   :widths: 25 45 30
   :header-rows: 1

   * - API
     - Purpose
     - Usage in Izenda Front-end
   * - `POST export/{format:exportformat}`_
     - Exports the dashboard, report or report part specified in request parameters.
     - Report List > Expand a report > Export
   * - `POST export/email`_
     - Emails or exports report/dashboard based on the input subscription parameter.
     -
   * - `POST export/performanceStatisticsTrend`_
     - Exports the performance statistics trend to csv.
     -
   * - `GET export/checkExportStatus/{fileSession}`_
     - Returns true if the export has been completed for the specified fileSession. |br|
       This should be the value in fileSessionKey in `POST export/{format:exportformat}`_.

       .. versionadded:: 2.0.6
     - \- Report List > Expand a report > Export |br|
       \- Report Designer > Export |br|
       \- Report Viewer > Export |br|

POST export/{format:exportformat}
--------------------------------------------------------------

Exports the dashboard, report or report part specified in request parameters.

**Request**

    **Parameters**:

      - Word
      - Excel
      - PDF
      - CSV
      - XML
      - JSON 
      - Query Execution
      - Definition (New in version 2.8.0)

    **Keys**:

This API accepts 2 types of data: |br|

   - The **application/x-www-form-urlencoded** type with the following keys:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  NULL
          -  Description
          -  Note
       *  -  **dashboardID** |br|
             string
          -  Y
          -  The id of the dashboard if available
          -
       *  -  **dashboardPartID** |br|
             string
          -  Y
          -  The id of the dashboard part if available
          -
       *  -  **reportID** |br|
             string
          -  Y
          -  The id of the report if available
          -
       *  -  **draftID** |br|
             string
          -  Y
          -  The id of the draft if available
          -
       *  -  **reportPartID** |br|
             string
          -  Y
          -  The id of the report part if available
          -
       *  -  **filters** |br|
             array of objects
          -  Y
          -  An array of :doc:`models/ReportFilterField` objects
          -
       *  -  **fileSessionKey** |br|
             string
          -  Y
          -  The key of this specific session, it will be set to cookie <fileSessionKey>=true on success
          -
       *  -  **reportDefinition** |br|
             string
          -  Y
          -  The report definition if available
          -
       *  -  **dashboardDefinition** |br|
             string
          -  Y
          -  The dashboard definition if available
          -
       *  -  **dashboardPartIndex** |br|
             string
          -  Y
          -  The index of the dashboard part if available
          -
       *  -  **access_token** |br|
             string
          -  Y
          -  The authentication token
          -
       *  -  **current_tenant** |br|
             string
          -  Y
          -  The id of the current tenant if available
          -

   - The **application/json** type with the request payload is an :doc:`models/ExportRequest` object.

**Response**

    The content of the export

**Samples**

   .. code-block:: http

      POST /api/export/pdf HTTP/1.1

   Request form (application/x-www-form-urlencoded):

   .. code-block:: text

      url:http://localhost:8888/report/view/e09f9d45-b721-4012-b8e7-c31c58d52af3
      reportId:e09f9d45-b721-4012-b8e7-c31c58d52af3
      filters:[]
      draftId:f862931f-f897-4f98-ab13-687b79b91806
      tenantId:
      fileSessionKey:e09f9d45-b721-4012-b8e7-c31c58d52af3294
      access_token:123Abc..=
      current_tenant:

   Request form (application/json):

   .. code-block:: text

      {
	   "reportId":"e09f9d45-b721-4012-b8e7-c31c58d52af3",
	   "filters":
           [
		{"key": "EF8414A4-AAC0-46BA-B29B-AC7D2775EBE3", "value": "Argentina", "operatorId": "737307D1-1E5F-407F-889F-1B3C9A66DD6F"},
		{"key": "204142B3-0BCF-4B3D-A834-D5E531CFDD2F", "value": 1, "operatorId": "737307D1-1E5F-407F-889F-1B3C9A66DD6F"}
	   ]
      }

   Response::

      the file

   The cookie will be set:

   .. code-block:: text

      e09f9d45-b721-4012-b8e7-c31c58d52af3294=true

POST export/email
--------------------------------------------------------------

Emails or exports report/dashboard based on the input subscription parameter.

**Request**

    Payload: a :doc:`models/Subscription` object

**Response**

    * true if successful
    * false if not

**Samples**

   .. code-block:: http

      POST /api/export/email HTTP/1.1

   Request payload::

      {
        "reportId": "e09f9d45-b721-4012-b8e7-c31c58d52af3",
        "deliveryType": "Email",
        "deliveryMethod": "link",
        "exportAttachmentType": "Pdf",
        "emailSubject": "{reportName}",
        "emailBody": "Dear,<br><br>Please open report by clicking on the following link.<br><br>{reportLink} <br><br>Regards,<br>{currentUserName}",
        "recipients": "jdoe@acme.com",
        "additionalRecipients": ""
      }

   Sample response::

      true


POST export/performanceStatisticsTrend
--------------------------------------------------------------

Exports the performance statistics trend to csv.

**Request**

    **Keys**:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  NULL
          -  Description
          -  Note
       *  -  **access_token** |br|
             string
          -
          -  The access token
          -
       *  -  **current_tenant** |br|
             string (GUID)
          -
          -  The id of the tenant
          -

**Response**

    The file 

**Samples**

   .. code-block:: http

      POST /api/export/performanceStatisticsTrend HTTP/1.1

   Request form (application/x-www-form-urlencoded):

   .. code-block:: text

      access_token:123Abc..=
      current_tenant:

   Request form (application/json):
   
   .. code-block:: text
   
      {
	"access_token" : "123Abc...",
	"current_tenant" : ""	
      }

   Response::

      the file

GET export/checkExportStatus/{fileSession}
--------------------------------------------------------------

Returns true if the export has been completed for the specified fileSession. |br|
This should be the value in fileSessionKey in `POST export/{format:exportformat}`_.

.. versionadded:: 2.0.6

**Request**

   No payload 

**Response**

   *  **true** if the export has been completed
   *  **false** if not

**Samples**

   .. code-block:: http

      GET /api/export/checkExportStatus/my_file_session_key HTTP/1.1

   Response::

      false
