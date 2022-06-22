.. _dataproducts:

*******************
Data Products
*******************


Halo catalogs and Merger Trees
============================

The folder ``Rockstar/CAMELS-SAM/LH_???/Rockstar`` contains the CAMELS-SAM Rockstar halo catalogs for each simulation. The format of the catalogs is the default of the code, and we refer the user to the `Rockstar documentation <https://bitbucket.org/gfcstanford/rockstar/src/main/>`_ for further details. Due to storage limitations, we have kept just the `out_??.list` files and all ``ROCKSTAR`` configuration files that were used to run it. Additional files are stored on long-term magnetic tape; please contact the CAMELS team to discuss accessing them.

We also release the merger trees constructed through ``ConsistentTrees``, `tree_?_?_?.dat' for each subvolume created in the simulation within ``Rockstar/CAMELS-SAM/LH_???/ConsistentTrees``. We refer the reader to the `consistent trees documentation <https://bitbucket.org/pbehroozi/consistent-trees/src/main/>`_ for details on the format of the files. The SC-SAM can be rerun with new parameters upon these trees.



The Santa Cruz SAM for galaxy formation
===================

We use the Santa Cruz semi-analytic model (SAM) for galaxy formation (Somerville et al. 2008, 2015, 2021) to robustly populate our large N-body simulations with galaxies. SAMs can be thought of an alternative to full hydrodynamic simulations, which apply simplified empirical recipes for physical processes of galaxy formation and evolution within dark matter halo 'merger trees' (e.g. from ``ConsistentTrees`` our of ``ROCKSTAR``). Like numerical simulations, SAMs include free parameters that are calibrated to galaxy observations (e.g. Yung et al. 2019 for the local universe). The SC-SAM pipeline used in this work is nearly identical to that applied to IllustrisTNG300 in Gabrielpillai et al. (2021); see their work for complete justification and verification for the fiducial set up.


.. raw:: html

   <details>
   <summary> Click to expand/collapse this table describing the SC-SAM *galaxy* outputs at each redshift </summary>

+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| Field                    | Shape  | Units    | Description                                                                     |
+==========================+========+==========+=================================================================================+
| GalpropBirthHaloID       | N      | --       | ID of host halo from Haloprop                                                   |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropHaloIndex         | N      | --       | Index of host halo in Haloprop (recommend usage: when loading whole subvolumes) |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropHaloIndex_Snapshot| N      | --       | Index of host halo in Haloprop (recommended usage: when loading snapshots)      |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMBH               | N      | 10^9 M☉  | Black hole mass                                                                 |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMH2               | N      | 10^9 M☉  | Molecular hydrogen cold gas mass                                                |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMHI               | N      | 10^9 M☉  | Neutral hydrogen cold gas mass                                                  |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMHII              | N      | 10^9 M☉  | Singly ionized hydrogen cold gas mass                                           |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMaccdot           | N      | M☉ / yr  | accretion rate onto black hole                                                  |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMaccdot_radio     | N      | M☉ / yr  | accretion rate onto black hole in radio mode                                    |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMbulge            | N      | 10^9 M☉  | Stellar mass of the bulge                                                       |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMcold             | N      | 10^9 M☉  | Total cold gas mass                                                             |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMvir              | N      | 10^9 M☉  | Total dark matter halo mass                                                     |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMstar             | N      | 10^9 M☉  | Total stellar mass                                                              |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMstar_merge       | N      | 10^9 M☉  | Stellar mass entering via mergers                                               |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMstrip            | N      | 10^9 M☉  | Stripped mass of DM sub-halo |                                                  |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropMu_merger         | N      | --       | mass ratio of last merger (see S08)                                             |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropOutflowRate_Mass  | N      | M☉ / yr  | rate of outflowing gas from ISM                                                 |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropOutflowRate_Metal | N      | M☉ / yr  | rate of outflowing metals from ISM                                              |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropPos               | N, 3   | cMpc     | x, y, and z coordinates                                                         |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRbulge            | N      | kpc      | 3D half-mass Radius of bulge                                                    |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRdisk             | N      | kpc      | 3D half-mass Radius of disk                                                     |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRedshift          | N      | --       | redshift                                                                        |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRfric             | N      | Mpc      | distance from halo center                                                       |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRhalo             | N      | Mpc      | halo virial radius                                                              |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropRootHaloID        | N      | --       | ID of root halo at z = 0 from Haloprop                                          |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSatType           | N      | --       | 0 = central                                                                     |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSfr               | N      | M☉ / yr  | instantaneous SFR                                                               |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSfrave100myr      | N      | M☉ / yr  | SFR averaged over 100 Myr                                                       |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSfrave1gyr        | N      | M☉ / yr  | SFR averaged over 1 Gyr                                                         |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSfrave20myr       | N      | M☉ / yr  | SFR averaged over 20 Myr                                                        |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropSigmaBulge        | N      |  km / s  | velocity dispersion of bulge                                                    |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropTmerger           | N      | Gyr      | time since last merger                                                          |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropTmerger_major     | N      | Gyr      | time since last major merger                                                    |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropTsat              | N      | Gyr      | time since galaxy became a satellite in this halo                               |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropVdisk             | N      | km / s   | rotation velocity of disk                                                       |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropVel               | N, 3   | km / s   | x, y, and z components of velocity                                              |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropZcold             | N      | Z☉ * M☉  | metal mass in cold gas                                                          |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+
| GalpropZstar             | N      | Z☉ * M☉  | metal mass in stars                                                             |
+--------------------------+--------+----------+---------------------------------------------------------------------------------+


