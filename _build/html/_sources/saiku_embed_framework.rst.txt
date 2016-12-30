Saiku Embed Framework
=====================

Initialize The Client
---------------------
.. code-block:: javascript

    var myClient = new SaikuClient({
                server: "/saiku",
                path: "/rest/saiku/embed",
                user: "admin",
                password: "admin"
        });

Execute A Query
---------------

.. code-block:: javascript

     myClient.execute({
                       file: "/homes/home:admin/yardsyoy2.saiku",
                       htmlObject: "#saiku",
                       render: "chart",
                       mode: "line",
                       chartDefinition: {
                            width: 560,
                            colors: colors,
                            extensionPoints: {
                               legend: true,
                               legendShape: 'circle',
                               legendSize: {width: '100%'},
                               legendLabel_textStyle: "#990000",
                               legendFont: 'normal 11px "Open Sans"'
                             }
                        },
                        zoom: true,
                        params: {
                            teamname: rfiSchooldropdown.str
                        }
                       });

