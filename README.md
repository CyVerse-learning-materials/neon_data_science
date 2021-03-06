# NEON Data Science with CyVerse

The focus of this repository is on NEON AOP lidar and hyperspectral imagery, conducting analyses on cloud and HPC.

**Author**: Tyson Lee Swetnam

**Learning Objectives**: [NEON’s data science skills](http://www.neonscience.org/opportunities/learning-opportunities/neon-data-skills) provide notebooks and lesson plans for analyzing hyperspectral imagery. I plan to develop complementary notebooks for downloading [AOP lidar data](http://www.neonscience.org/data-collection/airborne-remote-sensing); segmenting individual organisms (herbaceous plants, woody shrubs, and trees) using open-source code, vertically sampling (all bands and time series) hyperspectral signatures for each organism.

The lessons are targeted toward advanced graduate students and researchers. 

Lessons are expected to take 30 minutes to 2 hours each to complete.

Students should work in small teams (paired programming) to develop their notebooks. 

## Prerequisites

* An active internet connection

* Fundamental understanding of Remote Sensing and Geographic Information Systems (GIS)
  * Raster and Vector analysis
    * Data science Lessons from [The Carpentries](https://software-carpentry.org/lessons/) are encouraged. 
    * Broad understanding of [geospatial data analysis in R](http://www.datacarpentry.org/r-spatial-data-management-intro/) is also encouraged. 
  * Point cloud analysis
    * discrete lidar
    * structure from motion photogrammetry
  * Image processing
    * hyperspectral
    * vegetation indexing
    * orthorectification
* Basic data science understanding of:
  * Software Container Technology, i.e. Docker, Singularity
  * Container management and orchestration, i.e. Docker Compose, Docker Swarm, Kubernetes
  * Computational notebooks, i.e. Jupyter Notebooks, Lab, Hub; RStudio R Markdown
  * Google Earth Engine
  * Open Source GIS software
    * QGIS
    * GRASS
    * SAGA
    * CloudCompare
    * PDAL
    * GDAL
* Moderate (to Advanced) computer language programming in:
  * R 
  * Python 
  * Bash
  * JavaScript

## Lesson 1: Data Science Workbench

**Goals**: Provision virtual machines on [CyVerse Atmosphere](https://atmo.cyverse.org/application) or [XSEDE Jetstream](https://use.jetstream-cloud.org/application), and [Discovery Environment](https://de.cyverse.org/de/), for data analyses.

**Value**: Learn to launch remote metal running on fast Internet2.

* Use [CyVerse Learning Center tutorials](https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/) to deploy container software ([Anaconda (Jupyter)](https://anaconda.org/anaconda/jupyter), [Docker](https://www.docker.com/), and [Singularity](http://singularity.lbl.gov/)).

* [Launch virtual machine]() and install the necessary software: [Rocker RStudio](https://hub.docker.com/u/rocker/), & [Jupyter](http://jupyter.org/) Notebooks and [Lab](https://github.com/jupyterlab/jupyterlab) for running NEON data analyses.

## Lesson 2: Get NEON AOP data

**Goals**: Learn how to download NEON data

**Value**: Get the data!

* Introduce the [NEON Data API](https://github.com/NEONScience/neon-data-api)   
* Develop Python Jupyter Notebooks for downloading lidar & imagery data 
* Develop Rmarkdown notebooks for downloading lidar & imagery data

## Lesson 3: Lidar data QAQC and Visualization

**Goals**: Learn basic lidar processing and visualization techniques.

**Value**: Improve classification (bare earth, vegetation, infrastructure) of lidar and visualize data anywhere. 

* Introduce [PDAL](https://www.pdal.io/) (w/ Docker) for lidar classification. 
  * CLI executions.
  * JSON scripting.
  * Colorize lidar data with aerial orthophotography

* Introduce [Potree](http://www.potree.org/), [Entwine](https://entwine.io/) & [Greyhound](https://greyhound.io/) for point cloud visualization.

* Discuss the use of [CloudCompare](http://www.danielgm.net/cc/) and [Blender]()

## Lesson 4: Lidar stem segmentation in R

**Goals**: Learn how to segment individual trees/shrubs/herbaceous plants from lidar data in R.

**Value**: Generate ecologically relevant inventory (census) of physical characteristics.

* Run [lidR](https://github.com/Jean-Romain/lidR) stem segmentations

* Develop individual object (plant) inventory for various scales.

* [Leaflet](https://rstudio.github.io/leaflet/) mapping in R.

## Lesson 5: NEON Hyperspectral QAQC & simple calibrations

**Goals**: Learn to use NEON hyperspectral imagery.

**Value**: Utilize hyperspectral imagery which will allow species level ID and phenology (health).

* Utilize existing [NEON Data Skills hyperspectral](http://neondataskills.org/hyperspectral-remote-sensing/)

## Lesson 6: Point/polygon sampling of individuals w/ corresponding hyperspectral signatures

**Goals**: Learn to point and polygon sample individual plants in R

**Value**: Ecologically relevant inventory with phenology and species.

* Attribute individual organisms with their corresponding hyperspectral reflectances

## Lesson 7: Statistical Analyses in RStudio

**Goals**: Conduct statistical analyses on your new datasets.

**Value**: Hypothesis testing using data.

* Graphical representations of the data 
  * `ggplot2`
  * `shiny`
  
* Statistical analyses
  * linear modelling, maximum likelihood, generalized additive models (gam), random forests

## Lesson 8: Statistical Analyses in Jupyter

**Goals**: Conduct statistical analsyes on your new datasets

**Value**: Hypothesis testing using data.

* Graphical representations of the data
  * `matplotlib`
  * `pandas`
  * `numpy`
  
## Lesson 9: Scaling analyses to multiple NEON sites

**Goal**: Develop workflows which utilize data from multiple NEON sites and time series analyses

* Introduce Makeflow and Singularity
* Introduce Dask Distributed
* Job requests for HPC
