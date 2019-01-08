
.. image:: https://res.cloudinary.com/latineo/image/upload/c_thumb,w_200,g_face/v1546981349/logo2.png
    :alt: CoZ logo

neo-python
----------

Nodo de Python y SDK para Blockchain de NEO

.. image:: https://img.shields.io/pypi/v/neo-python.svg
    :target: https://pypi.python.org/pypi/neo-python
    :alt: Pypi
.. image:: https://travis-ci.org/CityOfZion/neo-python.svg?branch=master
    :target: https://travis-ci.org/CityOfZion/neo-python
    :alt: Travis CI
.. image:: https://readthedocs.org/projects/neo-python/badge/?version=latest
    :target: https://neo-python.readthedocs.io/en/latest/?badge=latest
    :alt: ReadTheDocs
.. image:: https://coveralls.io/repos/github/CityOfZion/neo-python/badge.svg?branch=master
    :target: https://coveralls.io/github/CityOfZion/neo-python?branch=master
    :alt: Coveralls



Vision General
--------

¿Qué hace actualmente?
~~~~~~~~~~~~~~~~~~~~~~~~~



- Ejecutar un nodo P2P basado en Python
- CLI interactivo para configurar el nodo e inspeccionar blockchain
- Construir, desplegar y ejecutar contratos inteligentes
- Ejecuta contratos inteligentes en la cadena de bloques en una máquina virtual Python
- Funcionalidad de Wallet muy básica (no probada completamente, no la use
   en mainnet)
-  `NEP2 <https://github.com/neo-project/proposals/blob/master/nep-2.mediawiki>`_
   y
   `NEP5 <https://github.com/neo-project/proposals/blob/master/nep-5.mediawiki>`_
   funcionalidad de billetera compatible
- `NEP-7 <https://github.com/neo-project/proposals/blob/master/nep-7.mediawiki>`_ and `NEP-8 <https://github.com/neo-project/proposals/blob/c20182cecd92102b9e5a3158a005762eefb8dbdf/nep-8.mediawiki>`_ soporte
-  Cliente RPC
-  Servidor RPC
-  Notificaion de Servidor ( para ver transferencias de tokens NEP5 )
-  ``Runtime.Log`` y ``Runtime.Notify`` monitoreo de eventos


Que va a hacer
~~~~~~~~~~~~~~~

- Nodos de consenso
- Depuración e inspección de contratos inteligentes más robustos.


Documentación
~~~~~~~~~~~~~~

La documentación completa sobre cómo instalar, configurar y usar neo-python
se puede encontrar en `Leer el
Docs <https://neo-python.readthedocs.io/en/latest/>`_.

O tambien pueden ir a la carpeta ``Tutoriales`` para explicacion detallada de cada modulo


Obtén ayuda o ayuda
~~~~~~~~~~~~~~~~~~~~~

- hacer ping ** @ danny3s **, ** @ deivid** en el `NEO
   Discord <https://discord.gg/R8v48YA>`_.
- Postea las solicitudes de bienvenida. Echa un vistazo a la lista de temas para las ideas.
   Puedes ayudar con la funcionalidad de billetera, escribiendo pruebas o documentación,
   o en cualquier otra característica que considere impresionante, solo escribenos a 
   ``latineo01@gmail.com``.


Empezando
---------------

neo-python tiene dos sistemas de dependencias (el resto se cube con
``pip``):

-  `LevelDB <https://github.com/google/leveldb>`_
-  `Python
   3.6 <https://www.python.org/downloads/release/python-366/>`_ or `Python 3.7 <https://www.python.org/downloads/release/python-370/>`_ (3.5 e inferior no sirven)

Hay muchos más videos debajo del
`LatiNeo <https://www.youtube.com/channel/UC5xBCz4rBw-03zzjqX-WfpA?disable_polymer=true>` _
Canal de Youtube, para que lo visites.


Para este tutorial si eres un usuario Windows te recomiendo realizar los siguientes pasos en un servidor Ubuntu 16.04.5 x64 (les recomiendo digitaloceon o vultr que son baratos para realizar el tutorial) para que siempre tengas acceso al blockchain de NEO y no complicarte con las instalaciones directamente en Windows porque no sirve. Para los usuarios Linux y Mac si tienen la facilidad de instalarlo directamente en su computador sin ninguna dificultad.
Yo realizare todo el tutorial dentro de un servidor en DigitalOceon ( no les hago propaganda ), para ellos se comienza por actualizar el sistema con el siguiente comando:

