:original_name: swr_faq_0005.html

.. _swr_faq_0005:

Why Is an Image Uploaded Through the Client to SWR Different in Size From One Uploaded Through the SWR Console?
===============================================================================================================

Symptom
-------

Assume that a nginx image of v2.0.0 is created on the local Docker client. The **docker images** command is run to query **SIZE** of the image. The size is **22.8 MB**.

.. code-block::

   $ docker images
   REPOSITORY                         TAG             IMAGE ID       CREATED         SIZE
   nginx                              v2.0.0          22f2bf2e2b4f   9 days ago      22.8MB

#. Run the **docker push** command to upload the image to SWR. The size of the image is **9.5 MB**.
#. On the local Docker client, pack the image into a **.tar** package. Download the **nginx.tar** package to the local host, and upload the package to SWR. The size of the package is **23.2 MB**.

The size of the image uploaded through the client is different from that of the image uploaded through the SWR console.

Cause Analysis
--------------

Image layers are compressed into **.tgz** packages when images are uploaded to SWR through the client, whereas when they are uploaded through the SWR console, they are only packed without being compressed. Therefore, the same image will be of different sizes when it is uploaded in these two different ways.
