|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Launching a Data Science Virtual Machine
----------------------------------------

**Description: Provision VM for analyzing NEON AOP data**

..
	#### Comment: short text description goes here ####

CyVerse operates a cloud service it calls "`Atmosphere<http://www.cyverse.org/atmosphere>`_". Users can request up to 2,000 allocation units [hours (hr)] per month. E.g. a 1-core instance uses 1 AU/hr, a 4-core instance uses 4 AU/hr, and a 16-core instance uses 16 AU/hr)

Allocations are automatically reset to a default 128 AU on the 1st of each month. Users can request more AU by using the Intercom button in the lower right of the browser page. Requests are typically approved in <1 hour during standard business hours, and <24 hours on nights and weekends. 

`XSEDE Jetstream <https://portal.xsede.org/jetstream>`_ uses the same UI interface as Atmosphere. Startup allocations typically range from 25,000 - 250,000 AU per year. Research allocations between 250,000 to several million AU are also available through XSEDE. 

----


*Start a Cloud Instance*
~~~~~~~~~~~~~~~~~~~~~~~~

.. 	#### Comment: Step title should be descriptive (i.e. Cleaning Read data) ###

Log into `CyVerse Atmosphere <http://atmo.cyverse.org/>`_

Alternately, log into `XSEDE Jetstream <https://use.jetstream-cloud.org/application>`_

1. Select a featured image with a Graphic User Interface (GUI). 

**Atmosphere Image(s):**

.. list-table::
    :header-rows: 1

    * - Image Name
      - Version
      - Description
      - Link
    * - Ubuntu 16.04 GUI
      - 2.1
      - XFCE Base, iRODS 
      -	`Image <https://atmo.cyverse.org/application/images/1453>`_
    * - Ubuntu 16.04 non-GUI
      - 1.6
      - non-GUI Base, iRODS
      -	`Image <https://atmo.cyverse.org/application/images/1420>`_

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


2. Allow the instance to reach 'active' status. Instances typically take 3-7 minutes to boot up the first time.

3. Log into the Atmosphere's Apache Guacamole Web Shell to access a terminal, or use ``ssh`` on your local machine:

.. code-block:: bash

	ssh CyVerseUserName@<INSTANCE-IP-ADDRESS>

.. Note:: 
	To access Clipboard in Apache Guacamole Web Shell:

	- Open Clipboard and virtual keyboard
	  - On a standard keyboard: `ctrl` + `alt` + `shift` key
	  - On a MAC OS X keyboard: `control` + `command ⌘` + `shift` key

	- Select your text or paste text into the clipboard window.

	- Close the Clipboard window by selecting `control` + `command ⌘` + `shift` keys again

	- Right click with your mouse or double tap fingers on touchpad to paste in the web shell or Desktop

*EZ Installation*
~~~~~~~~~~~~~~~~~

For more details visit our `Data Science Quickstart Tutorial <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/>`_ on using `ez`. There are instructions for `ez` installation of Docker, Singularity, and Anaconda.

If you're on an instance which already has Anaconda installed, you'll still need to re-run `ez` to restart the Anaconda virtual enivronment. 


1. Install Anaconda with Python3 (`ez` comes preloaded on featured instances on Atmosphere and Jetstream) by typing:

	.. code-block :: bash
	
		ezj

2. Once the installation completes, a Jupyter Notebook will be running on the VM. 

3. Click the link to open a basic notebook. 

.. Note::

	To ensure your session doesn't die when you close your terminal use `tmux` or `screen` to start your remote sessions and to detach the screen before exiting.

	- detach screen: `ctrl + b` then `ctrl + d`

	- list tmux sessions: ``tmux ls``

	- re-attach screen: ``tmux attach -t <session id #>``

4. You can launch Jupyter Lab by exiting the notebook and typing `jupyter lab` - but this will allow Lab to only be available on the localhost, with no way to connect from a remote terminal. Exit the notebook by pressing `ctrl + c` twice, and then start a `Jupyter Lab <https://github.com/jupyterlab/jupyterlab>`_.

*Establishing a Secure Connection*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. On the VM start the Lab in terminal (don't forget to use `tmux`)

	.. code-block :: bash	
	
		jupyter lab --no-browser --ip=127.0.0.1 --port=8888

**Option 1: SSH tunnel**

2. Open a new terminal on your localhost or Web Shell tab in browser. 

	.. code-block :: bash
	
		ssh -nNT -L 8888:localhost:8888 CyVerseUserName@<IPADDRESS>

	Enter your password when prompted. 
	
	The terminal should stop responding after this.

3. In your browser, open a new tab and go to ``http://localhost:8888``

**Option 2: Caddy**

2. In the terminal:

	.. code-block :: bash
	
		echo "$(hostname)
		proxy / 127.0.0.1:8888
		" > Caddyfile
		curl https://getcaddy.com | bash -s personal http.nobots
		caddy

Caddy will output a secure url `https://` for the Atmosphere VM which you can then connect in a new browser tab.

3. Copy / Paste the `https://` url into a new browser tab.

..
	#### Comment: Suggested style guide:
	1. Steps begin with a verb or preposition: Click on... OR Under the "Results Menu"
	2. Locations of files listed parenthetically, separated by carets, ultimate object in bold
	(Username > analyses > *output*)
	3. Buttons and/or keywords in bold: Click on **Apps** OR select **Arabidopsis**
	4. Primary menu titles in double quotes: Under "Input" choose...
	5. Secondary menu titles or headers in single quotes: For the 'Select Input' option choose...
	####

.. Note::

	To install your own packages you'll need to change ownership of the Anaconda installation:
	
		.. code-block :: bash
		
			sudo chown $(id -u):$(id -g) /opt/anaconda3 -R
		
	Install additional `Jupyter kernels <https://github.com/jupyter/jupyter/wiki/Jupyter-kernels>`_
	
		.. code-block :: bash
		
			sudo add-apt-repository ppa:chronitis/jupyter
			sudo apt-get update
			conda install -c anaconda ipykernel
			sudo apt-get install irkernel ijavascript

*Installing RStudio-Server*
~~~~~~~~~~~~~~~~~~~~~~~~~~~

RStudio can be installed in several ways. 

First, you can follow the RStudio-Server `instructions for Linux <https://www.rstudio.com/products/rstudio/download-server/>`_

Second, you can use Docker (following the same `ez` `documentation <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/index.html>`_ as for Anaconda).

We suggest using containers from Docker Hub `Rocker <https://hub.docker.com/r/rocker/geospatial/>`_

Third, you can use Anaconda

`Instructions for Anaconda <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/rstudio.html>`_ 

**Description of output and results**

Congratulations - you've got a Virtual Machine ready to do some serious data science!

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
