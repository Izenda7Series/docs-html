.. _MongoDB:

==============
MongoDB
==============

What is MongoDB?
^^^^^^^^^

MongoDB is a document-based database that is designed to scale with the indexing and querying structure 
that you need for your business. It operates by storing data within JSON-like documents, allowing for 
data to vary and have a changing structure over time. This approach allows MongoDB to be an easily distributable 
database which is horizontally scalable. 

What does Izenda Support?
^^^^^^^^^

Our implementation of the MongoDB Driver (available in v3.1.0 or
later) is powered by CDATA and supports all of the following:

- Mongo v2.6 and above


Best Practices for Setting up and Using your MongoDB Instance:
^^^^^^^^^

For information on the best operational practices for your MongoDB instance, please check
their white paper documentation `here <https://www.mongodb.com/thank-you/white-paper/ops-best-practices>`__.

For performance best practices, please review their white paper on how to best leverage `MongoDB's performance <https://www.mongodb.com/thank-you/white-paper/performance-best-practices>`__




How do you set up your MongoDB connection in Izenda?
^^^^^^^^^

Establishing a connection to a MongoDB instance is done the same
way as setting up any connection to a relational database within Izenda.

1. Go to the Settings > Data Setup > Connection Strings page of your
   Izenda instance and hit ‘Add Connection’ along the top

2. From the Data Server Type dropdown select [MONGO] MongoDB

3. Insert your connection string to your MongoDB instance, like the following: Server= https://yourmongoinstanceurl ;Port=27017;Database=[YOUR DATABASE NAME];User=izenda;Password=xxxxx;

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
