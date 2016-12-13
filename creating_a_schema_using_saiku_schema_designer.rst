Creating A Schema Using Saiku Schema Designer
=============================================

What Is A Schema?
-----------------

A schema in its raw form is an XML document that defines how the data is laid out in your database. Within Saiku you might have multiple schema, each containing multiple cubes, within a cube are collections of Dimensions and Measures. The schema allows Saiku to display the UI elements that lets users discover answers to their data in a drag and drop format.

Understanding How A Schema Is Laid Out
--------------------------------------

A Saiku schema contains a number of distinct elements, the first section is called the Physical Schema, this is a description of how the tables you want to make available to you users are related to one another.
For example you might have a fact table related to sales, this probably wont have a key. You then have a dimension for customers, this has a key on a CUSTOMER_TK field. The customer dimension joins to the sales fact table via the CUSTOMER_TK fields in both tables, so you then link these tables together using those keys. This means when the SQL is executed, Saiku understands how the tables join together.
Once you have decided which tables are available you can then build the cubes, dimensions and measures that make up the main bulk of a schema.
A cube is a collection of dimensions and measures relating to a specific set of information, for example, you might have a cube for sales data, another for marketing stats and so on.
Dimensions reside both inside and outside of cubes, dimensions outside of cubes can be shared across cubes, unsurprisingly these are known as Shared Dimensions. Dimensions are usually textual data that can consist of hierarchies and levels. Returning to our customer dimension in the earlier description, a Dimension could be called Customer, within a Dimension you could have 0, 1 or many hierarchies, the choice is often driven by reporting requirements. In our customer example a hierarchy may simply be called Customer, within that hierarchy you might have a number of levels, for example Country, County, Town. You might then decide you want a second hierarchy called Category, where you have sorted your customers into distinct groups, this might contain a level called Groups. In doing this you could then easily create a report that shows sales by customer location and cross-tabulated with group information.
Lastly we have Measures. Measures are numerical stats that allow us to, measure, the data we are interrogating. So, sales totals, sales counts, cost, tax and so on are likely measures in a sales type cube. Measures in Saiku are always numerical.

Connecting
----------

Opening Saiku Schema Designer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To create a Saiku schema the first task is to open the schema designer. Administrators can click on the cube icon in the main toolbar.

This will then ask if you want to create a new schema or open an existing one. If you click on New you are then prompted for a schema name, which is a human readable name for the collection of cubes, it also needs to be unique as this is what the saved schema is called. When you click on create schema you are then asked to connect to a database.

Connecting to a database
~~~~~~~~~~~~~~~~~~~~~~~~

To create a schema you need a working data source that Saiku can connect to. This can be either a standard JDBC compliant database, or a Saiku Mongo connection. Select the connection type you want and fill in the data source information.

Driver: this is the jdbc driver class, some common examples are:

MySQL: `com.mysql.jdbc.Driver`

PostgreSQL: `org.postgresql.Driver`

Oracle: `oracle.jdbc.OracleDriver`

MSSQL: `net.sourceforge.jtds.jdbc.Driver`

URL: This is the JDBC url for your database connection, some common examples are:

MySQL: `jdbc:mysql://database`

PostgreSQL: `jdbc:postgresql://host/database`

Oracle: `jdbc:oracle:<drivertype>:@<database>`

MSSQL: `jdbc:jtds:sqlserver://server/`

Username: Database Username

Password: Database Password

Once this is done, you will be given the ability to select a database and schema from that database.
You should then be given a list of tables available to use within your Saiku schema.

Importing Tables
----------------

Defining Which Tables Are Available Within The Schema
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A Saiku schema doesn't need to have access to all tables within your schema, this would just confuse matters, so first we decide which tables we want to include.
At the top of the page you can see a list of tables and a summary of their first fields, if you need a table in your schema then drag the table from the top row and drop it on the canvas below.

If your table has a key field, like an ID or TK you can select the key in the next field, the key can also be made up of a number of fields.

You dimension tables should all have an ID, but your fact table may not have an ID field so you can just press cancel.
Once you have selected your tables you can then join the tables that link together. Drag a table join circle from one table to the target, usually you would drag from source to target, so for example if you join a dimension to the fact table, you would drag from the dimension to the fact table and select the foreign key, this will create the join.

If you join the wrong way, don't worry you can just click on the join and change the order.
Once you are happy with your tables, joins and keys you can then create your cubes.

Creating Cubes
--------------

Once you have your tables defined it is time to create your cubes, dimensions and measures.

