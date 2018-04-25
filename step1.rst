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

*Login*
~~~~~~~

Log into `CyVerse Atmosphere <http://atmo.cyverse.org/>`_

Alternately, log into `XSEDE Jetstream <https://use.jetstream-cloud.org/application>`_

Fill in your ``username`` and ``password`` and click "LOGIN"
           
*Create a Project*
~~~~~~~~~~~~~~~~~~

Select Projects and "Create New Project"

- Now, this is something you only need to do once.

- We'll do this with Projects, which gives you a bit of a workspace in which to keep things that belong to "you".

- Click on the "Projects" tab on the top and then click "CREATE NEW PROJECT"

- Enter the name "NEON2018" into the Project Name, and something simple like "NEON Data Institute 2018" into the description. Then click 'create'.

Select the newly created project

*Start a new Instance*
~~~~~~~~~~~~~~~~~~~~~~

From your Project folder, you can select "New" and "Instance"

1. Select a featured image with a Graphic User Interface (GUI). 

**Suggested Atmosphere Image(s):**

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

**Suggested Jetstream Image(s):**

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

- Find the "Ubuntu 16.04" image, click on it

- Name it something simple such as "workshop tutorial" and select 'tiny1 (CPU: 1, Mem: 4GB, Disk: 30GB)'.

- Leave rest of the fields as default.

- Wait for it to become active

- It should now be booting up! This will take 2-10 minutes, depending.

- Be Patient (but not too patient - if it takes >10 minutes the system may be at capacity, if you're trying to launch a large or extra large VM, try something smaller).

- You can click on your new instance to get more information.

*Accessing the Shell*
~~~~~~~~~~~~~~~~~~~~~

Once the instance is `active`, you can access it via ``ssh`` or by using the Web Shell provided by Atmosphere. 

- Click "Open Web Shell", *or*, if you know how to use ssh,
you can ssh in with your CyVerse username on the IP address of the machine 

.. code-block:: bash

	ssh CyVerseUserName@<INSTANCE-IP-ADDRESS>

You should see something like this

.. code-block:: bash

	Welcome to Ubuntu 16.04.2 LTS (GNU/Linux 4.4.0-81-generic x86_64)

	  Get cloud support with Ubuntu Advantage Cloud Guest:
	    http://www.ubuntu.com/business/services/cloud

	155 packages can be updated.
	0 updates are security updates.


	*** System restart required ***
	Welcome to
	    _   _                             _
	   / \ | |_ _ __ ___   ___  ___ _ __ | |__   ___ _ __ ___
	  / _ \| __| '_ ` _ \ / _ \/ __| '_ \| '_ \ / _ \ '__/ _ \
	 / ___ \ |_| | | | | | (_) \__ \ |_) | | | |  __/ | |  __/
	/_/   \_\__|_| |_| |_|\___/|___/ .__/|_| |_|\___|_|  \___|
	
	cyverse_username@vm142-39:~$

.. Note:: 

	To access the Clipboard in an Apache Guacamole Web Shell:

	- Open Clipboard and virtual keyboard
	  - On a standard keyboard: `ctrl` + `alt` + `shift` key
	  - On a MAC OS X keyboard: `control` + `command ⌘` + `shift` key

	- Select your text or paste text into the clipboard window.

	- Close the Clipboard window by selecting `control` + `command ⌘` + `shift` keys again

	- Right click with your mouse or double tap fingers on touchpad to paste in the web shell or Desktop

**Deleting your instance**

- To completely remove your instance, you can select the "delete" buttom from the instance details page. 

- This will open up a dialogue window. Select the "Yes, delete this instance" button.

- It may take Atmosphere a few minutes to process your request. The instance should disappear from the project when it has been successfully deleted. 

.. Note::

  It is advisable to delete the machine if you are not planning to use it in future to save valuable resources. However if you want to use it in future, you can suspend it.

*EZ Installation of Project Jupyter*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For more details visit our `Data Science Quickstart Tutorial <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/>`_ on using `ez`. There are instructions for `ez` installation of Docker, Singularity, and Anaconda.

If you're on an instance which already has Anaconda installed, you'll still need to re-run `ez` to restart the Anaconda virtual enivronment. 

1. Install Anaconda with Python3 (`ez` comes preloaded on featured instances on Atmosphere and Jetstream) by typing:

	.. code-block :: bash

		sudo apt-get update
		ezj

2. Once the installation completes, a Jupyter Notebook will be running on the VM. 

3. Click the link to open a basic notebook. 

.. Advanced installations::

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

Second, you can use Docker (following the same `ez` `documentation <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/index.html>`_ as for Anaconda). We suggest using containers from Docker Hub `Rocker <https://hub.docker.com/r/rocker/geospatial/>`_ on the instance.

Third, you can use `Anaconda <https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/rstudio.html>`_ 

Here we are going to use ``ezj`` to install both Anaconda (Jupyter) and R

	.. code-block :: bash
		
		ezj -R

This will trigger the Ansible playbook to install ``r-base``, ``r-essentials``, and a few other commonly used R Data Science packages.

After ``ezj -R`` has finished, you can install RStudio-Server

Install these misc. dependencies

	.. code-block :: bash
	
		conda update conda
		conda install gxx_linux-64
		conda install gcc_linux-64

Set Path and install ``gdebi``

	.. code-block :: bash
	
		export PATH="/opt/anaconda3/bin":$PATH
		sudo chown $(id -u):$(id -g) /opt/anaconda3/ -R
		echo "export RSTUDIO_WHICH_R='/opt/anaconda3/bin/R'" >> ~/.bash_profile
		sudo apt-get install gdebi-core

Install RStudio-Server with ``gdebi``:

	.. code-block :: bash
	
		wget https://download2.rstudio.org/rstudio-server-1.1.447-amd64.deb
		sudo gdebi --non-interactive rstudio-server-1.1.447-amd64.deb

The installation of RStudio-Server is going to fail because we haven't told it which R to use. Because we are using Anaconda's installation of R, and not the basic installation of R, we have to reassign RStudio to look for Anaconda

	.. code-block :: bash
	
		sudo sh -c 'echo "rsession-which-r=/opt/anaconda3/bin/R" >> /etc/rstudio/rserver.conf'

Restart the server

	.. code-block :: bash
	
		sudo rstudio-server start

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

.. |atmo-1| image:: ../img/atmo-1.png
  :width: 750
  :height: 700
