|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Working with QGIS, GRASS, SAGA-GIS
----------------------------------

**Description: Run GUI programs on the VM using Singularity Containers**

If you're running on Windows OS you can set up the `Windows-Linux subsystem <https://docs.microsoft.com/en-us/windows/wsl/install-win10>`_ to access a real Linux terminal. This will enable you to run secure shell connections to your VM.

Another option is to use the Atmosphere Web Desktop, which is running an XFCE Desktop.

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

Run the container with the ``singularity exec`` command to use the GUI applications, the interface for GRASS:

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

  Running the GUI applications requires a stable, fast, internet connection, else loading large raster layers may be very slow.
  
  You must use the Atmosphere Web Shell or ``ssh -X`` in the terminal to access the Container's GUI applications.
  
  	.. code-block :: bash
	
		ssh -X <USERNAME>@<IP-ADDRESS>
  
  If you are using the Web Desktop, you can resize the screen by opening the terminal emulator and typing ``xrandr``
  	
	.. code-block :: bash
		
		 SZ:    Pixels          Physical       Refresh
		 0   1024 x 768    ( 260mm x 195mm )   0   
		 1    800 x 600    ( 203mm x 152mm )   0   
		 2   1280 x 800    ( 325mm x 203mm )   0   
		 3   1280 x 960    ( 325mm x 244mm )   0   
		 4   1280 x 1024   ( 325mm x 260mm )   0   
		 5   1680 x 1050   ( 427mm x 267mm )   0   
		 6   1920 x 1080   ( 488mm x 274mm )   0   
		*7   1920 x 1200   ( 488mm x 305mm )  *0   
		 8   3360 x 1050   ( 853mm x 267mm )   0   
		 9   1024 x 700    ( 260mm x 178mm )   0   
		 10  1200 x 740    ( 305mm x 188mm )   0   
		 11  1600 x 1000   ( 406mm x 254mm )   0   
		 12  1600 x 1200   ( 406mm x 305mm )   0   
		 13  3200 x 1000   ( 813mm x 254mm )   0   
		 14  3200 x 1200   ( 813mm x 305mm )   0   
		Current rotation - normal
		Current reflection - none
		Rotations possible - normal 
		Reflections possible - none
  
  This will show you the list of possible screen resolutions. To reset the screen resolution to HD (1920x1080):
  
  	.. code-block :: bash
		
		xrandr -s 6
 
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
