Saiku Settings
==============


Saiku has a number of UI settings that can be adjusted by editing
saiku-server/tomcat/webapps/ROOT/js/saiku/Settings.js
Here are some of the most common:
Property
Default
Comments
VERSION Current version for various dialogs. If you want to reskin Saiku you might want to change this.
BASE_URLwindow.location.originThe base url of the Saiku server, usually detected automatically but can be overridden.
TOMCAT_WEBAPP/saikuIf you want to point to an alternative Saiku Server location, you can adjust this url.
REST_MOUNT_POINT/rest/saiku/Rest mount point, only needs changing if you make changes to the webapp.
DIMENSION_PREFETCHtrue
DIMENSION_SHOW_ALLtrue
DIMENSION_SHOW_REDUCEDfalse
TABLE_LAZYtrueEnable or Disable table lazy loading, improves performance on large tables.
TABLE_LAZY_SIZE1000Number of rows to be rendered initially.
TABLE_LAZY_LOAD_ITEMS20Batch size to load new items.
TABLE_LAZY_LOAD_TIME20Load throttling for lazy loading.
MEMBERS_FROM_RESULTtrueLimit the members displayed in the filter dialog to those returned by the previous query. (Can be changed in the query)
MEMBERS_LIMIT3000Max members to import into the filter dialog.
MEMBERS_LIMIT75Search result limit.
ALLOW_PARAMETERStrueAllow query parametrization.
DEFAULT_VIEW_STATEviewDefault to View or Edit mode.
EVALUATION_PANEL_LOGINtrueShow or hide the evaluation credentials notice on the login page.
