## New Query

To create a new query click on the New Query button, or click the little + icon beyond the far right tab.

![data shot](http://docs.analytical-labs.com/img/newquery.png)

## Selecting a cube

To create a query you need to select a cube which defines the data structure you are going to query. You'll find the cube list on the left hand side, select the cube you require.

![data shot](http://docs.analytical-labs.com/img/cubelist.png)

## Adding dimensions

Once you have selected the cube you require you will be given a dimension and measure listing, you can drag these from the left hand panel onto the Rows, Columns and Filter axis drop areas. Measures need to be kept together but dimensions can be place where needed.

![data shot](http://docs.analytical-labs.com/img/dimensionlist.png)

## Executing the query

By default Saiku is configured to automatically execute a query when objects have been placed on its axis. Saiku requires at least one Dimension or Measure on both Rows and Columns. Once this is in place the query will execute and when it has finished executing the result will be displayed on the screen. If you switch off Automatic Execution you can then adjust the query and press the execute button once you are happy with the configuration.

![data shot](http://docs.analytical-labs.com/img/executequery.png)

## Toggle fields

Once you have designed your query, if you require more screen space, click the toggle fields button and the Rows, Columns and Filter axis drop zones will be removed.

![data shot](http://docs.analytical-labs.com/img/togglefields.png)

## Toggle Sidebar

Similarly if you want to hide the left hand sidebar then clikc the Toggle Sidebar button and it will be hidden.

![data shot](http://docs.analytical-labs.com/img/togglesidebar.png)

## Hide Parents

Hide parents will remove the total rows and columns from the parent memebers in the result set.

![data shot](http://docs.analytical-labs.com/img/showparents.png)

## Non Empty

MDX queries are created by crosstabulating data, therefore they often contain an awful lot of empty cells. The Hide Empty button is therefore enabled by default and it hides the empty cells, if you toggle this button you will likely then see a much larger resultset containing many empty cells.

![data shot](http://docs.analytical-labs.com/img/nonempty.png)

## Swap Axis

OLAP has always had the idea of pivoting close to its heart, and here you can pivot the entire resultset 90 degrees. By clicking the Swap Axis button you will then, as suggested, move all the items on the Rows to the Columns axis and visa versa.

![data shot](http://docs.analytical-labs.com/img/swapaxis.png)

## Show MDX

All our queries are written in the MDX query language, you just don't need to understand it. But if you require the query being used, then if you click the Show MDX button, a window will be displayed with the MDX being used to query the database.

![data shot](http://docs.analytical-labs.com/img/showmdx.png)

## Show Explain Plan

Show plan is a relatively new feature within Mondrian, in a similar was that many databases have a Explain Query function, Mondrian has an explain plan function to display how the MDX query is constructed. This can help with query optimisation and streamlining.

![data shot](http://docs.analytical-labs.com/img/explainplan.png)

## Query Scenario

## Drill Through On Cell

Drill through allows you to see the underlying data in the query. Once you have run a query, select this option and then click on the cell you want to drill through on. You can then select the dimensions and measures you want in the drill through query and the row limit then hit okay. You'll then be presented with a popup window containing the drill through data.

![data shot](http://docs.analytical-labs.com/img/drillthru.png)

## Export drill through to CSV

Drill through to CSV exports the drill through data to a CSV file for further analysis.

![data shot](http://docs.analytical-labs.com/img/drillthrucsv.png)

## Export to XLS

Export to XLS will export the current query result set to an Excel file.

![data shot](http://docs.analytical-labs.com/img/exportxls.png)

## Export to CSV

Export to CSV will export the current query result set to a CSV file.

![data shot](http://docs.analytical-labs.com/img/exportcsv.png)

## Export to PDF

Export to PDF will export the current query result set to a PDF file.

![data shot](http://docs.analytical-labs.com/img/exportpdf.png)

## Switch to MDX Mode

Once you have designed you query you can then switch to MDX query mode by clicking this button. MDX query mode allows you to customise the query by altering the MDX query itself, but this is a one way operation and once you go to MDX mode you cannot get back to the drag and drop mode with any changes you have made.

![data shot](http://docs.analytical-labs.com/img/switchtomdxmode.png)

## Tags

## Sorting

To sort by a level click on the little up or down arrows on the level box, this will rerun the query with the selected sort.

![data shot](http://docs.analytical-labs.com/img/sort.png)

## Level Filtering

To filter a level, click on the magnifying glass icon on the level label. A dialog will pop up with the available members that you can select. Move the members you want included within the filter to the Used Members box and press Ok.

![data shot](http://docs.analytical-labs.com/img/magnify.png)

# Axis Filtering

The axis drop zone each have their own context menu on the label at the left. Within this context menu you will find submenus for filtering, limiting and sorting.

## Axis Filter

The axis filter allows you to add a custom MDX snippet to it. For example if I wanted to show all records where the Beverages amount was greater than 0 then I would add: [Product Department].Beverages > 0 to the custom filter box and press Ok.

## Limiting

You can also limit the members returned in a query, this is useful if you wanted to look at just the top or bottom products in a query. If I wanted to see the top selling products I would select the dropdown and then limit and then Top 10. Similarly you can select Top 10, Bottom 10, Top 10 by; where you can select the dimension you want to use in the Top count, Bottom 10 by; where you can select the dimension you want to use in the Bottom count and Custom Limit where you can customise the limiting further by different filters, quantities and sorting.

## Sorting

Sorting allows you to sort the resultset, if you select the dropdown and go to sort you will see Ascending and Descending, this sorts as expected. Ascending and Descending Breaking Heirarchy allows you to sort with multiple dimensions on the axis and not follow their heirarchical order. Again there is a custom filter dialog for more advanced filtering usage.

