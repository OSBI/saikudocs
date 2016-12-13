Adding A New Data Source
========================

Whilst we haven't yet had the time or resource to create a lovely graphical admin console for you system administrators we have tried to make it simple for you to add data sources to the Saiku platform.

The Saiku server is shipped with Foodmart by default. So I shall show you how to import the steel-wheels schema and configure it to use a MySQL database connection.

Firstly navigate to saiku-server/tomcat/webapps/saiku/WEB-INF/classes/saiku-datasources/ and copy the file named foodmart and rename it steelwheels.

Next edit this new steelwheels file and configure it in a similar way to the following:

.. code-block:: text

    type=OLAP
    name=steelwheels
    driver=mondrian.olap4j.MondrianOlap4jDriver
    location=jdbc:mondrian:Jdbc=jdbc:mysql://localhost/sampledata;Catalog=../webapps/saiku/steelwheels/steelwheels.mondrian.xml;JdbcDrivers=com.mysql.jdbc.Driver;
    username=dbuser
    password=password`

So what we have done here is told Saiku the new name of the connection is steelwheels. We then told Saiku the location of the database and mondrian schema, for which I have created a steelwheels folder under the webapp/ directory. We finally set the database username and password.

Once you have installed your schema definition, restart your server.

It doesn't get much simpler than that. Adding a new JDBC Driver

Obviously not everyone uses Hypersonic or MySQL to connect to their data warehouses. To use your specific database, please add the JDBC connector jar file to saiku-server/tomcat/webapps/saiku/WEB-INF/lib/ and then make the appropriate changes to the jdbc portion of the location string in the connection file.

Example Configurations
----------------------

PostgreSQL
~~~~~~~~~~

.. code-block:: text

    type=OLAP
    name=db_name
    driver=mondrian.olap4j.MondrianOlap4jDriver
    location=jdbc:mondrian:Jdbc=jdbc:postgresql://database_host:port/db_name;Catalog=res:data_directory/schema_file.mondrian.xml;JdbcDrivers=org.postgresql.Driver;
    username=db_user_name
    password=db_password

MS SQLServer (using JTDS)
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: text

    type=OLAP
    name =theSqlserverOne
    driver=mondrian.olap4j.MondrianOlap4jDriver
    location=jdbc:mondrian:Jdbc=jdbc:jtds:sqlserver://database_host:1433/db_name;Catalog=res:data_directory/schema_file.mondrian.xml;JdbcDrivers=net.sourceforge.jtds.jdbc.Driver
    username=db_user_name
    password=db_password

Configuring a JNDI OLAP connection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

First you need to configure the JNDI connection in Tomcat. One way to do that is to create a context.xml file in tomcat/webapps/saiku/META-INF/ and add a Resource element to it, for example:

**IMPORTANT** When tomcat is restarted to pick up this new context.xml file it will copy it to tomcat/conf/Catalina/localhost/saiku.xml. Further modifications to the JNDI resource must be made here since this file will take precedence over the one in tomcat/webapps/saiku/META-INF/


.. code-block:: xml 

	<Context>
	<Resource name="jdbc/MyDS" auth="Container" type="javax.sql.DataSource"
              username="<username>" password="<password>"
	      url="jdbc:postgresql://database_host:5432/db_name"
	      driverClassName="org.postgresql.Driver"
	      initialSize="5" maxWait="5000"
	      maxActive="120" maxIdle="5"
	      validationQuery="select 1"
	      poolPreparedStatements="true"/>
	</Context>

Next you need to expose this JNDI resource to the Saiku application by adding the following to tomcat/webapps/saiku/WEB-INF/web.xml

.. code-block:: xml 

  <resource-ref>
    <description>My Datasource</description>
    <res-ref-name>jdbc/MyDS</res-ref-name>
    <res-type>javax.sql.DataSource</res-type>
    <res-auth>Container</res-auth>
  </resource-ref>

Finally, setup your OLAP connection that Saiku can use for analysis.

.. code-block:: text

    type=OLAP
    name=usage
    driver=mondrian.olap4j.MondrianOlap4jDriver
    location=jdbc:mondrian:Datasource=java:/comp/env/jdbc/MyDS;Catalog=res:data_directory/schema_file.mondrian.xml`
 

