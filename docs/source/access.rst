************
Data Access
************

The available CAMELS-SAM data is stored in the Rusty cluster of the Flatiron Institute in New York City, and its data can be accessed through four different methods:

.. note::
   We gently remind users that CAMELS-SAM is large, even as we have limited ourselves to the most broadly useful data products. The *smallest* data products in CAMELS-SAM are the SC-SAM galaxy catalogs, which are on average 5GB per simulation, totaling 7TB across the suite. All available CAMELS-SAM data products total just under 40TB. 

Rusty
~~~~~

Users with an account on the Flatiron Institute Rusty cluster, can find all CAMELS-SAM data in ``/mnt/ceph/users/camels/PUBLIC_RELEASE``, within the relevant folders as 'SCSAM' or 'CAMELS-SAM'. For example, the ``ConsistentTrees`` merger tree files can be found in ``/mnt/ceph/users/camels/PUBLIC_RELEASE/Rockstar/CAMELS-SAM/LH_??/ConsistentTrees/tree_?_?_?.dat``.

Binder
~~~~~~

Binder is a system that allows users to read and manipulate data that is hosted at the Flatiron Institute through either a Jupyter notebook or a unix shell. The user can find some basic documentation `here <https://docs.simonsfoundation.org/index.php/Public:Binder>`_. All CAMELS-SAM data can be accessed, read, and manipulated through Binder. 

.. warning::

   Two important things need to be taken into account when using Binder. First, the Binder environment is ephemeral - after a few days of inactivity its contents are deleted, so one has to be vigilant about downloading any analysis results in time. Second, Binder is not designed to carry out long and heavy calculations. In this case we recommend the user to download the data and work with it locally. 

`Link to Binder <https://binder.flatironinstitute.org/~sgenel/CAMELS_PUBLIC>`_


Globus
~~~~~~~

The CAMELS-SAM data can be downloaded via globus, an online system designed to efficiently transfer large amounts of data. This is the method we recommend to transfer the data.

`Globus link <https://app.globus.org/file-manager?origin_id=58bdcd24-6590-11ec-9b60-f9dfb1abb183&origin_path=%2F>`_ 

url
~~~

We provide access to the CAMELS-SAM via a simple uniform resource locator (url). We do not recommend downloading large amounts of data through this system, as can be slow and unstable. However, for small or individual files it may be convenient.

`URL link <https://users.flatironinstitute.org/~fvillaescusa/priv/f3Mq1fwFYReuAdJTb8xNxa43Jb48L/PUBLIC_RELEASE>`_


.. note::
   CAMELS-SAM is not currently configured for access and exploration through Flathub. When is it, we will update this page (expected March 2022). This page was adapted from the CAMELS documentation: https://camels.readthedocs.io/en/latest/data_access.html.
