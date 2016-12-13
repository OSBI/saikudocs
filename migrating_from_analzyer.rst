Migrating From Pentaho Analyzer
===============================

Users of Pentaho Analzyer who would like to use Saiku with their existing queries can use this proof of concept utility to convert .xanalyzer files to .saiku
Step-by-step guide
Download the jar from https://dl.dropboxusercontent.com/u/8503756/saiku-xanalyzerconvert-3.7.5-jar-with-dependencies.jar
Export your .xanalyzer query from your BI Server and extract it from the zip file.
Execute the converter against the file:
java -jar ./saiku-xanalyzerconvert-3.7.5-jar-with-dependencies.jar <path_to_file> <mondrian_4_true_false>.

For example:
java -jar ./saiku-xanalyzerconvert-3.7.5-jar-with-dependencies.jar /tmp/test.xanalyzer true


If you want to run Pentaho Analyzer files on Saiku Standalone, make sure you set the Mondrian flag to true so it exports a slightly different format.
If your connection details differ on your Saiku server you might need to configure the connection details at the bottom of the new Saiku file, you can open this file in any text editor.
There are a lot of variables and differences between our tests and the real world, if your saved file isn't supported or doesn't work, please file a bug on JIRA with the sample xanalyzer file attached for us to debug.
