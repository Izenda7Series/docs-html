

============================
Report Designer Filters APIs
============================

The **Report Designer** page allows user to

-  create a report
-  select report data sources
-  create report filters
-  design report layout
-  set up report schedule

This page documents the APIs related to report filters.

List of APIs
------------

.. list-table::
   :class: apitable
   :widths: 35 65
   :header-rows: 1

   * - API
     - Purpose
   * - `GET report/filter/operators`_
     - Returns the list filter operators grouped by data type.
   * - `POST report/loadFilterDataSource`_
     - Returns a list of available report filter fields.
   * - `POST report/validateFilterSyntax`_
     - Validates a filter syntax.
   * - `POST report/loadFilter`_
     - Returns the report's filter fields, with data source and data source field names replaced by correct alias defined in Data Model.
   * - `POST report/filter/loadFields`_
     - Obsolete
   * - `GET report/filter/timePeriods`_
     - Returns pre-defined time periods (last week, next year, etc).
   * - `GET report/filter/dataFormat/{dataType}`_
     - Returns filter data formats for the specified data type.
   * - `GET report/field/dataFormat/{dataType}`_
     - Returns field data formats for the specified data type.
   * - `POST report/loadFilterFieldData`_
     - Returns data of a data source field for the Equivalence filter operators.
   * - `POST report/loadFilterFieldDataAsTree`_
     - Returns data of a data source field in a hierarchy, for the filter operators Equals (Tree) and Not Equal (Tree).
   * - `POST report/loadPartialFilterFieldData`_
     - Returns paged data source field data for Equivalence filter operators.
   * - `POST report/loadPartialFilterFieldDataAsTree`_
     - Returns paged data source field data in a hierarchy for the filter operators Equals (Tree) and Not Equal (Tree).
   * - `POST report/loadAllFilterFieldsData`_
     - Returns all data values for all filter fields in a report. |br|
       Deprecated, please use `POST report/loadPartialFilterFieldData`_ to avoid timeouts loading large data.
   * - `GET report/validateFilter/{report_id}`_
     - Validates that all required filters in specified report have filter value.

.. _GET_report/filter/operators:

GET report/filter/operators
------------------------------------------------

Returns the list filter operators grouped by data type.

**Request**

    No payload

**Response**

    An array of :doc:`models/ReportFilterOperatorGroup` objects

**Samples**

   .. code-block:: http

      GET /api/report/filter/operators HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "key": "...",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "95051abc-70eb-4908-8d13-04032aab3c66",
               "id": "1476ed4b-17ac-4e39-be1b-0a25f705ebea",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "...",
            "id": "95051abc-70eb-4908-8d13-05032aab3c66",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "boolean",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
               "id": "a52e09eb-8867-45e5-88bc-12ba9434f16f",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
               "id": "c77e5ab6-890d-4bf6-8773-13cc9c3bf67e",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
               "id": "a8339c19-7b65-4ee7-8ef4-13e340fba2e9",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "true",
               "name": "True",
               "operatorGroupId": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
               "id": "31d3e116-bde2-40d1-b259-2d750348299c",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "false",
               "name": "False",
               "operatorGroupId": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
               "id": "086dc2fc-23e3-4b54-bc46-2e5f572d2d3f",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "Boolean",
            "id": "7b127c0c-4996-4df8-aa72-09cf07569f5e",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "comparison",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "f8a69ec3-bc01-40fd-8dc1-0b7a259ee83e",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "6bac46ba-768f-4764-9109-0bc2736bcbfd",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "ce0fda8a-4515-409c-9d00-0bf56c2b4c4d",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "islessthan",
               "name": "Is Less Than",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "b78305b3-70f4-4724-a02c-1617a0ef95d3",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "isgreaterthan",
               "name": "Is Greater Than",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "53d73892-3a12-45cd-8b69-163ff6c41989",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "between",
               "name": "Between",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "94c4fb2e-c5d3-4160-a2f7-173418ca4e66",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notlessthan",
               "name": "Not Less Than",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "9fe2afd6-8fb6-4a34-b2e2-1822323af768",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notgreaterthan",
               "name": "Not Greater Than",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "0526507d-901b-4d41-8c4b-1831f90b180c",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notbetween",
               "name": "Not Between",
               "operatorGroupId": "08b322e2-ac79-406d-8367-046437b4fcd9",
               "id": "6ea8396b-49e3-4ed2-b9b6-18c1a737cffc",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "Comparison",
            "id": "08b322e2-ac79-406d-8367-056437b4fcd9",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "date&time",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "27a17b83-4b6a-4700-91a7-10558ef6ab23",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "98e2ec4a-f34f-4bf1-b2b2-108fbec8fa5b",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "63f26c6a-f763-4947-8517-10fd79de5e2a",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "between(calendar)",
               "name": "Between (Calendar)",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "78376aea-4d3c-4e8d-ab97-25c6c249be62",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notbetween(calendar)",
               "name": "Not Between (Calendar)",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "5522a5d7-0456-432b-b1fb-02a4283baa3d",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(calendar)",
               "name": "Equals (Calendar)",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "cb64b1fd-6dec-4b18-b348-02b5b984e6c6",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(calendar)",
               "name": "Not Equal (Calendar)",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "4d68d4a2-05ac-4f24-8496-02c1cfe75460",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "intimeperiod",
               "name": "In Time Period",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "f6b2f9d3-464d-4399-bfd2-265009d3fcf1",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "lessthandaysold",
               "name": "Less Than Days Old",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "05f7ea30-001d-4779-ad3b-2732ed97d61e",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "greaterthandaysold",
               "name": "Greater Than Days Old",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "1c6b9fbd-6377-4c8b-9acc-286ff0e853c5",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equalsdaysold",
               "name": "Equals Days Old",
               "operatorGroupId": "01076b28-8e77-4a54-95d8-060d142a77e6",
               "id": "a8d45242-f5f0-4839-ae98-287ddc178c96",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "Date & Time",
            "id": "01076b28-8e77-4a54-95d8-060d142a77e6",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "equivalence",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "0f043b65-e45d-4c22-9634-0da9e96493bc",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "d7096bd5-09e5-433d-924e-0e038bdc81fb",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "85252e31-7588-438f-85ff-0e0e9c16df8d",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(manualentry)",
               "name": "Equals (Manual Entry)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(selection)",
               "name": "Equals (Selection)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "042a04a3-dfe1-4ef9-bd27-1b657886f02e",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(popup)",
               "name": "Equals (Popup)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "bb2f8e2d-753e-4fc9-9646-1b977a043b9a",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(tree)",
               "name": "Equals (Tree)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "003c0e13-cc3c-412f-8fee-1cf21aa51e31",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(checkbox)",
               "name": "Equals (Checkbox)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "5ce630bc-6615-42c4-b11e-1d09c651eaae",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(manualentry)",
               "name": "Not Equal (Manual Entry)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "78ba4663-e8a4-407f-bab2-1dc014a4df56",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(selection)",
               "name": "Not Equal (Selection)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "75fcf433-81f2-4767-94b7-1e4257b826c4",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(popup)",
               "name": "Not Equal (Popup)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "5cdacf39-8eed-4ed3-8684-1e4461e85e1b",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(checkbox)",
               "name": "Not Equal (Checkbox)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "de9ab97b-4e57-4c8c-8415-1e5030415b50",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(tree)",
               "name": "Not Equal (Tree)",
               "operatorGroupId": "e023c1f4-42b3-469b-a8d9-04684feeb4ed",
               "id": "6bc89182-aa4c-4fa5-b151-208af7e8cd59",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "Equivalence",
            "id": "e023c1f4-42b3-469b-a8d9-05684feeb4ed",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "fieldcomparison",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "444b32e1-5ba5-4829-a8dc-0e3a0e6a69f3",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "83849954-987f-4213-b5b3-0febf0251d5c",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "38a333fb-39cf-424c-bbaf-1043600ca055",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "islessthan(field)",
               "name": "Is Less Than (Field)",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "c506759f-c000-46c3-a35a-21b7d5bbd447",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "isgreaterthan(field)",
               "name": "Is Greater Than (Field)",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "de669d47-d040-494c-91d9-21df45009964",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "equals(field)",
               "name": "Equals (Field)",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "ecd32d5d-32ce-493e-8f9f-225647357325",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notequal(field)",
               "name": "Not Equal (Field)",
               "operatorGroupId": "6938e8a8-c810-4044-be0b-05709faa4734",
               "id": "1e9fbb61-8a77-48a6-b95e-2357646360a5",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "Field Comparison",
            "id": "6938e8a8-c810-4054-be0b-05709faa4734",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }, {
            "key": "string",
            "filterOperators": [{
               "key": "...",
               "name": "...",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "97040a0e-7c33-4088-90ac-1146428428df",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "blank",
               "name": "Blank",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "c16bc286-3238-4a36-85e5-123eb989bee8",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notblank",
               "name": "Not Blank",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "966019de-d541-4ee4-9235-125732abb75a",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "like",
               "name": "Like",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "3396325a-4233-4180-8513-2bb991627800",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "beginswith",
               "name": "Begins With",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "0ac3a76f-cf80-4cd7-8cfd-2c74fadb330a",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "endswith",
               "name": "Ends With",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "09b9b1ba-21c5-4f05-808c-2cae6cca56d9",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }, {
               "key": "notlike",
               "name": "Not Like",
               "operatorGroupId": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
               "id": "30dd377c-5217-4665-8896-2d61efc73cfc",
               "state": 0,
               "modified": null,
               "dateTimeNow": "2016-06-13T07:49:32.7320046Z"
            }],
            "name": "String",
            "id": "c1b10232-6c6f-4bd5-91a1-09317a2b2e67",
            "state": 0,
            "modified": null,
            "dateTimeNow": "2016-06-13T07:49:32.7320056Z"
         }]



POST report/loadFilterDataSource
------------------------------------------------

Returns a list of available report filter fields.

**Request**

   Payload: a :doc:`models/ReportSavingParameter` object, with either:

   *  **reportKey** field populated - for an existing/draft report.
   *  **reportKey** empty and **reportDataSource**.\ **querySourceId** populated - for a new report.

