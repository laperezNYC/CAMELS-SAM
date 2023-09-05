==========
Using the SC-SAM catalogs
==========

The Santa Cruz SAM galaxy and halo catalogs are stored as text files with comma-separated values, as *galprop_0-99.dat* and *haloprop_0-99.dat* within all the SC-SAM-generated subvolumes. These files contain information about the halo and galaxies from all snapshots of a given simulation.


We give here an example for how to open these files and pull out galaxy or halo data fulfilling certain conditions. This runs in ``python3``, and most crucically requires ``pandas``, ``subprocess``, and ``numpy``. As the most relevant example for the original creators, this is how L.A. Perez pulled out information at a single redshift:

.. code-block:: python

  def ProcessSAMdat_single_redshift(path_to_SAM, Nsubvols, sought_z, fieldswanted, gal_or_halo):
      #NOTE: these ?_colnames are the columns, in order, of the data in the original .dat files. You can give fieldswanted in nearly any order, but the order that the columns will take in the final array will depend on the fields' order in these lists. NOTE: if you care about halo_index, birthhaloID, or roothaloID, redshift will NOT be in the 0th index; update the line below that assumes that!
      g_colnames = ['halo_index', 'birthhaloid', 'roothaloid', 'redshift', 'sat_type',
                    'mhalo', 'm_strip', 'rhalo', 'mstar', 'mbulge', 'mstar_merge', 'v_disk',
                    'sigma_bulge', 'r_disk', 'r_bulge', 'mcold', 'mHI', 'mH2', 'mHII', 'Metal_star',
                    "Metal_cold", 'sfr', 'sfrave20myr', 'sfrave100myr', 'sfrave1gyr',
                    'mass_outflow_rate', 'metal_outflow_rate', 'mBH', 'maccdot', 'maccdot_radio',
                    'tmerge', 'tmajmerge', 'mu_merge', 't_sat', 'r_fric', 'x_position',
                    'y_position', 'z_position', 'vx', 'vy', 'vz']
      h_colnames = ['halo_index', 'halo_id', 'roothaloid', 'orig_halo_ID', 'redshift', 'm_vir', 'c_nfw',
                    'spin', 'm_hot', 'mstar_diffuse', 'mass_ejected', 'mcooldot',
                    'maccdot_pristine', 'maccdot_reaccrete', 'maccdot_metal_reaccrete',
                    'maccdot_metal', 'mdot_eject', 'mdot_metal_eject', 'maccdot_radio',
                    'Metal_hot', 'Metal_ejected', 'snap_num']
      g_header_rows = []
      for i in range(0, len(g_colnames)):
          g_header_rows.append(i)
      h_header_rows = []
      for i in range(0, len(h_colnames)):
          h_header_rows.append(i)

      input_path=path_to_SAM

      if type(fieldswanted) == list:
          print(type(fieldswanted))
      else:
          return "Fieldswanted should be a list with the fields you want as strings!"

      All_halos=np.zeros((1,len(fieldswanted)))
      if gal_or_halo=="gal":
          checknums=0
          for x_i in np.arange(0,Nsubvols,1):
              for x_j in np.arange(0,Nsubvols,1):
                  for x_k in np.arange(0,Nsubvols,1):
                      galprop = pd.read_csv('{}/{}_{}_{}/galprop_0-99.dat'.format(input_path, x_i, x_j, x_k),
                                            delimiter=' ', skiprows=g_header_rows, names=g_colnames)
                      # print('galprop read for ',x_i, x_j, x_k,' shape:', galprop.shape)
                      current_galprops=galprop[fieldswanted[:]].to_numpy()
                      print('For subvolume ',x_i,x_j,x_k, current_galprops.shape)
                      unique_redshifts=set(current_galprops[:,0]) #update this if redshift will NOT be in the 0th column; see note above
                      unique_redshifts = np.array(sorted(unique_redshifts))
                      # print(unique_redshifts)
                      idx = (np.abs(unique_redshifts - sought_z)).argmin()
                      current_galprops_z=current_galprops[np.where(current_galprops[:,0][:]==unique_redshifts[idx])[0],:]
                      # print(current_galprops_z.shape)
                      checknums=checknums+len(current_galprops_z)
                      All_halos=np.concatenate((All_halos,current_galprops_z))
          print(All_halos.shape, checknums)
          return All_halos
      elif gal_or_halo=="halo":
          checknums2=0
          for x_i in np.arange(0,Nsubvols,1):
              for x_j in np.arange(0,Nsubvols,1):
                  for x_k in np.arange(0,Nsubvols,1):
                      haloprop = pd.read_csv('{}/{}_{}_{}/haloprop_0-99.dat'.format(input_path, x_i, x_j, x_k),
                                             delimiter=' ', skiprows=h_header_rows, names=h_colnames)
                      current_haloprops=haloprop[fieldswanted[:]].to_numpy()
                      print('For subvolume ',x_i,x_j,x_k, current_haloprops.shape)
                      unique_redshifts=set(current_haloprops[:,0])
                      unique_redshifts = np.array(sorted(unique_redshifts))
                      idx = (np.abs(unique_redshifts - sought_z)).argmin()
                      current_haloprops_z=current_haloprops[np.where(current_haloprops[:,0][:]==unique_redshifts[idx])[0],:]
                      # print(current_haloprops_z.shape)
                      checknums2=checknums2+len(current_haloprops_z)
                      All_halos=np.concatenate((All_halos,current_haloprops_z))
          print(All_halos.shape, checknums2)
          return All_halos[1:,:]
      else:
          print("gal_or_halo need to be a string, either 'gal' or 'halo', to get galprop or haloprop respectively. Make sure the fields you want are actually reflected!")
          print("Column names of galprop file: ", g_colnames)
          print("Column names of haloprop file: ", h_colnames)
          return All_halos

