Installing your EE license in the Pentaho BI Server
===================================================

If you purchase a Saiku EE license and run Saiku within a Pentaho BI Server, here's how you install the license
Step-by-step guide
Once your license has been issued, copy it to pentaho-solutions/system/saiku. If this server is remote you could use SCP via Linux or Putty on Windows or a Dropbox public folder to copy the file to the remote server. You should override an existing file called license.lic
Saiku normally uses named users, to maintain the list within the BI Server you need to edit the users.txt file located within the pentaho-solutions/system/saiku file. Make sure all valid logins are entered into this file 1 username per line, for example:
admin
joe
sue

You license will be limited to a certain number of users, as such the plugin will read the first x number of lines to find valid users. For example if you buy 5 users, the first 5 user names within that file will be valid and everyone else contained with the file will be excluded.

Saiku EE only
