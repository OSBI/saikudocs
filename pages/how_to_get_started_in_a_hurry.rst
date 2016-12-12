Because we are nice folks here at Analytical Labs we like to make your lives as easy as possible. To get started with Saiku we have created a bundle that has a sample set of data that means you can install and evaluate Saiku without having to supply your own data set and cube if you don't have one, or even know what a cube is.

To get started navigate to the Analytical Labs website and [download](http://meteorite.bi/saiku/download) a Saiku server package that includes the sample database (labeled Saiku Server (Including Foodmart DB)). This package contains a Tomcat server, the Saiku server, the Saiku user interface, an in memory database with a dataset called Foodmart and the Mondrian schema required to access the data from Saiku.

Once you have downloaded this archive, you need to extract it. To do this on a Windows computer you can use the built-in extractor tool or your favourite archive manager. In Linux you can do this with:


```
`$ tar xvfz saiku-server-foodmart-2.5.tar.gz
`
```
This will extract the archive into a directory called saiku-server. All that remains now is for you to start the server this can be done on a Windows machine by running start-saiku.bat. On a Linux box you have to do the following:


```
`$ cd saiku-server
$ sh start-saiku.sh
`
```
This will start the supplied Tomcat server and all the required components to make the Saiku server operational. After a few seconds if you navigate to [http://localhost:8080](http://localhost:8080) you will be greated with the Saiku user interface. To login enter the username: admin and the password: admin.

To create a new query click on the drop down box on the left hand side of the user interface and select a cube from the list. You will then be presented with a list of dimensions and measures which you can then drag from the browser area on the left to the Columns, Rows and Filters box on the main query window.

![data shot](http://docs.analytical-labs.com/img/shot1.jpg)

You have to put at least one dimension or measure on both Rows and Columns before a query becomes valid and results are rendered. Once you have done so you should be presented with the result table. You can then continue adding more artifacts to the axes or to the filters. A single click one of the objects you have dropped will open a filter dialog which will allow you to select specific members from the list to include only these within your query.

![data shot](http://docs.analytical-labs.com/img/shot3.jpg)

So there we go, pretty simple huh? Continue reading through the documentation to find out more about how to create your own cubes, what features are avaiable to users and how to customise different aspects of the Saiku system.