``sudo apt-get update && sudo apt-get upgrade``

Primero vamos a instalar pip para poder instalar las dependencias de Python fácilmente y también virtualvenv que nos permite crear un entorno virtual para nuestro proyecto sin necesidad de corromper otras versiones en otros proyectos:

``apt install python-pip``
``apt install virtualenv``

Puedes instalar `Python 3.7` y todas las dependencias del sistema como esta:

``sudo apt-get install python3.7 python3.7-dev python3.7-venv python3-pip libleveldb-dev libssl-dev g++``

Puedes instalar Python 3.6 y todas las dependencias del sistema como esta:

``sudo apt-get install python3.6 python3.6-dev python3.6-venv python3-pip libleveldb-dev libssl-dev g++``

Les recomiendo colocar todas las dependencias del proyecto en su propio entorno virtual, de esta manera no contaminamos la instalación global, lo que podría generar conflictos de versión.

Instalar desde GitHub
~~~~~~~
::

	git clone https://github.com/CityOfZion/neo-python.git
	cd neo-python

	# Si deseas usar la rama de desarrollo, cambia a sino salta este paso
	git checkout development

	# Crea un entorno virtual usando Python 3.7 y activarlo o saltar al siguiente paso si instalaste Python 3.6
	python3.7 -m venv venv
	source venv/bin/activate

	# Crea un entorno virtual usando Python 3.6 y activarlo
	python3.6 -m venv venv
	source venv/bin/actívate

	# Si no te funciona los comandos anteriores puedes usar el siguiente
	virtualenv venv
	source venv/bin/activate


Instalar desde PyPi
~~~~~~~

::

	# Crea la carpeta del proyecto
	mkdir myproject
	cd myproject

	# Crea un entorno virtual usando Python 3.7 y activarlo o saltar al siguiente paso si instalaste Python 3.6
	python3.7 -m venv venv
	source venv/bin/activate

	# Crea un entorno virtual usando Python 3.6 y activarlo
	python3.6 -m venv venv
	source venv/bin/actívate

	# Si no te funciona los comandos anteriores puedes usar el siguiente
	virtualenv venv
	source venv/bin/activate



Docker
--------

Antes de inicializar el blockchain de NEO debemos instalar una última cosa que es Docker. El software de TI de Docker es tecnología en contenedores que permite la creación y el uso de contenedores Linux.
Vamos a usar uno en especifico que es creado por City Of Zion, donde nos proporionan una billetera con 100000000.0 NEO y 16024 GAS (falsos) para nuestras pruebas en el blockchain privado y en el tesnet. Lo cual nos facilita el desarrollo porque no necesitamos comprar o ni siquiera pedir a otros usuarios que nos envíen NEO o GAS para nuestros contractos inteligentes.
Comenzamos por instalar Docker con el siguiente comando:

``apt install docker.io``

Ejecutar Neo-Python
--------

Inicializa un contenedor de neo-privatenet y sigue estos pasos:
~~~~~~~

::

	# Descarga la versión mas reciente de Docker
	docker pull cityofzion/neo-python
	docker pull cityofzion/neo-privatenet
	# Inicializa el contenedor de red privada. Asigna el directorio de trabajo actual en el host a:
	# `/neo-python/sc/` and exposes the ports.
	docker run --rm -d --name neo-privatenet -p 20333-20336:20333-20336/tcp -p 30333-30336:30333-30336/tcp cityofzion/neo-privatenet

	# Inicializa el contenedor de Neo-Python
	docker run --rm -it --net=host -v $(pwd):/neo-python/sc -h neo-python --name neo-python cityofzion/neo-python /bin/bash

	# Inicia Neo-Python en la red privada
	np-prompt -p


License
-------

-  Open-source
   `MIT <https://github.com/CityOfZion/neo-python/blob/master/LICENSE.md>`_.
-  Contributors: `@localhuman <https://github.com/localhuman>`_ (Creator), `@metachris <https://github.com/metachris>`_, `@ixje <https://github.com/ixje>`_, and `many more <https://github.com/CityOfZion/neo-python/graphs/contributors>`_

Donations
---------

Accepted at **AUxDFKAoWRg4SrKqYXF9jWy83SuPruEsbo**
