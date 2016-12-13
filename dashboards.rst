Dashboards
==========

Dashboards are reports that show a collection of sub reports on a single screen. These reports usually have something in common and allow users to see the bigger picture.


Dashboard Design
----------------

You can create dashboards within Saiku using the Dashboard Designer that was released in Saiku Enterprise 3.2. To create a dashboard, the first thing that is required are some saved queries created using the regular Saiku query designer. Once you have your required queries you can then create dashboards by clicking on the Create Dashboard button on the splash screen.

You will be greeted with a prompt asking if you want to create a new dashboard or open an existing one. Click on New and another dialog will open asking how many widgets you would like to have by default in the new dashboard. This isn't a fixed amount you can add or remove widgets later. Once you have entered the number of widgets and click create the blank dashboard will be created.

As you can see in the above screenshot we have a basic dashboard with a 2x2 grid. To add new widgets you can click on the Create Widget icon in the toolbar, to remove widget click on the widgets cog icon and click Remove Widget.

Filtering Reports
-----------------

Of course just viewing the report might not provide the best insight into your data, and as such a filter might be needed to help you display different areas of your business. To add a filter, first you must add a parameter to your Saiku report. You can do this in the selections dialog and when you save this parameter it is then picked up and used by the dashboard designer.

Once you have added this report to your dashboard you can then see the Filter button enabled within the cog context menu. If you select that you can then choose which filter(if you have more than one) you would like to configure.

From the filter edit dialog you can give the filter a label so people understand the context. You also need to select the type, currently are Radio Button, Text Box, Dropdown and Dropdown Multiselect. If you have lots of values you might want Dropdown or Dropdown Multiselect if you just have a few the Radio Button dialog might be better, or if you want a user to type in a value just select Text Box.
In the Content section you can then define if you want a user generated list of values or lookup the values from the data warehouse.
If you click create list you are shown the following dialog

This lets you simply add elements to a list of values that the user can the choose from.
If you select lookup you are shown the following

From here you can select Current Level which will lookup the values available to you from the current level in the query, this is the normal selection, if you would like to override it you can also select the override radio button. From here you can then select the schema, cube, dimension, hierarchy and level that the selection list is create from.
Once you have the filter created press the save button and you are returned to the dashboard edit screen.

Viewing
-------

To view a dashboard, in edit mode you can press the Show Dashboards button. This will open the dashboard in View mode and allow you to click around with it.
If you aren't in Edit mode opening a new dashboard is simple. Click on the create dashboard icon on the splash screen

Then in the next dialog press the open button and find the saved dashboard.

When you select a dashboard you can see 4 buttons at the bottom of the open dialog. Edit puts you back into edit mode. View (New Tab) will open the dashboard within the Saiku UI like any other Saiku Report. View (New Window) will open the dashboard in a new browser tab or window which maximises screen space and gets rid of other UI elements.
To filter a dashboard click on the Filter icon in the top left and the filter bar will pop out allowing you to refine the data you are viewing.


Adding Content
--------------

Once you have a grid organised you can then add content to your dashboard. To do this find the report you want to add in the tree on the left hand navigation window.

Then drag the report from the left hand panel to a widget in the main dashboard and drop it. This will then give you a table view of the report you have just added to the dashboard.

As you can see this widget isn't big enough to display the whole table, so we can adjust the widget size by dragging the resize handle in the bottom right corner of the widget.

You can remove reports from widgets by clicking on the cog icon and clicking the Remove Report menu item.
Of course, we are dealing with graphical dashboards, so a table may not be the best way of displaying the information in the query. In this case we can switch from table mode to chart mode. To do this click on the cog icon and in the Render Type menu select Chart and then if you want to override the default chart type select the chart type you would like to use.
You should now see your report rendered as a chart.

Adding Embed Code
-----------------


To add a JavaScript code, add a report to the widget and open the context menu and click "Embed Code". This screen should appear for you:

In the text field "External Resources", you must add the URI of the external JavaScript libraries, as in this example:

