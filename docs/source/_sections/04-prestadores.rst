=======
API Prestadores
=======

La API de Prestadores expone datos del Registro Nacional de Prestadores Individuales de Salud. Permite buscar prestadores por rut, nombres, apellidos, titulos y región; y consultar los antecedentes de un prestador mediante su rut.

La API se compone de tres métodos:

    /prestadores
    /prestadores/{rut}
    /prestadores/antecedentes/{rut}



Prestadores
===========

Los métodos `/prestadores` y `/prestadores/{rut}` devuelven la ficha de un prestador en dos formatos: JSON y HL7.

En el caso de `/prestadores` la respuesta es una lista de los prestadores encontrados en la búsqueda, mientras que en `/prestadores/{rut}` la respuesta es un único prestador.



Estándar FHIR
-------------

Los métodos de la API de Prestadores entregan los datos en un formato json basado en el estándar FHIR de HL7 https://en.wikipedia.org/wiki/Fast_Healthcare_Interoperability_Resources.

Puede leer la documentación del estándar en https://www.hl7.org/fhir/practitioner.html. Para acceder a un ejemplo en JSON vea https://www.hl7.org/fhir/practitioner-example.json.html



Estructura JSON/FHIR de salida
------------------------------


.. code-block:: json

   [
       {
           "resourceType": "Practitioner",
           "id": "16329928",
           "text": {
               "status": "Registrado",
               "div": "
   \n     
   Registro de Ejemplo Supersalud
   \n   
   "
           },
           "identifier": [
               {
                   "use": "oficial",
                   "system": "RNPI",
                   "value": "16329928"
               }
           ],
           "active": "Registrado",
           "name": [
               {
                   "use": "oficial",
                   "text": "Bernarda Ivette Macaya Neira",
                   "family": "Macaya Neira",
                   "given": "Bernarda Ivette"
               }
           ],
           "telecom": [
               {
                   "system": "phone",
                   "value": "",
                   "use": "work"
               }
           ],
           "address": [
               {
                   "use": "work",
                   "type": "physical",
                   "text": "",
                   "district": ""
               }
           ],
           "gender": "Femenino",
           "birthDate": "02-12-1986",
           "qualification": [
               {
                   "identifier": [
                       {
                           "system": "RNPI",
                           "value": "16329928"
                       }
                   ],
                   "issuer": {
                       "display": "Centro de Formación Técnica INACAP;"
                   }
               }
           ]
       }












Estructura JSON
---------------

Este es un ejemplo de salida en formato JSON del metódo `/prestadores`

.. code-block:: json

   {
      "headers":[
         "habilitadora",
         "nombres",
         "regiónPrestador",
         "rut",
         "searchRegionTrabajo",
         "sexo",
         "telefonos",
         "titulos",
         "vigencia",
         "apellidoMaterno",
         "apellidoPaterno",
         "codigoBusqueda",
         "comunaPrestador",
         "direccion",
         "especialidad",
         "estado",
         "email",
         "fechaNacimiento"
      ],
      "data":[
         [
            "Centro de Formación Técnica INACAP",
            "Bernarda Ivette",
            "",
            "16329928",
            "VIII Región del Biobío|Región del Bío Bío",
            "Femenino",
            "",
            "Técnico de Nivel Superior en Enfermería",
            "",
            "Macaya",
            "Neira",
            "Técnico en Nivel Superior en Salud",
            "",
            "",
            "",
            "Registrado",
            "",
            "02-12-1986"
         ]
      ],
      "cols":18,
      "rows":2,
      "length":2,
      "timestamp":0
   }


Diccionario
-----------
`habilitadora`: Nombre de la institución que entrega la matrícula habilitante
`nombres`: Nombres del prestador consultado
`regiónPrestador`: Región en la que se registró el prestador
`rut`: RUT, identificador único
`searchRegionTrabajo`: Regiones en las que se encuentra inscripto el prestador
`sexo`: Sexo
`telefonos`: Teléfonos de contacto
`titulos`: Títulos habilitantes
`vigencia`: Vigencia de la matrícula
`apellidoMaterno`: Apellido materno 
`apellidoPaterno`: Apellido paterno
`codigoBusqueda`: Título habilitante
`comunaPrestador`: Comuna en la que se encuentra inscripto
`direccion`: Dirección 
`especialidad`: Especialidad principal registrada
`estado`: Estado del prestador, su único valor es "Registrado"
`email`: Correo electrónico de contacto
`fechaNacimiento`: Fecha de nacimiento expresada en formato dd-mm-yyyy




Antecedentes
============

El método `/prestadores/antecedentes/{rut}` devuelve los antedecentes de un prestador en formato JSON. Requiere que se envie el rut del prestador para obtener sus antecedentes.


Ejemplo de salida
-----------------

.. code-block:: json

   {
       "headers": [
           "regionEst",
           "estado",
           "rutEstablecimiento",
           "fechaActivacion",
           "rut",
           "fechaAntecedente",
           "sexo",
           "fechaNacimiento",
           "tipoAntecedente",
           "nombres",
           "nombreFantasia",
           "nomEstablecimiento",
           "nroRegistro",
           "observacion",
           "procedencia",
           "apellidoMaterno",
           "apellidoPaterno",
           "claseAntecedente",
           "codigoBusqueda",
           "codAntecedente",
           "comuna",
           "comunaEst",
           "direccion",
           "dirEstablecimiento"
       ],
       "data": [
           [
               "",
               "Registrado",
               "",
               "",
               "8120308",
               "16-10-2012",
               "Masculino",
               "",
               "T",
               "Jose Orlando",
               "CFT Santo Tomás",
               "",
               "152069",
               "",
               "CFT Santo Tomás",
               "Abarca",
               "Arevalo",
               "Título",
               "Técnico en Nivel Superior en Salud",
               "Técnico en Enfermería de Nivel Superior",
               "",
               "",
               "",
               ""
           ],
           [
               "",
               "Registrado",
               "",
               "",
               "8120308",
               "27-05-1992",
               "Masculino",
               "12-04-1959",
               "T",
               "José Orlando",
               "SS Metropolitano Norte",
               "",
               "152069",
               "",
               "SEREMI Región Metropolitana",
               "Abarca",
               "Arévalo",
               "Título",
               "Auxiliares de Enfermería",
               "Auxiliar de Enfermería",
               "",
               "",
               "",
               ""
           ]
       ],
       "cols": 24,
       "rows": 3,
       "length": 3,
       "timestamp": 0
   }



Diccionario
-----------

`regionEst`: 
`estado`: 
`rutEstablecimiento`: 
`fechaActivacion`: 
`rut`: 
`fechaAntecedente`: 
`sexo`: 
`fechaNacimiento`: 
`tipoAntecedente`: 
`nombres`: 
`nombreFantasia`: 
`nomEstablecimiento`: 
`nroRegistro`: 
`observacion`: 
`procedencia`: 
`apellidoMaterno`: 
`apellidoPaterno`: 
`claseAntecedente`: 
`codigoBusqueda`: 
`codAntecedente`: 
`comuna`: 
`comunaEst`: 
`direccion`: 
`dirEstablecimient`: 




Usabilidad
==========


