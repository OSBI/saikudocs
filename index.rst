Introduction
============

Background
~~~~~~~~~~
   
Saiku was founded in 2008 by Tom Barber and Paul Stoellberger. Originally called the Pentaho Analysis Tool, if started life as a basic GWT based wrapper around the OLAP4J library. Over the years it has evolved, and after a complete rewrite in 2010, it was reborn as Saiku.

Saiku offers a user friendly, web based analytics solution that lets users, quickly and easily analyse corporate data and create and share reports. The solution connects to a range of OLAP Servers including Mondrian, Microsoft Analysis Services, SAP BW and Oracle Hyperion and can be deployed rapidly and cost effectively to allow users to explore data in real time.

OLAP Analysis
-------------

On-Line Analytical Processing (OLAP) is a category of software technology that enables analysts, managers and executives to gain insight into data through fast, consistent, interactive access to a wide variety of possible views of information that has been transformed from raw data to reflect the real dimensionality of the enterprise as understood by the user. OLAP functionality is characterized by dynamic multi-dimensional analysis of consolidated enterprise data supporting end user analytical and navigational activities (The OLAP Council)

By harnessing the power of OLAP, Saiku allows users to choose the measures and dimensions they need to analyse and “slice and dice” the data and drill into the detail to uncover relationships, opportunities and issues. The intuitive user interface lets users drill down and up, filter, pivot, sort, and chart against OLAP and In-Memory engines. Utilizing the Olap4J library, Saiku is the first application on the market to offer support for Mondrian’s Scenario feature allowing non destructive editing of query results, giving users the ability to adjust the figures and perform “what-if” analysis over their data. By harnessing the power of Mondrian, Saiku offers scalable in-memory analysis. Large amounts of data can be stored in memory in a distributed manner across the local network, offering greatly improved performance over large data warehouses as the aggregated data is retrieved from the network instead of reading from disk.

.. image:: ./attachments/screenshot.png

Architecture
------------

Saiku is a modular analysis suite offering lightweight OLAP which remains easily embeddable, extendable and configurable. The Saiku RESTful server connects to existing OLAP systems, which powers user-friendly, intuitive analytics via our lightweight JQuery based frontend.

Look and feel can be completely customized as the user interface is based entirely on open standards. The supplied user interface is written in HTML, Javascript and CSS, making it easy to change or entirely replace the user interface. By using RESTful standards, the server can be easily integrated into different user interface technologies and 3rd party applications, the only requirements being that the 3rd party application can send and receive HTTP communication and understand JSON data instructions. The client application needs no understanding of MDX or related query languages.

Open Source
-----------

To make sure Saiku survives and sticks to its open source roots, Analytical Labs was created as a business to front Saiku and offer consultancy and development around the Saiku infrastructure. Analytical Labs is based in London.

Saiku is freely available to download from [www.saikuanalytics.com](http://www.analytical-labs.com). Organisations can use the solution internally without having to pay license fees. For customers who would like to use the solution in an Enterprise environment a number of options are available for support and to embed the solution into commercial applications.

Administration Guide
====================

.. toctree::
   :maxdepth: 2

   installation_guide.rst
   administrators_console.rst
   schema.rst
   saiku_settings.rst
   embedding.rst
   backups.rst
   migration.rst
   webdav.rst
   safemode.rst
   localization.rst
   default_reports.rst
   migrating_from_analzyer.rst

User Guide
==========

.. toctree::
   :maxdepth: 2

   creating_a_query.rst
   filtering.rst
   charts_and_graphs.rst
   mdx_mode.rst
   calculated_members.rst
   parameter_support.rst
   drilling.rst
   totals_and_subtotals.rst
   dashboards.rst
   saiku_tips_and_tricks.rst
   how_to_articles.rst

Project Information
===================

.. toctree::
   :maxdepth: 2
   
   saiku_project_information.rst 

Development
===========

.. toctree::
   :maxdepth: 2
  
   development.rst
   server_documentation.rst


Getting Help
============

IRC
~~~

If you prefer more "real time" help and support. We have a very active and helpful community on the Saiku IRC channel. This can be found at ##saiku on the Freenode IRC network. Feel free to drop in and introduce yourself we'll be more than willing to answer any questions or queries you may have.

Commercial Support
~~~~~~~~~~~~~~~~~~

For customers who require Enterprise Support we offer a complete technical support solution. Support is available on an annual subscription basis. Support is provided via a dedicated support portal where customers can raise issues and support requests, track issue progress and receive responses from our full time support team.

For more information on our support services and pricing please visit our [website](http://saiku.meteorite.bi)
 

Licensing
=========

Saiku Analytics is licenced under the Apache Licence. Prior to version 2.4 the Saiku server component was licensed under the GPL v2 license and the UI under the LGPL license. From version 2.4 onwards we have switched the entire stack to the Apache license V2. We believe that using a more permissive license will help Saiku grow as a product as it allows people to use the software more freely.

