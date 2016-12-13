Conditional Formatting
======================

Saiku supports conditional formatting defined in the schema, and in an MDX query. Currently you can't apply run time formatting to drag and drop queries but this is in the roadmap.
Schema Based Formatting
To apply schema conditional formatting, you can open your schema and create a calculated member similar to this:
<CalculatedMembers>
 <CalculatedMember name='Profit' dimension='Measures'>
 <Formula>[Measures].[Store Sales] - [Measures].[Store Cost]</Formula>
 <CalculatedMemberProperty name="FORMAT_STRING" expression="Iif(([Measures].[Store Sales]) &lt; 10000, '|(#,##0.00 &#8364;)|style=red', '|#,##0.00 &#8364;|style=green')"/>
 </CalculatedMember>
</CalculatedMembers>

This snippet says that if the Store Sales value is less than 10,000 then its style is the colour red and apply a format mask to the number as well which ends with the Euro symbol. Similarly if it is more than 10,000 then make the cell green and apply a format mask.
MDX Query Formatting
You can also add conditional formatting to an MDX query:
WITH
MEMBER Measures.ProfitFormatted as Measures.Profit, FORMAT_STRING = IIf(Measures.Profit > 2000, "|### €|style='lightgreen'|link='http://www\.analytical-labs\.com?profit\=" || Cast(Product.CurrentMember.Name as STRING) || "'|","|(### €)|style='red'|")
SET [~ROWS] AS
    {[Promotion].[Media Type].[Media Type].Members}
SELECT
NON EMPTY {[Measures].[ProfitFormatted]} ON COLUMNS,
NON EMPTY [~ROWS] ON ROWS
FROM [Sales]


In this example you can see it applies a format which includes a link to an external url and passes the current member as a parameter.
