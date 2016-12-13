MSSQL has the concept of different instances on the same server which you address with instance names. Because of the way Saiku creates a connection string, this can be problematic, so here is one solution.
A big thanks to Amit at avatisolutions.com for the explanation!
Step-by-step guide
Configure MSSQL to assign instances to dynamic ports (https://support.microsoft.com/en-us/kb/823938)
For main Saiku database connections you can now use the dynamic port to connect to a specific instance: jdbc:jtds:sqlserver://myserver:51218
For Saiku Schema Designer you can continue using the instance name as before: jdbc:jtds:sqlserver://myserver;instance=Amit
