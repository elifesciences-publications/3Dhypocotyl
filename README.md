<h2>Introduction</h2>

The files provided via this project are used to run mechanical growth simulations of 3D hypocotyls
using the <a href="https://www.gitlab.com/slcu/teamhj/tissue">Tissue</a> simulation software,
and can be used to produce the computational model output in Bou Daher et al (2018). 
The simulations include cell wall mechanics where individual walls can have specified 
(asymmetric or anisotropic) elastisities; pressure and anisotropic forces can be applied,
and growth is modelled using a Lockhart type of growth rule.

<h3>Reference</h3>

Bou Daher F, Chen Y, Bozorg B, Heywood Clough J, Jönsson H, Braybrook SA (2018)
Anisotropic growth is achieved through the additive mechanical effect of material 
anisotropy and elastic asymmetry
<a href="https://www.biorxiv.org/content/early/2018/05/07/316364"><i>bioRxiv</i></a>.

<h3>Files</h3>

We have divided the files into two directories, each containing the files needed to generate 
the results presented in Fig4 and FigS4, respectively. In the directories files of 
the types described below can be found.

* <tt>README.txt</tt> files contain instructions on how to run simulations to generate
the individual results.

* <tt>*.model</tt> files contain all the parameter values for the mechanical and 
growth rules.  

* <tt>*.init</tt> files contain the initial geometry description, including 
flags for defining different type of walls to be given special mechanical properties.

*  <tt>*.rk</tt> files contain instructions to the solver on e.g. time of simulation 
and output format.

* <tt>hypocotyl3D.pvsm</tt> files has information for 3D visualisation of the output
structure in <a href="http://www.paraview.org">Paraview</a> (see Output section below).

* <tt>*.data</tt> files hold data, such as length, for plotting different graphs.

* <tt>*.gnplt</tt> files have instructions for plotting the graphs using 
<a href="http://www.gnuplot.info/">Gnuplot</a>. 


<h3>Solver</h3>

All simulations have been performed using the in-house developed c++ solver 
<a href="https://www.gitlab.com/slcu/teamhj/tissue">Tissue</a>. Installation and compiling 
instructions can be found via the <a href="https://gitlab.com/slcu/teamHJ/tissue/wikis/Installation">
wiki page</a>.

In short, a simulation is run by providing a set of .model, .init, and .rk files at terminal:

```
TISSUE/bin/solver example.model example.init example.rk
```
where <tt>TISSUE</tt> is the full path to the directory where tissue was downloaded 
and it is assumed you are in the directory where the model/init/rk files are stored.
This will generate a <tt>vtk</tt> directory where output files are stored. A descrption 
on what the individual reations/rules defined in the *.model file does is provided 
in the Tissue Documentation. This is also true for the format of the *.init and *.rk files.

<h3>Outputs</h3>

Hypocotyl geometries are stored as <a href="https://www.vtk.org">vtk</a> files (in the vtk directory) during the simulation
and the user can specify how often a 'snapshot' should be taken (in the *.rk files). 
These can for example be visualised using <a
href="http://www.paraview.org">Paraview</a> (see example Figure) 
Settings for the visualisations are found in the files *.* that can be loaded into 
paraview by <tt>file/load...</tt>.

<center><img width=500 src="paraview_example.png"></center>

<h3>Contacts</h3>

Behruz Bozorg (behruz@thep.lu.se)<br>
Henrik Jönsson (henrik.jonsson@slcu.cam.ac.uk)<br>
Siobhan Braybrook (siobhanb@ucla.edu)

