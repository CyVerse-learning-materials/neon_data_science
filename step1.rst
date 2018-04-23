|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_


Starting a VM
-------------

**Description: Provision your VM for analyzing NEON data**

..
	#### Comment: short text description goes here ####

----

**Input Data:**

.. list-table::
    :header-rows: 1

    * - Input
      - Description
      - Example
    * -
      -
      -

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

*Clone this Repository onto the VM*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Change into a directory (`cd`) you're comfortable installing software into and have `sudo` privileges.

2. `git clone` the Jupyter Notebook examples repository onto your VM:

.. code-block:: bash
	git clone https://github.com/tyson-swetnam/QUBES_NEON.git

*EZ Installation*
~~~~~~~~~~~~~~~~~

For more detail visit CyVerse Learning Center's [Data Science Quickstart Tutorial](https://cyverse-ez-quickstart.readthedocs-hosted.com/en/latest/). CyVerse has set up an `ez` installation for Docker, Singularity, and Anaconda (Jupyter Notebooks and Lab).

1. Install Anaconda with Python3 (Featured instances on Atmosphere and Jetstream)

.. code-block:: bash
	ezj

2. Once the installation completes, Jupyter Notebook will be running on the VM. 

Click the link to open a basic notebook. You can launch Jupyter Lab by exiting the notebook and typing `jupyter lab` - but this will allow Lab to only be available on the localhost, with no way to connect from a remote terminal.

.. Note::

	To ensure your session doesn't die when you close your terminal use `tmux` or `screen` to start your remote sessions and to detach the screen before exiting.

	- detach screen: `ctrl + b` then `ctrl + d`

	- list tmux sessions: `tmux ls`

	- re-attach screen: `tmux attach -t <session id #>`

3. Exit the notebook by pressing `ctrl + c` twice, and then start a `Jupyter Lab (BETA)<https://github.com/jupyterlab/jupyterlab>`_.

To create a secure connection to Jupyter Lab, you will need to start the lab and open an `ssh` tunnel.

.. code-block:: bash
	jupyter lab --no-browser --ip=127.0.0.1 --port=8888

Next, open a new terminal tab or window. 

.. code-block:: bash
	ssh -nNT -L 8888:localhost:8888 CyVerseUserName@<IPADDRESS>

Enter your password and the terminal should stop responding

Open a new browser tab and open `localhost:8888`


4. Yet another option to set up a secure connection using Caddyfile

.. code-block:: bash
	echo "$(hostname)
	proxy / 127.0.0.1:8888
	" > Caddyfile
	curl https://getcaddy.com | bash -s personal http.nobots
	caddy

Caddy will output a secure `https://` url for the Atmosphere VM which you can then connect to.

..
	#### Comment: Suggested style guide:
	1. Steps begin with a verb or preposition: Click on... OR Under the "Results Menu"
	2. Locations of files listed parenthetically, separated by carets, ultimate object in bold
	(Username > analyses > *output*)
	3. Buttons and/or keywords in bold: Click on **Apps** OR select **Arabidopsis**
	4. Primary menu titles in double quotes: Under "Input" choose...
	5. Secondary menu titles or headers in single quotes: For the 'Select Input' option choose...
	####

**Output/Results**

.. list-table::
    :header-rows: 1

    * - Output
      - Description
      - Example
    * -
      -
      -


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