In the field "JavaScript", you'll add your custom JS code, see example:

Then click the "Run" button and your code will run.


To retrieve the Saiku data, you must add the syntax correctly in your JavaScript code. See more information below.
Adding Embed Code (styling table)
It is also possible add some CSS styles in your table.


(info) SEE OTHER EXAMPLES HERE.
Example of data returned from Saiku
This is an example of Saiku data, you must understand how it is structured, for a better understanding with the syntax that will be used in the JavaScript code.
ROWS (11/21)
[0]  { "name": "Pearl Chardonnay Wine", "data": [210, 54.28, 136.5] },
[1]  { "name": "Pearl Imported Beer", "data": [175, 63.12, 159.25] },
[2]  { "name": "Walrus Light Beer", "data": [187, 191.12, 484.33] },
[3]  { "name": "Good White Zinfandel Wine", "data": [159, 247.85, 621.69] },
[4]  { "name": "Good Light Beer", "data": [115, 100.04, 250.7] },
[5]  { "name": "Pearl Light Wine", "data": [198, 46.07, 112.86] },
[6]  { "name": "Pearl Chardonnay", "data": [189, 131.7, 328.86] },
[7]  { "name": "Portsmouth Light Beer", "data": [175, 259.92, 663.25] },
[8]  { "name": "Portsmouth Imported Beer", "data": [187, 152.32, 403.92] },
[9]  { "name": "Good Imported Beer", "data": [154, 98.17, 249.48] },
[10] { "name": "Pearl Chablis Wine", "data": [209, 231.12, 560.12] }
...
COLS (4)
[0] "Product Name",
[1] "Unit Sales",
[2] "Store Cost",
[3] "Store Sales"
Syntax (to add in code JS)
Syntax
Description
{IDPANEL}
Returns the id of the respective widget, for example:
$('#{IDPANEL}').highcharts(...);
{ROWS_name_VALUES}
or
{ROWS_data_VALUES}
Returns an array of values of the object ROWS, for example:
{ROWS_name_VALUES}
>> ["Pearl Chardonnay Wine", "Pearl Imported Beer", "Walrus Light Beer", "Good White Zinfandel Wine"]
{ROWS_data_VALUES}
>> [[210, 54.28, 136.5], [175, 63.12, 159.25], [187, 191.12, 484.33], [159, 247.85, 621.69]]
{COLS_name_VALUES}
Returns an array of values of the object COLS, for example:
{COLS_name_VALUES}
>> ["Product Name", "Unit Sales", "Store Cost", "Store Sales"]
{ROWS_name_data_EMPTY_name_data}
Returns an object with names and data (or just names or data), for example:
{ROWS_name_data_EMPTY_name_data}
>>
{ "name": "Pearl Chardonnay Wine", "data": [210, 54.28, 136.5] },
{ "name": "Pearl Imported Beer", "data": [175, 63.12, 159.25] },
{ "name": "Walrus Light Beer", "data": [187, 191.12, 484.33] },
{ "name": "Good White Zinfandel Wine", "data": [159, 247.85, 621.69] }

{ROWS_name_EMPTY_name}
>>
{ "name": "Pearl Chardonnay Wine" },
{ "name": "Pearl Imported Beer" },
{ "name": "Walrus Light Beer" },
{ "name": "Good White Zinfandel Wine" }

{ROWS_data_EMPTY_data}
>>
{ "data": [210, 54.28, 136.5] },
{ "data": [175, 63.12, 159.25] },
{ "data": [187, 191.12, 484.33] },
{ "data": [159, 247.85, 621.69] }

{ROWS_product_value_EMPTY_name_data}
>>
{ "name": "Pearl Chardonnay Wine", "data": [210, 54.28, 136.5] },
{ "name": "Pearl Imported Beer", "data": [175, 63.12, 159.25] },
{ "name": "Walrus Light Beer", "data": [187, 191.12, 484.33] },
{ "name": "Good White Zinfandel Wine", "data": [159, 247.85, 621.69] }

The name EMPTY is very important, because it is an escape word.