**Response**

    An array of :doc:`models/ReportFilterField` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadFilterDataSource HTTP/1.1

   Request payload for a draft report::

      {
         "reportKey":{"key":"b95d2611-10c5-4808-aa68-9db2ccc719ff"}
      }

   Sample response::

      [
         {
            "connectionName": "MSSQL",
            "querySourceCategoryName": "dbo",
            "sourceFieldName": "CategoryID",
            "sourceFieldVisible": true,
            "sourceFieldFilterable": true,
            "sourceDataObjectName": "Categories",
            "sourceDataObjectFullName": null,
            "dataType": "Numeric",
            "isParameter": false,
            "isCalculated": false,
            "calculatedTree": null,
            "compareFieldCalculatedTree": null,
            "compareValueCalculatedTree": null,
            "compareField": null,
            "selected": false,
            "dataFormat": null,
            "reportId": null,
            "useMappedFieldAlias": false,
            "uniqueId": null,
            "comparisionValue": null,
            "inTimePeriodType": null,
            "valueInTimePeriod": null,
            "hasModifiedCalculatedTree": false,
            "isHiddenFilter": false,
            "isInheritableFilter": false,
            "operatorName": null,
            "filterId": "00000000-0000-0000-0000-000000000000",
            "reportFieldAlias": null,
            "reportPartTitle": null,
            "querySourceFieldId": "1c21c9b2-cc58-4181-89b5-76740bf04c64",
            "querySourceType": "Table",
            "querySourceId": "8ea14631-ce4f-4546-a6e9-04094c69d4af",
            "relationshipId": null,
            "alias": null,
            "position": 0,
            "visible": true,
            "required": false,
            "cascading": true,
            "operatorId": null,
            "operatorSetting": null,
            "value": null,
            "dataFormatId": null,
            "sortType": "Unsorted",
            "fontFamily": null,
            "fontSize": 0,
            "textColor": null,
            "backgroundColor": null,
            "fontBold": false,
            "fontItalic": false,
            "fontUnderline": false,
            "querySourceUniqueName": null,
            "querySourceFieldName": null,
            "comparisonFieldUniqueName": null,
            "isNegative": false,
            "id": "00000000-0000-0000-0000-000000000000",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         },
         {
            "connectionName": "MSSQL",
            "querySourceCategoryName": "dbo",
            "sourceFieldName": "CategoryName",
            "sourceFieldVisible": true,
            "sourceFieldFilterable": true,
            "sourceDataObjectName": "Categories",
            "sourceDataObjectFullName": null,
            "dataType": "Text",
            "isParameter": false,
            "isCalculated": false,
            "calculatedTree": null,
            "compareFieldCalculatedTree": null,
            "compareValueCalculatedTree": null,
            "compareField": null,
            "selected": false,
            "dataFormat": null,
            "reportId": null,
            "useMappedFieldAlias": false,
            "uniqueId": null,
            "comparisionValue": null,
            "inTimePeriodType": null,
            "valueInTimePeriod": null,
            "hasModifiedCalculatedTree": false,
            "isHiddenFilter": false,
            "isInheritableFilter": false,
            "operatorName": null,
            "filterId": "00000000-0000-0000-0000-000000000000",
            "reportFieldAlias": null,
            "reportPartTitle": null,
            "querySourceFieldId": "8a628514-1024-4051-92a8-33752b79d58b",
            "querySourceType": "Table",
            "querySourceId": "8ea14631-ce4f-4546-a6e9-04094c69d4af",
            "relationshipId": null,
            "alias": null,
            "position": 0,
            "visible": true,
            "required": false,
            "cascading": true,
            "operatorId": null,
            "operatorSetting": null,
            "value": null,
            "dataFormatId": null,
            "sortType": "Unsorted",
            "fontFamily": null,
            "fontSize": 0,
            "textColor": null,
            "backgroundColor": null,
            "fontBold": false,
            "fontItalic": false,
            "fontUnderline": false,
            "querySourceUniqueName": null,
            "querySourceFieldName": null,
            "comparisonFieldUniqueName": null,
            "isNegative": false,
            "id": "00000000-0000-0000-0000-000000000000",
            "state": 0,
            "deleted": false,
            "inserted": true,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }
      ]

   Request payload for a new report::

      {
         "reportKey": {
            "key": null,
            "modified": null,
            "tenantId": null
         },
         "report": {
            "reportDataSource": [
               {
                  "querySourceId": "8ea14631-ce4f-4546-a6e9-04094c69d4af",
                  "querySourceName": "Categories"
               },
               {
                  "querySourceId": "9338a5fd-336b-4fdf-a9c5-dfe9e66b5be2",
                  "querySourceName": "Products"
               }
            ]
         }
      }

   Sample response is similar to above.

       

POST report/validateFilterSyntax
------------------------------------------------

Validates a filter syntax.

**Request**

    Payload: a :doc:`models/FilterSyntax` object

**Response**

    An :doc:`models/OperationResult` object, with the **success** field true if the syntax is valid

**Samples**

   .. code-block:: http

      POST /api/report/validateFilterSyntax HTTP/1.1

   Request payload::

      {
        "availableFilter" : [1, 2, 3, 4],
        "syntax" : "(1 OR 2) AND (3 OR 4)"
      }

   Sample response::

      {
        "success" : true,
        "messages" : null
      }


POST report/loadFilter
------------------------------------------------

Returns the report's filter fields, with data source and data source field names replaced by correct alias defined in Data Model.

**Request**

    Payload: a :doc:`models/ReportFilterParameter` object

**Response**

    A :doc:`models/ReportFilterSetting` object

**Samples**

   .. code-block:: http

      POST /api/report/loadFilter HTTP/1.1

   Request payload::

      {
         "reportKey":{"key":"d5771750-9cec-4ef8-b3c0-ff62d12a4e1f"}
      }

   Response::

      {
        "filterFields" : [{
              "connectionName" : "Northwind",
              "querySourceCategoryName" : "dbo",
              "sourceFieldName" : "",
              "sourceFieldVisible" : true,
              "sourceFieldFilterable" : true,
              "sourceDataObjectName" : "Orders",
              "sourceDataObjectFullName" : "Northwind.dbo.Orders",
              "dataType" : "Money",
              "isParameter" : false,
              "calculatedTree" : null,
              "selected" : false,
              "filterId" : "e4bf0bd8-6fd8-47f0-8b50-580455c371da",
              "reportFieldAlias" : null,
              "querySourceFieldId" : "8c3a5156-b571-4232-9577-3d4ea247c022",
              "querySourceType" : "Table",
              "querySourceId" : "04067f51-5551-4f22-a760-ad4f804de79c",
              "relationshipId" : "00000000-0000-0000-0000-000000000000",
              "alias" : "Freight",
              "position" : 1,
              "visible" : false,
              "required" : false,
              "cascading" : true,
              "operatorId" : "53d73892-3a12-45cd-8b69-163ff6c41989",
              "operatorSetting" : null,
              "value" : "100",
              "dataFormatId" : "00000000-0000-0000-0000-000000000000",
              "sortType" : "Unsorted",
              "fontFamily" : null,
              "fontSize" : 0,
              "textColor" : null,
              "backgroundColor" : null,
              "fontBold" : false,
              "fontItalic" : false,
              "fontUnderline" : false,
              "id" : "8e5e49e5-0a5a-49c5-94f7-7126d9b913dc",
              "state" : 0,
              "version" : null,
              "created" : null,
              "createdBy" : null,
              "modified" : null,
              "modifiedBy" : null
           }
        ],
        "logic" : "",
        "visible" : false,
        "reportId" : "d5771750-9cec-4ef8-b3c0-ff62d12a4e1f",
        "id" : "e4bf0bd8-6fd8-47f0-8b50-580555c371da",
        "state" : 0,
        "version" : null,
        "created" : null,
        "createdBy" : null,
        "modified" : null,
        "modifiedBy" : null
      }

POST report/filter/loadFields
-----------------------------------------


**Request**

    Payload: a :doc:`models/ReportFilterParameter` object.

**Response**

    An array of :doc:`models/ReportFilterField` object

**Samples**

   .. code-block:: http

      POST /api/report/filter/loadFields HTTP/1.1

   Sample Request Payload::

      {
         "reportKey":{"key":"5447a5c1-a0c8-4bf6-bd68-f09234ba5e84"},
         "filterId" : "021c76a2-b108-4dd3-962c-4d5d2d1b22fe",
         "fieldId" : "4f43a428-6e23-42c9-bb51-ab19f7966943"
      }

   Sample Response::

      {
         "connectionName": null,
         "querySourceCategoryName": null,
         "sourceFieldName": "ShipperID",
         "sourceFieldVisible": false,
         "sourceFieldFilterable": false,
         "sourceDataObjectName": "Shippers",
         "sourceDataObjectFullName": "SQL-Northwind.dbo.Shippers",
         "dataType": null,
         "isParameter": false,
         "isCalculated": false,
         "calculatedTree": null,
         "compareFieldCalculatedTree": null,
         "compareValueCalculatedTree": null,
         "compareField": null,
         "selected": false,
         "dataFormat": null,
         "reportId": null,
         "useMappedFieldAlias": false,
         "uniqueId": null,
         "comparisionValue": null,
         "inTimePeriodType": null,
         "valueInTimePeriod": null,
         "hasModifiedCalculatedTree": false,
         "isHiddenFilter": false,
         "isInheritableFilter": false,
         "operatorName": null,
         "type": 0,
         "isRunningField": false,
         "isDrillDown": false,
         "filterId": "021c76a2-b108-4dd3-962c-4d5d2d1b22fe",
         "reportFieldAlias": null,
         "reportPartTitle": null,
         "querySourceFieldId": "d5a8a521-6832-4973-8b2c-3360dc52814c",
         "querySourceType": "Table",
         "querySourceId": null,
         "relationshipId": null,
         "alias": "ShipperID",
         "position": 1,
         "visible": true,
         "required": false,
         "cascading": true,
         "operatorId": "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
         "operatorSetting": null,
         "value": "",
         "dataFormatId": null,
         "sortType": "ASC",
         "fontFamily": "Roboto",
         "fontSize": 14,
         "textColor": "#000",
         "backgroundColor": "#fff",
         "fontBold": false,
         "fontItalic": false,
         "fontUnderline": false,
         "querySourceUniqueName": "[con;#0].[cat;#0].[Shippers]",
         "querySourceFieldName": "ShipperID",
         "comparisonFieldUniqueName": "",
         "isNegative": false,
         "id": "4f43a428-6e23-42c9-bb51-ab19f7966943",
         "state": 0,
         "deleted": false,
         "inserted": true,
         "version": 1,
         "created": "2017-09-28T07:49:39.2630000+07:00",
         "createdBy": "System5 Admin5",
         "modified": "2017-09-28T07:49:39.2630000+07:00",
         "modifiedBy": "System5 Admin5"
      }


GET report/filter/timePeriods
------------------------------------------------

Returns pre-defined time periods (last week, next year, etc).

