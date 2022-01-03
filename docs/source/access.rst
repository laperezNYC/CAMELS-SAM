************
Data Access
************

*UPDATED FROM THE CAMELS DOCUMENTATION AT:* https://camels.readthedocs.io/en/latest/data_access.html.

The available CAMELS-SAM data is stored in the Rusty cluster of the Flatiron Institute in New York City, and its data can be accessed through five different methods:

.. warning::

We gently remind users that CAMELS-SAM is large, even as we have limited ourselves to the most broadly useful data products. The *smallest* data products in CAMELS-SAM are the SC-SAM galaxy catalogs, which are approximately 5GB per simulation, totaling 5TB across the suite. All available CAMELS-SAM data products total just under 60TB. 


Binder
~~~~~~

Binder is a system that allows users to read and manipulate data that is hosted at the Flatiron Institute through either a Jupyter notebook or a unix shell. The user can find some basic documentation `here <https://docs.simonsfoundation.org/index.php/Public:Binder>`_. All CAMELS-SAM data can be accessed, read, and manipulated through Binder. 

.. warning::

   Two important things need to be taken into account when using Binder. First, the Binder environment is ephemeral - after a few days of inactivity its contents are deleted, so one has to be vigilant about downloading any analysis results in time. Second, Binder is not designed to carry out long and heavy calculations. In this case we recommend the user to download the data and work with it locally. 

``!!!!!must update!!!!!``
.. `Link to Binder <https://binder.flatironinstitute.org/~sgenel/CAMELS_PUBLIC>`_


Globus
~~~~~~~

The full CAMELS data can be downloaded via globus, an online system designed to efficiently transfer large amounts of data. This is the method we recommend to transfer the data.

``!!!!!must update!!!!!``
.. `Globus link <https://app.globus.org/file-manager?origin_id=58bdcd24-6590-11ec-9b60-f9dfb1abb183&origin_path=%2F>`_ 

url
~~~

We provide access to the full CAMELS data via a simple uniform resource locator (url). We do not recommend downloading large amounts of data through this system, as can be slow and unstable. However, for small or individual files it may be convenient.

``!!!!!must update!!!!!``
.. `URL link <https://users.flatironinstitute.org/~fvillaescusa/priv/f3Mq1fwFYReuAdJTb8xNxa43Jb48L/PUBLIC_RELEASE>`_


FlatHUB
~~~~~~~

``!!!!!is this true???!!!!!``
FlatHUB is a platform that allows users to explore and compare data from different simulations by browsing and filtering the data, making simple preview plots, and downloading sub-samples of the data. We provide access to the SC-SAM galaxy catalogs through this platform.

``!!!!!must update!!!!!``
.. `Link to FlatHUB <http://flathub.flatironinstitute.org/group/cosmo-hydro/camels/>`_


Rusty
~~~~~

Users with an account on the Flatiron Institute Rusty cluster, can find all CAMELS-SAM data in ``/mnt/ceph/users/camels/PUBLIC_RELEASE``, within the relevant folders as 'SCSAM'. For example, the ``ConsistentTrees`` merger tree files can be found in ``/mnt/ceph/users/camels/PUBLIC_RELEASE/Rockstar/SCSAM/LH_??/trees/tree_?_?_?.dat``.



​
