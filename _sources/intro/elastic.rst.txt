.. _Elasticsearch:

==============
Elasticsearch
==============

What is Elasticsearch?
^^^^^^^^^

Elasticsearch is a distributed, RESTful, full-text search engine that
operates against document-oriented or semi-structured data. Much like a
database, it is intended to store, index, retrieve, and manage your
data. Users can send JSON documents via an API or ingestion
tools, after which Elasticsearch will automatically store the document
and create indexed reference values. Once uploaded, users are then able
to search and retrieve documents using the Elasticsearch API.

What does Izenda Support?
^^^^^^^^^

Our implementation of the Elacsticsearch Driver (available in v2.18.0 or
later) is powered by CDATA and supports all of the following:

- Elasticsearch v2.2 and above

- Both SQL and REST endpoint

- Querying multiple indices at one time


Best Practices for Setting up and Using your Elastic Instance:
^^^^^^^^^

For hosting and leveraging an Amazon Elasticsearch Service, there are
several best practices recommended by Amazon found
`here <https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/aes-bp.html>`__.

For general use case best practices, there are two recommendations from
the `Elasticsearch
documentation <https://www.elastic.co/guide/en/elasticsearch/reference/current/general-recommendations.html>`__
that still hold true for Izenda:

- Don’t return large result sets

    -  Elasticsearch is great at getting the top matches for queries, but isn’t designed for database-specific scenarios like returning all documents that match a particular query.

- Avoid large documents

    - By default, Elasticsearch will not index any document larger than 100MB.

    - By manually changing this, you are still limited to a maximum document size of 2GB

    - Excessive large documents will put a strain on your network, memory, and disk usage.


How do you set up your Elastic connection in Izenda?
^^^^^^^^^

Establishing a connection to an Elasticsearch instance is done the same
way as setting up any connection to a relational database within Izenda.

1. Go to the Settings > Data Setup > Connection Strings page of your
   Izenda instance and hit ‘Add Connection’ along the top

2. From the Data Server Type dropdown select [ES] Elasticsearch

3. Insert your connection string to your Elasticsearch instance, which may look like the following: server=https://yourelasticinstanceurl;Port=9243;User=izenda;Password=xxxxx;FlattenArrays=7;

4. Hit ‘Test’ to see if your credentials are valid. If they are
   incorrect, please adjust your connection string and try again.

5. Once the test is successful, hit ‘Connect’ to let Izenda connect to
   your instance and gather metadata for our data model.

6. Once connected you will be able to select which objects from your
   the instance you wish to use within Izenda by moving them into the
   ‘Visible Data Sources’ column and hitting save.

Configuring your Data Model in Izenda:
^^^^^^^^^

Now that your connection is saved and you’ve set your Visible Data
Sources, you can now move to the Settings > Data Setup > Data Model page
to begin making any customizations like aliasing or categorizing these
objects. More information on this area and its features can be
found \ `here <https://www.izenda.com/docs/ui/doc_data_model_tables,_views_and_stored_procedures.html>`__\ .
