# What structural properties tell us about halo age

## Description 
This project aims at studying, understanding and predicting relations and correlations between the age of Dark Matter
Halos and their Structural properties, as well how structural properties are influenced by cosmology. 
The science of this project is described in detail in the fourth chapter of my PhD thesis 
: https://uwspace.uwaterloo.ca/handle/10012/19584

## Requirements 
All codes are Jupyter notebooks. They all use simulations, and will require the Simulation class 
found here : https://github.com/amourayuba/Simulations 
As well as cosmo_parameters module found here : https://github.com/amourayuba/Halo_Analytical_Calculations. 
The codes will also require Numpy, Pandas, Astropy, Scipy, Matplotlib and scikit-learn.
The data requirement will be highlighted for each subprojects. They can all be generated through the Simulation class. 


## Sub-projects 
### Age_PCA 
#### Description
Performs a Principal Component Analysis on halo age properties to understand the dimensionality of it. 
MAH_PCA is a PCA on the Mass Accretion History only. While age_properties_PCA uses different formation history 
properties. 
#### Data requirements
The PCA is performed on the Mass Accretion Histories. These can be generated, given a simulation object 
sim1 through the sim1.make_mah(), or if they already have been generated, through sim1.get_mah(). Refer to the
Simulation class for the format of the MAH data, as well as the default folder. 

It also uses age data which can be generated through sim1.make_zxs() method, by default this method will save the 
data. This will produce 4 types of age data: 
"zx" : redshift at which the halo had x/100 of its z=z_0 mass. 
"zmm" : redshift of last major merger
"mofz" : mass fraction at z 
"oth" : table including McBride parameters, as well as the Mass of Index of the halo. 

If the data is already saved in the proper folder, one can get them through sim1.get_agedata(z, atype)
where "atype" is one of the four data types above.

#### Outputs 
The notebooks produce different plots and figures that are explained in Chapter 4 of my PhD thesis. 

### Structure_vs_Age
#### Description
Performs analysis of the link between halo age and structural properties. As well as a PCA on structural properties and 
age. 
#### Data Requirements 
This will require .AHF_halos files for each considered simulation in the proper folder. They will be read 
through the medthod simulation.read_halos(snapshot=snap). 

Age data are also necessary. See above for the description on how to make them or get them. 

2D and 3D structural property files are needed. These can be made using the codes available 
in https://github.com/amourayuba/Halo_structure, and specifically in structural_properties. 
The description of each structural property is in Chapter 4 of my PhD thesis. The details of the format of the 
files are in the project repository above. 

The notebooks generate tables combining specific age properties and 2D/3D structural properties. But these can be
made and saved through the method make_structure_data() of the simulation class. 
If this is already done, then one only needs to load the data files *data_3d*.dat and *data_2d*.dat
that will be located in the appropriate simulation directory.

#### Outputs and Results 
A selection of the figures are in Chapter 4 of the PhD thesis. The first type of figures that 
are generated are of type 2D density plots of structural_proprty = f(age_property) for age properties z50, z10, zmm30 
and $\gamma$ - $\beta$. 
These were selected given the results found in age_PCA above. All structural properties are considered.

Figures including median and scatter relations are also included.

Scatter plots with different configurations of age and structural properties are also included. 

The second type of result is a PCA on structural properties and age combined. 


### Structure_vs_Cosmology
#### Description
This project compares structural properties, aggregated over many halos, for different cosmologies. 

#### Data Requirements 
This will require .AHF_halos files for each considered simulation in the proper folder. They will be read 
through the medthod simulation.read_halos(snapshot=snap). 

It uses the method get_2d{3d}prop(property) of the Simulation class. That method needs the 2D/3D property files 
generated through the structural_properties routines of https://github.com/amourayuba/Halo_structure. This method gets 
the values of "property" (e.g. com_offset, concentration ...) for all halos. 

#### Outputs and Results 
*) Distributions of sturctural properties for different cosmologies 
*) Medians of different structural properties as a function of cosmology 
*) Interpolations plots of structural properties in the $\Omega_m$-$\sigma_8$ plane. 

