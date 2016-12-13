By default the log files are stored in saiku-server/tomcat/logs.
In this directory you will find, catalina.out and saiku.log both of which contain useful information when debugging or monitoring the Saiku server.
Administrators can also access these log files by browsing:
http://localhost:8080/saiku/rest/saiku/admin/log/{logfilename}
So for example to view the current saiku.log open a new tab and enter:
http://localhost:8080/saiku/rest/saiku/admin/log/saiku.log
