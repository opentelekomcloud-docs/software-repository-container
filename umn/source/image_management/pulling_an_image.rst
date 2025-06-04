:original_name: swr_01_0017.html

.. _swr_01_0017:

Pulling an Image
================

Scenario
--------

You can run the **docker pull** command to pull images from SWR.

Procedure
---------

#. Log in to the VM running the container engine as the **root** user.

#. Obtain a login command by referring to :ref:`Step 1 <swr_01_0011__en-us_topic_0112596104_en-us_topic_0075378957_li58001655123>` and access SWR.

#. Log in to the SWR console.

#. In the navigation pane, choose **My Images** and click the target image.

#. .. _swr_01_0017__en-us_topic_0084266454_li197783469319:

   On the **Image Tags** tab page, in the same row as the target image tag, click |image1| in the **Image Pull Command** column to copy the command.


   .. figure:: /_static/images/en-us_image_0000001154597496.png
      :alt: **Figure 1** Obtaining the image pull command

      **Figure 1** Obtaining the image pull command

#. Run the **image pull** command obtained in :ref:`Step 5 <swr_01_0017__en-us_topic_0084266454_li197783469319>` on the VM.

   Run the **docker images** command to check whether the images are successfully pulled.

   .. code-block::

      # docker images
      REPOSITORY                                  TAG       IMAGE ID       CREATED         SIZE
      xxx/group/nginx                             v2.0.0    22f2bf2e2b4f   5 hours ago     22.8MB

#. (Optional) Run the following command to save the image as an archive file:

   **docker save** [*Image name:tag name*] **>** [*Archive file name*]

containerd
----------

#. Log in to the SWR console.

#. In the navigation pane, choose **My Images**. Then click the name of the target image.

#. .. _swr_01_0017__en-us_topic_0000001952079513_li16192124154316:

   On the **Tags** tab, click **containerd command** in the **Operation** column to copy the image pull command. Alternatively, go to the **Pull/Push** tab to copy the image pull command.

   .. note::

      The command is only valid for six hours after it is generated. To obtain a long-term valid command, see :ref:`Obtaining a Long-Term Valid containerd Pull/Push Command <swr_01_1001>`.

#. Log in to the VM running containerd as the **root** user.

#. Run the command copied in :ref:`3 <swr_01_0017__en-us_topic_0000001952079513_li16192124154316>`.

   -  If the command was copied from the **Operation** column, run it as follows.

      |image2|

   -  If the command was copied from the **Pull/Push** tab, run it as follows (replace *{Tag}* with the new image tag).

      |image3|

#. Check whether the image is pulled successfully.

   -  If the command was copied from the **Operation** column, run **crictl images** to check whether the pull is successful.

      |image4|

   -  If the command was copied from the **Pull/Push** tab, run **ctr images list** to check whether the pull is successful.

      |image5|

.. |image1| image:: /_static/images/en-us_image_0000002319087477.png
.. |image2| image:: /_static/images/en-us_image_0000002000854844.png
.. |image3| image:: /_static/images/en-us_image_0000002037053129.png
.. |image4| image:: /_static/images/en-us_image_0000002001013122.png
.. |image5| image:: /_static/images/en-us_image_0000002037094013.png