This API also returns custom time periods if available (see :ref:`POST_report/timePeriod` and IAdHocExtension's :ref:`CustomTimePeriod`).

**Request**

    No payload

**Response**

    An array of :doc:`models/TimePeriod` object

**Samples**

   .. code-block:: http

      GET /api/report/filter/timePeriods HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
            {
               "name": "In the Future",
               "type": "Long-term Period",
               "value": "",
               "isCustomFilter": false,
               "customId": "b8ef8ad0-7a90-4f70-b3f3-52cbaf518335",
               "id": "b8ef8ad0-7a90-4f70-b3f3-52cbaf518335",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "In the Past",
               "type": "Long-term Period",
               "value": "",
               "isCustomFilter": false,
               "customId": "dae256be-21d4-45c1-8d34-52cf05ba7cf5",
               "id": "dae256be-21d4-45c1-8d34-52cf05ba7cf5",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current Fiscal Year",
               "type": "Fiscal Year",
               "value": "0",
               "isCustomFilter": false,
               "customId": "1559a72d-22a1-4c8e-b3b4-53414e5b7ff5",
               "id": "1559a72d-22a1-4c8e-b3b4-53414e5b7ff5",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Previous Fiscal Year",
               "type": "Fiscal Year",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "4c35be45-4b5e-4fc2-931f-53acf34bf7dd",
               "id": "4c35be45-4b5e-4fc2-931f-53acf34bf7dd",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next Fiscal Year",
               "type": "Fiscal Year",
               "value": "1",
               "isCustomFilter": false,
               "customId": "7aad066f-fbcc-4494-9343-54a803244fa0",
               "id": "7aad066f-fbcc-4494-9343-54a803244fa0",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current and Previous Fiscal Year",
               "type": "Fiscal Year",
               "value": "0&-1",
               "isCustomFilter": false,
               "customId": "6bc051a5-85a1-401e-b5bb-55480ec6485e",
               "id": "6bc051a5-85a1-401e-b5bb-55480ec6485e",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current and Next Fiscal Year",
               "type": "Fiscal Year",
               "value": "0&1",
               "isCustomFilter": false,
               "customId": "f1e19c1e-0970-4b3a-b1fa-5561efc783e5",
               "id": "f1e19c1e-0970-4b3a-b1fa-5561efc783e5",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "0",
               "isCustomFilter": false,
               "customId": "52cc45ab-3d7c-4814-a237-55d43b41b385",
               "id": "52cc45ab-3d7c-4814-a237-55d43b41b385",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current and Next Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "0&1",
               "isCustomFilter": false,
               "customId": "f64ee3b3-0f5d-4ac4-a0db-561cfed6d00c",
               "id": "f64ee3b3-0f5d-4ac4-a0db-561cfed6d00c",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current and Previous Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "0&-1",
               "isCustomFilter": false,
               "customId": "4a689982-d21e-41a8-9ee6-565b6e23985a",
               "id": "4a689982-d21e-41a8-9ee6-565b6e23985a",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "1",
               "isCustomFilter": false,
               "customId": "eaae70a0-ce64-45df-9a43-5737bb110bd4",
               "id": "eaae70a0-ce64-45df-9a43-5737bb110bd4",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Previous Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "35e57b59-a63b-47bb-80d8-574b9e7fd4b0",
               "id": "35e57b59-a63b-47bb-80d8-574b9e7fd4b0",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Next 3 Fiscal Quarter",
               "type": "Fiscal Quarter",
               "value": "0&1&2&3",
               "isCustomFilter": false,
               "customId": "d41cf2a0-41ec-4e62-a9bd-57916b9ea6bc",
               "id": "d41cf2a0-41ec-4e62-a9bd-57916b9ea6bc",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current Year",
               "type": "Calendar Year",
               "value": "0",
               "isCustomFilter": false,
               "customId": "fa1b763b-206f-42f7-a99b-597d7c97582e",
               "id": "fa1b763b-206f-42f7-a99b-597d7c97582e",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Previous Year",
               "type": "Calendar Year",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "eedd820b-3a54-47a1-8c6e-59fc077464dd",
               "id": "eedd820b-3a54-47a1-8c6e-59fc077464dd",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "0",
               "isCustomFilter": false,
               "customId": "bfd892b0-f905-48e1-9766-5a894da73115",
               "id": "bfd892b0-f905-48e1-9766-5a894da73115",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Next Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "0&1",
               "isCustomFilter": false,
               "customId": "ebe01191-9c66-4324-9fc2-5aa7497ba130",
               "id": "ebe01191-9c66-4324-9fc2-5aa7497ba130",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Previous Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "0&-1",
               "isCustomFilter": false,
               "customId": "12a7ff3a-cbe0-437b-b0f0-5bb731c69a40",
               "id": "12a7ff3a-cbe0-437b-b0f0-5bb731c69a40",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "1",
               "isCustomFilter": false,
               "customId": "ad5dcad5-cf2f-4207-82f1-5bcdde289ed1",
               "id": "ad5dcad5-cf2f-4207-82f1-5bcdde289ed1",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Previous Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "5497b872-bf2f-4e2a-9e69-5c6b4a5917ce",
               "id": "5497b872-bf2f-4e2a-9e69-5c6b4a5917ce",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Next 3 Calendar Quarter",
               "type": "Calendar Quarter",
               "value": "0&1&2&3",
               "isCustomFilter": false,
               "customId": "66716758-155f-46a2-a03d-5ca2e2d31894",
               "id": "66716758-155f-46a2-a03d-5ca2e2d31894",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last Month",
               "type": "Calendar Month",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "007f892b-1de2-4bcb-b0c4-5d0a91007a54",
               "id": "007f892b-1de2-4bcb-b0c4-5d0a91007a54",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "This Month",
               "type": "Calendar Month",
               "value": "0",
               "isCustomFilter": false,
               "customId": "3a94dc2b-e390-4226-b28b-5d20cdd07d17",
               "id": "3a94dc2b-e390-4226-b28b-5d20cdd07d17",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next Month",
               "type": "Calendar Month",
               "value": "1",
               "isCustomFilter": false,
               "customId": "39e5d006-df2b-4c53-b137-5d930a527247",
               "id": "39e5d006-df2b-4c53-b137-5d930a527247",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Previous Month",
               "type": "Calendar Month",
               "value": "0&-1",
               "isCustomFilter": false,
               "customId": "115a294e-e0ed-405b-82fc-5ee4083bb7bc",
               "id": "115a294e-e0ed-405b-82fc-5ee4083bb7bc",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Current & Next Month",
               "type": "Calendar Month",
               "value": "0&1",
               "isCustomFilter": false,
               "customId": "36552d12-b977-433f-a5ed-5f052abe5d94",
               "id": "36552d12-b977-433f-a5ed-5f052abe5d94",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last Week",
               "type": "Calendar Week",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "1773cbcb-7b8b-4e08-a0dd-5f27cb0eb0d8",
               "id": "1773cbcb-7b8b-4e08-a0dd-5f27cb0eb0d8",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "This Week",
               "type": "Calendar Week",
               "value": "0",
               "isCustomFilter": false,
               "customId": "de89026f-f5f2-4914-98d8-5fbb626d5ec6",
               "id": "de89026f-f5f2-4914-98d8-5fbb626d5ec6",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next Week",
               "type": "Calendar Week",
               "value": "1",
               "isCustomFilter": false,
               "customId": "edab4b2d-86c9-415b-8c9f-60cab8356ba6",
               "id": "edab4b2d-86c9-415b-8c9f-60cab8356ba6",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Today",
               "type": "Day",
               "value": "0",
               "isCustomFilter": false,
               "customId": "607596fd-1e09-4dba-a929-611b0e729522",
               "id": "607596fd-1e09-4dba-a929-611b0e729522",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Yesterday",
               "type": "Day",
               "value": "-1",
               "isCustomFilter": false,
               "customId": "110ac414-0c3b-4b16-879e-6249bbdc7751",
               "id": "110ac414-0c3b-4b16-879e-6249bbdc7751",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Tomorrow",
               "type": "Day",
               "value": "1",
               "isCustomFilter": false,
               "customId": "fe7e33d7-3b51-4727-b759-62f891153987",
               "id": "fe7e33d7-3b51-4727-b759-62f891153987",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last 7 Days",
               "type": "Day",
               "value": "-7",
               "isCustomFilter": false,
               "customId": "fac2ee3e-0a31-4322-876c-642e4cbb17a6",
               "id": "fac2ee3e-0a31-4322-876c-642e4cbb17a6",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last 30 Days",
               "type": "Day",
               "value": "-30",
               "isCustomFilter": false,
               "customId": "10c3733c-6743-4e94-b78a-651da8594689",
               "id": "10c3733c-6743-4e94-b78a-651da8594689",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last 60 Days",
               "type": "Day",
               "value": "-60",
               "isCustomFilter": false,
               "customId": "655b7087-cf4d-4065-ad5b-65296e678db9",
               "id": "655b7087-cf4d-4065-ad5b-65296e678db9",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last 90 Days",
               "type": "Day",
               "value": "-90",
               "isCustomFilter": false,
               "customId": "94290104-b096-48a1-90d2-657e0fd6fc22",
               "id": "94290104-b096-48a1-90d2-657e0fd6fc22",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Last 120 Days",
               "type": "Day",
               "value": "-120",
               "isCustomFilter": false,
               "customId": "cbf65ffb-5fd4-499c-8034-65c709af533c",
               "id": "cbf65ffb-5fd4-499c-8034-65c709af533c",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next 7 Days",
               "type": "Day",
               "value": "7",
               "isCustomFilter": false,
               "customId": "20b7a28b-6a09-4bb1-9400-65c863f19c56",
               "id": "20b7a28b-6a09-4bb1-9400-65c863f19c56",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next 30 Days",
               "type": "Day",
               "value": "30",
               "isCustomFilter": false,
               "customId": "013781da-925b-4cd7-a75b-67ef1f58252a",
               "id": "013781da-925b-4cd7-a75b-67ef1f58252a",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next 60 Days",
               "type": "Day",
               "value": "60",
               "isCustomFilter": false,
               "customId": "bc00ee20-b7c6-47eb-8233-686e9813da32",
               "id": "bc00ee20-b7c6-47eb-8233-686e9813da32",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next 90 Days",
               "type": "Day",
               "value": "90",
               "isCustomFilter": false,
               "customId": "2cb2bd5b-5228-470c-8ef7-68e8cc030f61",
               "id": "2cb2bd5b-5228-470c-8ef7-68e8cc030f61",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next 120 Days",
               "type": "Day",
               "value": "120",
               "isCustomFilter": false,
               "customId": "5a0b0b87-e153-4047-97d7-6934bd0742e2",
               "id": "5a0b0b87-e153-4047-97d7-6934bd0742e2",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Next and Last 30 Days",
               "type": "Day",
               "value": "-30&30",
               "isCustomFilter": false,
               "customId": "923fc0dd-6d08-483b-a9f9-6a2997698f1b",
               "id": "923fc0dd-6d08-483b-a9f9-6a2997698f1b",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            }
         ]


GET report/filter/dataFormat/{dataType}
------------------------------------------------

Returns filter data formats for the specified data type.

**Request**

    No payload

**Response**

    An array of :doc:`models/DataFormat` objects

