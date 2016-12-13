Safe Mode
=========

Saiku tries to start its Mondrian connections when the application is booted. This usually works fine, but occasionally due to misconfiguration or other error the Mondrian engine gets stuck trying to connect and the platform doesn't start properly.

To remedy this issue Saiku supports a "safe mode" which will start the platform but prevent any datasources from connecting allowing you to remove the troublesome connection and restore your Saiku server back to a working state.

To start Saiku in safe mode, add `-Dsaiku.safemode=true` to your `CATALINA_OPTS` or `JAVA_OPTS` and restart your Saiku server.
