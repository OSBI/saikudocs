License Management
==================



Enterprise Edition Only
Uploading a new license
If you trial has ended and you want to replace the license with a full license or if your full license need changing, then visit, http://servername:8080/upload.html from this screen you can add a new license and click the upload button. Assuming everything goes okay, then you will be notified that the upload was successful. Log out and login again for the new license to take effect.


Maintaining the Named User List
If you have a user limit on your server license then you need to maintain the named user list. This list is a list of usernames allowed to login to Saiku, this list should be less than or equal to the number of licenses purchased. If you add more users than purchased seats then those users will not be able to login to Saiku.
To add users navigate to the Admin Console and then Users List, by default this list is prepopulated with the Admin user, and you need to keep an Administrative user on the list otherwise you won't be able to access the admin panel.
To add users simply add their name to the username box and click add user.

If your administrative user is not Admin you also need to change the main username which will allow you access to the server if you don't have the user in the named user list. To adjust this you need to look in tomcat/webapps/saiku/WEB-INF/saiku-beans.xml and find the licenseUtilsBean.
To override the default user change the adminuser property to match your username.