Lines commented out are to confirm the files are being read correctly; *checknums* and *All_halos.shape* should be the same length, if all (sub)halos were correctly accessed at each redshift. If your fieldswanted includes 'halo_index', 'birthhaloid', or 'roothaloid', update "unique_redshifts=set(current_galprops[:,0])" to reflect that redshfit won't be the first column.

Due to know the ``.dat`` format is organized, one must specify exactly which properties should be collected as the ``fieldswanted`` string. See :doc:`dataproducts` for the complete list of available properties for galaxies (*galprop*) and halos (*haloprop*). Additionally, the number of subvolumes is important, and corresponds to how the SC-SAM automatically splits up large volumes for processing (either 1 or 8 for CAMELS-SAM). For example, to access galaxy data at *z=0, 0.1, 0.5, 1.0* for CAMELS-SAM simulations LH0 through LH5:


.. code-block:: python

  import numpy as np
  import pandas as pd
  import os
  import subprocess
  import math

  galprop_fields = ['redshift', 'sfr', 'mstar', 'mhalo', 'Metal_star', 'sat_type', 'x_position', 'y_position', 'z_position']
  haloprop_fields = ['redshift','snap_num','spin','m_vir']
  redshifts=[0.0, 0.1, 0.5, 1.0]

  StartSim=0
  EndSim=5

  for i in np.arange(StartSim,EndSim,1):

      os.chdir('/mnt/ceph/users/camels/Sims/SCSAM/cLH'+str(i)) #!!!!!UPDATE LOCATIONS!!!!!!!
      os.system('ls')
      totaldirs=(subprocess.check_output('''ls -l sc-sam/ | grep -c ^d''', shell=True,text=True))
      totaldirs=np.float64(totaldirs)
      Nsubvol=np.int64(totaldirs**(1./3.))

      for ZS in np.arange(0,len(redshifts),1):
          Z=redshifts[ZS]
          CurrentSAMdat= ProcessSAMdat_single_redshift('/mnt/ceph/users/camels/Sims/SCSAM/cLH'+str(i)+'/sc-sam', Nsubvol, Z, galprop_fields, 'gal')
          print('CAMELS-SAM simulation LH',i,' at redshift ', Z, ' has this many galaxies: ', CurrentSAMdat.shape)
          '''This output is a numpy array that can be manipulated in whatever way you like! Columns will be galprop_fields as listed above, each row is a SAM galaxy at redshift Z (or more exactly, whatever Nbody simulation redshift is closest to what you've requested).'''


