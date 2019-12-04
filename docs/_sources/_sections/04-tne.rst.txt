================================
API Tarjeta Nacional Estudiantil
================================

La API Tarjeta Nacional Estudiantil expone datos de asignaciones de TNE por año.

La API se compone de un método:

    | ``/tne``


 El método ``/tne``  responde la solicitud en formato JSON


Estructura de la solicitud
--------------------------

     | Tipo: ``GET``
     | Endpoint: ``https://api.desarrolladores.junaeb.cl/tarjeta-nacional-estudiantil/v1/tne.json?anio=2018&auth_key=YOUR_AUTH_KEY``
     | Content-Type: ``"application/json"``

Solicitud cURL
^^^^^^^^^^^^^^^

 .. code-block:: rest

       curl --request GET \
       'https://api.desarrolladores.junaeb.cl/tarjeta-nacional-estudiantil/v1/tne.json?anio=2018&auth_key=YOUR_AUTH_KEY'


Solicitud HTTP
^^^^^^^^^^^^^^^

 .. code-block:: rest

       https://api.desarrolladores.junaeb.cl/tarjeta-nacional-estudiantil/v1/tne.json?anio=2018&auth_key=YOUR_AUTH_KEY


Estructura de respuesta
-----------------------

Este es un ejemplo de salida en formato JSON del metódo ``/tne``

.. code-block:: json

        {
        	"apiVersion": "1.0",
        	"tne": [
        	{	"anio": 2018,
        		"codigoEstalecimiento": 49,
        		"nombreEstalecimiento": "SANTA MARIA",
        		"codigoComuna": 1034,
        		"nombreComuna": "ESC. BAS. GUILLERMO BAÑADOS",
        		"educacionBasica": 20,
        		"educacionMedia": 0,
         		"total": 20
                }
            ],
            "columnas": 8,
            "filas": 1,
            "total": 7290,
            "timestamp": 1572959435297
        }



Diccionario
-----------

====================        ===================================
Atributo                    Descripción
====================        ===================================
anio                        Año consultado
codigoEstalecimiento        Código del establecimiento RBD
nombreEstalecimiento        Nombre del establecimiento
codigoComuna                Código de comuna
nombreComuna                Nombre de comuna
educacionBasica             Cantidad de TNE en edudación básica
educacionMedia              Cantidad de TNE en edudación media
total                       Cantidad total de TNE
====================        ===================================
