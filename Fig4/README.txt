Instructions to generate results presented in Figure 4 in

Bou Daher F, Chen Y, Bozorg B, Heywood Clough J, Jönsson H, Braybrook SA (2018)
Anisotropic growth is achieved through the additive mechanical effect of material 
anisotropy and elastic asymmetry

These instructions assume you have installed the Tissue software in file directory TISSUE.

'>' indicates that the command is to be executed in a terminal window (without the >), e.g.
> command

For more information, see: https://gitlab.com/slcu/teamHJ/behruz/3Dhypocotyl

---------------------------------------------------------------------- 
Figure 4A:
----------------------------------------------------------------------

(A.i) To generate the middle panel with symmetric walls, run:

> TISSUE/bin/simulator symmetric.model 3Dhypocotyl.init nogrowth.rk

This will create a directory 'vtk' in which output files are generated.

These can be loaded into Paraview for visualisation ['File/Open' and select the file(s)
followed by pressing the 'apply' button]. To help visualising the right thing,
3Dhypocotyl.pvsm can be used to load visualisation settings and files used for the 
figure into Paraview ['File/Load State...', Select the 3Dhypocotyl.pvsm file, 
Choose 'Search files under specified directory' and select the vtk directory].
Note that the above mentioned Paraview state file is generated from Paraview 4.0.1.
Loading it in other versions may result in warnings, but the geometry should still display. 

New simulations will again save the results in the vtk directory, so if
you would like to save multiple output results, you need to either move the vtk
directory between simulations [e.g. >mv vtk symmetricOutput], run
Tissue from different directories, or provide the save directory using
flag -vtk_output 'dir' when running from the terminal.

(A.ii) To generate the right panel with asymmetric (100x) walls, run:

> TISSUE/bin/simulator asymmetric.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above.

---------------------------------------------------------------------- 
Figure 4B:
----------------------------------------------------------------------

(B.i) To generate the left panel with symmetric anticlinal walls and anisotropic 
internal cell walls with only elastic deformation, run:

> TISSUE/bin/simulator -init_output symmetricAnisoW.init -init_output_format centerTriTissue symmetricAnisoW.model 3Dhypocotyl.init nogrowth.rk 

Paraview can be used to visualise the data generated in the 'vtk' directory as described above.
Note, the '-init_output' results in the final state being saved in the file symmetricAnisoW.init,
which will be used in step (B.iii) below.

(B.ii) To generate the sencond from left panel with asymmetric anticlinal walls and 
anisotropic internal cell walls with only elastic deformation, run:

> TISSUE/bin/simulator -init_output asymmetricAnisoW.init -init_output_format centerTriTissue asymmetricAnisoW.model 3Dhypocotyl.init nogrowth.rk 

Paraview can be used to visualise the data generated in the 'vtk' directory as described above. In addition,
the file asymmetricAnisoW.init to be used in step (B.iv) below is created.

(B.iii) To generate the second from right panel with symmetric anticlinal walls and anisotropic 
internal cell walls with growth, run:

> TISSUE/bin/simulator -centerTri_init symmetricAnisoWGrowth.model
  symmetricAnisoW.init growth.rk > symmetricAnisoW.data

Paraview can be used to visualise the data generated in the 'vtk'
directory as described above, and the additional output to
symmetricAnisoW.data is used to store length data (see 4C below). Note,
the symmetricAnisoW.init file is needed and is created in step (B.i) above.

(B.iv) To generate the right panel with asymmetric anticlinal walls and anisotropic internal cell walls with growth, run:

> TISSUE/bin/simulator -centerTri_init asymmetricAnisoWGrowth.model
  asymmetricAnisoW.init growth.rk > asymmetricAnisoW.data

Paraview can be used to visualise the data generated in the 'vtk'
directory as described above, and asymmetricAnisoW.data stores tissue
information (4C, below). Note,
the asymmetricAnisoW.init file is needed and is created in step (B.ii) above.

---------------------------------------------------------------------- 
Figure 4C:
----------------------------------------------------------------------

Length and strain anisotropy information are generated in (B.iii) and
(B.iv) from the simulations and stored in the files symmetricAnisoW.data
and asymmetricAnisoW.data. First and second columns are the length of the template 
as well as strain anisotropy averaged over the outer cell faces of
epidermis.
