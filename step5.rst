|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_

Working with Google Earth Engine API
------------------------------------

**Description: Run Earth Engine from your Jupyter Notebook or Lab**

..
	#### Comment: short text description goes here ####

*Install Earth Engine API*
~~~~~~~~~~~~~~~~~~~~~~~~~~

`Official Instructions <https://developers.google.com/earth-engine/python_install-datalab-local>`_

Requirements: Docker

Build Dependencies:

    .. code-block :: bash
    
    	ezd -p # In this example I'm also installing Portainer.io
	sudo usermod -aG docker $USER

Set the paths:

    .. code-block :: bash
    
    	export GCP_PROJECT_ID=gee-projects
	export CONTAINER_IMAGE_NAME=gcr.io/earthengine-project/datalab-ee:latest
	export WORKSPACE=${HOME}/workspace/datalab-ee
	mkdir -p $WORKSPACE
	cd $WORKSPACE

Run the Container (detached):

    .. code-block :: bash
   
        docker run -it -d -p "127.0.0.1:8081:8080" -v "$WORKSPACE:/content" -e "PROJECT_ID=$GCP_PROJECT_ID" $CONTAINER_IMAGE_NAME

Establish a secure connection with `Caddy <https://caddyserver.com/>`_:

    .. code-block :: bash
    	tmux

    .. code-block :: bash
    
    	echo "$(hostname)
	proxy / 127.0.0.1:8080 {
	    websocket
	    transparent
	}
	" > Caddyfile
	curl https://getcaddy.com | bash -s personal http.nobots
	caddy

Download Data
~~~~~~~~~~~~~



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