**Samples**

   .. code-block:: http

      GET /api/report/filter/dataFormat/datetime HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "name": "MM/dd/yyyy",
            "format": "MM/dd/yyyy",
            "description": "01/01/2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "1",
            "id": "8074c8aa-55c7-4326-b6cd-0d4b0f7300cb",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yyyy",
            "format": "M/d/yyyy",
            "description": "1/1/2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "2",
            "id": "99b3e614-e8b5-4029-92f4-0eb3b4567ee8",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM/dd/yy",
            "format": "MM/dd/yy",
            "description": "01/01/16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "3",
            "id": "dac64bc3-f80d-471d-9c85-108e1b4ba12f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yy",
            "format": "M/d/yy",
            "description": "1/1/16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "4",
            "id": "1a096ce2-ec61-434a-8661-111c1144d280",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yyyy",
            "format": "dd/MM/yyyy",
            "description": "01/01/2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "5",
            "id": "39205d97-69c0-4218-aebc-1258050ee213",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yyyy",
            "format": "d/M/yyyy",
            "description": "1/1/2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "6",
            "id": "37ea8e5a-221c-4e00-88c2-1462db60c321",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yy",
            "format": "dd/MM/yy",
            "description": "01/01/16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "7",
            "id": "47965d0b-abc8-4e20-a588-14c45a73c3f9",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yy",
            "format": "d/M/yy",
            "description": "1/1/16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "8",
            "id": "de0efa66-6346-4313-800c-1619704e1d77",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/MM/dd",
            "format": "yyyy/MM/dd",
            "description": "2016/01/01",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "9",
            "id": "aae0b97a-0b8b-4279-b6ab-172b2a5a7b94",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/M/d",
            "format": "yyyy/M/d",
            "description": "2016/1/1",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "10",
            "id": "dd8d2ffe-8df3-49b2-93e6-181b0a7d3823",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yy",
            "format": "MM-yy",
            "description": "01-16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "11",
            "id": "0833ea48-a1ec-43bc-889f-18c64165104f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yy",
            "format": "M-yy",
            "description": "1-16",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "12",
            "id": "0549ff60-f999-4c9f-b7ce-19ca7136c108",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yyyy",
            "format": "MM-yyyy",
            "description": "01-2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "13",
            "id": "8428b370-13c3-444e-aace-1a6310257460",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yyyy",
            "format": "M-yyyy",
            "description": "1-2016",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "14",
            "id": "0aec04a1-c573-4858-967d-1a65899905fb",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-MM",
            "format": "yy-MM",
            "description": "16-01",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "15",
            "id": "1f15d83b-b08f-4fef-a2b8-1af83b3d3089",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-M",
            "format": "yy-M",
            "description": "16-1",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "16",
            "id": "ce48ffc4-ba34-44b4-a6a3-1e3aa9bfb489",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-MM",
            "format": "yyyy-MM",
            "description": "2016-01",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "17",
            "id": "a5dc228e-87be-4131-89e7-21b2942ceb6c",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-M",
            "format": "yyyy-M",
            "description": "2016-1",
            "category": "Short Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "18",
            "id": "5cde36e7-3bc1-46be-a0aa-22578b7b3dcf",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yy",
            "format": "[Month Name]-yy",
            "description": "January-16",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "19",
            "id": "b330e42b-5f3f-449c-8437-24fcb3900cdc",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yyyy",
            "format": "[Month Name]-yyyy",
            "description": "January-2016",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "20",
            "id": "d80cabee-2301-45e2-9923-252122708817",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-[Month Name]",
            "format": "yyyy-[Month Name]",
            "description": "2016-January",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "21",
            "id": "cd72509f-b5eb-4f6b-93c6-2631950aaad5",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-[Month Name]",
            "format": "yy-[Month Name]",
            "description": "16-January",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "yearandmonth",
            "position": "22",
            "id": "565be5b0-a2ec-44e9-a2dd-2b7e46b9ab89",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] dd, yyyy",
            "format": "[Day Names of the Week], [Month Name] dd, yyyy",
            "description": "Friday, January 01, 2016",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "23",
            "id": "518ebae0-be84-410e-8d61-2c121bd5c768",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] d, yyyy",
            "format": "[Day Names of the Week], [Month Name] d, yyyy",
            "description": "Friday, January 1, 2016",
            "category": "Long Date",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "date",
            "position": "24",
            "id": "64742c1f-d2d0-46da-8e80-2c1cb57a55e1",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "HH:mm tt (12-hour time)",
            "format": "HH:mm tt (12-hour time)",
            "description": "01:05 AM",
            "category": "Short Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "34",
            "id": "69b175fb-a3f2-40bb-9162-2eb8cf5f7169",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "H:mm tt (12-hour time)",
            "format": "H:mm tt (12-hour time)",
            "description": "1:05 PM",
            "category": "Short Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "35",
            "id": "f629aeb7-7cd5-48e9-a194-30a1c9796b55",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "HH:mm (24-hour time)",
            "format": "HH:mm (24-hour time)",
            "description": "13:05",
            "category": "Short Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "36",
            "id": "2e2acfa1-02aa-42d6-872c-3188c2d423c9",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "H:mm (24-hour time)",
            "format": "H:mm (24-hour time)",
            "description": "1:05",
            "category": "Short Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "37",
            "id": "9ddf1adf-b54b-4b29-8fcf-32129371724d",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "HH:mm:ss tt",
            "format": "HH:mm:ss tt",
            "description": "01:05:20 AM",
            "category": "Long Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "38",
            "id": "55ae7c7a-f463-43ef-ba3a-327b02c5a196",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "H:mm:ss tt",
            "format": "H:mm:ss tt",
            "description": "1:05:08 PM",
            "category": "Long Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "39",
            "id": "f0692195-e1c7-4029-89b4-32bd89250f80",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "HH:mm:ss",
            "format": "HH:mm:ss",
            "description": "13:05:08",
            "category": "Long Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "40",
            "id": "c710dc48-20c8-4122-b213-3307cb096a01",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "H:mm:ss",
            "format": "H:mm:ss",
            "description": "1:05:08",
            "category": "Long Hour",
            "subCategory": "",
            "dataType": "Date & Time",
            "groupBy": "time",
            "position": "41",
            "id": "987f0bc1-1348-4b05-ad50-347a200c223f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM/dd/yyyy HH:mm:ss tt",
            "format": "MM/dd/yyyy HH:mm:ss tt",
            "description": "01/01/2016 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "42",
            "id": "9d33f3e0-b1ab-42fa-9b8e-356011065066",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yyyy HH:mm:ss tt",
            "format": "M/d/yyyy HH:mm:ss tt",
            "description": "1/1/2016 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "43",
            "id": "2a9e0025-7bc0-4cd7-bc73-364986805790",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM/dd/yy HH:mm:ss tt",
            "format": "MM/dd/yy HH:mm:ss tt",
            "description": "01/01/16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "44",
            "id": "8a3ab3b3-f3b3-4a92-a92d-38db2f8b1642",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yy HH:mm:ss tt",
            "format": "M/d/yy HH:mm:ss tt",
            "description": "1/1/16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "45",
            "id": "617ab284-1175-4099-b0eb-3bb677630347",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yyyy HH:mm:ss tt",
            "format": "dd/MM/yyyy HH:mm:ss tt",
            "description": "01/01/2016 01:05 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "46",
            "id": "0d64d305-4a30-4e1e-8598-3bedce6a6922",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yyyy HH:mm:ss tt",
            "format": "d/M/yyyy HH:mm:ss tt",
            "description": "1/1/2016 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "47",
            "id": "936cc5c5-7f2a-4658-9623-3ca7ffc79774",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yy HH:mm:ss tt",
            "format": "dd/MM/yy HH:mm:ss tt",
            "description": "01/01/16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "48",
            "id": "4c1e0945-dd57-4505-b52f-3cf82366966e",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yy HH:mm:ss tt",
            "format": "d/M/yy HH:mm:ss tt",
            "description": "1/1/16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "49",
            "id": "ffff1be2-d4a3-4fe3-b1b3-3cfbbc19b602",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/MM/dd HH:mm:ss tt",
            "format": "yyyy/MM/dd HH:mm:ss tt",
            "description": "2016/01/01 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "50",
            "id": "0c6e93f8-8d3f-4606-b06f-3d97fce22f47",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/M/d HH:mm:ss tt",
            "format": "yyyy/M/d HH:mm:ss tt",
            "description": "2016/1/1 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "51",
            "id": "fa8c8ded-cb76-4c09-9e99-4005050c4c00",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yy HH:mm:ss tt",
            "format": "MM-yy HH:mm:ss tt",
            "description": "01-16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "52",
            "id": "f396a198-335a-4ff3-bc5f-40a45bff2b2c",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yy HH:mm:ss tt",
            "format": "M-yy HH:mm:ss tt",
            "description": "1-16 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "53",
            "id": "525f7687-51ae-4df9-8308-415e4713d1ee",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yyyy HH:mm:ss tt",
            "format": "MM-yyyy HH:mm:ss tt",
            "description": "01-2016 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "54",
            "id": "49d4e3f7-6c74-4464-bca3-454d1b97de6f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yyyy HH:mm:ss tt",
            "format": "M-yyyy HH:mm:ss tt",
            "description": "1-2016 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "55",
            "id": "90ace7c2-534c-4130-9a51-45f6d3fc1693",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-MM HH:mm:ss tt",
            "format": "yy-MM HH:mm:ss tt",
            "description": "16-01 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "56",
            "id": "1bda7a16-2e0b-405c-b65f-465693fc47f6",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-M HH:mm:ss tt",
            "format": "yy-M HH:mm:ss tt",
            "description": "16-1 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "57",
            "id": "27f16394-b625-43e0-a651-48069468f1be",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-MM HH:mm:ss tt",
            "format": "yyyy-MM HH:mm:ss tt",
            "description": "2016-01 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "58",
            "id": "4f2b4b1f-44ae-4e5d-9fdb-482b35bca7ca",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-M HH:mm:ss tt",
            "format": "yyyy-M HH:mm:ss tt",
            "description": "2016-1 01:05:08 AM",
            "category": "Short Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "59",
            "id": "43a3ccd0-1f47-450c-9ff8-489099d3f44f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM/dd/yyyy HH:mm:ss",
            "format": "MM/dd/yyyy HH:mm:ss",
            "description": "01/01/2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "60",
            "id": "8079bc9c-199f-4f26-adb4-4b6a6e667a6e",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yyyy HH:mm:ss",
            "format": "M/d/yyyy HH:mm:ss",
            "description": "1/1/2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "61",
            "id": "3f1ec142-fd4b-4f6a-8f39-4d2901660360",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM/dd/yy HH:mm:ss",
            "format": "MM/dd/yy HH:mm:ss",
            "description": "01/01/16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "62",
            "id": "7844971b-6945-47d2-909c-4ee118d84b72",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M/d/yy HH:mm:ss",
            "format": "M/d/yy HH:mm:ss",
            "description": "1/1/16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "63",
            "id": "5f12e0cf-b5b3-4fb8-966c-4ef10a75a211",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yyyy HH:mm:ss",
            "format": "dd/MM/yyyy HH:mm:ss",
            "description": "01/01/2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "64",
            "id": "e33e2fd3-3fa5-4a63-a700-522c62781d62",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yyyy HH:mm:ss",
            "format": "d/M/yyyy HH:mm:ss",
            "description": "1/1/2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "65",
            "id": "d91c8331-3a1e-4e1f-b1ec-558e465194b0",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "dd/MM/yy HH:mm:ss",
            "format": "dd/MM/yy HH:mm:ss",
            "description": "01/01/16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "66",
            "id": "57e7e874-f2e2-4a36-9213-56ba0500d62b",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "d/M/yy HH:mm:ss",
            "format": "d/M/yy HH:mm:ss",
            "description": "1/1/16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "67",
            "id": "eefd6063-e59d-42ec-a0d6-56cfb4daf691",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/MM/dd HH:mm:ss",
            "format": "yyyy/MM/dd HH:mm:ss",
            "description": "2016/01/01 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "68",
            "id": "784191b5-429d-4db3-9cd1-5764d2bd4f14",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy/M/d HH:mm:ss",
            "format": "yyyy/M/d HH:mm:ss",
            "description": "2016/1/1 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "69",
            "id": "5ecab5c8-8ac7-4de7-a1b1-5a1647905941",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yy HH:mm:ss",
            "format": "MM-yy HH:mm:ss",
            "description": "01-16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "70",
            "id": "9934ed15-4eb2-4d24-9b5b-5a967abbb2b3",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yy HH:mm:ss",
            "format": "M-yy HH:mm:ss",
            "description": "1-16 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "71",
            "id": "e667285f-3b35-463f-9e74-5adb93569afe",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "MM-yyyy HH:mm:ss",
            "format": "MM-yyyy HH:mm:ss",
            "description": "01-2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "72",
            "id": "4745208e-4ecc-4038-aac7-5afc7319c36b",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "M-yyyy HH:mm:ss",
            "format": "M-yyyy HH:mm:ss",
            "description": "1-2016 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "73",
            "id": "e85030bc-8076-4e40-80b5-5b5f1196a292",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-MM HH:mm:ss",
            "format": "yy-MM HH:mm:ss",
            "description": "16-01 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "74",
            "id": "3dfcc6e1-2391-4cc9-b263-5dac3359602a",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-M HH:mm:ss",
            "format": "yy-M HH:mm:ss",
            "description": "16-1 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "75",
            "id": "ec708bba-7a50-4b1f-af5f-5dd8afc80110",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-MM HH:mm:ss",
            "format": "yyyy-MM HH:mm:ss",
            "description": "2016-01 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "76",
            "id": "353f1ebc-5d53-4802-a269-60516cd92ded",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-M HH:mm:ss",
            "format": "yyyy-M HH:mm:ss",
            "description": "2016-1 13:05:08",
            "category": "Short Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "77",
            "id": "6d443fad-8764-497c-abe4-61c534e26787",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yy HH:mm:ss tt",
            "format": "[Month Name]-yy HH:mm:ss tt",
            "description": "January-16 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "78",
            "id": "4fa8464a-d29c-44e1-9ada-647b36b6d109",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yyyy HH:mm:ss tt",
            "format": "[Month Name]-yyyy HH:mm:ss tt",
            "description": "January-2016 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "79",
            "id": "ec36fff8-eccb-49a1-813c-67164e64d984",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-[Month Name] HH:mm:ss tt",
            "format": "yyyy-[Month Name] HH:mm:ss tt",
            "description": "2016-January 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "80",
            "id": "cfe19542-05a0-4205-88c1-683a840bfab6",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-[Month Name] HH:mm:ss tt",
            "format": "yy-[Month Name] HH:mm:ss tt",
            "description": "16-January 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "81",
            "id": "196ca9d3-a366-45a9-9bd5-68b6fc3bddf2",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss tt",
            "format": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss tt",
            "description": "Friday, January 01, 2016 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "82",
            "id": "0523248a-c64e-498e-b0b1-69eb20b817bb",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss tt",
            "format": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss tt",
            "description": "Friday, January 1, 2016 01:05:08 AM",
            "category": "Long Date & Long Hour",
            "subCategory": "12-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "83",
            "id": "73420f7b-ff6d-40c5-820e-6bb3e2953b41",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yy HH:mm:ss",
            "format": "[Month Name]-yy HH:mm:ss",
            "description": "January-16 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "84",
            "id": "b8ac0da6-0300-4565-ba2a-6c1980eaa25b",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Month Name]-yyyy HH:mm:ss",
            "format": "[Month Name]-yyyy HH:mm:ss",
            "description": "January-2016 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "85",
            "id": "9c544e73-32e9-4c7d-9de8-6c229bd73a3e",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yyyy-[Month Name] HH:mm:ss",
            "format": "yyyy-[Month Name] HH:mm:ss",
            "description": "2016-January 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "86",
            "id": "7d463002-30df-4056-a14d-6c687e4e7a92",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "yy-[Month Name] HH:mm:ss",
            "format": "yy-[Month Name] HH:mm:ss",
            "description": "16-January 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "yearmonthandtime",
            "position": "87",
            "id": "c58457a6-98a1-4e69-92c9-6e093e2f58f3",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss",
            "format": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss",
            "description": "Friday, January 01, 2016 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "88",
            "id": "54c32a12-c057-42f6-b256-70d389788e88",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss",
            "format": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss",
            "description": "Friday, January 1, 2016 13:05:08",
            "category": "Long Date & Long Hour",
            "subCategory": "24-hour",
            "dataType": "Date & Time",
            "groupBy": "dateandtime",
            "position": "89",
            "id": "3bd8ea56-6110-4057-9bd0-76086ec5ebcf",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }]

   .. code-block:: http

      GET /api/report/filter/dataFormat/numeric HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [{
            "name": "0.00",
            "format": "0.00",
            "description": "Positive: 15000.25, Negative: -15000.25",
            "category": "Number",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "90",
            "id": "e31031c5-8be1-4266-abd9-773960317c56",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "0,000.00",
            "format": "0,000.00",
            "description": "Positive: 15,000.25, Negative: -15,000.25",
            "category": "Number",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "91",
            "id": "42b78f79-bef7-4eb1-9e5d-77d7eb79411f",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-(0.00)",
            "format": "-(0.00)",
            "description": "Positive: 15000.25, Negative: -(15000,25)",
            "category": "Number",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "92",
            "id": "83575413-69d8-445c-a36a-78c8d654aba2",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-(0,000.00)",
            "format": "-(0,000.00)",
            "description": "Positive: 15,000.25, Negative: -(15,000.25)",
            "category": "Number",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "93",
            "id": "104a55b9-70fb-429c-a9d9-78d99cc09f53",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "$0.00",
            "format": "$0.00",
            "description": "Positive: $15000.25, Negative: -$15000.25",
            "category": "Currency",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "95",
            "id": "a8813d10-9860-4564-99b1-7a562c523a8e",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "$0,000.00",
            "format": "$0,000.00",
            "description": "Positive: $15,000.25, Negative: -$15,000.25",
            "category": "Currency",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "96",
            "id": "12506ff6-bef8-414d-a1c3-7b61ebbe6320",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-($0.00)",
            "format": "-($0.00)",
            "description": "Positive: $15000.25, Negative: -($15000.25)",
            "category": "Currency",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "97",
            "id": "bf844ffd-ee52-4bcb-b24c-7bb29b1cd4d1",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-($0,000.00)",
            "format": "-($0,000.00)",
            "description": "Positive: $15,000.25, Negative: -($15,000.25)",
            "category": "Currency",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "98",
            "id": "9022c8dd-ad27-47fa-b25c-7df7efee0559",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "0.00%",
            "format": "0.00%",
            "description": "Positive: 15000.25%, Negative: -15000.25%",
            "category": "Percentage",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "101",
            "id": "c2ec0a9f-5c13-4db5-bf9a-80758c05ab0c",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "0,000.00%",
            "format": "0,000.00%",
            "description": "Positive: 15,000.25%, Negative: -15,000.25%",
            "category": "Percentage",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "102",
            "id": "3b59cca3-159e-4814-8a11-8394c285ea6b",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-(0.00%)",
            "format": "-(0.00%)",
            "description": "Positive: 15000.25%, Negative: -(15000.25%)",
            "category": "Percentage",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "103",
            "id": "b5717e46-05ee-4304-8500-83d443c565ee",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }, {
            "name": "-(0,000.00%)",
            "format": "-(0,000.00%)",
            "description": "Positive: 15,000.25%, Negative: -(15,000.25%)",
            "category": "Percentage",
            "subCategory": "",
            "dataType": "Numeric",
            "groupBy": "",
            "position": "104",
            "id": "be821d25-8977-4473-b0d6-8457aa43175e",
            "state": 0,
            "version": null,
            "created": null,
            "createdBy": null,
            "modified": null,
            "modifiedBy": null
         }]

