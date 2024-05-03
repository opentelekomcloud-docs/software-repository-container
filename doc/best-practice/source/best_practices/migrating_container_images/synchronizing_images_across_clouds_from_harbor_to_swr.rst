:original_name: cce_bestpractice_0332.html

.. _swr_bestpractice_0004:

Synchronizing Images Across Clouds from Harbor to SWR
=====================================================

Scenarios
---------

Harbor accesses SWR through a public network. For details, see :ref:`Accessing SWR Through a Public Network <swr_bestpractice_0004__en-us_topic_0291248669_section176591736173817>`.

Background
----------

Harbor is an open-source enterprise-class Docker Registry server developed by VMware. It extends the Docker Distribution by adding the functionalities such as role-based access control (RBAC), image scanning, and image replication. Harbor has been widely used to store and distribute container images.

.. _swr_bestpractice_0004__en-us_topic_0291248669_section176591736173817:

Accessing SWR Through a Public Network
--------------------------------------

#. .. _swr_bestpractice_0004__en-us_topic_0291248669_li137017409395:

   Configure a registry endpoint on Harbor.

   .. note::

      Open Telekom Cloud SWR has not yet integrated with Harbor. You need clone `this repo <https://github.com/akyriako/harbor/tree/opentelekomcloud_adapter>`__ and build it from branch **opentelekomcloud_adapter**.


   .. TODO: version of Harbor which supports OTC adaptor

   .. .. note::

   ..    Open Telekom Cloud SWR has integrated with Harbor 1.10.5 and later versions. You only need to set **Provider** to **Open Telekom Cloud SWR** when configuring your endpoint. This document uses Harbor 2.4.1 as an example.

   a. Add an endpoint.

      |image1|

   b. Configure the following parameters.

      |image2|

      -  **Provider**: Select **Open Telekom Cloud SWR**.
      -  **Name**: Enter a customized name.
      -  **Endpoint URL**: Enter the public network domain name of SWR in the format of **https://{SWR image repository address}**. To obtain the image repository address, log in to the SWR console, choose **My Images**, and click **Upload Through Client**. You can view the image repository address of the current region on the page that is displayed.
      -  **Access ID**: Enter an access ID in the format of **Regional project name@[AK]**.
      -  Access Secret: Enter an AK/SK. To obtain an AK/SK, see `Obtaining a Long-Term Valid Login Command <https://docs.otc.t-systems.com/software-repository-container/umn/image_management/obtaining_a_long-term_valid_login_command.html>`__.
      -  **Verify Remote Cert**: **Deselect** the option.

#. Configure a replication rule.

   a. Create a replication rule.

      |image3|

   b. Configure the following parameters.

      -  **Name**: Enter a customized name.

      -  **Replication mode**: Select **Push-based**, indicating that images are pushed from the local Harbor to the remote repository.

      -  **Source resource filter**: Filters images on Harbor based on the configured rules.

      -  **Destination registry**: Select the endpoint created in :ref:`1 <swr_bestpractice_0004__en-us_topic_0291248669_li137017409395>`.

      -  **Destination**

         **Namespace**: Enter the organization name on SWR.

         **Flattening**: Select **Flatten All Levels**, indicating that the hierarchy of the registry is reduced when copying images. If the directory of Harbor registry is **library/nginx** and the directory of the endpoint namespace is **dev-container**, after you flatten all levels, the directory of the endpoint namespace is **library/nginx -> dev-container/nginx**.

      -  **Trigger Mode**: Select **Manual**.

      -  **Bandwidth**: Set the maximum network bandwidth when executing the replication rule. The value **-1** indicates no limitation.

#. After creating the replication rule, select it and click **REPLICATE** to complete the replication.

   |image4|



.. |image1| image:: /_static/images/en-us_image_0000001469005545.png
.. |image2| image:: /_static/images/en-us_image_0000001418569120.png
.. |image3| image:: /_static/images/en-us_image_0000001468885853.png
.. |image4| image:: /_static/images/en-us_image_0000001418729104.png