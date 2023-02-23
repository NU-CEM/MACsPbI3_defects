# Data and analysis code for "Steric Engineering of Point Defects in Lead Halide Perovskites"

- 📖 The paper is currently under review, but you can read the pre-print [here](https://arxiv.org/abs/2302.08412).

All of the code is distributed as [Jupyter Notebooks](https://jupyter.org/). If you are looking for the code that implements the interpolation method used in the paper, please see [this repository](https://github.com/NU-CEM/Kabsch_interpolation).

## `./Data/`

- `./Crystal_structures/` contains the crystal structures used in the study. They are in the Vasp POSCAR format. All structures contain an iodine interstitial unless specified as "pristine". The naming convention is `POSCAR_[MA:Cs ratio]_[charge].vasp`
- `./Electronic_structure/` contains:
  - a Vasp CHGCAR file for the neutral iodine interstitial in MACsPbI (MA:Cs 14:2) (Figure S1)
  - a Vasp PROCAR file for the pristine MACsPbI (MA:Cs 14:2) density-of-states analysis (Figure S2).
  - CHGCAR and vasprun.xml files for the neutral and negative iodine defect supercells. The naming convention is `CHGCAR_[MA:Cs ratio]_[charge]_[functional].vasp`
- `./Symmetry_mode_analysis/` contains the symmetry mode analysis data generated using [isodistort](https://stokes.byu.edu/iso/isodistort.php) (Figure 3 and Figures S3-S5). The naming convention is `SMA_[MA:Cs ratio].txt`.
- `./Ellipsoid_data/` contains data about the ellipsoids fitted to PbI6 octahedra, for each of the pristine structures (Table S2).
- `./Figure_1/` contains the data required for plotting Figure 1

## Code - Julia 1.6.1

To run this code you will need the following standard Julia packages installed: Plots, LaTeXStrings, DataFrames, Statistics, CSV. You will also need [CarrierCapture.jl](https://github.com/WMD-group/CarrierCapture.jl/). Note that I use Julia 1.6.1.
- `CarrierCapture_MAPbI.ipynb` is a Jupyter Notebook with the first-principles non-radiative carrier capture analysis for MAPbI (Figure 1).
- `CarrierCapture_MACsPbI.ipynb` is a Jupyter Notebook with the first-principles non-radiative carrier capture analysis for MACsPbI (MA:Cs 14:2) (Figure 1).

## Code - Python 3 (mostly)

All of the Python packages make use of the standard scientific python stack: [scipy](https://scipy.org/), [numpy](https://numpy.org/), [pandas](https://pandas.pydata.org/), [matplotlib](https://matplotlib.org/).
- `Ellipsoidal_analysis.ipynb` analyses the minimum bounding ellipsoids in the pristine structures (Table S2). Note that to re-generate the ellipsoid data from the structures you will need to use [pieface](https://github.com/jcumby/PIEFACE) which is written in Python 2. Alternatively, you can analyse the data already generated and pickled.
- `Geometry_analysis.ipynb` uses [ase](https://wiki.fysik.dtu.dk/ase/) to analyse the bond angles and bond lengths in the pristine and defect structures (Table S2 and Table S3).
- `Symmetry_mode_analysis.ipynb` contains the code for analysing the output of [isodistort](https://stokes.byu.edu/iso/isodistort.php) (Figure 3 and Figures S3 to S5).
- `Figure_1.ipynb` contains the code for generating Figure 1.
- `Figure_2.ipynb` contains the code for generating Figure 2.
