Saiku offers three different authentication mechanisms:

* in memory authentication
* JDBC authentication
* LDAP authentication

By default in memory authentication mechanism is used.

## In Memory Authentication

In memory authentication loads up a list of users and their roles into memory when the server is started and then users are authenticated against it.

The users are stored in `saiku-server/tomcat/webapps/saiku/WEB-INF/users.properties` in the following format (one user per line):


```
`username=password,role[,another_role]
`
```
You can edit this file to remove the default users and to create new users with passwords and assigned role(s).

Once you have added new users, save the file and restart the Saiku server to see the new users take effect.

## JDBC & LDAP Authentication

The Saiku backend is controlled by the Spring framework, and as such we can use the authentication mechanisms that Spring supports. We have shippded sample configurations for both JDBC and LDAP support. To get more information regarding the Spring security mechanisms check out their [website](http://projects.spring.io/spring-security/), and specifically [here](http://docs.spring.io/spring-security/site/docs/3.2.0.RELEASE/reference/htmlsingle/#ldap) for LDAP information.

### JDBC Authentication

In order to use JDBC authentication follow these steps:

Edit file `saiku-server/tomcat/webapps/saiku/WEB-INF/applicationContext-spring-security.xml` and change import tag to `<import resource="applicationContext-spring-security-jdbc.xml"/>`Edit authentication configuration in file `saiku-server/tomcat/webapps/saiku/WEB-INF/applicationContext-spring-security-jdbc.xml`Inside the JDBC configuration file you will see pointers to driverClassName, url, username and password. Alter these to match your database connection details. Also if you need to change the queries to reference different columns and/or table names then do so in the queries above.

### LDAP Authentication

In order to use LDAP authentication follow these steps:

Edit file `saiku-server/tomcat/webapps/saiku/WEB-INF/applicationContext-spring-security.xml` and change import tag to `<import resource="applicationContext-spring-security-ldap.xml"/>`Edit authentication configuration in file `saiku-server/tomcat/webapps/saiku/WEB-INF/applicationContext-security-ldap.properties`Here you will find most of the variables that you will need to configure, so adjust these to match your system. The LDAP configuration is generally the more tricky of the two, largely because LDAP varies wildly from installation to installation. Once you've done this you can restart the server and see whats missing, invariably this will take a few attempts to get accurate.