.. _GET_report/field/dataFormat/{dataType}:

GET report/field/dataFormat/{dataType}
------------------------------------------------

Returns field data formats for the specified data type.

``dataType`` in this API includes ``PageNumber``. This option returns available formats for the Page Number item (in Report > Format menu).

This API also returns custom data formats if available (see IAdHocExtension's :ref:`LoadCustomDataFormat`).

**Request**

    No payload

**Response**

    An array of :doc:`models/DataFormat` objects

**Samples**

   .. code-block:: http

      GET /api/report/field/dataFormat/datetime HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
           {
             "name": "MM/dd/yyyy",
             "format": "MM/dd/yyyy",
             "description": "01/01/2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "1",
             "id": "8074c8aa-55c7-4326-b6cd-0d4b0f7300cb",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yyyy",
             "format": "M/d/yyyy",
             "description": "1/1/2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "2",
             "id": "99b3e614-e8b5-4029-92f4-0eb3b4567ee8",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM/dd/yy",
             "format": "MM/dd/yy",
             "description": "01/01/16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "3",
             "id": "dac64bc3-f80d-471d-9c85-108e1b4ba12f",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yy",
             "format": "M/d/yy",
             "description": "1/1/16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "4",
             "id": "1a096ce2-ec61-434a-8661-111c1144d280",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yyyy",
             "format": "dd/MM/yyyy",
             "description": "01/01/2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "5",
             "id": "39205d97-69c0-4218-aebc-1258050ee213",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yyyy",
             "format": "d/M/yyyy",
             "description": "1/1/2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "6",
             "id": "37ea8e5a-221c-4e00-88c2-1462db60c321",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yy",
             "format": "dd/MM/yy",
             "description": "01/01/16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "7",
             "id": "47965d0b-abc8-4e20-a588-14c45a73c3f9",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yy",
             "format": "d/M/yy",
             "description": "1/1/16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "8",
             "id": "de0efa66-6346-4313-800c-1619704e1d77",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/MM/dd",
             "format": "yyyy/MM/dd",
             "description": "2016/01/01",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "9",
             "id": "aae0b97a-0b8b-4279-b6ab-172b2a5a7b94",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/M/d",
             "format": "yyyy/M/d",
             "description": "2016/1/1",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "10",
             "id": "dd8d2ffe-8df3-49b2-93e6-181b0a7d3823",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yy",
             "format": "MM-yy",
             "description": "01-16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "11",
             "id": "0833ea48-a1ec-43bc-889f-18c64165104f",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yy",
             "format": "M-yy",
             "description": "1-16",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "12",
             "id": "0549ff60-f999-4c9f-b7ce-19ca7136c108",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yyyy",
             "format": "MM-yyyy",
             "description": "01-2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "13",
             "id": "8428b370-13c3-444e-aace-1a6310257460",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yyyy",
             "format": "M-yyyy",
             "description": "1-2016",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "14",
             "id": "0aec04a1-c573-4858-967d-1a65899905fb",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-MM",
             "format": "yy-MM",
             "description": "16-01",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "15",
             "id": "1f15d83b-b08f-4fef-a2b8-1af83b3d3089",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-M",
             "format": "yy-M",
             "description": "16-1",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "16",
             "id": "ce48ffc4-ba34-44b4-a6a3-1e3aa9bfb489",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-MM",
             "format": "yyyy-MM",
             "description": "2016-01",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "17",
             "id": "a5dc228e-87be-4131-89e7-21b2942ceb6c",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-M",
             "format": "yyyy-M",
             "description": "2016-1",
             "category": "Short Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "18",
             "id": "5cde36e7-3bc1-46be-a0aa-22578b7b3dcf",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yy",
             "format": "[Month Name]-yy",
             "description": "January-16",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "19",
             "id": "b330e42b-5f3f-449c-8437-24fcb3900cdc",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yyyy",
             "format": "[Month Name]-yyyy",
             "description": "January-2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "20",
             "id": "d80cabee-2301-45e2-9923-252122708817",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-[Month Name]",
             "format": "yyyy-[Month Name]",
             "description": "2016-January",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "21",
             "id": "cd72509f-b5eb-4f6b-93c6-2631950aaad5",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-[Month Name]",
             "format": "yy-[Month Name]",
             "description": "16-January",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandmonth",
             "formatDataType": null,
             "position": "22",
             "id": "565be5b0-a2ec-44e9-a2dd-2b7e46b9ab89",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] dd, yyyy",
             "format": "[Day Names of the Week], [Month Name] dd, yyyy",
             "description": "Friday, January 01, 2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "23",
             "id": "518ebae0-be84-410e-8d61-2c121bd5c768",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] d, yyyy",
             "format": "[Day Names of the Week], [Month Name] d, yyyy",
             "description": "Friday, January 1, 2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "24",
             "id": "64742c1f-d2d0-46da-8e80-2c1cb57a55e1",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Day",
             "format": "Day",
             "description": "16",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "day",
             "formatDataType": null,
             "position": "25",
             "id": "c7cd571e-efa9-4ec6-bee9-02e0a8afb143",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Month",
             "format": "Month",
             "description": "01",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "month",
             "formatDataType": null,
             "position": "26",
             "id": "7e4ed46a-c06a-4d47-b032-03aa530ab331",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Year",
             "format": "Year",
             "description": "2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "year",
             "formatDataType": null,
             "position": "27",
             "id": "76875180-32c1-4180-b92f-03bdb14c4f6a",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Month Name",
             "format": "Month Name",
             "description": "January",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "month",
             "formatDataType": null,
             "position": "28",
             "id": "8e4b292a-9685-4bca-93ca-03bdeee470cc",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Day of Week",
             "format": "Day of Week",
             "description": "Sunday",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "weekday",
             "formatDataType": null,
             "position": "29",
             "id": "1856a6e8-15f9-4602-9c80-03ccb98fd821",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Date",
             "format": "Date",
             "description": "02/15/2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "date",
             "formatDataType": null,
             "position": "30",
             "id": "fdcafa84-11d5-4e0d-a0db-04c7762d7afb",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Week Number",
             "format": "Week Number",
             "description": "Week 07 - 2016",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "weeknumber",
             "formatDataType": null,
             "position": "31",
             "id": "07ad61ba-02e0-4270-b541-0524f384895e",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy - Qtr",
             "format": "yyyy - Qtr",
             "description": "2016-Q1",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "yearandquarter",
             "formatDataType": null,
             "position": "32",
             "id": "06195f60-9fae-402c-ad1c-06153747d0b9",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "Qtr",
             "format": "Qtr",
             "description": "Q1",
             "category": "Long Date",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "quarter",
             "formatDataType": null,
             "position": "33",
             "id": "8bec5d4e-ce5a-4393-9aca-066d6560b546",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "HH:mm tt (12-hour time)",
             "format": "HH:mm tt (12-hour time)",
             "description": "01:05 AM",
             "category": "Short Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "34",
             "id": "69b175fb-a3f2-40bb-9162-2eb8cf5f7169",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "H:mm tt (12-hour time)",
             "format": "H:mm tt (12-hour time)",
             "description": "1:05 PM",
             "category": "Short Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "35",
             "id": "f629aeb7-7cd5-48e9-a194-30a1c9796b55",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "HH:mm (24-hour time)",
             "format": "HH:mm (24-hour time)",
             "description": "13:05",
             "category": "Short Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "36",
             "id": "2e2acfa1-02aa-42d6-872c-3188c2d423c9",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "H:mm (24-hour time)",
             "format": "H:mm (24-hour time)",
             "description": "1:05",
             "category": "Short Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "37",
             "id": "9ddf1adf-b54b-4b29-8fcf-32129371724d",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "HH:mm:ss tt",
             "format": "HH:mm:ss tt",
             "description": "01:05:20 AM",
             "category": "Long Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "38",
             "id": "55ae7c7a-f463-43ef-ba3a-327b02c5a196",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "H:mm:ss tt",
             "format": "H:mm:ss tt",
             "description": "1:05:08 PM",
             "category": "Long Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "39",
             "id": "f0692195-e1c7-4029-89b4-32bd89250f80",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "HH:mm:ss",
             "format": "HH:mm:ss",
             "description": "13:05:08",
             "category": "Long Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "40",
             "id": "c710dc48-20c8-4122-b213-3307cb096a01",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "H:mm:ss",
             "format": "H:mm:ss",
             "description": "1:05:08",
             "category": "Long Hour",
             "subCategory": "",
             "dataType": "Date & Time",
             "groupBy": "time",
             "formatDataType": null,
             "position": "41",
             "id": "987f0bc1-1348-4b04-ad50-347a200c223f",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM/dd/yyyy HH:mm:ss tt",
             "format": "MM/dd/yyyy HH:mm:ss tt",
             "description": "01/01/2016 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "42",
             "id": "9d33f3e0-b1ab-42fa-9b8e-356011065066",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yyyy HH:mm:ss tt",
             "format": "M/d/yyyy HH:mm:ss tt",
             "description": "1/1/2016 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "43",
             "id": "2a9e0025-7bc0-4cd7-bc73-364986804790",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM/dd/yy HH:mm:ss tt",
             "format": "MM/dd/yy HH:mm:ss tt",
             "description": "01/01/16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "44",
             "id": "8a3ab3b3-f3b3-4a92-a92d-38db2f8b1642",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yy HH:mm:ss tt",
             "format": "M/d/yy HH:mm:ss tt",
             "description": "1/1/16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "45",
             "id": "617ab284-1175-4099-b0eb-3bb677630347",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yyyy HH:mm:ss tt",
             "format": "dd/MM/yyyy HH:mm:ss tt",
             "description": "01/01/2016 01:05 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "46",
             "id": "0d64d305-4a30-4e1e-8598-3bedce6a6922",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yyyy HH:mm:ss tt",
             "format": "d/M/yyyy HH:mm:ss tt",
             "description": "1/1/2016 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "47",
             "id": "936cc5c5-7f2a-4658-9623-3ca7ffc79774",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yy HH:mm:ss tt",
             "format": "dd/MM/yy HH:mm:ss tt",
             "description": "01/01/16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "48",
             "id": "4c1e0945-dd57-4504-b52f-3cf82366966e",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yy HH:mm:ss tt",
             "format": "d/M/yy HH:mm:ss tt",
             "description": "1/1/16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "49",
             "id": "ffff1be2-d4a3-4fe3-b1b3-3cfbbc19b602",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/MM/dd HH:mm:ss tt",
             "format": "yyyy/MM/dd HH:mm:ss tt",
             "description": "2016/01/01 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "50",
             "id": "0c6e93f8-8d3f-4606-b06f-3d97fce22f47",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/M/d HH:mm:ss tt",
             "format": "yyyy/M/d HH:mm:ss tt",
             "description": "2016/1/1 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "51",
             "id": "fa8c8ded-cb76-4c09-9e99-4005050c4c00",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yy HH:mm:ss tt",
             "format": "MM-yy HH:mm:ss tt",
             "description": "01-16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "52",
             "id": "f396a198-335a-4ff3-bc5f-40a45bff2b2c",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yy HH:mm:ss tt",
             "format": "M-yy HH:mm:ss tt",
             "description": "1-16 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "53",
             "id": "525f7687-51ae-4df9-8308-415e4713d1ee",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yyyy HH:mm:ss tt",
             "format": "MM-yyyy HH:mm:ss tt",
             "description": "01-2016 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "54",
             "id": "49d4e3f7-6c74-4464-bca3-454d1b97de6f",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yyyy HH:mm:ss tt",
             "format": "M-yyyy HH:mm:ss tt",
             "description": "1-2016 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "55",
             "id": "90ace7c2-534c-4130-9a51-45f6d3fc1693",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-MM HH:mm:ss tt",
             "format": "yy-MM HH:mm:ss tt",
             "description": "16-01 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "56",
             "id": "1bda7a16-2e0b-405c-b65f-465693fc47f6",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-M HH:mm:ss tt",
             "format": "yy-M HH:mm:ss tt",
             "description": "16-1 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "57",
             "id": "27f16394-b625-43e0-a651-48069468f1be",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-MM HH:mm:ss tt",
             "format": "yyyy-MM HH:mm:ss tt",
             "description": "2016-01 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "58",
             "id": "4f2b4b1f-44ae-4e5d-9fdb-482b35bca7ca",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-M HH:mm:ss tt",
             "format": "yyyy-M HH:mm:ss tt",
             "description": "2016-1 01:05:08 AM",
             "category": "Short Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "59",
             "id": "43a3ccd0-1f47-450c-9ff8-489099d3f44f",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM/dd/yyyy HH:mm:ss",
             "format": "MM/dd/yyyy HH:mm:ss",
             "description": "01/01/2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "60",
             "id": "8079bc9c-199f-4f26-adb4-4b6a6e667a6e",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yyyy HH:mm:ss",
             "format": "M/d/yyyy HH:mm:ss",
             "description": "1/1/2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "61",
             "id": "3f1ec142-fd4b-4f6a-8f39-4d2901660360",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM/dd/yy HH:mm:ss",
             "format": "MM/dd/yy HH:mm:ss",
             "description": "01/01/16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "62",
             "id": "7844971b-6945-47d2-909c-4ee118d84b72",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M/d/yy HH:mm:ss",
             "format": "M/d/yy HH:mm:ss",
             "description": "1/1/16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "63",
             "id": "5f12e0cf-b5b3-4fb8-966c-4ef10a75a211",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yyyy HH:mm:ss",
             "format": "dd/MM/yyyy HH:mm:ss",
             "description": "01/01/2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "64",
             "id": "e33e2fd3-3fa5-4a63-a700-522c62781d62",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yyyy HH:mm:ss",
             "format": "d/M/yyyy HH:mm:ss",
             "description": "1/1/2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "65",
             "id": "d91c8331-3a1e-4e1f-b1ec-558e465194b0",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "dd/MM/yy HH:mm:ss",
             "format": "dd/MM/yy HH:mm:ss",
             "description": "01/01/16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "66",
             "id": "57e7e874-f2e2-4a36-9213-56ba0400d62b",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "d/M/yy HH:mm:ss",
             "format": "d/M/yy HH:mm:ss",
             "description": "1/1/16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "67",
             "id": "eefd6063-e59d-42ec-a0d6-56cfb4daf691",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/MM/dd HH:mm:ss",
             "format": "yyyy/MM/dd HH:mm:ss",
             "description": "2016/01/01 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "68",
             "id": "784191b5-429d-4db3-9cd1-5764d2bd4f14",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy/M/d HH:mm:ss",
             "format": "yyyy/M/d HH:mm:ss",
             "description": "2016/1/1 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "69",
             "id": "5ecab5c8-8ac7-4de7-a1b1-5a1647904941",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yy HH:mm:ss",
             "format": "MM-yy HH:mm:ss",
             "description": "01-16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "70",
             "id": "9934ed15-4eb2-4d24-9b5b-5a967abbb2b3",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yy HH:mm:ss",
             "format": "M-yy HH:mm:ss",
             "description": "1-16 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "71",
             "id": "e667285f-3b35-463f-9e74-5adb93569afe",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "MM-yyyy HH:mm:ss",
             "format": "MM-yyyy HH:mm:ss",
             "description": "01-2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "72",
             "id": "4745208e-4ecc-4038-aac7-5afc7319c36b",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "M-yyyy HH:mm:ss",
             "format": "M-yyyy HH:mm:ss",
             "description": "1-2016 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "73",
             "id": "e85030bc-8076-4e40-80b5-5b5f1196a292",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-MM HH:mm:ss",
             "format": "yy-MM HH:mm:ss",
             "description": "16-01 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "74",
             "id": "3dfcc6e1-2391-4cc9-b263-5dac3359602a",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-M HH:mm:ss",
             "format": "yy-M HH:mm:ss",
             "description": "16-1 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "75",
             "id": "ec708bba-7a50-4b1f-af5f-5dd8afc80110",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-MM HH:mm:ss",
             "format": "yyyy-MM HH:mm:ss",
             "description": "2016-01 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "76",
             "id": "353f1ebc-5d53-4802-a269-60516cd92ded",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-M HH:mm:ss",
             "format": "yyyy-M HH:mm:ss",
             "description": "2016-1 13:05:08",
             "category": "Short Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "77",
             "id": "6d443fad-8764-497c-abe4-61c534e26787",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yy HH:mm:ss tt",
             "format": "[Month Name]-yy HH:mm:ss tt",
             "description": "January-16 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "78",
             "id": "4fa8464a-d29c-44e1-9ada-647b36b6d109",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yyyy HH:mm:ss tt",
             "format": "[Month Name]-yyyy HH:mm:ss tt",
             "description": "January-2016 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "79",
             "id": "ec36fff8-eccb-49a1-813c-67164e64d984",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-[Month Name] HH:mm:ss tt",
             "format": "yyyy-[Month Name] HH:mm:ss tt",
             "description": "2016-January 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "80",
             "id": "cfe19542-05a0-4204-88c1-683a840bfab6",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-[Month Name] HH:mm:ss tt",
             "format": "yy-[Month Name] HH:mm:ss tt",
             "description": "16-January 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "81",
             "id": "196ca9d3-a366-45a9-9bd5-68b6fc3bddf2",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss tt",
             "format": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss tt",
             "description": "Friday, January 01, 2016 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "82",
             "id": "0523248a-c64e-498e-b0b1-69eb20b817bb",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss tt",
             "format": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss tt",
             "description": "Friday, January 1, 2016 01:05:08 AM",
             "category": "Long Date & Long Hour",
             "subCategory": "12-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "83",
             "id": "73420f7b-ff6d-40c5-820e-6bb3e2953b41",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yy HH:mm:ss",
             "format": "[Month Name]-yy HH:mm:ss",
             "description": "January-16 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "84",
             "id": "b8ac0da6-0300-4565-ba2a-6c1980eaa25b",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Month Name]-yyyy HH:mm:ss",
             "format": "[Month Name]-yyyy HH:mm:ss",
             "description": "January-2016 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "85",
             "id": "9c544e73-32e9-4c7d-9de8-6c229bd73a3e",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yyyy-[Month Name] HH:mm:ss",
             "format": "yyyy-[Month Name] HH:mm:ss",
             "description": "2016-January 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "86",
             "id": "7d463002-30df-4046-a14d-6c687e4e7a92",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "yy-[Month Name] HH:mm:ss",
             "format": "yy-[Month Name] HH:mm:ss",
             "description": "16-January 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "yearmonthandtime",
             "formatDataType": null,
             "position": "87",
             "id": "c58457a6-98a1-4e69-92c9-6e093e2f58f3",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss",
             "format": "[Day Names of the Week], [Month Name] dd, yyyy HH:mm:ss",
             "description": "Friday, January 01, 2016 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "88",
             "id": "54c32a12-c047-42f6-b256-70d389788e88",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           },
           {
             "name": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss",
             "format": "[Day Names of the Week], [Month Name] d, yyyy HH:mm:ss",
             "description": "Friday, January 1, 2016 13:05:08",
             "category": "Long Date & Long Hour",
             "subCategory": "24-hour",
             "dataType": "Date & Time",
             "groupBy": "dateandtime",
             "formatDataType": null,
             "position": "89",
             "id": "3bd8ea56-6110-4047-9bd0-76086ec5ebcf",
             "state": 0,
             "deleted": false,
             "inserted": true,
             "version": null,
             "created": null,
             "createdBy": null,
             "modified": null,
             "modifiedBy": null
           }
         ]

   .. code-block:: http

      GET /api/report/field/dataFormat/PageNumber HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json

         [
            {
               "name": "Page Number",
               "format": "Page Number",
               "description": "",
               "category": "",
               "subCategory": "",
               "dataType": "Page Number",
               "groupBy": "",
               "formatDataType": null,
               "position": "111",
               "customId": "dd465832-37ea-41d7-91d5-021dc4a04176",
               "id": "dd465832-37ea-41d7-91d5-021dc4a04176",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Page Number of Total Page Numbers",
               "format": "Page Number of Total Page Numbers",
               "description": "",
               "category": "",
               "subCategory": "",
               "dataType": "Page Number",
               "groupBy": "",
               "formatDataType": null,
               "position": "112",
               "customId": "7371329e-de2a-4585-b229-02549c9682fa",
               "id": "7371329e-de2a-4585-b229-02549c9682fa",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            },
            {
               "name": "Page Number / Total Page Numbers",
               "format": "Page Number / Total Page Numbers",
               "description": "",
               "category": "",
               "subCategory": "",
               "dataType": "Page Number",
               "groupBy": "",
               "formatDataType": null,
               "position": "113",
               "customId": "703c194f-c90c-4512-9b2f-0350e9241102",
               "id": "703c194f-c90c-4512-9b2f-0350e9241102",
               "state": 0,
               "deleted": false,
               "inserted": true,
               "version": null,
               "created": null,
               "createdBy": null,
               "modified": null,
               "modifiedBy": null
            }
         ]

