Creating A Schema Using Saiku Schema Designer
=============================================


What Is A Schema?
A schema in its raw form is an XML document that defines how the data is laid out in your database. Within Saiku you might have multiple schema, each containing multiple cubes, within a cube are collections of Dimensions and Measures. The schema allows Saiku to display the UI elements that lets users discover answers to their data in a drag and drop format.
Understanding How A Schema Is Laid Out
A Saiku schema contains a number of distinct elements, the first section is called the Physical Schema, this is a description of how the tables you want to make available to you users are related to one another.
For example you might have a fact table related to sales, this probably wont have a key. You then have a dimension for customers, this has a key on a CUSTOMER_TK field. The customer dimension joins to the sales fact table via the CUSTOMER_TK fields in both tables, so you then link these tables together using those keys. This means when the SQL is executed, Saiku understands how the tables join together.
Once you have decided which tables are available you can then build the cubes, dimensions and measures that make up the main bulk of a schema.
A cube is a collection of dimensions and measures relating to a specific set of information, for example, you might have a cube for sales data, another for marketing stats and so on.
Dimensions reside both inside and outside of cubes, dimensions outside of cubes can be shared across cubes, unsurprisingly these are known as Shared Dimensions. Dimensions are usually textual data that can consist of hierarchies and levels. Returning to our customer dimension in the earlier description, a Dimension could be called Customer, within a Dimension you could have 0, 1 or many hierarchies, the choice is often driven by reporting requirements. In our customer example a hierarchy may simply be called Customer, within that hierarchy you might have a number of levels, for example Country, County, Town. You might then decide you want a second hierarchy called Category, where you have sorted your customers into distinct groups, this might contain a level called Groups. In doing this you could then easily create a report that shows sales by customer location and cross-tabulated with group information.
Lastly we have Measures. Measures are numerical stats that allow us to, measure, the data we are interrogating. So, sales totals, sales counts, cost, tax and so on are likely measures in a sales type cube. Measures in Saiku are always numerical.
Connecting
Importing Tables
Creating Cubes
Saving/Exporting
Advanced
Creating A Schema Using Saiku Schema Designer
Opening Saiku Schema Designer
To create a Saiku schema the first task is to open the schema designer. Administrators can click on the cube icon in the main toolbar.

This will then ask if you want to create a new schema or open an existing one. If you click on New you are then prompted for a schema name, which is a human readable name for the collection of cubes, it also needs to be unique as this is what the saved schema is called. When you click on create schema you are then asked to connect to a database.

Connecting to a database
To create a schema you need a working data source that Saiku can connect to. This can be either a standard JDBC compliant database, or a Saiku Mongo connection. Select the connection type you want and fill in the data source information.

Driver: this is the jdbc driver class, some common examples are:
MySQL: com.mysql.jdbc.Driver
PostgreSQL: org.postgresql.Driver
Oracle: oracle.jdbc.OracleDriver
MSSQL: net.sourceforge.jtds.jdbc.Driver

URL: This is the JDBC url for your database connection, some common examples are:
MySQL: jdbc:mysql://database
PostgreSQL: jdbc:postgresql://host/database

Oracle: jdbc:oracle:<drivertype>:@<database>
MSSQL: jdbc:jtds:sqlserver://server/
Username: Database Username
Password: Database Password
Once this is done, you will be given the ability to select a database and schema from that database.
You should then be given a list of tables available to use within your Saiku schema.