Here is a more generalized way to open the SAM files for a given set of fields, and not only at a single redshift. Many thanks to Phil Bull for writing it up and allowing me to share it with other users! 

.. code-block:: python

  import glob
  root_dir_PB=str('/mnt/ceph/users/camels/PUBLIC_RELEASE/SCSAM/LH_'+str(i)+'/sc-sam')
  #For the LH_ suite, i here will go from 0 to 999; CV_0 to CV_4 also available. For the 1P set, use CV_0 or CV_1, and note the name of the sc-sam folder.
  galprop_fields = ['redshift', 'sfr', 'mstar', 'mhalo', 'Metal_star', 'sat_type', 'x_position', 'y_position', 'z_position']
  haloprop_fields = ['redshift','snap_num','spin','m_vir']
  
  def load_catalog(fields, root_dir, halos=False, max_rows_per_subvol=None, verbose=True):
    """
    Load a catalog of galaxies or halos from the data files.
    """
    # Galaxy/halo catalog column names
    g_cols = ['halo_index', 'birthhaloid', 'roothaloid', 'redshift', 'sat_type',
                  'mhalo', 'm_strip', 'rhalo', 'mstar', 'mbulge', 'mstar_merge', 'v_disk',
                  'sigma_bulge', 'r_disk', 'r_bulge', 'mcold', 'mHI', 'mH2', 'mHII', 'Metal_star',
                  'Metal_cold', 'sfr', 'sfrave20myr', 'sfrave100myr', 'sfrave1gyr',
                  'mass_outflow_rate', 'metal_outflow_rate', 'mBH', 'maccdot', 'maccdot_radio',
                  'tmerge', 'tmajmerge', 'mu_merge', 't_sat', 'r_fric', 'x_position',
                  'y_position', 'z_position', 'vx', 'vy', 'vz']
    h_cols = ['halo_index', 'halo_id', 'roothaloid', 'orig_halo_ID', 'redshift', 'm_vir', 'c_nfw',
                  'spin', 'm_hot', 'mstar_diffuse', 'mass_ejected', 'mcooldot',
                  'maccdot_pristine', 'maccdot_reaccrete', 'maccdot_metal_reaccrete',
                  'maccdot_metal', 'mdot_eject', 'mdot_metal_eject', 'maccdot_radio',
                  'Metal_hot', 'Metal_ejected', 'snap_num']

    # Select set of columns
    cols = h_cols if halos else g_cols
    data_file = "haloprop_0-99.dat" if halos else "galprop_0-99.dat"

    # Check that requested fields are valid
    bad_fields = []
    for f in fields:
        if f not in cols:
            bad_fields.append(f)
    if len(bad_fields) > 0:
        raise KeyError("Fields %s not found. Available fields: %s" % (bad_fields, cols))

    # Determine which column indices to keep
    use_cols = [cols.index(col) for col in cols if col in fields]

    # Count subvolumes
    subvol_dirs = glob.glob("%s/*_*_*" % root_dir)

    # Loop over sub-volumes and load data
    d = []
    for i, subvol_dir in enumerate(subvol_dirs):
        if verbose:
            print("Loading subvolume %d / %d" % (i+1, len(subvol_dirs)))
        _d = np.genfromtxt(os.path.join(subvol_dir, data_file),
                           comments='#',
                           usecols=use_cols,
                           max_rows=max_rows_per_subvol)
        d.append(_d)
        if verbose:
            print("    Loaded %d rows" % _d.shape[0])
    d = np.concatenate(d)
    return d

.. Note::
The original pipeline created by Gabrielpillai et al. (2021) included a final step to organize these data into smaller ``.hdf5`` files, but once all the modifications to the pipeline were made for CAMELS-SAM, this step was no longer feasible. Therefore, we share the raw ``.dat`` data format to guarantee all properties are accessible, even if at the cost of larger files that take longer to process.'
