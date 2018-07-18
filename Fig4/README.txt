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

These can be loaded into Paraview for visualisation [File/Load and select the file(s)
followed by pressing the 'apply' button], and 3Dhypocotyl.pvsm can be used to load
visualisation settings used in the figure into Paraview [File/...].

Note, that new simulations will again save the results in the vtk directory, so if
you would like to save multiple output results, you need to either move the vtk
directory between simulations [e.g. >mv vtk symmetricOutput],
or run Tissue from different directories.

(A.ii) To generate the right panel with asymmetric (100x) walls, run:

> TISSUE/bin/simulator asymmetric.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above.

---------------------------------------------------------------------- 
Figure 4B:
----------------------------------------------------------------------

(B.i) To generate the left panel with symmetric walls and anisotropic Forces with only elastic
deformation, run:

> TISSUE/bin/simulator -init_output_file symmetricAnisoF.init symmetricAnisoF.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above.
Note, the '-init_output_file' results in the final state being saved in the file symmetricAnisoF.init,
which will be used in step (B.iii) below.

(B.ii) To generate the sencond from left panel with asymmetric walls and anisotropic Forces
with only elastic deformation, run:

> TISSUE/bin/simulator -init_output_file asymmetricAnisoF.init asymmetricAnisoF.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above. In addition,
the file asymmetricAnisoF.init to be used in step (B.iv) below is created.

(B.iii) To generate the second from right panel with symmetric walls and anisotropic Forces with growth, run:

> TISSUE/bin/simulator symmetricAnisoFGrowth.model symmetricAnisoF.init growth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above. Note,
the symmetricAnisoF.init file is needed and is created in step (B.i) above.

(B.iv) To generate the right panel with asymmetric walls and anisotropic Forces with growth, run:

> TISSUE/bin/simulator asymmetricAnisoFGrowth.model asymmetricAnisoF.init growth.rk

Paraview can be used to visualise the data generated in the 'vtk' directory as described above. Note,
the asymmetricAnisoF.init file is needed and is created in step (B.ii) above.

---------------------------------------------------------------------- 
Figure 4B:
----------------------------------------------------------------------

Length information can be extracted from the simulations above. For simplicity, we have saved the data in files
symmetricLength.data and asymmetricLength.data that can be used for plotting the graph. To do this using Gnuplot:

> gnuplot length.gnplt

which will generate a file length.eps (without some of the labels).
