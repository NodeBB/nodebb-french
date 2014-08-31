
Debian
======

Le guide actuel pour Ubuntu n'est pas totalement compatible avec Debian, de nombreuses choses sont différentes notamment l'installation de NodeJS et Redis.

Requis
^^^^^^^^^^^^^^^^^^^^^^^
Les pré-requis de NodeBB : 

* Node.js, au moins 0.10 et plus 
* Redis, version 2.6 ou supérieure 
* CURL installé, il suffit de faire `` sudo apt-get install curl`` afin de l'installer

Installation de Node.js
^^^^^^^^^^^^^^^^^^^^^^^

Debian 7, 6 et antérieurs ne possède pas de paquets `nodejs` par défaut mais il existe quelques solutions pour installer Node.js sur votre distribution Debian.

Wheezy Backport :
------------------

Cette solution est **SEULEMENT pour Debian 7** , vous n'avez plus qu'à lancer les commande suivantes en tant que super utilisateur**:

.. code:: bash

	$ echo "deb http://ftp.us.debian.org/debian wheezy-backports main" >> /etc/apt/sources.list
	$ apt-get update


Pour installer Node.js et NPM, executez ces commandes :

.. code:: bash

	$ apt-get install nodejs-legacy
	$ curl --insecure https://www.npmjs.org/install.sh | bash


Ceci installera une version de Node.js qui sera supérieur à la 0.8 (29 Mars 2014 : 0.10.21)

Compilation à partir du code source :
------------------

Cette solution est uniquement recommandé pour **Debian 6 ou supérieur** , vous n'avez plus qu'à lancer les commande suivantes **en tant que super utilisateur**:

.. code:: bash

	$ sudo apt-get install python g++ make checkinstall
	$ src=$(mktemp -d) && cd $src
	$ wget -N http://nodejs.org/dist/node-latest.tar.gz
	$ tar xzvf node-latest.tar.gz && cd node-v*
	$ ./configure
	$ fakeroot checkinstall -y --install=no --pkgversion $(echo $(pwd) | sed -n -re's/.+node-v(.+)$/\1/p') make -j$(($(nproc)+1)) install
	$ sudo dpkg -i node_*


Via DotDeb
^^^^^^^^^^^^^^^^^^^^^^^

Dotdeb est un dépôt contenant des paquets permettant de transformer vos machines Debian en serveurs LAMP puissants, stables et mis à jour.
* Nginx,
* PHP 5.4 and 5.3 ( des extensions PHP utiles : APC, imagick, Pinba, xcache, Xdebug, XHpro..)
* MySQL 5.5,
* Percona toolkit,
* Redis,
* Zabbix,
* Passenger…

Dotdeb supporte :

* Debian 6.0 “Squeeze“ et 7 “Wheezy“
* Les architectures amd64 (64bit) et i386 (32bit)

Debian 7 (Wheezy) :
------------------

Pour le dépôt DotDeb au complet :

.. code:: bash

	$ sudo echo 'deb http://packages.dotdeb.org wheezy all' >> /etc/apt/sources.list
	$ sudo echo 'deb-src http://packages.dotdeb.org wheezy all' >> /etc/apt/sources.list


Après ça, ajoutez les clés GPC suivantes :

.. code:: bash

	$ wget http://www.dotdeb.org/dotdeb.gpg
	$ sudo apt-key add dotdeb.gpg


Et mettez à jour vos sources :

.. code:: bash

	$ sudo apt-get update


Debian 6 (Squeeze)
------------------

Pour le dépôt DotDeb au complet :

.. code:: bash

	$ sudo echo 'deb http://packages.dotdeb.org squeeze all' >> /etc/apt/sources.list
	$ sudo echo 'deb-src http://packages.dotdeb.org squeeze all' >> /etc/apt/sources.list


Après ça, ajoutez les clés GPC suivantes :
.. code:: bash

	$ wget http://www.dotdeb.org/dotdeb.gpg
	$ sudo apt-key add dotdeb.gpg


Et mettez à jour vos sources :

.. code:: bash

	$ sudo apt-get update


Installation de NodeBB
^^^^^^^^^^^^^^^^^^^^^^^

Maintenant que nous avons installé NodeJS et Redis, NodeBB est prêt à être installé, lancez cette commande pour installer les logiciels de base:
.. code:: bash

	$ apt-get install redis-server imagemagick git


Ensuite on clône le dépôt :

.. code:: bash

	$ cd /path/to/nodebb/install/location
	$ git clone git://github.com/NodeBB/NodeBB.git nodebb

Maintenant nous allons installer toutes les dépendances de NodeBB via NPM :

.. code:: bash

	$ cd /path/to/nodebb/install/location/nodebb (or if you are on your install location directory run : cd nodebb)
	$ npm install

Et enfin lancez la paramétrisation de NodeBB en exécutant l'application avec `--setup`:

.. code:: bash

	$ ./nodebb setup


1. `URL of this installation` : soit votre adresse IP publique ou le nom de domaine pointant vers cette adresse IP.  
    **Exemple:** ``http://0.0.0.0`` ou ``http://exemple.org``  

2. ``Port number of your NodeBB`` le port nécéssaire pour acceder a votre site:  
    **Note:** Si vous ne comptez pas utiliser Nginx comme proxy, choisissez le port 80 pour mettre votre forum en production.  
3. Si vous avez installer Redis avec les solutions ci dessus, laissez les paramètres par défaut pour la suite.

Et enfin.. exécutez notre forum NodeBB !

.. code:: bash

	$ ./nodebb start


**Note:** Si le forum crash, NodeBB ne se redémarrera pas seul. Si vous avez besoin d'un redémarrage automatique, jettez un oeil au solutions suivantes : ``supervisor`` et ``forever``,  :doc:`ICI <../../running/index>`

Extras
^^^^^^^^^^^^^^^^^^^^^^^

Vous pouvez sécuriser votre installation de NodeBB, `jettez un oeil ici <https://github.com/NodeBB/NodeBB#securing-nodebb>`_.

Vous pouvez utiliser Nginx (ou semblable) pour servir de proxy à votre installation de NodeBB, afin de le rendre accessible depuis le port 80, :doc:`jettez un oeil ici <../../configuring/proxies>`
