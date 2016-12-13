Webdav Access
=============


As Saiku 3 Standalone has migrated to a Jackrabbit JCR repository, we now allow access to this repository via Webdav.

Webdav drives look like network drives to operating systems and so you can "mount" Saiku's repository in My Computer on Windows or as a drive in Finder on Mac OS.

The default path to the Webdav server is dav://<hostname>:<port>/saiku/repository/default/homes

and once you have mounted it, you can navigate the files and directories using My Computer you can also access the repository via a browser on the same url.

Webdav Clients include Cadaver(Linux), Cyberduck(Windows/Mac) and many others.

The default credentials are admin/sa!kuanalyt!cs.

To change the password, you need to follow the instructions in tomcat/webapps/saiku/WEB-INF/saiku-beans.xml
