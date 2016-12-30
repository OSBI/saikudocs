Connecting To Microsoft Analysis Server
=======================================

Saiku provides an excellent interface to Microsoft Analysis Server and is very easy to setu.
If you aren't using Analysis Services role based security you can select the XMLA menu option from the new data sources menu then enter the url where you have installed the MSMDPump DLL

If you want to use role based security you can still do this using an Advanced Data source, for example:

type=OLAP
name=Internal
driver=org.olap4j.driver.xmla.XmlaOlap4jDriver
location=jdbc:xmla:Server=http://localhost/OLAP/msmdpump.dll
username=admin
password=admin
security.enabled=true
security.type=passthrough

By enabling security and adding the passthrough type Saiku will now pass the logged in users username and password to the XMLA endpoint so that Analysis Services can validate the user and assign the correct permissions to their queries.
