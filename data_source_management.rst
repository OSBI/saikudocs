Data Source Management
======================

Schema Upload
-------------

All Saiku connections require a Mondrian schema definition to tell Saiku how the database maps to a cube. 
To find out more about schema design I would read some of the resources available on the internet, for example: http://type-exit.org/adventures-with-open-source-bi/2010/07/a-basic-mondrian-cube-introducing-the-star-schema/.

Once you have designed your cube you can then upload it to the Saiku server, to do this you need to login as an administrator and go to the Administration console. Then click on the Add Schema button on the left pane. In the main window click the browse button and select your schema file. Next enter a unique name for this schema and then press the upload button. Assuming all goes well you will see an okay message and the new schema listed in the left hand panel.

Remove Old Schemas
------------------
To remove an old schema select the schema from the list on the left hand side, and then in the main screen click the Remove button. Your schema will then be removed from the server.

Data Source Creation
--------------------
Once you have a valid schema available and uploaded to the server, you can then create a data source.

In the Administration Console you click on the Add Data Source button in the left panel. Once this is done you then give the data source a unique name, and if you are wanting to use the embedded Mondrian server you select the Mondrian connection type, if you are wanting to connect to a MSAS/Essbase or remote Mondrian server (or anything else that speaks XML/A) you can select XMLA from the connection type dropdown.

Next you enter the JDBC or XMLA url to the server, this depends on the database type so you will have to consult your documentation, here are a few examples:

`jdbc:mysql://localhost/foodmart`

`jdbc:h2:../../data/foodmart`

`jdbc:postgresql://localhost/foodmart`

you get the idea.

In the next box you need to select the schema that is valid for this database, and then your JDBC driver for example:

`org.h2.Driver`

`com.mysql.jdbc.Driver`

`org.postgresql.Driver`

You also need to make sure that the driver is available to the Saiku server by adding it to the tomcat classpath if it is not already available. To do this you can place it in tomcat/webapps/saiku/WEB-INF/lib and then restart the Saiku server.

Finally you need to add the username and password for the database you are connecting to and then click save. You should then see the data source listed in the list on the left hand panel.

If you are a Saiku 2.x user and you already have a number data sources available in a text file, or you want to add some details that require extra configuration on the commend line, you can click the Advanced button and enter the details into the text box instead of the input fields.

![](wiki-attachment:datasource.png)

Remove Data Source
------------------

If you no longer require a data source you can select it from the list on the left hand panel and then click Remove from the main window, this will remove the data source from the system.

Refresh Data Source Cache
-------------------------

Saiku will by default cache the data returned from queries to improve performance where possible. If you update the data available within the data base you can tell it to refresh the database cache by selecting the data source from the list and then clicking the Refresh Cache button.

Advanced Data Source Definitions
--------------------------------

Saiku 3.x also accepts old style data source definitions with some minor changes because of the JCR repository. Once you have a schema uploaded you can then click the Add Data Source button and then Advanced. At this point you will be presented with a large text area field.

A Saiku 3 advanced data source looks like this:


`type=OLAP 
name=dsname 
driver=mondrian.olap4j.MondrianOlap4jDriver 
location=jdbc:mondrian:Jdbc=jdbc:jtds:sqlserver://localhost:1433/database;Catalog=mondrian:///datasources/myschema.xml;JdbcDrivers=net.sourceforge.jtds.jdbc.Driver; 
username=sa 
password=password`
 

As you can see, it looks very much like the Saiku 2.x data source except the catalog path has changed to a mondrian:// VFS pointer.

Securing data with roles
------------------------

Saiku can restrict access to data at row level by applying role based security to your data source. To do this you need to define an Advanced datasource and apply the following:

`security.enabled=true
security.type=lookup
security.mapping=ROLE_ADMIN=No HR Cube`

Line 1 is self explanatory

Line 2 is the type of mapping, you can use lookup which will attempt to map Spring roles to Mondrian roles defined in the security.mapping row, or you can use one2one which will attempt to lookup the users roles defined in Saiku within the cube definition and apply those as security. If you are using XMLA you can also use passthrough, which will pass the security on to the XMLA provider.

Line 3 is if you use lookup type, this allows you to map Saiku roles to cube roles, so in this example the users who have the role ROLE_ADMIN will be mapped to the No HR Cube role within the schema defintion which looks like:

.. code-block:: xml 

   <Role name='No HR Cube'>
       <SchemaGrant access='all'>
           <CubeGrant cube='HR' access='none'/>
       </SchemaGrant>
   </Role>

As you can see this role prevents access to the whole HR cube.

Additonal Connection Techniques
-------------------------------

.. toctree::
   :maxdepth: 2
   
   connecting_to_microsoft_analysis_server.rst
   connect_saiku_to_mssql_with_instance_names.rst
