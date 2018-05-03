|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Working with QGIS, GRASS, SAGA-GIS
----------------------------------

**Description: Run GUI programs on the VM using Singularity Containers**

..
	#### Comment: short text description goes here ####

*Build the Container yourself*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to develop your own containers you can download the example Singularity file from my `Github repository <https://github.com/tyson-swetnam/osgeo-singularity>`_ and make your own changes

.. 	#### Comment: Step title should be descriptive (i.e. Cleaning Read data) ###

`EZ Install Singularity on Atmosphere or Jetstream <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/>`_

To `install Singularity <https://singularity.lbl.gov/install-linux>`_ on linux follow these instructions.

CyVerse recently taught a `Container Bootcamp <https://cyverse-container-camp-workshop-2018.readthedocs-hosted.com/en/latest/index.html>`_ with in depth instructions for working with Docker and Singularity.

As of early May 2018, Singularity is version `2.5.0` 

  .. code-block :: bash
  
    VERSION=2.4.5
    wget https://github.com/singularityware/singularity/releases/download/$VERSION/singularity-$VERSION.tar.gz
    tar xvf singularity-$VERSION.tar.gz
    cd singularity-$VERSION
    ./configure --prefix=/usr/local
    make
    sudo make install
    cd ..
    sudo rm -rf singularity-$VERSION.tar.gz

Singularity build dependencies:

	.. code-block :: bash
		sudo apt-get install debootstrap

Get the Singularity file from terminal:

1. Clone github repository onto the VM (e.g. ``/home/user/``)

  .. code-block :: bash
    
    git clone https://github.com/tyson-swetnam/osgeo-singularity
    cd osgeo-singularity

2. Select ``Singularity`` file and view it if you like, make any changes you wish.

3. Build the container locally:

  .. code-block :: bash
  
      sudo singularity build osgeo.simg Singularity

*Download the Container from Singularity-Hub*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The container image is hosted on Singularity Hub and can be downloaded from there.

1. Pull the image from Singularity-Hub

  .. code-block :: bash
  
    singularity pull --name osgeo.simg shub://tyson-swetnam/osgeo-singularity

*Running CLI scripts*
~~~~~~~~~~~~~~~~~~~~~

To run the container from the CLI:

  .. code-block :: bash
  
      singularity shell osgeo.simg

Calling the container from your Jupyter Notebook (Python3)

  .. code-block :: bash


*Run GUI Applications*
~~~~~~~~~~~~~~~~~~~~~~

Run the container with the `exec` command to use the GUI applications, the interface for GRASS:

  .. code-block :: bash
  
    singularity exec osgeo.simg grass74

GRASS has a problem with its environment variables not being set within the container. You can do  this by hand while the container is running:


For QGIS:

  .. code-block :: bash

    singularity exec osgeo.simg qgis


For Saga-GIS:

  .. code-block :: bash
    
    singularity exec osgeo.simg saga_gui

.. Note:: 

  You must use the Atmosphere Web Shell or an `ssh` terminal to access the container GUI applications; else you must set the Display variables from the Jupyter Notebook

----

**Fix or improve this documentation**

- On Github: `Repo link <https://github.com/CyVerse-learning-materials/neon_data_science>`_
- Send feedback: `Tutorials@CyVerse.org <Tutorials@CyVerse.org>`_

----

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_

.. |CyVerse logo| image:: ./img/cyverse_rgb.png
    :width: 500
    :height: 100
.. _CyVerse logo: http://learning.cyverse.org/
.. |Home_Icon| image:: ./img/homeicon.png
    :width: 25
    :height: 25
.. _Home_Icon: http://learning.cyverse.org/
