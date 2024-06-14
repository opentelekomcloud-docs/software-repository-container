:original_name: swr_bestpractice_0015.html

.. _swr_bestpractice_0015:

Migrating Images to SWR Using image-syncer
==========================================

Scenarios
---------

If small quantity of images need to be migrated, you can use Docker commands. However, for thousands of images and several TBs of image repository data, it takes a long time and even data may be lost. In this case, you can use the open-source image migration tool `image-syncer <https://github.com/AliyunContainerService/image-syncer>`__.

Procedure
---------

#. Download, decompress, and run image-syncer.

   The following uses image-syncer v1.3.1 as an example.

   **wget https://github.com/AliyunContainerService/image-syncer/releases/download/v1.3.1/image-syncer-v1.3.1-linux-amd64.tar.gz**

   **tar -zvxf image-syncer-v1.3.1-linux-amd64.tar.gz**

#. Create **auth.json**, the authentication information file of the image repositories.

   image-syncer supports the Docker image repository based on Docker Registry V2. Enter the authentication information as required. In the following example, the image repository of eu-de is migrated to eu-nl.

   The following describes how to write the authentication information of the source and target repositories.

   .. code-block::

      {
          "swr.eu-de.otc.t-systems.com": {
              "username": "eu-de_otc@F1I3Q......",
              "password": "2fd4c969ea0......"
          },
          "swr.eu-nl.otc.t-systems.com": {
              "username": "eu-nl_otc@4N3FA......",
              "password": "f1c82b57855f9d35......"
          }
      }

   In the preceding commands, **swr.eu-de.otc.t-systems.com** indicates the image repository address. You can obtain the username and password from the login command as follows:

   Log in to the SWR console, and click **Generate Login Command** in the upper right corner to obtain the login command in the dialog box displayed, as shown in the following figure.

   .. _swr_bestpractice_0015__en-us_topic_0000001262561396_fig27182115592:

   .. figure:: /_static/images/en-us_image_0000001400827629.png
      :alt: **Figure 1** Generating a login command

      **Figure 1** Generating a login command

   In :ref:`the above figure <swr_bestpractice_0015__en-us_topic_0000001262561396_fig27182115592>`, **eu-de_otc@9LA......** is the username;

   **077be..............** is the password;

   **swr.eu-de.otc.t-systems.com** is the image repository address.

   .. caution::

      For security, the example username and password are random. You should use the actual username and password obtained from the console.

#. Create **images.json**, the image synchronization description file.

   In the following example, the source repository address is on the left, and the target repository address is on the right. image-syncer also supports other description modes. For details, see `README.md <https://github.com/AliyunContainerService/image-syncer/blob/master/README.md>`__.

   .. code-block::

      {
          "swr.eu-de.otc.t-systems.com/org-ss/canary-consumer": "swr.eu-nl.otc.t-systems.com/dev-container/canary-consumer"
      }

#. Run the following command to migrate the images to SWR:

   **./image-syncer --auth=./auth.json --images=./images.json --namespace=dev-container --registry=swr.eu-de.otc.t-systems.com --retries=3 --log=./log**

   .. table:: **Table 1** Command parameter description

      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                                                                                                                                                                                                     |
      +=============+=================================================================================================================================================================================================================================================================================+
      | --config    | Sets the path of config file. This file needs to be created before starting synchronization. Default config file is at "current/working/directory/config.json". (This flag can be replaced with flag **--auth** and **--images** which for better organization.)                |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --images    | Sets the path of image rules file. This file needs to be created before starting synchronization. Default config file is at "current/working/directory/images.json".                                                                                                            |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --auth      | Sets the path of authentication file. This file needs to be created before starting synchronization. Default config file is at "current/working/directory/auth.json".                                                                                                           |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --log       | Sets the path of log file. Logs will be printed to Stderr by default.                                                                                                                                                                                                           |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --namespace | Sets default-namespace. default-namespace can also be set by environment variable **DEFAULT_NAMESPACE**. If they are both set at the same time, **DEFAULT_NAMESPACE** will not work at this synchronization. default-namespace will work only if default-registry is not empty. |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --proc      | Number of goroutines. Default value is 5.                                                                                                                                                                                                                                       |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --retries   | Number of retries. Default value is 2. The retries of failed sync tasks will start after all sync tasks are executed once. Reties of failed sync tasks will resolve most occasional network problems during synchronization.                                                    |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | --registry  | Sets default-registry. Default-registry can also be set by environment variable **DEFAULT_REGISTRY**. If they are both set at the same time, **DEFAULT_REGISTRY** will not work at this synchronization. default-registry will work only if default-namespace is not empty.     |
      +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   After the migration command is executed, you can log in to the target image repository to view the migrated images.
