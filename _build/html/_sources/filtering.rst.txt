Filtering
=========

Overview
--------

Filtering Overview


There are a number of ways of refining the data you see from your query these include filtering the dimension members that appear in the resultset or using the Filter axis.
A Saiku query has 4 drop zones to help you define your query, Measures, Columns, Rows and Filter. The filter axis allows you to filter what is visible in the result but using dimensions that aren't displayed on the table, for example, you may want to show store sales by region on a table, but only for 2014, and as such you would add the time dimension to the Filter axis. But, for example, if you wanted to show Q1 sales year on year, you would put the Year and Quarter levels on to the rows or columns axis, this means they would then show up in the table.

To select particular rows of data(members) then you need to click on the label in the dropbox to get the Filter popup dialog. Once you see this you can then select the members you want to see and move them to the selected side on the right and click the Ok button. When you press Ok the dialog will close and the query will be executed with the new filters in place.


Advanced
--------

Include / Exclude
Saiku now supports include & exclude within the filter dialog, which makes the filtering far more flexible on moving data sets. For example, you might just want to exclude 2 members, rather than include a fixed list which might need updating when your dimensions are updated.
To exclude just add the members you want to exclude to the filter area and then instead of selecting the Include radio button, select the exclude button instead.

Searching and Pre-Filtering on Server
If you have large dimensions, Saiku pre filters them on the server to improve user interface performance. This list on the left may be truncated because it would be too long and cause your browser to hang. To filter you can use the Search box at the top of the filter dialog.

You know if your filter dialog is being filtered when the Items: count equals the Display Limit count. The limit is adjustable by the administrator by looking in the Settings file
