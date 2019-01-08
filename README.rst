
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
   Discord <https://discord.gg/R8v48YA> `_.
- Postea las solicitudes de bienvenida. Echa un vistazo a la lista de temas para las ideas.
   Puedes ayudar con la funcionalidad de billetera, escribiendo pruebas o documentación,
   o en cualquier otra característica que considere impresionante, solo escribenos a 
   ``latineo01@gmail.com``.


Empezando
---------------

neo-python tiene dos dependencias del sistema (todo lo demás está cubierto con
`` pip``):

- `LevelDB <https://github.com/google/leveldb>` _
- `Python
   3.6 <https://www.python.org/downloads/release/python-366/> `_ o` Python 3.7 <https://www.python.org/downloads/release/python-370/> `_ ( 3.5 y por debajo no es compatible)

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

Docker
------

Using Docker is another option to run neo-python. There are example
Dockerfiles provided in the
`/docker folder <https://github.com/CityOfZion/neo-python/tree/development/docker>`_,
and we have an image on Docker hub, tagged after the neo-python
releases: https://hub.docker.com/r/cityofzion/neo-python/

Native installation
-------------------

Instructions on the system setup for neo-python:

LevelDB
~~~~~~~

OSX
^^^

::

    brew install leveldb

Ubuntu/Debian 16.10+
^^^^^^^^^^^^^^^^^^^^

Ubuntu starting at 16.10 supports Python 3.6+ in the official repositories.

First, ensure Ubuntu is fully up-to-date with this:

::

   sudo apt-get update && sudo apt-get upgrade

You can install Python 3.7 and all the system dependencies like this:

::

   sudo apt-get install python3.7 python3.7-dev python3.7-venv python3-pip libleveldb-dev libssl-dev g++


Or, you can install Python 3.6 and all the system dependencies like this:

::

    sudo apt-get install python3.6 python3.6-dev python3.6-venv python3-pip libleveldb-dev libssl-dev g++

Older Ubuntu versions (eg. 16.04)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For older Ubuntu versions you'll need to use an external repository like
Felix Krull's deadsnakes PPA at
https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa (read more
`here <https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get>`__).

(The use of the third-party software links in this documentation is done
at your own discretion and risk and with agreement that you will be
solely responsible for any damage to your computer system or loss of
data that results from such activities.)

::

    apt-get install software-properties-common python-software-properties
    add-apt-repository ppa:deadsnakes/ppa
    apt-get update
    apt-get install python3.6 python3.6-dev python3.6-venv python3-pip libleveldb-dev libssl-dev g++

Centos/Redhat/Fedora
^^^^^^^^^^^^^^^^^^^^

::

    # Install Python 3.6:
    yum install -y centos-release-scl
    yum install -y rh-python36
    scl enable rh-python36 bash

    # Install dependencies:
    yum install -y epel-release
    yum install -y readline-devel leveldb-devel libffi-devel gcc-c++ redhat-rpm-config gcc python-devel openssl-devel

Windows
^^^^^^^

Currently, you should use the Linux subsystem with Ubuntu, or a
Virtual Machine with Linux. You can find more information and a guide
for setting up the Linux subsystem
`here <https://medium.com/@gubanotorious/installing-and-running-neo-python-on-windows-10-284fb518b213>`__.

Installing "Ubuntu" from Microsoft Store installs Ubuntu 16.04. You should install Ubuntu 18.04 from Microsoft Store found here: https://www.microsoft.com/en-us/p/ubuntu-1804/9n9tngvndl3q?activetab=pivot%3aoverviewtab

Help needed for running natively. Installing the Python package plyvel seems to require C++
compiler support tied to Visual Studio and libraries. Refer to
`documentation <https://neo-python.readthedocs.io/en/latest/installwindows.html>`__.

Python 3.6+
~~~~~~~~~~~

neo-python is compatible with **Python 3.6 and later**.

On \*nix systems, install Python 3.6 or Python 3.7 via your package manager, or
download an installation package from the `official
homepage <https://www.python.org/downloads/>`__.


Install
~~~~~~~

It is recommended to put all project dependencies into its own virtual
environment, this way we don't pollute the global installation which
could lead to version conflicts.


