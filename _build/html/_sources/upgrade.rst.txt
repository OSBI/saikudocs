Upgrade
=======

iUpgrading Saiku is very simple.
First stop the server by running the stop-saiku script so that the databases and repository are shut down cleanly.
Next install the new Saiku server in a different location.
Finally replace the data and repository directories in the new installation with the folders from your old installation, this will copy over all your existing users, reports, schema and datasources.
Restart Saiku.
If you customised any of the configuration files then these will need upgrading as well.
