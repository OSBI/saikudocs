Saiku Enterprise Manual Deployment
==================================

New in Saiku EE 3.7 we now have a build for manual deploymet of Saiku for those of you who don't want to use the supplied Tomcat distribution.
To install this you can donwload the package from here.
To install it follow these instructions:
Unzip archive
Deploy ROOT.war and saiku.war to your server and unzip/extract them.
Copy data.zip and repository.zip to another location which your server can access and unzip into separate folders.
Set the correct permissions on the folders so that your server can read and write to these files and folders.
Update the configs you need to update web.xml, saiku-beans.xml and applicationContext-spring-security-jdbc by default, these are located in the saiku.war webapp in WEB-INF here is an example:
sed -i.bak -e 's/${foodmart_url}/jdbc:h2:\/tmp\/saiku\/data\/foodmart;MODE=MySQL/g' /var/lib/tomcat7/webapps/saiku/WEB-INF/web.xml
sed -i.bak -e 's/${earthquake_url}/jdbc:h2:\/tmp\/saiku\/data\/earthquakes;MODE=MySQL/g' /var/lib/tomcat7/webapps/saiku/WEB-INF/web.xml
sed -i.bak -e 's/..\/..\/data/\/tmp\/saiku\/data\//g' /var/lib/tomcat7/webapps/saiku/WEB-INF/web.xml
sed -i.bak -e 's/..\/..\/repository\//\/tmp\/saiku\/repository\//g' /var/lib/tomcat7/webapps/saiku/WEB-INF/web.xml
sed -i.bak -e 's/..\/..\/repository\//\/tmp\/saiku\/repository\//g' /var/lib/tomcat7/webapps/saiku/WEB-INF/saiku-beans.xml
sed -i.bak -e 's/..\/..\/data/\/tmp\/saiku\/data\//g' /var/lib/tomcat7/webapps/saiku/WEB-INF/saiku-beans.xml
sed -i.bak -e 's/..\/webapps/\/var\/lib\/tomcat7\/webapps\//g' /var/lib/tomcat7/webapps/saiku/WEB-INF/saiku-beans.xml
sed -i.bak -e 's/..\/..\/data/\/tmp\/saiku\/data/g' /var/lib/tomcat7/webapps/saiku/WEB-INF/applicationContext-spring-security-jdbc.xml
Restart your server, and visit the home page: http://localhost:8080 you should be presented with a login screen and be able to login with the default admin/admin credentials.