Cubes contain collections of dimensions and measures, so for example you might have a cube that deals with Sales, and another cube that deals with Purchases and so on.

When you open the schema designer you will see we have pre populated the designer with a blank cube.

By default this cube is called Cube 1 which isn't very useful so the first thing you should do is give it a proper name.

Dimensions
~~~~~~~~~~

Now you have done this we can create some dimensions. To do this you drag the tables you allocated in the screen before across from the left column to the centre column, when you drop it the schema designer will ask you if you want to "Auto generate all the attributes from every column of <tablename>?" If you have a table full of 1 level attributes then this can be a quick and useful way to import all your attributes quickly, but often you want to be able to define the keys and names of just a few columns or customise it entirely, in which case you can click Yes and edit it after the fact or No and insert the attributes manually.

Attributes
~~~~~~~~~~

Attributes are mappings of table columns to the schema, so for example you might have a customer table and within that a customer name, address, phone number, country etc. These are attributes in your dimension, so create attributes to include them in your dimension.

If you have a hierarchy you might need to create a joined key that explains to Saiku how the hierarchical join would work, for example if you wanted to create a hierarchy that allowed users to select Country then drill down to State you would likely have to create a compound key in the schema of Country and State and select a name column that assigns State to the name.

If you don't want to define Hierarchies and Levels and instead just want a selection of 1 level attributes available to your users, you can check Has Hierarchy and then you don't need to create a hierarchy for it to be displayed in the Saiku UI, if you plan to create Hierarchies and Levels, leave this blank.

Hierarchies
~~~~~~~~~~~

Hierarchies are collections of levels, levels are attributes ordered as such that the drill and display order makes sense.

So using our customer dimension as an example, you might have a hierarchy also called Customers and an all member name called All Customers, within that you might have a few levels, Country, State, City, Customer Name. This would be a logical hierarchy for customers where you want to be able to slice and dice by geography. Similarly if you were creating time dimensions, Year, Month, Day would be a logical level order.

You can add as many hierarchies as you require per dimension, most will only have 1 or 2, but there is no restriction on the amount of hierarchies you have.
 
Cubes
~~~~~

So as mentioned earlier a cube is a collection of dimensions and measures. The dimensions we have created are shared globally so they need to be imported into the cube we are creating and along with that one or more measures need to be defined so we can "measure" our data.

First we have to understand the concept of measure groups, for those of you who have used Saiku 2.x or Mondrian 3 then there used to be a concept called virtual cubes where you would define multiple cubes and if you needed to compare measures in different cubes you would create a virtual cube, in Saiku 3 we use Measure Groups, these are tied to tables and you can have 1 or more of them. You don't have to have different fact tables for measure groups, you might just want to bucket your measures into different sections(currently the Saiku UI doesn't expose this but it is in development), or as discussed you might want to include more than one fact table in your cube.

Once you have created your measure groups you can select one for editing, first you need to select the fact table you will be creating the measures from, and give it a name, Default is fine, you might want to call it something different.

Next you add measures to your cube. Measures are always numeric but can be Sum/Average/Min/Max etc.

Give the measure a name, select the column that represents the measure and the aggregation you want to use. If you want to apply a format string you can add it in the box below, although this isn't mandatory.

Add as many measures as you require, then press the next button.

Lastly we need to link the dimensions we created in the previous section to the cube. So in the Select Dimension box select the dimension you want to import into your cube. If the dimension is based on the same table as the fact table used in the current measure group then the Select Foreign Key box will disabled itself as you don't require a key, but if your dimension is linking to an external table then you need to select the column in the fact table that links to this external table.

Once you have added all your dimension links, make sure you press the Update button to save the changes to that measure group.


Saving/Exporting
----------------

Saving
~~~~~~
To save the schema to the Saiku repository, exit the Cubes and Dimensions dialog by pressing the Save button, and then click on the Create Schema button in the main dashboard designer toolbar: ￼

This will publish your schema to the repository saving it in a file with the same name as the schema. You can then go across to the Administration panel to create or update a data source to use your new schema.

Note
Currently you cannot open a saved schema for futher editing, so it is recommended that you keep the schema designer open until you are happy with the schema design. To make further modifications you can export your schema (see below) and open the file in a text editor.

Exporting
~~~~~~~~~
If you want to make further changes to your schema, backup or use it elsewhere you can click the Download button in the Administration panel under the schema you want to export and it will download the schema to an XML file on your local computer. You can then make changes to the file locally and upload it back to the server for further use.
