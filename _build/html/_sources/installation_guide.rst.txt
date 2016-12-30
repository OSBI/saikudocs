Installation Guide
==================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   deploy_saiku_ui_under_a_different_path.rst
   saiku_enterprise_manual_deployment.rst
   upgrade.rst


Saiku Enterprise Edition
------------------------

Requirements
Saiku has very few requirements, it will run in less than 1GB of RAM, and will run on any computer running Java.
Currently the only prerequisite is JDK7.
Downloading Saiku Enterprise Edition
To install Saiku Enterprise Edition the first job is to download the installer and create a license from our licensing portal.
You license is tied to your server hostname and as such you need to make sure you provide the correct hostname, this is not the url you connect to your server with but the dns hostname.
To find your hostname on Linux/Mac open a shell and type
hostname
On windows you need to run
ipconfig /all
Running the installer
The installer is an executable jar file, on most operating systems you should be able to double click and run the file, this will pop up the first page of the installer. If you are wanting to install Saiku Enterprise on a remote server, or a computer without a graphics card, you can run
java -jar ./saikuinstaller-x.y.z.jar -console
and you will be given a text based installer.
If you are installing in console mode when you get to the screen asking for the license, pass it the path to the license file. For example if you put the license in /tmp the path would be /tmp/license.lic
Once the installer is complete it will then start Saiku server and you should be able to find a login screen at http://servername:8080/.
To login to the standard install you will be able to login with admin/admin.
If for some reason you do not see a login screen, look in
installation directory/server/tomcat/logs/catalina.out
This will contain any errors that occurred during the server startup.

Saiku Community Edition
-----------------------

This guide should help you when installing Saiku 3.0 for the first time.
Installation:
Make sure you have a version of JDK 7 installed.
Check that the JAVA_HOME environment variable is set.
Download the zip or gzip file for Saiku
Unzip the archive to your desired location.
Running Saiku 3.0 for the first time:
Open a command prompt or terminal.
Navigate to where the installer copied the files
Execute either start-saiku.sh or start-saiku.bat ( depending or your operating system ).
Open a browser and navigate to the URL: http://<server-name-or-ip>:8080/
You should be greeted by the Saiku login page.
To login to Saiku you will need a free license. You can get this http://licensing.meteorite.bi
Things to check if you're having problems:
Are you using JDK7?
Is the JAVA_HOME variable set in the OS?
Is port 8080 blocked in the firewall?


Other Methods
-------------

Docker Image
We supply Saiku Community Edition as a docker image for easy deployment. To deploy Saiku run:
docker pull buggtb/saikuce
for Saiku Community Edition and it will pull down the latest snapshot build.
Or for enterprise run:
docker pull buggtb/saikueeofficial
and it will install the latest stable release.
Saiku will run a full server on port 8080 on the running docker container.
Juju Charm
Meteorite BI have teamed up with Canonical to get Saiku Analytics into the Juju Charm Store, whilst we work on finishing up the acceptance you can still test the Saiku CE Juju charm by running:
juju deploy tomcat
juju deploy cs:~f-tom-n/trusty/saikuanalytics
juju add-relation saikuanalytics tomcat
juju expose tomcat
Again, this will run Saiku on Tomcat, the default port is 8080.

Pentaho Plugin
--------------

To install Saiku EE plugin, do this via the Pentaho Marketplace. This one click install will install the EE plugin and set it up ready for use after a server restart.
The Pentaho plugin has 2 items that need configuring.
To install the license you can place it in ~/.pentaho or pentaho-solutions/system/saiku/ named license.lic. If you install it in ~/.pentaho of course it will survive re-installation which can make administration easier.
The other item that needs configuring is the user file. For named user licenses you need to configure the users allowed to login with your license. So if you purchased a single user, you can enter a single username, if you purchased 100 users, you can enter 100 user names etc. This file can be located in the same place as the license and is called users.txt. In this file enter a username per row, so for the pentaho default users you'd have:
joe
suzy
pat
tiffany

Make sure the file ends with a blank line. Once these are configured, you can log out and back into the Pentaho BI server and the new license and users configuration will be picked up by the Saiku plugin.

