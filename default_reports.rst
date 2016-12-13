Default Reports
===============

If your users have regular reports you would like them to see when logging into Saiku you can now set Default Reports. The report definition can be set by user, role or globally.
Inside tomcat/webapps/ROOT/js/saiku/Settings.js you will find this:
DEFAULT_REPORT_SHOW: true, // true/false
 DEFAULT_REPORTS: {
 'admin': [
 {
 path: '/homes/home:admin/test.saiku', // example: /homes/home:admin/chart.saiku
 visible: true // true/false
 }
 ],
 '_': [
 {
 path: 'ADD_PATH2',
 visible: false
 }
 ],
 'ROLE_ADMIN': [
 {
 path: 'ADD_PATH3',
 visible: false
 }
 ]
 },
To edit the default reports, you just need to customise this to your own requirements. The first entry is for the user admin and they have 1 report visible when they login. The second entry is _ this is a global indicator. When anyone logs in they will be shown these reports. Finally, you'll see an entry for ROLE_ADMIN, this is role based report loading.

To find the path to the report you would like your users to see, open the repository browser and copy the path metadata like this:
