|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Using the NEON Data API w/ Python
---------------------------------

**Description: Downloading data in Jupyter Notebooks**

..
	#### Comment: short text description goes here ####

*Clone Github Repository*
~~~~~~~~~~~~~~~~~~~~~~~~~

Example notebooks are hosted online on the CyVerse GIS Github. 

.. 	#### Comment: Step title should be descriptive (i.e. Cleaning Read data) ###

Prerequisite: `Launched Jupyter Notebook or Lab on VM <step1.rst>`_

In the terminal:

1. Clone notebooks from NEON Data Science or CyVerse GIS to a location on the VM (e.g. ``/home/user/``)

  .. code-block :: bash
    
    git clone https://github.com/cyverse-gis/neon_data_science
    cd neon_data_science/lessons

2. Select a notebook in Jupyter and start it.

3. Follow notebook instructions.


*Download data from CyVerse DataStore in Bash*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CyVerse uses a system called `iRODS <https://docs.irods.org/>`_ to move files onto and off of its Data Store. 

iRODS uses multi-threaded file transfers for faster downloads and uploads than traditional ``wget`` or ``curl`` 

Prerequisite: `Installed iRODS iCommands and initiated connection <step2.rst>`_

1. Use the ``ils`` command to view your files on the Data Store

2. Use the `iget <https://docs.irods.org/4.2.2/icommands/user/#iget>`_ command to download files from the Data Store

  .. code-block :: bash
  
    iget -KPQbrvf /iplant/home/user/neon/L1/DiscreteLidar/classified_points /home/user/Downloads
    
In this example we are using the flags to:

      -K  verify the checksum
      -P  output the progress of the download.
      -Q  use RBUDP (datagram) protocol for the data transfer
      -b  bulk file transfer
      -r  recursive - retrieve subcollections
      -v  verbose
      -f  force - write local files even it they exist already (overwrite them)

*Upload data to the CyVerse DataStore*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Use the `iput <https://docs.irods.org/4.2.2/icommands/user/#iput>`_ command to upload files to the Data Store

  .. code-block :: bash
  
    iput -KPQbrvf /home/user/neon_data_science/results /iplant/home/user/neon/results

Note, we are using the same flags as the ``iget`` statement above.

*Jupyter Lab Google Drive Client*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After you've setup your Jupyter Lab, you can view files in your Google Drive and move them onto the VM.


..
	#### Comment: Suggested style guide:
	1. Steps begin with a verb or preposition: Click on... OR Under the "Results Menu"
	2. Locations of files listed parenthetically, separated by carets, ultimate object in bold
	(Username > analyses > *output*)
	3. Buttons and/or keywords in bold: Click on **Apps** OR select **Arabidopsis**
	4. Primary menu titles in double quotes: Under "Input" choose...
	5. Secondary menu titles or headers in single quotes: For the 'Select Input' option choose...
	####

----

**Description of output and results**


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
