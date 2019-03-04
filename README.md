<p align="center">
    <img src ="magic_logo.png" alt="MAGIC logo" width="275"/>
</p>

# Multi-Application Guiding Interface for Commissioning (MAGIC)

[![PyPI - License](https://img.shields.io/pypi/l/Django.svg)](https://github.com/spacetelescope/jwql/blob/master/LICENSE)
[![Python](https://img.shields.io/badge/Python-3.6-blue.svg)](https://www.python.org/)
[![STScI](https://img.shields.io/badge/powered%20by-STScI-blue.svg?colorA=707170&colorB=3e8ddd&style=flat)](http://www.stsci.edu)

The Multi-Application Guiding Interface for Commissioning (MAGIC) package provides convenient access to  numerous ancillary tools that will be used, as the name suggests, with the JWST FGS during OTE Commissioning. The package allows for user interaction with commissioning data and creates files that are needed for the operation of the flight software and the execution of visits.

These tools comprise of four main components that can be run individually
or together:

### 1. NIRCam to FGS image conversion (``convert_image``)
This tool can take in a simulated (or real) NIRCam image and will convert
it to an FGS (guider 1 or guider 2) image. In addition to rotating the image,
adjusting the pixel scale and image size, this tool corrects bad pixels and
normalizes the image to a specific magnitude of star.


### 2. Star Selection Tool (``star_selector``)
This tool will take the FGS image either created with the first tool, or
an FGS image that it is passed by the user, and allow the user to choose
the guide star and reference stars using a GUI.


### 3. Flight Software File Writer (``fsw_file_writer``)
This module requires an FGS image and a file that includes a list of the
coordinates of the guide star and reference stars, along with their count
rates. This tool will create all files necessary to test this image different
flight software simulators (FGS DHAS, FGSES, etc.) These include all the
files necessary to run the ID, ACQ1, ACQ2, and TRK steps in these simulators.


### 4. Segment Guiding Tool (``segment_guiding``)
Used to facilitate guiding on unstacked segment arrays during commissioning. When
provided 1) the commanded RA and Dec of a guide star and 2) the V2/V3 (or x/y)
positions of all segments in an array, the segment guiding tool calculates the
effective RA and Dec of all segments on the sky.


Installation notes
------------------
This package was developed in a python 3.5 environment. Python 2.7 is not yet supported.

The following supplemental packages are required, and will be **automatically installed** with the package:
* `astropy`
* `matplotlib`
* `numpy`
* `photutils`
* `PyQt5`
* `pysiaf`
* `pytest`
* `pyyaml`
* `requests`

##### To install:

1) Activate your Python 3 (preferably Astroconda) environment.

2) Clone the gitlab repository to your local machine

	git clone git@grit.stsci.edu:wfsc/tools.git

3) Install the `jwst_magic` package:

	cd tools/fgs-commissioning

	pip install -e .a



Running the Tools
-----------------
These tools are best run in the IPython terminal, in an AstroConda environment
(see the [AstroConda installation page](https://astroconda.readthedocs.io/en/latest/getting_started.html)
for installing AstroConda). Simply activate your Python 3 environment, and
launch the GUI with the following steps:

    In[1]: import jwst_magic

    In[2]: jwst_magic.run_tool_GUI()


Tutorial
-----------------
See the [`FGS Commissioning Tool Tutorial.ipynb`](./notebooks/FGS%20Commissioning%20Tool%20Tutorial.ipynb)
notebook for examples on how to run the tools on a modular level from within a Jupyter notebook.

Contributing
-----------------
There are two pages to review before you begin contributing to `fgs-commissioning` development.
The first is our [style guide](./style_guide/style_guide.md) and the second is our suggested [git workflow page](./style_guide/git_workflow.md),
which contains an in-depth explanation of the workflow.

The following is an example of a best work flow for contributing to the project
(adapted from the [`spacetelescope` `jwql` contribution guidelines](https://github.com/spacetelescope/jwql)):

1. Create a branch off of the `tools` repository using the JIRA issue name plus a
   short description of the issue (e.g. `JWSTFGS-375-fix-fgs-image-conversion`)
2. Make your software changes.
3. Push that branch to your personal GitHub repository (i.e. origin).
4. On the `tools` repository, create a pull request that merges the branch into `tools:master`.
5. Assign a reviewer from the team for the pull request.
6. Iterate with the reviewer over any needed changes until the reviewer accepts and merges your branch.
7. Delete your local copy of your branch.


Code of Conduct
-----------------
Users and contributors to `fgs-commissioning` should adhere to the [Code of Conduct](./CODE_OF_CONDUCT.md).
Any issues or violations pertaining to the Code of Conduct should be brought to
the attention of a `MAGIC` team member listed below.

Questions
-----------------
Any questions regarding the `fgs-commissioning` project or its software should be directed to
`kbrooks@stsci.edu` and `lchambers@stsci.edu`.

Current Development Team
-----------------
* Lauren Chambers (@lchambers)
* Keira Brooks (@kbrooks)