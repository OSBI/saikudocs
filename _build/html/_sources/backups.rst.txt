Backups and Restoration
=======================

It is recommended you backup the Jackrabbit repository from time to time in case of corruption.

To do this you need to navigate to the Backup/Restore menu in the Administration console. You can then click the backup button to get a zipped up export of the entire JCR repository.

To restore the repository you can unzip the latest backup you made and then upload the XML file to the server which will restore the repository. The restoration attempts to sync with whatever is already there so if you want to start afresh, you are advised to remove what it already in the repository using the Webdav access feature.
