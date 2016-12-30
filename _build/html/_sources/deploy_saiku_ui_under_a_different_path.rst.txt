Deploy Saiku UI Under A Different Path
======================================

By default Saiku will provide the UI under localhost:8080 if you want to serve it under a different path you have to make a few changes.
Step-by-step guide
Install Saiku as normal
Move tomcat/webapps/ROOT to your new folder, for example tomcat/webapps/saikuui
Update the platformbean in tomcat/webapps/saiku/WEB-INF/saiku-beans.xml to point to your new path, ../webapps/ROOT/js/saiku/plugins/ ----> ../webapps/saikuui/js/saiku/plugins/
Refresh the browser or restart your server.
 
