Administrators Console
======================

Saiku Administration Console was first released with Saiku 3.0.0 because we moved from flat files to a JCR based repository. Currently the Administration Console is used to administering Users, Data Sources, Schema and Licenses.
Users with the administrator role(by default ROLE_ADMIN) have access to the Admin console by clicking the A icon in the main toolbar.

Once you have opened the Admin Console tab you will see a tree menu on the left side of the window. Contained in this menu is the user management section, data source management, maintenance area and license information.

User Management
---------------

.. toctree::
   :maxdepth: 2
  
   user_management.rst

By default Saiku user management is performed using the user management screen within the Saiku Admin Console.

To add a user you click on the Add User item.

You will then be presented with the user creation area.

+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Username      |  The username that the user will login with                                                                                                                |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Email Address |  The users email address. Currently this is unused, but we have report emailing and scheduled delivery on the roadmap that would make use of this feature. |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Password      |  The users password                                                                                                                                        |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Roles         |  Roles assigned to that user for access permissions and data source security. These are free form and can be anything you like, but it is recommended you  |
|               |  follow a naming policy. For example, our default roles are ROLE_ADMIN and ROLE_USER.                                                                      |
+---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+


Once you have filled in the users profile you can then press save and the user will be added to Saiku.

To edit a user, click on that user in the user list and make changes to their profile

Data Source Management
----------------------

.. toctree::
   :maxdepth: 2
   
   data_source_management.rst

Saiku data sources come in two parts, the schema and the database connection.

The first job is to upload a valid Mondrian schema, in Saiku 3 we use Mondrian 4 which has an alternative schema design to Mondrian 3. Mondrian 4 is supposed to be able to read Mondrian 3 schema, but your mileage will vary, it is recommended you write your schema in Mondrian 4 syntax, or use the Saiku Schema Designer.

To upload a schema to Saiku, in the Admin Console, there is an Add Schema item in the left tree. Click this row and then choose your file to upload and give it a name.

When you press upload, the schema will be uploaded to the server and saved in its repository.

If you need to change it or remove it you can click on its name in the Schema subsection and press remove.

Next you need to add a data source, to do this click the Add Data Source item and you will then be presented with the data source configuration dialog.

In this section you can add a human readable name, select between Mondrian and XMLA connection types, and more.

+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Name             | A human readable name for the data source.                                                                                                                 |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Connection Type  | Mondrian, XMLA or Mongo(EE only), change to XMLA if you are wanting to connect to an XMLA data source like Microsoft Analysis Services or Oracle Essbase.  |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| URL              | In Mondrian mode, this is the JDBC url of your database, for example, jdbc:mysql://localhost/foodmart.                                                     |
|                  | In XMLA mode the URL is the http:// url to your XMLA data source.                                                                                          |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Schema           | Not available in XMLA mode. This is the schema you have designed and uploaded to Saiku.                                                                    |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Jdbc Driver      | The class of the JDBC driver, for example com.mysql.jdbc.Driver.                                                                                           |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Username         | Your data source username.                                                                                                                                 |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Password         | Your data source password.                                                                                                                                 |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Advanced         | This opens a freeform text area for more advanced connection types, for example if you need to use a digital schema processor.                             |
+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

Maintenance
-----------

The maintenance area allows you to backup and restore various aspects of the Saiku server.

To backup your repository press the Backup Now! button. This will download a zip file to your server containing the contents of your repository.

To restore the repository, select the backup file and press the Restore Repository button.

If you are migrating from Saiku 2.x you can also use the restore legacy reports button, to upload a zip file containing legacy reports which will be deployed to the server, due to changes in file structure and data sources, this is an experimental feature.

You might find it more flexible and easier to manage in a production environment to mount Saiku as a Webdav drive and backup/restore and maintain files using a file system instead of the administration console. Find out more here.

License Information
-------------------

.. toctree::
   :maxdepth: 2

   license_management.rst
   
Saiku uses licenses to manage users and authentication. In the license area you can see the license type you have and its expiry date.

If you are an EE user who doesn't have a RAM based or unlimited user license, you also need to maintain the users list. This list is the valid users allowed to login to your platform. For example, if you purchase a 20 user Saiku license, the first 20 users in this list will be allowed to login to Saiku as stipulated in your license details.

Logging
=======

.. toctree::
   :maxdepth: 2

   log_files.rst

