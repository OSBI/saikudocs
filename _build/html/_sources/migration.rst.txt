Migration From Saiku 2.x
========================

Saiku 3 has a lot of new features in the backend our biggest change is adding a JCR repository. This change allows us to add extra functionality to the server and removes the need for having a bunch of files residing directly within the webapp, but it does add an extra layer of complexity when it comes to migrating and managing the new repository.

Importing Legacy Schema and Data Sources
----------------------------------------

As a one off import you can import legacy data sources and schema by placing them in the .... directory. This will cause the Saiku Server to attempt to import them into the JCR repository when the server starts and make them available to report off. Due to the complexity of these things, some changes will have to be made to the datasource definitions once they are imported because the catalogue uri is now Catalog=mondrian:///datasources/myschemapath.xml , the importer will try and change this setting during the import but due the various ways of configuring the Saiku server your mileage may vary.

Importing Legacy Reports
------------------------
We also realise that people who have been using the Saiku Server 2.x will have a number of legacy reports that they may like to make available in the new server. To manage this we have created a legacy reports import facility. If you navigate to the Backup/Restore menu on the Administration console you will see the Restore Legacy Reports option. To use this you need to zip up your old reports in a zip file, don't organise them into different sub directories as the server doesn't know how to manage them, just put them all in the root directory. Then upload the zip file to the server. The server will then extract these reports to /etc/legacyreports where you can then move them to various other directories.

Because there are various differences with both Saiku 3 and Mondrian 4 in the way they process queries although we try our best to translate queries from the Saiku 2.x format into Saiku 3 queries, you may find that some do not work and will need manually recreating. Luckily the repository and file formats for Saiku 3 won't be changing so this is a one time upgrade.
 
