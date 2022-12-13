:original_name: swr_faq_0035.html

.. _swr_faq_0035:

Can I Pull Container Images on the SWR Console to a Local PC?
=============================================================

Container images stored in SWR cannot be directly downloaded through the console. You can perform the following operations to pull the images:

#. Obtain the image pull command on the image details page.

#. Run the obtained command on the device where the Docker client is installed.

   Example:

   **docker pull swr.eu-de.otc.t-systems.com/group/nginx:v1**

#. Save the image as a TAR or TAR.GZ file.

   Example:

   **docker save** **nginx:v1** **>** **nginx.tar**

#. Download the file to the local host.
