# Mesh_Morphing_for_Geophysics

This repository accompanies the paper "Quantifying the influence of fault geometry via mesh morphing with applications to dynamic rupture and thermal models of subduction", by Gabrielle M. Hobson $^1$, Dave A. May $^1$, and Alice-Agnes Gabriel $^{1,2}$. 

$^1$ Scripps Institution of Oceanography, University of California San Diego

$^2$ Ludwig-Maximilians-Universität München

### Installation and Environment

This github repository can be cloned on the command line like so:

`git clone https://github.com/gabriellemhobson/Mesh_Morphing_for_Geophysics`

After navigating into the main directory `Mesh_Morphing_for_Geophysics`, the `environment.yaml` file can be used to create a conda environment:

`conda env create -f environment.yaml`

This will create a conda environment named `meshmorphing4geo`.

The mesh generation process requires the freely available software GMSH, version 4.10 and the ability to run GMSH commands on the command line. 
This may require adding the GMSH app to your PATH variable like so:

`export PATH=:$PATH:/path/to/Gmsh.app`

To verify that GMSH commands work on the command line, enter the following line:

`gmsh --info`

To be able to load modules from within a different directory, we must add the path to our Python path environment variable. While in the main directory `Mesh_Morphing_for_Geophysics`, run:

export PYTHONPATH=$PYTHONPATH:$PWD

### Structure

The modules used to perform morphing are in the directory `modules`. Currently there are two modules, one tailored to subduction thermal model examples, and the other tailored to the TPV13 dynamic rupture example. 

The `toy_examples` directory currently contains a simple example that morphs a plane embedded in a 2D square box, changing the angle between the plane and the vertical. The code generates plots to visualize the coarse reference mesh, the displacement field, and the morphed mesh. 

The `subduction_thermal_examples` directory contains two examples: `global_curvature` demonstrates morphing of the slab interface geometry in a range representative of the global variation, where the slab interface is represented by a parabolic expression; `slab2_uncertainty` demonstrates morphing of the slab interface geometry within the range of uncertainty reported by Slab2 (Hayes et al., 2018). 

The `DR_examples` directory contains the `tpv13` example, which This example demonstrates morphing of an embedded fault so that it has varying fault dip. The reference mesh is that of the TPV13-3D SCEC benchmark, which is implemented in SeisSol.

Each of the example directories has a README file with more details on the setup and procedure of running the example. 