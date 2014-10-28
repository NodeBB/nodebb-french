
Ubuntu
--------------------

Pour commencer, installons nos logiciels de base:

.. code:: bash

	$ sudo apt-get install git nodejs nodejs-legacy npm redis-server imagemagick npm


Si vous souhaitez utiliser MongoDB, LevelDB ou tout autre base de données à la place de Redis, veuillez consulter la section :doc:`Configuration de base de données <../configuring/databases>`.

**If your package manager only installed a version of Node.js that is less than 0.8 (e.g. Ubuntu 12.10, 13.04), use ``node --version`` to determine your version of Node.js:**
**Si votre gestionnaire de paquets a seulement installé une version de Node.js inférieure à 0.8 (ex Ubuntu 12.10, 13.04), utilisez ``node --version`` pour déterminer votre version de Node.js**



.. code:: bash

	$ sudo add-apt-repository ppa:chris-lea/node.js
	$ sudo apt-get update && sudo apt-get dist-upgrade


Ensuite, clonez ce dépot:


.. code:: bash

	$ git clone git://github.com/NodeBB/NodeBB.git nodebb


Récupérez les dépendances dont NodeBB a besoin:

.. code:: bash

    $ cd nodebb
    $ npm install


Lancez le script d'installation en lançant l'application avec l'option ``setup`` :


.. code:: bash

	$ ./nodebb setup


Les paramètres par défaut correspondent à un serveur lcal sur le port par défaut, avec une base de données redis sur la même machine et le même port. 

Pour finir, lançons le forum !


.. code:: bash

	$ ./nodebb start


NodeBB can also be started with helper programs, such as ``supervisor`` and ``forever``. :doc:`Take a look at the options here <../../running/index>`.
NodeBB peut également fonctionner à l'aide de programmes de supervision tels que ``supervisor`` ou ``forever``. :doc:`Jetez un coup d'œil à ces options ici <../../running/index>`.
