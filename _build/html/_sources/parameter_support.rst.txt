Parameter Support
=================

For more advanced use cases, Saiku now supports parameters to inject variables into the query. If you embed a Saiku report into a 3rd party platform or want to provide an alternative filter mechanism, parameters allow you to define where users can make changes to filters on the fly without having to open the filter dialog box.
Assign A Parameter Name
Firstly you need to assign a parameter name. To do this put your level on an axis and click on it to popup the filter selection dialog. In here you will see the Parameter Name text box to add your parameter name, give it a name and press ok.

Populate the parameter value
To use the parameter via the Saiku UI you can then enter the parameter value in the textbox at the top of the query:

Enter the value you want and press the query run button and your query will then be executed with the parameter in place:

.. code-block:: mdx

    SET [~ROWS] AS
        {[Store].[Stores].[Mexico]}
    SELECT
    NON EMPTY {[Measures].[Unit Sales], [Measures].[Measure Name]} ON COLUMNS,
    NON EMPTY [~ROWS] ON ROWS
   FROM [Sales]