.. raw:: html
   </details>
   <br />

Note: the version of the SC-SAM used to first run CAMELS-SAM did not save all SF histories (due to our particular needs and priorities), so the averaged SFR properties are currently all zero. We will update this text if the SC-SAM is rerun for any subset of the simulations to update this.

.. raw:: html

   <details>
   <summary> Click to expand/collapse this table describing the SC-SAM *halo* outputs at each redshift </summary>

+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| Field                            | Shape  | Units         | Description                                                                     |
+==================================+========+===============+=================================================================================+
| HalopropC_nfw                    | N      | --            | NFW concentration parameter for DM halo                                         |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropHaloID                   | N      | --            | Halo ID given by Consistent-Trees                                               |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropIndex                    | N      | --            | Index of halo in the file (recommended usage: when loading whole subvolumes)    |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropIndex_Snapshot           | N      | --            | Index of halo in file (recommended usage: when loading snapshots)               |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMaccdot_metal            | N      | M☉ / Z☉ / yr  | accretion rate of metals into the halo                                          |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMaccdot_pristine         | N      | M☉ / yr       | accretion rate of pristine gas into the halo                                    |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMaccdot_radio            | N      | M☉ / yr       | accretion rate onto the BH in radio mode                                        |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMaccdot_reaccreate       | N      | M☉ / yr       | accretion rate of “recycled” gas                                                |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMaccdot_reaccreate_metal | N      | M☉ / Z☉ / yr  | accretion rate of “recycled” metals                                             |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMass_ejected             | N      | 10^9 M☉       | total gas mass in “ejected” reservoir                                           |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMcooldot                 | N      | 10^9 M☉ / yr  | rate of gas cooling/accretion from halo into ISM                                |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMdot_eject               | N      | M☉ / yr       | rate of ejection of gas from halo                                               |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMdot_eject_metal         | N      | M☉ / Z☉ / yr  | rate of ejection of metals from halo                                            |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMetal_eject              | N      | Z☉ / yr       | total mass of metals in “ejected” reservoir                                     |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMhot                     | N      | 10^9 M☉       | mass of hot (CGM) gas in halo   						      |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMstar_diffuse            | N      | 10^9 M☉       | mass of stars in a diffuse stellar halo (from disrupted satellites)             |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropMvir                     | N      | 10^9 M☉       | halo virial mass                                                                |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropRedshift                 | N      | --            | redshift                                                                        |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropRockstarHaloID           | N      | --            | Halo ID from the Rockstar run                                                   |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropRootHaloID               | N      | --            | Halo ID of the root halo for this merger tree                                   |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropSnapNum                  | N      | --            | snapshot file number                                                            |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropSpin                     | N      | N             | spin of DM halo                                                                 |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropSubfindID_DMO            | N      | --            | Subfind index in TNG DMO simulation of bijective match                          |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropSubfindID_FP             | N      | --            | Subfind index in TNG FP simulation of bijective match                           |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+
| HalopropZhot                     | N      | 10^9 M☉ / Z☉  | metal mass in hot halo (CGM)                                                    |
+----------------------------------+--------+---------------+---------------------------------------------------------------------------------+


.. raw:: html

   </details>
   <br />



Identifying each simulation's parameters
==========

Within each of these data product directories and within each simulation's folder exists the file ``CosmoAstro_params.txt``. This file includes the exact values of the cosmological and astrophysical parameters that created each CAMELS-SAM N-body simulation and halo/galaxy catalogs. There are six numbers listed, which are:

#. | :math:`\Omega_{M}`
   | The true value of :math:`\Omega_{M}` of the given simulation.

#. | :math:`\sigma_{8}`
   | The true value of :math:`\sigma_{8}` of the given simulation.

#. | :math:`A_{\rm SN1} \times 1.7` for SC-SAM
   | The value given to the SC-SAM for the :math:`\epsilon_{\rm SN0}` free parameter, which is equal to the prefactor :math:`A_{\rm SN1}` *times* 1.7 (the best-fit fiducial value for this SC-SAM free amplitude parameter for local observations.) :math:`A_{\rm SN1}` was generated log-uniformly between 0.25 and 4.0.
   
#. | :math:`A_{\rm SN2} + 3.0` for SC-SAM
   | The value given to the SC-SAM for the :math:`\alpha_{\rm rh}` free parameter, which is equal to the prefactor :math:`A_{\rm SN2}` *plus* 3.0 (the best-fit fiducial value for this SC-SAM free power law slope for local observations.) :math:`A_{\rm SN2}` was generated uniformly between -2.0 and 2.0.

#. | :math:`A_{\rm AGN} \times 0.002` for SC-SAM
   | The value given to the SC-SAM for the :math:`\kappa_{\rm radio}` free parameter, which is equal to the prefactor :math:`A_{\rm AGN}` *times* 0.002 (the best-fit fiducial value for this SC-SAM free amplitude parameter for local observations.) :math:`A_{\rm AGN}` was generated log-uniformly between 0.25 and 4.0.
   
#. | 0.005
   | This is an unused parameter in CAMELS-SAM for :math:`\epsilon_{\rm wind, QSO}` from the SC-SAM. This was originally meant to be the analogous to :math:`A_{\rm AGN2}` in CAMELS, but the iteration of the SC-SAM used in this work showed little to no response to varying this parameter beyond its fiducial value. 
