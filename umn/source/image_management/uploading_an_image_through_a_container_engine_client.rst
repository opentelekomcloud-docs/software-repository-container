:original_name: swr_01_0011.html

.. _swr_01_0011:

Uploading an Image Through a Container Engine Client
====================================================

Scenario
--------

You can run **docker push** (Docker) or **ctr push** (containerd) on the server where the container engine client is installed to push an image to SWR.

Constraints
-----------

If you use Docker, the Docker version must be between 1.11.2 (included) and 24.0.9 (included). The size of each image layer cannot exceed 10 GB. You can push a maximum of 20 image layers concurrently.

Prerequisites
-------------

-  You have created an organization in SWR. For details, see :ref:`Creating an Organization <swr_01_0014__section12921632181415>`.
-  If you use an ECS that is not a CCE node to connect to SWR using a private network address, configure **insecure-registries** as follows:

   #. Modify the **/etc/docker/daemon.json** file. If the file does not exist, manually create it. Add the following content to the file:

      .. code-block::

         {
             "insecure-registries": [
                 "{Intranet address}"
             ]
         }

      To obtain the value of {*Intranet address*}, log in to the SWR console. On the **Dashboard** page, click **Generate Login Command** and obtain the private network address in the private network command.

      .. note::

         If **insecure-registry** has been configured in the **DOCKER_OPTS** configuration item in the **/etc/default/docker** file, you do not need to modify the **/etc/docker/daemon.json** file.

         Run the following command to add the private network IP address to the end of the **DOCKER_OPTS** configuration item:

         **vi /etc/default/docker**

         Example:

         .. code-block::

            # Use DOCKER_OPTS to modify the daemon startup options. DOCKER_OPTS="--insecure-registry={existing configurations} --insecure-registry={Intranet address}"

   #. Restart Docker for the configuration to take effect.

      **sudo systemctl daemon-reload**

      **sudo systemctl restart docker**

Docker
------

The following walks you through the steps of uploading an image to SWR through the client by taking the **nginx:v1** image built in :ref:`Basics of Docker <swr_01_0006>` as an example.

#. .. _swr_01_0011__en-us_topic_0112596104_en-us_topic_0075378957_li58001655123:

   Access SWR.

   a. Log in to the SWR console and then the VM running Docker as the **root** user.

   b. .. _swr_01_0011__li753764116129:

      In the navigation pane, choose **Dashboard** and click **Generate Login Command** in the upper right corner. On the displayed page, click |image1| to copy the login command.

      .. note::

         -  A temporary login command is valid for 24 hours. For details about how to obtain a login command that will remain valid for a long term, see :ref:`Obtaining a Long-Term Valid Docker Login Command <swr_01_1000>`. After you obtain a long-term valid login command, your temporary login commands will still be valid as long as they are in their validity periods.
         -  The domain name at the end of the login command is the image repository address. Record the address for later use.

   c. Run the **docker login** command on your Docker client (a device that has Docker installed).

      The message "Login Succeeded" will be displayed upon a successful login.

#. Run the following command on the device where Docker is installed to label the **nginx** image:

   **docker tag** *[Image name 1*:*tag 1]* *[Image repository address]*/*[Organization name]*/*[Image name 2*:*tag 2]*

   In the preceding command:

   -  [Image name 1:tag 1]: Replace it with the actual name and tag of the image to be pushed.
   -  [Image repository address]: You can query the address on the SWR console. It is the domain name at the end of the login command in :ref:`1.b <swr_01_0011__li753764116129>`.
   -  [Organization name]: Replace it with the name of the organization created.
   -  [Image name 2: tag 2]: Replace it with the desired image name and tag.

   Example:

   **docker tag nginx:v1 swr.eu-de.otc.t-systems.com/group/nginx:v1**

#. Push the image to the image repository by running the following command:

   **docker push** *[Image repository address]*/*[Organization name]*/*[Image name* 2:*tag 2]*

   Example:

   **docker push swr.eu-de.otc.t-systems.com/group/nginx:v1**

   The following information will be returned upon a successful push:

   .. code-block::

      6d6b9812c8ae: Pushed
      695da0025de6: Pushed
      fe4c16cbf7a4: Pushed
      v1: digest: sha256:eb7e3bbd8e3040efa71d9c2cacfa12a8e39c6b2ccd15eac12bdc49e0b66cee63 size: 948

   To view the pushed image, refresh the **My Images** page.

containerd
----------

#. Log in to the SWR console.

#. In the navigation pane, choose **My Images**. Then click the name of the target image.

#. .. _swr_01_0011__li16192124154316:

   On the **Pull/Push** tab, click **Generate Push Command** and copy the command.

   .. note::

      The command is only valid for six hours after it is generated. To obtain a long-term valid command, see :ref:`Obtaining a Long-Term Valid containerd Pull/Push Command <swr_01_1001>`.

#. Log in to the VM running containerd as the **root** user.

#. Run the command copied in :ref:`3 <swr_01_0011__li16192124154316>`.

   |image2|

#. Check whether the image is pushed successfully.

.. |image1| image:: /_static/images/en-us_image_0000002319267849.png
.. |image2| image:: /_static/images/en-us_image_0000002037092213.png