1. Install from Github:

  ::

    git clone https://github.com/CityOfZion/neo-python.git
    cd neo-python

    # if you want to use the development branch, switch now
    git checkout development

    # create virtual environment using Python 3.7 and activate or skip to the next step for Python 3.6
    python3.7 -m venv venv
    source venv/bin/activate

    # create virtual environment using Python 3.6 and activate
    python3.6 -m venv venv
    source venv/bin/activate

    # install the package in an editable form
    (venv) pip install wheel -e .

2. Install from PyPi

  ::

    # create project dir
    mkdir myproject
    cd myproject

    # create virtual environment using Python 3.7 and activate or skip to the next step for Python 3.6
    python3.7 -m venv venv
    source venv/bin/activate

    # create virtual environment using Python 3.6 and activate
    python3.6 -m venv venv
    source venv/bin/activate

    (venv) pip install wheel neo-python


Running
-------

After installing requirements and activating the environment, there is
an easy to use CLI (``np-prompt``) that starts the node and allows some
basic interactivity.

::

    np-prompt
    NEO cli. Type 'help' to get started

    neo> state
    Progress: 1054913 / 1237188

    neo>

By default, the CLI connects to the **TestNet** (see below how to switch
to MainNet or PrivNet).

Let's query for a block in the current server by hash or by block index:

::

    np-prompt
    NEO cli. Type 'help' to get started

    neo> block 122235
    {
        "index": 122235,
        "script": "",
        "merkleroot": "1d5a895ea34509a83becb5d2f9391018a3f59d670d94a2c3f8deb509a07464bd",
        "previousblockhash": "98ae05cb68ab857659cc6c8379eb7ba68b57ef1f5317904c295341d82d0a1713",
        "tx": [
            "1d5a895ea34509a83becb5d2f9391018a3f59d670d94a2c3f8deb509a07464bd"
        ],
        "version": 0,
        "time": 1479110368,
        "hash": "74671375033f506325ef08d35632f74083cca564dc7ea6444c94d3b9dec3f61b",
        "consensus data": 16070047272025254767,
        "next_consensus": "59e75d652b5d3827bf04c165bbe9ef95cca4bf55"
    }
    neo>

Bootstrapping the Blockchain
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you use neo-python for the first time, you need to synchronize the
blockchain, which may take a long time. Included in this project is the script
``np-bootstrap`` to automatically download a chain directory for you.

np-bootstrap Usage
^^^^^^^^^^^^^^^^^^

::

    $ np-bootstrap -h
    usage: np-bootstrap [-h] [-m] [-c CONFIG] [-n] [-s] [--datadir DATADIR]

    optional arguments:
      -h, --help            show this help message and exit
      -m, --mainnet         use MainNet instead of the default TestNet
      -c CONFIG, --config CONFIG
                            Use a specific config file
      -n, --notifications   Bootstrap notification database
      -s, --skipconfirm     Bypass warning about overwritting data in Chains/SC234
      --datadir DATADIR     Absolute path to use for database directories

Bootrapping Testnet
^^^^^^^^^^^^^^^^^^^

To bootstrap the testnet blockchain, run ``np-bootstrap``, get a cup of coffee
and wait. Then, bootstrap the testnet notifications database with ``np-bootstrap -n``.

Bootstrapping Mainnet
^^^^^^^^^^^^^^^^^^^^^

To bootstrap the mainnet blockchain, run ``np-bootstrap -m`` and get 8 cups of coffee
(9+ GB file). Then, bootstrap the mainnet notifications database with
``np-bootstrap -m -n``.

**Important:** do not use the chain files from
https://github.com/CityOfZion/awesome-neo.git, they will not work with
neo-python.

Basic Wallet commands
~~~~~~~~~~~~~~~~~~~~~

::

    create wallet {wallet_path}
    open wallet {wallet_path}
    wallet close

    wallet (verbose)
    wallet rebuild (start block)
    wallet create_addr {number of addresses}
    wallet delete_addr {addr}
    
    export wif {address}
    import wif {wif}
    
    export nep2 {address}
    import nep2 {nep2_encrypted_key}
    
    send {assetId or name} {address} {amount} (--from-addr={addr}) (--fee={priority_fee}) (--owners=[{addr}, ...]) (--tx-attr=[{"usage": <value>,"data":"<remark>"}, ...])

