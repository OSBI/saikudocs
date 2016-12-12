Mondrian roles allow you to prohibit certain users from seeing certain objects in Saiku.

Examples:

* Regular employees can see data only for regions they work in, while senior management can see all regions.
* Senior management can see schemas related to financial performance (e.g P&L schema), while other employees can see only schemas related to operational performance.
* Only HR department, CEO and CFO can drill-down salaries to employee level, other board members can drill-down to sum of salaries per department only.

Note that Mondrian does hiding of objects and filtering of data automatically when roles are configured, there is no difference to queries or appearance from user perspective.

## Adding Roles

Adding roles is always a process with three easy steps:

Configure roles in Mondrian schemaEnable security in data sourceAdd and configure mapping of rolesAs a first step you must add some roles to your Mondrian schema. You can use Pentaho Schema Workbench to do this. Full documentation regarding how roles work can be found [here](http://mondrian.pentaho.com/documentation/schema.php#Access_control).

Next you need to edit you Saiku data source, within this file you need firstly to enable role based security.


```
`security.enabled=true
`
```
Finally, you have to choose one type of role mapping and configure it properly. There are the following types of role mapping:

* one2one
* mapping
* passthrough

### One2one

One2one offers the ability for Saiku to try and map the role of the logged in user, to the role defined in the schema. So for example if the user has a security role called CTO, Saiku will try and map this to a role called CTO it finds in the Mondrian schema.

To enable one2one add the following to your data source file:


```
`security.type=one2one
`
```
### Mapping

The mapping setting allows you to manually define mapping setups within the data source file.

To do this add the following to your data source file:


```
`security.type=mapping
`
```
You can then map Spring roles to Mondrian roles by adding:


```
`security.mapping=springRole=mondrianRole1;theBoss=CEO
`
```
As you can see the above would try and map two spring roles called springRole and theBoss to two Mondrian roles called mondrianRole1 and CEO.

### Pasthrough

As the name suggests, pasthrough passes the username and password of the logged in user to the connection, which is useful for remote XML/A connections.

To enable passthrough add this to your datasource file:


```
`security.type=passthrough
`
```
