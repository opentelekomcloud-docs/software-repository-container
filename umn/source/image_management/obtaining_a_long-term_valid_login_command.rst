:original_name: swr_01_1000.html

.. _swr_01_1000:

Obtaining a Long-Term Valid Login Command
=========================================

Scenario
--------

This section describes how to obtain a login command that is valid for a year.

.. note::

   For security purposes, it is advised to obtain the login command in the development environment.

Procedure
---------

#. .. _swr_01_1000__li5768123671815:

   Obtain the region project name and image repository address.

   a. Log in to the management console, click your username in the upper right corner, and click **My Credentials**.
   b. On the **Project List** tab page, search for the project corresponding to the current region.
   c. Obtain the image repository address by referring to :ref:`1.b <swr_01_0011__en-us_topic_0112596104_li182568055016>`. The domain name at the end of the login command is the image repository address.

#. .. _swr_01_1000__li1863783911295:

   Obtain an AK/SK.

   .. note::

      The access key ID (AK) and secret access key (SK) are a pair of access keys used together to authenticate users who wish to make API requests. The AK/AS pair provides functions similar to a password. If you already have an AK/SK, skip this step.

   a. Log in to the management console, click your username in the upper right corner, and click **My Credentials**.
   b. On the **Access Keys** tab page, click **Add Access Key**.
   c. Enter the login password and verification code sent to your mailbox or mobile phone.
   d. Download the access key, which includes the AK and SK.

      .. note::

         Keep the access key secure and do not disclose it to any unauthorized personnel.

#. .. _swr_01_1000__li132430753010:

   Log in to a Linux PC and run the following command to obtain the login key:

   **printf "$AK" \| openssl dgst -binary -sha256 -hmac "$SK" \| od -An -vtx1 \| sed 's/[ \\n]//g' \| sed 'N;s/\\n//'**

   In the command, **$AK** and **$SK** indicate the AK and SK obtained in :ref:`Step 2 <swr_01_1000__li1863783911295>` respectively.


   .. figure:: /_static/images/en-us_image_0165729699.png
      :alt: **Figure 1** Sample command output

      **Figure 1** Sample command output

#. Put the information you obtained in the following format to generate a long-term valid login command:

   **docker login -u** [*Regional project name*]\ **@**\ [*AK*] **-p** [*Login key*] [*Image repository address*]

   In the command, the regional project name and image repository address are obtained in :ref:`Step 1 <swr_01_1000__li5768123671815>`, the AK in :ref:`Step 2 <swr_01_1000__li1863783911295>`, and the login key in :ref:`Step 3 <swr_01_1000__li132430753010>`.


   .. figure:: /_static/images/en-us_image_0000001154534788.png
      :alt: **Figure 2** Long-term login command

      **Figure 2** Long-term login command

   .. note::

      The login key is encrypted and cannot be decrypted. Therefore, other users cannot obtain the SK from -p.

      The login command can be used on other devices.

#. Run the **history -c** command to clear the operation records.
