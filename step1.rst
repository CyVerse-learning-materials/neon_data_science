|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Launching a Data Science Virtual Machine
----------------------------------------

**Description: Provision VM for analyzing NEON AOP data**

..
	#### Comment: short text description goes here ####

----


*Start a Cloud Instance*
~~~~~~~~~~~~~~~~~~~~~~~~

.. 	#### Comment: Step title should be descriptive (i.e. Cleaning Read data) ###


1.Use a featured image with a Graphic User Interface (GUI). 

2. Allow the instance to reach 'active' status. Instances typically take 3-7 minutes to boot up the first time.

3. Log into the Apache Guacamole Web Shell to access a terminal, or use `ssh` on your local machine:

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

For more details visit our [Data Science Quickstart Tutorial](https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/) on using `ez`. There are instructions for `ez` installation of Docker, Singularity, and Anaconda.

If you're on an instance which already has Anaconda installed, you'll still need to re-run `ez` to restart the Anaconda virtual enivronment. 

1. Install Anaconda with Python3 (`ez` comes preloaded on featured instances on Atmosphere and Jetstream) by typing:

.. code-block:: bash
	ezj

2. Once the installation completes, a Jupyter Notebook will be running on the VM. 

3. Click the link to open a basic notebook. 

.. Note::

	To ensure your session doesn't die when you close your terminal use `tmux` or `screen` to start your remote sessions and to detach the screen before exiting.

	- detach screen: `ctrl + b` then `ctrl + d`

	- list tmux sessions: `tmux ls`

	- re-attach screen: `tmux attach -t <session id #>`

4. You can launch Jupyter Lab by exiting the notebook and typing `jupyter lab` - but this will allow Lab to only be available on the localhost, with no way to connect from a remote terminal. Exit the notebook by pressing `ctrl + c` twice, and then start a `JupyterLab<https://github.com/jupyterlab/jupyterlab>`_.

*Establishing a Secure Connection*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. On the VM start the Lab in terminal (don't forget to use `tmux`)

.. code-block:: bash
	jupyter lab --no-browser --ip=127.0.0.1 --port=8888

**Option: 1 SSH tunnel**

2. Open a new terminal on your localhost or Web Shell tab in browser. 

.. code-block:: bash
	ssh -nNT -L 8888:localhost:8888 CyVerseUserName@<IPADDRESS>

	Enter your password. The terminal should stop responding after this.

3. In your browser, open a new tab and go to `http://localhost:8888`

**Caddy**

1. On the VM in a terminal:

.. code-block:: bash
	echo "$(hostname)
	proxy / 127.0.0.1:8888
	" > Caddyfile
	curl https://getcaddy.com | bash -s personal http.nobots
	caddy

2. Caddy will output a secure url `https://` for the Atmosphere VM which you can then connect in a new browser tab.

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

	.. code-block:: bash
		sudo chown $(id -u):$(id -g) /opt/anaconda3 -R
		
	Install additional Jupyter `kernels<https://github.com/jupyter/jupyter/wiki/Jupyter-kernels>`_

	.. code-block:: bash
		sudo add-apt-repository ppa:chronitis/jupyter

	.. code-block:: bash
		sudo apt-get update
		conda install -c anaconda ipykernel
		sudo apt-get install irkernel ijavascript

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
