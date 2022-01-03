.. _dataproducts:

*******************
Halo catalogs and merger trees
*******************

The folder ``Rockstar/CAMELS-SAM/`` contains the CAMELS-SAM Rockstar halo catalogs for each simulation. The format of the catalogs is the default of the code, and we refer the user to the `Rockstar documentation <https://bitbucket.org/gfcstanford/rockstar/src/main/>`_ for further details. Due to storage limitations, we have kept just the `out_??.list` files and all ``ROCKSTAR`` configuration files that were used to run it. Additional files are stored on long-term magnetic tape; please contact the CAMELS team to discuss accessing them.

We also release the merger trees constructed through ``ConsistentTrees``, `tree_?_?_?.dat' for each subvolume created in the simulation within ``Rockstar/CAMELS-SAM/LH_???/trees/``. We refer the reader to the `consistent trees documentation <https://bitbucket.org/pbehroozi/consistent-trees/src/main/>`_ for details on the format of the files. The SC-SAM can be rerun with new parameters upon these trees.
