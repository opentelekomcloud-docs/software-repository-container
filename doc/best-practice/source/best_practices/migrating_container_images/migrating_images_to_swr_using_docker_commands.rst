:original_name: swr_bestpractice_0012.html

.. _swr_bestpractice_0012:

Migrating Images to SWR Using Docker Commands
=============================================

Scenarios
---------

SWR provides easy-to-use image hosting and efficient distribution services. If small quantity of images need to be migrated, enterprises can use the **docker pull/push** command to migrate images to SWR.

Procedure
---------

#. .. _swr_bestpractice_0012__en-us_topic_0000001281347382_en-us_topic_0000001262401516_li13905204219362:

   Pull images from the source repository.

   Run the **docker pull** command to pull the images.

   Example: **docker pull nginx:latest**

   Run the **docker images** command to check whether the images are successfully pulled.

   .. code-block::

      # docker images
      REPOSITORY                        TAG       IMAGE ID       CREATED         SIZE
      nginx                             latest    22f2bf2e2b4f   5 hours ago     22.8MB

#. Push the images pulled in :ref:`1 <swr_bestpractice_0012__en-us_topic_0000001281347382_en-us_topic_0000001262401516_li13905204219362>` to SWR.

   a. Log in to the VM where the target container is located and log in to SWR. For details, see `Uploading an Image Through a Container Engine Client <https://docs.otc.t-systems.com/software-repository-container/umn/image_management/uploading_an_image_through_the_client.html>`__.

   b. Tag the images.

      **docker tag** **[Image name:Tag name] [Image repository address]/[Organization name]/[Image name:Tag name]**

      Example:

      **docker tag nginx:v1 swr.eu-de.otc.t-systems.com/cloud-develop/nginx:v1**

   c. Run the following command to push the images to the target image repository.

      **docker push** **[Image repository address]/[Organization name]/[Image name:Tag name]**

      Example:

      **docker push swr.eu-de.otc.t-systems.com/cloud-develop/nginx:v1**

   d. Check whether the following information is returned. If yes, the push is successful.

      .. code-block::

         fbce26647e70: Pushed
         fb04ab8effa8: Pushed
         8f736d52032f: Pushed
         009f1d338b57: Pushed
         678bbd796838: Pushed
         d1279c519351: Pushed
         f68ef921efae: Pushed
         v1: digest: sha256:0cdfc7910db531bfa7726de4c19ec556bc9190aad9bd3de93787e8bce3385f8d size: 1780

      To view the pushed image, refresh the **My Images** page.