POST report/loadFilterFieldData
------------------------------------------------

Returns data of a data source field for the Equivalence filter operators.

**Request**

    Payload: a :doc:`models/ReportFilterSetting` object

**Response**

    An array of string values

**Samples**

   .. code-block:: http

      POST /api/report/loadFilterFieldData HTTP/1.1

   Request payload::

      {
        "logic" : "",
        "visible" : false,
        "filterFields" : [{
              "connectionName" : "Northwind",
              "querySourceCategoryName" : "dbo",
              "sourceFieldName" : "ShipCountry",
              "sourceFieldVisible" : true,
              "sourceFieldFilterable" : true,
              "sourceDataObjectName" : "Orders",
              "dataType" : "Text",
              "filterId" : "00000000-0000-0000-0000-000000000000",
              "querySourceFieldId" : "b703f89d-745d-4f14-baf4-325078c6fa56",
              "querySourceType" : "Table",
              "querySourceId" : "9ef435d9-0864-403e-b74e-69e86115e8ce",
              "relationshipId" : null,
              "alias" : "ShipCountry",
              "position" : 1,
              "visible" : false,
              "required" : false,
              "cascading" : true,
              "operatorId" : "003c0e13-cc3c-412f-8fee-1cf21aa51e31",
              "operatorSetting" : null,
              "value" : "",
              "sortType" : "Unsorted",
              "fontFamily" : null,
              "fontSize" : 0,
              "textColor" : null,
              "backgroundColor" : null,
              "fontBold" : false,
              "fontItalic" : false,
              "fontUnderline" : false,
              "id" : "00000000-0000-0000-0000-000000000000",
              "state" : 0,
              "modified" : null,
              "dateTimeNow" : "",
              "isParameter" : false,
              "sourceDataObjectFullName" : "Northwind.dbo.Orders",
              "selected" : true,
              "dataFormatId" : null
           }
        ],
        "id" : "3b6f20f2-09f3-42a9-9e1e-c9db71b4ea7a",
        "reportId" : "59aaae21-d3f7-43aa-bda0-590f3106dbb9"
      }

   Response::

      ["Finland", "USA", "Italy", "Brazil", "Germany", "Switzerland", "Mexico", "Sweden", "Argentina", "Austria", "UK", "Poland", "BrazilRT", "Canada", "Ireland", "Norway", "France", "Belgium", "Spain", "Venezuela", "Denmark", "Portugal"]