For a complete list of commands use ``help``.

Running on MainNet
~~~~~~~~~~~~~~~~~~

To run the prompt on MainNet, you can use the CLI argument ``-m`` (eg.
``np-prompt -m``), for running on PrivNet you can use ``-p``. Be
sure to check out the details of the parameters:

::

    $ np-prompt -h
    usage: np-prompt [-h] [-m | -p [host] | --coznet | -c CONFIG]
                     [-t {dark,light}] [-v] [--datadir DATADIR] [--version]

    optional arguments:
      -h, --help            show this help message and exit
      -m, --mainnet         Use MainNet instead of the default TestNet
      -p [host], --privnet [host]
                            Use a private net instead of the default TestNet,
                            optionally using a custom host (default: 127.0.0.1)
      --coznet              Use the CoZ network instead of the default TestNet
      -c CONFIG, --config CONFIG
                            Use a specific config file
      -t {dark,light}, --set-default-theme {dark,light}
                            Set the default theme to be loaded from the config
                            file. Default: 'dark'
      -v, --verbose         Show smart-contract events by default
      --datadir DATADIR     Absolute path to use for database directories
      --maxpeers MAXPEERS   Max peers to use for P2P Joining
      --version             show program's version number and exit

Logging
~~~~~~~

Currently, ``np-prompt`` logs to ``prompt.log``

--------------

Tests
-----

Note we make use of a Blockchain fixture database (~15 MB). This file is not kept in the repo,
but is downloaded the first time the tests are run, this can take some time (depending on the internet connection),
but happens only once.

Useful commands
---------------

::

    make lint
    make test
    make coverage
    make docs


    # run only neo-python tests
    python -m unittest discover neo

    # run only neo-boa tests
    python -m unittest discover boa_test

Updating the version number and releasing new versions of neo-python
--------------------------------------------------------------------

This is a checklist for releasing a new version, which for now means:

1. Merging the changes from development into master
2. Setting the version from eg. ``0.4.6-dev`` to ``0.4.6`` (which
   automatically created a tag/release)
3. On the dev branch, setting the version to the next patch, eg.
   ``0.4.7-dev``
4. Pushing master, development and the tags to GitHub

Make sure you are on the development branch and have all changes merged
that you want to publish. Then follow these steps:

::

    # Only in case you want to increase the version number again (eg. scope changed from patch to minor):
    # bumpversion --no-tag minor|major

    # Update CHANGELOG.rst: make sure all changes are there and remove `-dev` from the version number
    vi CHANGELOG.rst
    git commit -m "Updated changelog for release" CHANGELOG.rst

    # Merge development branch into master
    git checkout master
    git merge development

    # Set the release version number and create the tag
    bumpversion release

    # Switch back into the development branch
    git checkout development

    # Increase patch number and add `-dev`
    bumpversion --no-tag patch

    # Push to GitHub, which also updates the PyPI package and Docker Hub image
    git push origin master development --tags

Troubleshooting
---------------

If you run into problems, check these things before ripping out your
hair:

-  Double-check that you are using Python 3.6.x or Python 3.7.x
-  Update the project dependencies (``pip install -e .``)
-  If you encounter any problems, please take a look at the
   `installation
   section <https://neo-python.readthedocs.io/en/latest/install.html#further-install-notes>`_
   in the docs, and if that doesn't help open an issue. We'll try to
   help.
-  You can reach us on the `NEO Discord <https://discord.gg/R8v48YA>`_,
   or simply file a `GitHub
   issue <https://github.com/CityOfZion/neo-python/issues/new>`_.

License
-------

-  Open-source
   `MIT <https://github.com/CityOfZion/neo-python/blob/master/LICENSE.md>`_.
-  Contributors: `@localhuman <https://github.com/localhuman>`_ (Creator), `@metachris <https://github.com/metachris>`_, `@ixje <https://github.com/ixje>`_, and `many more <https://github.com/CityOfZion/neo-python/graphs/contributors>`_

Donations
---------

Accepted at **AUxDFKAoWRg4SrKqYXF9jWy83SuPruEsbo**
