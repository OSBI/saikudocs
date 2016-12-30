<a href="#readme"></a>

<p align="center">
  <img src="https://raw.githubusercontent.com/OSBI/saiku/assets/L.png" align="left">
  <img src="https://raw.githubusercontent.com/OSBI/saiku/assets/R.png" align="right">
  <b>
    When something doesn't work as expected, then please subscribe to the 
    <a href="https://groups.google.com/a/saiku.meteorite.bi/forum/#!forum/user">Saiku User Group list</a> 
    and send your doubt. If that doesn't solve your problem, then please ask for help on 
    <a href="https://groups.google.com/a/saiku.meteorite.bi/forum/#!forum/dev">Saiku Dev Group</a>.
  </b>
</p>
***

<h1 align="center">Saiku Analytics</h1>
<h2 align="center">The world's greatest open source OLAP browser</h2>
<p align="center"><a href="http://www2.meteorite.bi/saiku-demo/"><img src="https://raw.githubusercontent.com/OSBI/saiku/assets/saiku-demo-1.jpg"/></a></p>
<hr />
<p align="center">
  <a href="http://www.meteorite.bi/"><b>homepage</b></a> |
  <a href="http://licensing.meteorite.bi/"><b>Saiku License</b></a> |
  <a href="http://wiki.meteorite.bi/display/SAIK/Saiku"><b>wiki</b></a> |
  <a href="http://community.meteorite.bi/"><b>community</b></a> |
  <a href="https://groups.google.com/a/saiku.meteorite.bi/forum/#!forum/dev"><b>mailing list</b></a> |
  <a href="http://webchat.freenode.net/?channels=##saiku"><b>chat</b></a> |
  <a href="https://twitter.com/SaikuAnalytics"><b>news</b></a>
</p>
***

<p align="justify">
  Saiku allows business users to explore complex data sources, 
  using a familiar drag and drop interface and easy to understand 
  business terminology, all within a browser. Select the data you 
  are interested in, look at it from different perspectives, 
  drill into the detail. Once you have your answer, save your results, 
  share them, export them to Excel or PDF, all straight from the browser.
  <a href="http://www.meteorite.bi/">(more)</a>
</p>
***

<p align="center">
  <b>
    Please consider supporting development by making a
    <a href="http://www.meteorite.bi/products/saiku/sponsorship">donation</a>.
  </b>
</p>
***

## Saiku Documentation

### Build Instructions

Saiku docs require you have Python 2.X with [Sphinx](http://www.sphinx-doc.org) package installed. In order to install Shinx, on a terminal window, type:

```bash
pip install Sphinx
```

On OSX, you'll have to run it on sudo mode:

```bash
sudo -H pip install Sphinx
```

To build Saiku docs you should clone its repository or download its zip package and decompress in a local folder. Inside the Saiku docs folder, on a terminal window, type:

```bash
make html
```

This command will create a `_build` directory and inside it the folders and files of Saiku documentation. To read the newly generated docs, simply open the `_build/html/index.html` file on a web browser.
