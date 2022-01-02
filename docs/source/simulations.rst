Simulations and Data Products
=====

.. _Overview:

Overview of CAMELS-SAM
------------

The backbone of CAMELS-SAM are the 1,000+ N-body only ``AREPO`` simulations we generated across 100 snapshots between :math:`z=127` to :math:`z=0` across the broad cosmological parameter space of CAMELS. Each simulation was run through ``ROCKSTAR`` to generate halo catalogs at each snapshot, and then ``ConsistentTrees`` to generate merger trees. We feed this finely sampled merger tree history into the ``Santa Cruz semi-analytic model`` (SC-SAM, hence CAMELS-SAM) for galaxy formation. The parameters we vary across the suite are :math:`\Omega_{\rm M}`, :math:`\sigma_{8}`, :math:`\A_{\rm SN1}`, :math:`A_{\rm SN2}`, and :math:`A_{\rm AGN}`. The later 3 are pre-factors to three SC-SAM parameters controlling, respectively, the amplitude and rate of mass outflow from massive stars out of a galaxy, and the strength of the radio jet mode of AGN.

In this documentation, **simulation** indicates that there exists an N-body only simulation (i.e. snapshots) that generated the product; **simulation products** refers to the ``ROCKSTAR`` and ``ConsistentTrees`` products generated from the simulations; and **galaxy catalog** refers to the output halo and subhalo/galaxy catalogs that the Santa Cruz SAM generated. The raw simulations are enormously large (>450TB after compression), and are therefore not able to be publically released as the CAMELS snapshots are. Please contact the CAMELS team to discuss access to the CAMELS-SAM snapshots, and otherwise refer to the CAMELS data acess instructions for how to access everything else: https://camels.readthedocs.io/en/latest/data_access.html.


Simulation sets within the suite
------------

Within CAMELS-SAM, these are these three sets of products publically released:

- | **LH**. This set contains 1,000 simulation products and galaxy catalogs. Each simulation has a different value of the cosmological and astrophysical parameters, are arranged in a latin-hypercube. Each simulation has a different value of the initial random seed. This set represents the main CAMELS-SAM dataset. LH stands for Latin-Hypercube.
- | **CV**. This set contains 5 simulation products and galaxy catalogs. All the simulations share the value of the cosmological and astrophysical parameters, and they only differ in the value of their initial random seed. This set is typically used to study the effect of cosmic variance due to the simulated volume size. CV stands for Cosmic Variance.
- | **1P**. This set contains 12 galaxy catalogs. In this set, the SC-SAM was run at the smallest and largest value of each SAM parameter for two of the CV simulations (:math:`0,1`). The value of the random seed is the same in all galaxy catalogs generated atop the same CV simulation. This set can be used to study the change induced by the astrophysical SC-SAM parameters in a given quantity. 1P stands for 1-parameter at a time. (We emphasize this differs from the CAMELS 1P set, which more finely samples the parameter space and also focus on the cosmological parameters.) 


Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

