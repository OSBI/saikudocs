Whilst we haven't yet had the time or resource to create a lovely graphical admin console for you system administrators we have tried to make it simple for you to add new data sources to the Saiku platform.

# Data Source Definition

All data sources are stored as plain text files in folder `saiku-server/tomcat/webapps/saiku/WEB-INF/classes/saiku-datasources/` with one data source per file. You can use your favourite text editor to add/edit data source.

This is how sample data source for MySQL looks like:


```
`type=OLAP
name=steelwheels
driver=mondrian.olap4j.MondrianOlap4jDriver
location=jdbc:mondrian:Jdbc=jdbc:mysql://localhost/sampledata;Catalog=res:foodmart/Foodmart.xml;JdbcDrivers=com.mysql.jdbc.Driver;
username=dbuser
password=password
`
```
Every data source definition contains at least the following elements:

* `type` - Always OLAP.
* `name` - Name of data source. This name will be shown to Saiku user together with schema name. Can contain spaces.
* `driver` - Driver for specific database. See examples below to find correct driver for your data.
* `location` - Location of data and Mondrian schema (see Location Details).
* `username` - Username to be used when connecting to data source.
* `password` - Password to be used when connecting to data source.

## Location Details

For MySQL, PostgreSQL and DB2 you have to define the following in `location`:

JDBC connection stringMondrian schema destinationJDBC driver name### JDBC Connection String

The following describes JDBC connection string patterns for most common databases:

* MySQL: `[jdbc:mysql://[database]() host]/[database name]`
* PostgreSQL: `[jdbc:postgresql://[database]() host]:[port]/[database name]`
* DB2: `[jdbc:db2://[database]() host]:[port]/[DATABASE NAME]`

### Mondrian Schema Destination

Destination of Mondrian schema is specified using `Catalog` attribute. Destination must include full file name, including extension.

Examples:

* `Catalog=[res:foodmart/Foodmart.xml](http://resfoodmart)` will search for schema named `Foodmart.xml` in directory `saiku-server/tomcat/webapps/saiku/WEB-INF/classes/foodmart`
* `Catalog=res:Foodmart.xml` will search for schema named `Foodmart.xml` in directory `saiku-server/tomcat/webapps/saiku/WEB-INF/classes/`

### JDBC Driver Name

* MySQL: `com.mysql.jdbc.Driver`
* PostgreSQL: `org.postgresql.Driver`
* DB2: `com.ibm.db2.jcc.DB2Driver`

# Adding a New JDBC Driver

Obviously not everyone uses Hypersonic or MySQL to connect to their data warehouses. To use your specific database you will have to add new JDBC driver to Saiku:

Get JDBC driver for your database.Add the JDBC connector jar file to `saiku-server/tomcat/webapps/saiku/WEB-INF/lib/`.Restart server.# Sample Data Sources

## Mondrian on MySQL


```
`type=OLAP
name=steelwheels
driver=mondrian.olap4j.MondrianOlap4jDriver
location=jdbc:mondrian:Jdbc=jdbc:mysql://localhost/sampledata;Catalog=res:foodmart/Foodmart.xml;JdbcDrivers=com.mysql.jdbc.Driver;
username=dbuser
password=password
`
```
## XML/A (Pentaho BI Server)


```
`type=OLAP
name=xmla
driver=org.olap4j.driver.xmla.XmlaOlap4jDriver
location=jdbc:xmla:Server=http://localhost:8080/pentaho/Xmla?userid=joe&password=password;
username=joe
password=password
`
```
## XML/A (PALO)


```
`type=OLAP
name=xmla
driver=org.olap4j.driver.xmla.XmlaOlap4jDriver
location=jdbc:xmla:Server=http://localhost:4242/
username=joe
password=password
`
```
## Mondrian on PostgreSQL


```
`type=OLAP
name=db_name
driver=mondrian.olap4j.MondrianOlap4jDriver
location=jdbc:mondrian:Jdbc=jdbc:postgresql://localhost:5432/db_name;Catalog=res:foodmart/Foodmart.xml;JdbcDrivers=org.postgresql.Driver;
username=db_user_name
password=db_password
`
```
JDBC driver for PostgreSQL can be downloaded here: [http://jdbc.postgresql.org/download.html](http://jdbc.postgresql.org/download.html)

## XML/A (Microsoft SSAS)

__Note__: you need to install the [mdmdpump.dll](http://technet.microsoft.com/en-us/library/cc917711.aspx) and then configure access.


```
`type=OLAP
name=xmla
driver=org.olap4j.driver.xmla.XmlaOlap4jDriver
location=jdbc:xmla:Server=http://192.168.0.1/olap/msmdpump.dll
username=joe
password=password
`
```
## DB2

Note With DB2, schema files must define tables, views and columns in UPPER CASE. DB2 is case sensitive. If you specify a table or column name without double-quotes, it is converted to upper case. This happens in both a CREATE TABLE statement and in SELECT statements. The solution is either to use double-quotes when creating your schema (so your table will be called czas) or to specify the table and column names in upper-case in your mondrian schema file.


```
`type=OLAP
name=datasource_name
driver=mondrian.olap4j.MondrianOlap4jDriver
location=jdbc:mondrian:Jdbc=jdbc:db2://servername:port/SAMPLE;Catalog=res:foodmart/Foodmart.xml;JdbcDrivers=com.ibm.db2.jcc.DB2Driver;
username=username
password=password
`
```
