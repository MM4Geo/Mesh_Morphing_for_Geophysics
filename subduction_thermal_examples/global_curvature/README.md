# Subduction Example: Varying the Curvature of the Subduction Interface Within a Globally Representative Range

### Setup 

This example demonstrates morphing of the slab interface geometry in a range representative of the global variation, where the slab interface is represented by a parabolic expression:

$y = - \alpha x^2$ 

The geometric parameter of interest is $\alpha$, which describes the curvature of the interface. 
We aim to generate morphed meshes in the full range $\alpha \in \left[ 5 \times 10^{-4},  3.5 \times 10^{-3} \right]$, and so we select a slightly wider range, $\alpha \in \left[ 4.5 \times 10^{-4},  4 \times 10^{-3} \right]$, when defining target points to define the displacement field. 

### Procedure

The first step in this example is to run: 

`python3 generate_target_data.py`

This generates a directory called `target_data` which contains a subdirectory for each parameter value used to generate a slab interface profile data. Each subdirectory contains a y_x.csv file that stores the coordinates of the profile.

It creates a file called `training_y_x_merged.csv` which compiles all of those seperate csv files into one file with every profile in it. This is what is actually used in later steps. 

Finally, a log file called `training_log.csv` is generated which stores each parameter value, whether or not that parameter value corresponds to the reference mesh, the directory where data is stored, and the filepath to the reference mesh file if applicable. 

The next step is to run: 

`python3 apply_mesh_morphing.py`

This uses information from `training_log.csv` and `training_y_x_merged.csv` to load the reference mesh and apply mesh morphing. It loads and uses the module `MeshMorph` from `mesh_morphing_subduction.py` in the `utils` directory. The variable `tag_dict` is used to specify which curves will be morphed in both directions, in one direction only, or held in place with zero displacement. 
Samples are drawn in the $\alpha \in \left[ 5 \times 10^{-4},  3.5 \times 10^{-3} \right]$ and mesh morphing is applied. 
The morphed meshes are written to a directory called `meshes_morphed`. 
This script also generates bar plots of mesh quality for three different metrics. 

Finally, to visualize the results, you can run: 

`python3 plot_profile_variability.py`

This generates an outline plot showing the morphed meshes (solid curves) and exact profiles (points). If the agreement is not sufficiently close, more values of $\alpha$ should be used to define target points along interfaces. 