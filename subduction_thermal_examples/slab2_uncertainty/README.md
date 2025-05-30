# Subduction Example: Varying the Depth of the Subduction Interface Within the Reported Uncertainty Range from Slab2

### Setup 

This example demonstrates morphing of the slab interface geometry within the range of uncertainty reported by Slab2. The geometric parameter of interest is $\beta$, which is the fraction the Slab2 depth uncertainty by which to shift the profile depth.
So for a slab interface profile with coordinates $(x_B, y_B)$ and uncertainty values $(x_B, U_B)$, the target interface coordinates will be $(x_B, y_B + \beta U_B)$

The reference mesh is provided in the `cascadia` directory. This mesh corresponds to a profile taken of the Slab2 geometry and the reported uncertainty along the profile is stored in the file `profile_unc.csv`. 

### Procedure

To run this example, execute: 

`python3 apply_mesh_morphing.py`

This script defines target points in the range $\beta \in [-1.1, 1.1]$ for mesh morphing, which are written to the file `y_x_merged.csv`. 
Those points are passed to the class `Mesh_Morph` from the module `mesh_morphing_subduction.py` in the `utils` directory, along with the reference mesh. 
Mesh morphing is applied for values of $\beta \in [-1.0, 1.0]$, and morphed meshes are written to the directory `meshes_morphed`. 
The mesh quality is measured and plotted in bar plots for three different metrics. 