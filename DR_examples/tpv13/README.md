# Dynamic Rupture Example: Varying the Fault Dip Angle of the TPV13-3D Benchmark

### Setup 

This example demonstrates morphing of an embedded fault so that it has varying fault dip. 
The reference mesh is that of the TPV13-3D SCEC benchmark, which is implemented in SeisSol. 

https://seissol.readthedocs.io/en/latest/tpv13.html 

The files in `seissol_base_files` are adapted from SeisSol:

https://github.com/SeisSol/Examples/tree/master/tpv12_13 


https://github.com/SeisSol/Training/tree/main/tpv13 

The reference mesh is provided in the directory `reference` for completeness, though the script `apply_mesh_morphing.py` also generates the reference mesh. 

### Procedure

This example can be run like so:

`python3 apply_mesh_morphing.py`

The script above loads the file `trace_angle.csv` and uses the class `Extrude_Fault` in `extrude_and_generate_vertices.py` to generate the reference mesh and also to generate target points at different dip angles. It also defines dip values to which the fault will be morphed, and morphs the reference mesh.
The morphing is done using the `Mesh_Morph` class in `modules/mesh_morph_DR.py`; it includes a correction step so that the morphed mesh is very close to planar.  

If the variable `WRITE_EXACT` is set to True, meshes will be generated that have the same dip value as the morphed meshes; the mesh generation is time consuming, so `WRITE_EXACT` is False by default. 
These exact meshes can be used for comparison with the morphed meshes. 

It also takes modifies the files in `seissol_base_files` and writes them to the `output` subdirectory for the associated dip. The commands to convert the morphed mesh file to `.hdf5` using pumgen and to run SeisSol are written to a file called `prep_run_seissol.sh`. This is done for ease of handling filepaths; it is set up for convenience and not for parallel jobs. It should be noted that the commands in `prep_run_seissol.sh` will run each SeisSol job one at a time on one process; the number of threads is set as an environment variable by the user (see https://seissol.readthedocs.io/en/latest/environment-variables.html).