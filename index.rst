|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_

NEON Data Science Institute 2018
================================

..
    #### Comment: Use short, imperative titles e.g. Upload and share data, uploading and
    sharing data ####

Moving Geospatial Data Analysis onto hybrid Cloud & HPC
-------------------------------------------------------

The purpose of this tutorial is to set up a linux-based Virtual Machine running on CyVerse Atmosphere or XSEDE Jetstream to do interactive geospatial analyses in Jupyter Notebooks and RStudio-Server. 

The VM(s) can also be run in any other number of ways that the user sees fit.

..
    #### Comment: Avoid covering upstream and downstream steps that are not explicitly and
    necessarily part of the tutorial - write or link to separate quick
    starts/tutorials for those parts ####

Contents
--------

.. toctree::
	:maxdepth: 2

	Home <self>
	Launching a Data Science Virtual Machine <step1.rst>
	Setting up Data Clients <step2.rst>
	Data transfer <step3.rst>
	GIS with Containers <step4.rst>
	Google Earth Engine API <step5.rst>

..
	#### Comment:This tutorial can have multiple pages. The table of contents assumes
	you have an additional page called 'Step One' with content located in 'step1.rst'
	Edit these titles and filenames as needed ####


Prerequisites
-------------

Downloads, access, and services
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*In order to complete this tutorial you will need access to the following services/software*

..
	#### comment: delete any row not needed in this table ####

.. list-table::
    :header-rows: 1

    * - Prerequisite
      - Preparation/Notes
      - Link/Download
    * - CyVerse account
      - You will need a CyVerse account to complete this exercise
      - `Register <https://user.cyverse.org/>`_
    * - Atmosphere access
      - You must have access to Atmosphere
      - `Request Access <https://user.cyverse.org/services/available>`_
    * - CyVerse Data Store allocation increase (Optional)
      - You must be registered for CyVerse
      - `Request Increase (form #2) <https://user.cyverse.org/forms>`_
    * - Jetstream access (Optional)
      - You must have registered with XSEDE
      - `Request Access <https://portal.xsede.org/my-xsede#/guest>`_
    * - Cyberduck
      - Standalone program for uploading/downloading data to Data Store
      - `Download <https://cyberduck.io/>`_

Platform(s)
~~~~~~~~~~~

*We will use the following CyVerse platform(s):*

 ..
   #### comment: delete any row not needed in this table ####

.. list-table::
    :header-rows: 1

    * - Platform
      - Interface
      - Link
      - Platform Documentation
      - Quick Start
    * - Data Store
      - GUI/Command line
      - `Data Store <http://www.cyverse.org/data-store>`_
      - `Data Store Manual <https://wiki.cyverse.org/wiki/display/DS/Data+Store+Table+of+Contents>`_
      - `Guide <https://cyverse-data-store-guide.readthedocs-hosted.com/en/latest/>`__
    * - Discovery Environment
      - Jupyter Notebooks / non-interactive Docker jobs
      - `Discovery Environment <https://de.cyverse.org/de/>`_
      - `DE Manual <https://wiki.cyverse.org/wiki/display/DEmanual/Table+of+Contents>`_
      - `Guide <http://learning.cyverse.org/projects/cyverse-discovery-environment-guide/>`__
    * - Atmosphere
      - Command line (ssh) and/or Desktop (VNC)
      - `Atmosphere <https://atmo.cyverse.org>`_
      - `Atmosphere Manual <https://wiki.cyverse.org/wiki/display/atmman/Atmosphere+Manual+Table+of+Contents>`_
      - `Guide <https://cyverse-atmosphere-guide.readthedocs-hosted.com/en/latest/>`__
    

Application(s) used
~~~~~~~~~~~~~~~~~~~
..
	#### Comment: these tables are examples, delete whatever is unnecessary ####

**Discovery Environment App(s):**

.. list-table::
    :header-rows: 1

    * - Name
      - Version
      - Location
      - App Link
      - Notes/other
    * - Jupyter Notebooks
      - 0.1
      - TBA
      - TBA
      - TBA
   
**Atmosphere Image(s):**

Here are the tested Ubuntu images. 

**Warning:** The latest version of Ubuntu (18.04) may not have current packages for some software.

.. list-table::
    :header-rows: 1

    * - Image Name
      - Version
      - Description
      - Link
    * - Ubuntu 16.04 GUI
      - 2.1
      - Ubuntu 16.04 GUI XFCE Base
      -	`Image <https://atmo.cyverse.org/application/images/1453>`_
    * - Ubuntu 16.04 non-GUI
      - 1.6
      - Ubuntu 16.04 non-GUI Base
      -	`Image <https://atmo.cyverse.org/application/images/1420>`_
    * - Ubuntu 18.04 GUI
      - 1.0
      - Ubuntu 18.04 GUI XFCE Base
      -	`Image <https://atmo.cyverse.org/application/images/1556`_
    * - Ubuntu 18.04 non-GUI
      - 1.0
      - Ubuntu 18.04 non-GUI Base
      -	`Image <https://atmo.cyverse.org/application/images/1552>`_ 

**Jetstream Image(s):**

.. list-table::
    :header-rows: 1

    * - Image Name
      - Version
      - Description
      - Link
    * - Ubuntu 16.04 GUI
      - 1.13
      - Ubuntu 16.04 LTS Development + GUI support + Docker
      -	`Image <https://use.jetstream-cloud.org/application/images/107>`_
    * - Ubuntu 14.04 GUI
      - 1.17
      - Base Ubuntu 14.04.3 + Xfce + Xfce-goodies, firefox, icon sets and themes
      -	`Image <https://use.jetstream-cloud.org/application/images/54>`_


Input and example data
~~~~~~~~~~~~~~~~~~~~~~

*In order to complete this tutorial you will need to have the following inputs prepared*

..
	#### comment: delete any row not needed in this table ####

.. list-table::
    :header-rows: 1

    * - Input File(s)
      - Format
      - Preparation/Notes
      - Example Data
    * - Discrete lidar
      - *.laz, *.las, *.xyz, *.bin
      - classified
      - `Data Portal <http://data.neonscience.org/home>`_ 
    * - Orthophotography
      - *.tif
      - 
      -
    * - Hyperspectral
      - *.hdf
      -
      -

----

**Fix or improve this documentation**

- On Github: `Repo link <https://github.com/CyVerse-learning-materials/neon_data_science>`_
- Send feedback: `Tutorials@CyVerse.org <Tutorials@CyVerse.org>`_

----

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`__


.. |CyVerse logo| image:: ./img/cyverse_rgb.png
    :width: 500
    :height: 100
.. _CyVerse logo: http://learning.cyverse.org/
.. |Home_Icon| image:: ./img/homeicon.png
    :width: 25
    :height: 25
.. _Home_Icon: http://learning.cyverse.org/
