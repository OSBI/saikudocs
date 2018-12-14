License Management
==================

Enterprise Edition Only

Uploading a new license
-----------------------
If you trial has ended and you want to replace the license with a full license or if your full license need changing, then visit, http://servername:8080/upload.html from this screen you can add a new license and click the upload button. Assuming everything goes okay, then you will be notified that the upload was successful. Log out and login again for the new license to take effect.

Installing your EE license in the Pentaho BI server
---------------------------------------------------
If you purchase a Saiku EE license and run Saiku within a Pentaho BI Server, here's how you install the license

Once your license has been issued, copy it to pentaho-solutions/system/saiku. If this server is remote you could use SCP via Linux or Putty on Windows or a Dropbox public folder to copy the file to the remote server. You should override an existing file called license.lic

Saiku normally uses named users, to maintain the list within the BI Server you need to edit the users.txt file located within the pentaho-solutions/system/saiku file. Make sure all valid logins are entered into this file 1 username per line, for example:

    admin
    
    joe
    
    sue

You license will be limited to a certain number of users, as such the plugin will read the first x number of lines to find valid users. For example if you buy 5 users, the first 5 user names within that file will be valid and everyone else contained with the file will be excluded.


Maintaining the Named User List
-------------------------------
If you have a user limit on your server license then you need to maintain the named user list. This list is a list of usernames allowed to login to Saiku, this list should be less than or equal to the number of licenses purchased. If you add more users than purchased seats then those users will not be able to login to Saiku.
To add users navigate to the Admin Console and then Users List, by default this list is prepopulated with the Admin user, and you need to keep an Administrative user on the list otherwise you won't be able to access the admin panel.
To add users simply add their name to the username box and click add user.

If your administrative user is not Admin you also need to change the main username which will allow you access to the server if you don't have the user in the named user list. To adjust this you need to look in tomcat/webapps/saiku/WEB-INF/saiku-beans.xml and find the licenseUtilsBean.
To override the default user change the adminuser property to match your username.

The list of named users is independent of any users you have in the user management section as different authentication mechanisms may not use the User Management section to create users.

The list will allow you to add more users than the license permits, but they are evaluated in list order, so for example, if you have a 10 user license and add 15 users, if the person trying to authenticate comes in the last 5, they will not be allowed to login to Saiku.

Saiku User Quota
----------------

Included in the release of Saiku 3.6 was the new User Quota system. This allows Saiku Analytics customers with full licenses to allow unlicensed users to login up to 30 times. This allows users without a license to get a taste of Saiku and at that time you can then make a decision about buying the user a license.
Once the user has used has used up all of their available logins they will be locked out and you are then required to buy a license for continued use.
Users are informed of their quota usage in the query workspace, and administrators can find out about the quota usage in the About box which can be accessed from the main toolbar.