.. _POST_report/loadFilterFieldDataAsTree:

POST report/loadFilterFieldDataAsTree
------------------------------------------------

.. figure:: /_static/images/Report_Designer_loadFilterFieldDataAsTree.png
   :align: right
   :width: 219px

   Data returned by loadFilterFieldDataAsTree on UI

Returns data of a data source field in a tree-like structure, for the filter operators Equals (Tree) and Not Equal (Tree). |br|

**Request**

    Payload: a :doc:`models/ReportFilterSetting` object

**Response**

    A :doc:`models/ValueTreeNode` object

**Samples**

   .. code-block:: http

      POST /api/report/loadFilterFieldDataAsTree HTTP/1.1

   Request payload::

      {
        "logic" : "",
        "visible" : false,
        "filterFields" : [{
              "connectionName" : "Northwind",
              "querySourceCategoryName" : "dbo",
              "sourceFieldName" : "ShipCountry",
              "sourceFieldVisible" : true,
              "sourceFieldFilterable" : true,
              "sourceDataObjectName" : "Orders",
              "dataType" : "Text",
              "filterId" : "00000000-0000-0000-0000-000000000000",
              "querySourceFieldId" : "b703f89d-745d-4f14-baf4-325078c6fa56",
              "querySourceType" : "Table",
              "querySourceId" : "9ef435d9-0864-403e-b74e-69e86115e8ce",
              "relationshipId" : null,
              "alias" : "ShipCountry",
              "position" : 1,
              "visible" : false,
              "required" : false,
              "cascading" : true,
              "operatorId" : "003c0e13-cc3c-412f-8fee-1cf21aa51e31",
              "operatorSetting" : null,
              "value" : "",
              "sortType" : "Unsorted",
              "fontFamily" : null,
              "fontSize" : 0,
              "textColor" : null,
              "backgroundColor" : null,
              "fontBold" : false,
              "fontItalic" : false,
              "fontUnderline" : false,
              "id" : "00000000-0000-0000-0000-000000000000",
              "state" : 0,
              "modified" : null,
              "dateTimeNow" : "",
              "isParameter" : false,
              "sourceDataObjectFullName" : "Northwind.dbo.Orders",
              "selected" : true,
              "dataFormatId" : null
           }
        ],
        "id" : "3b6f20f2-09f3-42a9-9e1e-c9db71b4ea7a",
        "reportId" : "59aaae21-d3f7-43aa-bda0-590f3106dbb9"
      }

   Response::

      [{
           "nodes" : [{
                 "nodes" : [],
                 "text" : "[Blank]",
                 "value" : "[Blank]"
              }, {
                 "nodes" : [],
                 "text" : "Finland",
                 "value" : "Finland"
              }, {
                 "nodes" : [],
                 "text" : "USA",
                 "value" : "USA"
              }, {
                 "nodes" : [],
                 "text" : "Italy",
                 "value" : "Italy"
              }, {
                 "nodes" : [],
                 "text" : "Brazil",
                 "value" : "Brazil"
              }, {
                 "nodes" : [],
                 "text" : "Germany",
                 "value" : "Germany"
              }, {
                 "nodes" : [],
                 "text" : "Switzerland",
                 "value" : "Switzerland"
              }, {
                 "nodes" : [],
                 "text" : "Mexico",
                 "value" : "Mexico"
              }, {
                 "nodes" : [],
                 "text" : "Sweden",
                 "value" : "Sweden"
              }, {
                 "nodes" : [],
                 "text" : "Argentina",
                 "value" : "Argentina"
              }, {
                 "nodes" : [],
                 "text" : "Austria",
                 "value" : "Austria"
              }, {
                 "nodes" : [],
                 "text" : "UK",
                 "value" : "UK"
              }, {
                 "nodes" : [],
                 "text" : "Poland",
                 "value" : "Poland"
              }, {
                 "nodes" : [],
                 "text" : "BrazilRT",
                 "value" : "BrazilRT"
              }, {
                 "nodes" : [],
                 "text" : "Canada",
                 "value" : "Canada"
              }, {
                 "nodes" : [],
                 "text" : "Ireland",
                 "value" : "Ireland"
              }, {
                 "nodes" : [],
                 "text" : "Norway",
                 "value" : "Norway"
              }, {
                 "nodes" : [],
                 "text" : "France",
                 "value" : "France"
              }, {
                 "nodes" : [],
                 "text" : "Belgium",
                 "value" : "Belgium"
              }, {
                 "nodes" : [],
                 "text" : "Spain",
                 "value" : "Spain"
              }, {
                 "nodes" : [],
                 "text" : "Venezuela",
                 "value" : "Venezuela"
              }, {
                 "nodes" : [],
                 "text" : "Denmark",
                 "value" : "Denmark"
              }, {
                 "nodes" : [],
                 "text" : "Portugal",
                 "value" : "Portugal"
              }
           ],
           "text" : "[All]",
           "value" : "[All]"
        }
      ]

