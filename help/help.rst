Besoin d'aide?
==========


FAQ
--------------------------

Si vous avez des dificultées avec NodeBB, jettez un oeil ici, la solution y est probablement.

Comment demarrer/arrêter/redemarrer NodeBB?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Vous pouvez entrer la commande ``./nodebb`` pour lancer l'executable qui s'occuperas de demarrer ou d'arrêter NodeBB:

.. code:: bash

    $ ./nodebb
	Welcome to NodeBB
	Usage: ./nodebb {start|stop|reload|restart|log|setup|reset|upgrade|dev|watch}

	start    Start the NodeBB server *(Demarre le serveur NodeBB)*
	stop     Stops the NodeBB server *(Arrête le le serveur NodeBB)*
	reload   Restarts NodeBB *(Redemarre NodeBB)*
	restart  Restarts NodeBB *(Redemarre aussi NodeBB)*
	log      Opens the logging interface (useful for debugging) *(Permet de voir les logs, pour fournir de quoi debug par exemple, si vous rencontrez un prolbème)*
	setup    Runs the NodeBB setup script *(Lance le script d'installation de NodeBB, utile aussi pour modifier des choses comme la base de donnée ou les ports...)
	reset    Disables all plugins, restores the default theme. *(Désactive* ***TOUT*** *les plugins, et remet le thème par défaut)* 
	upgrade  Run NodeBB upgrade scripts, ensure packages are up-to-date *(Lance le script de mise a jour, afin de verifier que les packtages (plugins, theme, dépendances...) soit à jour* ***Note : Ne permet pas de mettre a jour NodeBB lui même ! Voir le guide d'upgrade !*** *)*
	dev      Start NodeBB in interactive development mode *(Demarre NodeBB en mode développement, pratique pour developper un plugins)*
	watch    Start NodeBB in development mode and watch for changes *(Demarre NodeBB en mode développement aussi, et regarde constament si il y a des changements de fait)*

How do I upgrade my NodeBB?
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Please consult :doc:`Upgrading NodeBB <../upgrading/index>`

I upgraded NodeBB and now X isn't working properly!
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Please consult :doc:`Upgrading NodeBB <../upgrading/index>`

I installed an incompatible plugin, and now my forum won't start!
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you know which plugin caused problems, disable it by running: ``./nodebb reset plugin="nodebb-plugin-pluginName"``

Otherwise, disable all plugins by running: ``./nodebb reset plugins``

Is it possible to install NodeBB via FTP?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is possible to transfer the files to your remote server using FTP, but you do require shell access to the server in order to actually "start" NodeBB. Here is `a handy guide for installing NodeBB on DigitalOcean <http://burnaftercompiling.com/nodebb/setting-up-a-nodebb-forum-for-dummies/>`_

I'm getting an "npm ERR!" error
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For the most part, errors involving ``npm`` are due to Node.js being outdated. If you see an error similar to this one while running ``npm install``:

.. code:: bash

    npm ERR! Unsupported
    npm ERR! Not compatible with your version of node/npm: connect@2.7.11

You'll need to update your Node.js version to 0.8 or higher.

To do this on Ubuntu:

.. code:: bash

    # add-apt-repository ppa:chris-lea/node.js
    # apt-get update && apt-get dist-upgrade -y

If successful, running the following command should show a version higher than 0.8

.. code:: bash

    # apt-cache policy nodejs

URLs on my NodeBB (or emails) still have the port number in them!
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are using :doc:`nginx <../configuring/proxies/nginx>` or :doc:`Apache <../configuring/proxies/apache>` as a reverse proxy, you don't need the port to be shown. Simply run `./nodebb setup` and specify the base URL without a port number.

Alternatively, edit the ``config.json`` file using your favourite text editor and change ``use_port`` to ``false``.


Submit Bugs on our Issue Tracker
--------------------------------

Before reporting bugs, please ensure that the issue has not already been filed on our `tracker <https://github.com/NodeBB/NodeBB/issues?state=closed>`_, or has already been resolved on our `support forum <http://community.nodebb.org/category/6/bug-reports>`_. If it has not been filed, feel free to create an account on GitHub and `create a new issue <https://github.com/NodeBB/NodeBB/issues>`_.


Ask the NodeBB Community
------------------------

Having trouble installing NodeBB? Or did something break? Don't hesitate to `join our forum <community.nodebb.org/register>`_ and ask for help. Hopefully one day you'll be able to help others too :)
