Instructions to generate results presented in Figure S4 in

Bou Daher F, Chen Y, Bozorg B, Heywood Clough J, Jönsson H, Braybrook SA (2018)
Anisotropic growth is achieved through the additive mechanical effect of material 
anisotropy and elastic asymmetry

These instructions assume you have installed the Tissue software in file directory TISSUE.

'>' indicates that the command is to be executed in a terminal window (without the >), e.g.
> command

For more information, see: https://gitlab.com/slcu/teamHJ/behruz/3Dhypocotyl

---------------------------------------------------------------------- 
Figure S4A:
----------------------------------------------------------------------

(A.i) To generate the top left panel with symmetric walls and
anisotropic Force with only elastic deformation, run:

> TISSUE/bin/simulator -init_output symmetricAnisoF.init -init_output_format centerTriTissue symmetricAnisoF.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk'
directory as described for Fig 4. Note, the '-init_output'
results in the final state being saved in the file
symmetricAnisoW.init, which will be used in step (A.iii) below.

(A.ii) To generate the top right panel with asymmetric walls and
anisotropic Force with only elastic deformation, run:

> TISSUE/bin/simulator -init_output asymmetricAnisoF.init -init_output_format centerTriTissue asymmetricAnisoF.model 3Dhypocotyl.init nogrowth.rk

Paraview can be used to visualise the data generated in the 'vtk'
directory as described for Fig4. In addition, the file
asymmetricAnisoW.init to be used in step (A.iv) below is created.

(A.iii) To generate the middle left panel with symmetric walls and
anisotropic Force with growth, run:

> TISSUE/bin/simulator -centerTri_init symmetricAnisoFGrowth.model symmetricAnisoF.init growth.rk 1>symmetricAnisoF.data

Paraview can be used to visualise the data generated in the 'vtk'
directory as described for Fig4. Note,
the symmetricAnisoW.init file is needed and is created in step (A.i) above.

(A.iv) To generate the middle right panel with asymmetric walls and
anisotropic Force with growth, run:

> TISSUE/bin/simulator -centerTri_init asymmetricAnisoFGrowth.model asymmetricAnisoF.init growth.rk 1>asymmetricAnisoF.data

Paraview can be used to visualise the data generated in the 'vtk'
directory as described for Fig 4. Note,
the asymmetricAnisoF.init file is needed and is created in step (A.ii) above.

(A.v) Bottom panel. see S4C.

---------------------------------------------------------------------- 
Figure S4B:
----------------------------------------------------------------------

Changes to the length when changing parameters can be extracted by
simulating the model/init files provided in the sensitivityF and
sensitivityW directories, respectively. For simplicity, we provide the
data in sensitivityF.data and sensitivityW.data for plotting. To plot
these data using Gnuplot:

> gnuplot sensitivity.gnplt

which will generate two files, sensitivityF.eps and sensitivityW.eps.

---------------------------------------------------------------------- 
Figure S4C:
----------------------------------------------------------------------

Length and strain anisotropy information are generated in A.iii and A.iv from 
the simulations and stored in the files symmetricAnisoF.data and 
asymmetricAnisoF.data. First and second columns are the length of the template 
as well as strain anisotropy averaged over the outer cell faces of epidermis. 
These can be used for plotting the graph in S4C and bottom panel in S4A. 
To do this using Gnuplot, for bottom panel in S4A:

> gnuplot length.gnplt

and for S4C:

> gnuplot aniso.gnplt


which will generate file length.eps and aniso.eps (without some of the labels).