POST report/loadPartialFilterFieldData
--------------------------------------------------------------

Returns paged data source field data for Equivalence operators in filter.

**Request**

    A :doc:`models/ReportFilterFieldPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of string values

**Samples**

   .. code-block:: http

      POST /api/report/loadPartialFilterFieldData HTTP/1.1

   .. container:: toggle

      .. container:: header

         Request payload:

      .. code-block:: json

            {
               "skipItems": 0,
               "pageSize": 100,
               "reportParameter": {
                  "reportKey": {
                     "key": "968a482b-bda8-4650-b09a-bf35b4d734b3",
                     "modified": null,
                     "tenantId": null
                  },
                  "section": 0,
                  "saveAs": false,
                  "ignoreCheckChange": false,
                  "report": {
                     "name": "Example Report",
                     "type": 1,
                     "previewRecord": 10,
                     "advancedMode": true,
                     "allowNulls": false,
                     "isDistinct": false,
                     "categoryId": null,
                     "category": {
                        "id": null,
                        "name": "",
                        "type": 1,
                        "tenantId": null
                     },
                     "subCategory": {
                        "id": null,
                        "name": "",
                        "type": 1,
                        "tenantId": null
                     },
                     "subCategoryId": null,
                     "reportDataSource": [{
                        "aliasId": "205c0e5f-fff8-409b-a54a-b6687619486d_Orders",
                        "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                        "querySourceName": "Orders",
                        "selected": true,
                        "categoryId": "fe0c29b6-6f72-40f4-bb92-cfb6b05bd00e",
                        "primaryFields": [{
                           "name": "OrderID",
                           "alias": "",
                           "dataType": "int",
                           "izendaDataType": "Numeric",
                           "allowDistinct": false,
                           "visible": true,
                           "filterable": true,
                           "querySourceId": "00000000-0000-0000-0000-000000000000",
                           "parentId": null,
                           "expressionFields": [],
                           "filteredValue": "",
                           "type": 0,
                           "groupPosition": 0,
                           "position": 0,
                           "extendedProperties": "{\"PrimaryKey\":true}",
                           "physicalChange": 0,
                           "approval": 0,
                           "existed": false,
                           "matchedTenant": false,
                           "originalName": "OrderID",
                           "originalId": "00000000-0000-0000-0000-000000000000",
                           "isParameter": false,
                           "isCalculated": false,
                           "hasAggregatedFunction": false,
                           "inaccessible": false,
                           "isCheck": false,
                           "id": "2be8c595-91a3-4250-8828-dbbc07eaba83"
                        }]
                     }],
                     "reportRelationship": [],
                     "reportFilter": {
                        "logic": "",
                        "visible": false,
                        "filterFields": [{
                           "connectionName": "Northwind-BA",
                           "querySourceCategoryName": "dbo",
                           "sourceFieldName": "ShipPostalCode",
                           "sourceFieldVisible": true,
                           "sourceFieldFilterable": true,
                           "sourceDataObjectName": "Orders",
                           "dataType": "Text",
                           "filterId": "00000000-0000-0000-0000-000000000000",
                           "querySourceFieldId": "cacc4fe7-797f-405e-bb92-7a4b8afcddcc",
                           "querySourceType": "Table",
                           "querySourceId": "205c0e5f-fff8-409b-a54a-b6687619486d",
                           "alias": "ShipPostalCode",
                           "position": 1,
                           "visible": true,
                           "required": false,
                           "cascading": true,
                           "operatorId": "737307d1-1e5f-407f-889f-1b3c9a66dd6f",
                           "value": "",
                           "sortType": "ASC",
                           "fontBold": false,
                           "fontItalic": false,
                           "fontUnderline": false,
                           "state": 1,
                           "dateTimeNow": "",
                           "isParameter": false,
                           "sourceDataObjectFullName": "Northwind-BA.dbo.Orders",
                           "selected": true,
                           "uniqueId": "42",
                           "isInheritableFilter": false
                        }],
                        "id": "0a1a5771-dbe9-4148-9d2f-f79a4c83b962",
                        "reportId": "968a482b-bda8-4650-b09a-bf35b4d734b3"
                     },
                     "reportPart": [],
                     "version": 0,
                     "schedules": [],
                     "ownerId": "9d2f1d51-0e3d-44db-bfc7-da94a7581bfe",
                     "accesses": [],
                     "dynamicQuerySourceFields": [],
                     "snapToGrid": false,
                     "isGlobal": false
                  },
                  "expandedLevel": 0,
                  "reportState": 0
               },
               "includeAll": false,
               "includeBlank": true,
               "criteria": [{
                  "key": "filter"
               }]
            }

   Response::

      {
         "result": [
            "[BLANK]",
            "[NULL]",
            "02389-673",
            "82520",
            "83720",
            "PO31 7PJ",
            "T2F 8M4",
            "V3F 2K1"
         ],
         "pageIndex": 0,
         "pageSize": 100,
         "total": 8,
         "skipItems": 0,
         "isLastPage": true
      }

POST report/loadPartialFilterFieldDataAsTree
--------------------------------------------------------------

Returns paged data source field data in a hierarchy for Equivalence operators in filter.

**Request**

    A :doc:`models/ReportFilterFieldPagedRequest` object

**Response**

    A :doc:`models/PagedResult` object, with **result** field containing an array of :doc:`models/ValueTreeNode` objects

**Samples**

   .. code-block:: http

      POST /api/report/loadPartialFilterFieldDataAsTree HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample Response:

      .. code-block:: json

         {
            "result": [
               {
                     "nodes": [
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "[Blank]",
                           "value": "[Blank]",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "[Null]",
                           "value": "[Null]",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "02389-673",
                           "value": "02389-673",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "82520",
                           "value": "82520",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "83720",
                           "value": "83720",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "PO31 7PJ",
                           "value": "PO31 7PJ",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "T2F 8M4",
                           "value": "T2F 8M4",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        },
                        {
                           "nodes": [],
                           "parent": null,
                           "id": 0,
                           "text": "V3F 2K1",
                           "value": "V3F 2K1",
                           "numOfChilds": 0,
                           "numOfCheckedChilds": 0,
                           "indeterminate": false,
                           "fullPath": null,
                           "computeNameSettings": null,
                           "isCheck": false
                        }
                     ],
                     "parent": null,
                     "id": 0,
                     "text": "[All]",
                     "value": "[All]",
                     "numOfChilds": 30,
                     "numOfCheckedChilds": 0,
                     "indeterminate": false,
                     "fullPath": null,
                     "computeNameSettings": null,
                     "isCheck": false
               }
            ],
            "pageIndex": 0,
            "pageSize": 100,
            "total": 0,
            "skipItems": 0,
            "isLastPage": false
         }


POST report/loadAllFilterFieldsData
------------------------------------------------

Returns all data values for all filter fields in a report. |br|
Deprecated, please use `POST report/loadPartialFilterFieldData`_ to avoid timeouts loading large data.

**Request**

    Payload: a :doc:`models/ReportFilterSetting` object

**Response**

    An array of objects as following:

    .. list-table::
       :header-rows: 1

       *  -  Field
          -  Description
          -  Note
       *  -  **filterFieldId** |br|
             string (GUID)
          -  The id of the filter field
          -
       *  -  **data** |br|
             array of strings
          -  An array of all values of the filter field converted to strings.
          -

**Samples**

   .. code-block:: http

      POST /api/report/loadAllFilterFieldsData HTTP/1.1

   Request payload::

      {
        "reportId" : "babe2f8c-a9b9-4a28-98b9-426b8c15497c",
        "filter" : null
      }

   Response::

      [{
           "filterFieldId" : "d192bde7-0e51-4daa-8113-d3d79b539337",
           "data" : ["France", "Germany", "BrazilRT", "Belgium", "Brazil", "Switzerland", "Venezuela", "Austria", "Mexico", "USA", "Sweden", "Finland", "Italy", "Spain", "UK", "Ireland", "Portugal", "Canada", "Denmark"]
        }
      ]

.. _Validate_Filter:

GET report/validateFilter/{report_id}
--------------------------------------

Validates that all required filters in specified report have filter value.

**Request**

    No payload

**Response**

     - true if all required filters have filter value
     - false if not

**Sample**
   .. code-block:: http

      GET report/validateFilter/737c3aa4-f9df-46a0-acc9-312dc2e7f085 HTTP/1.1

   .. container:: toggle

      .. container:: header

         Sample response:

      .. code-block:: json
         
         true
