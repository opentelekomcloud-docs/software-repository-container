:original_name: swr_02_0052.html

.. _swr_02_0052:

Generating a Temporary Login Command
====================================

Description
-----------

Generate a temporary login command using the value of **X-Swr-Dockerlogin** in the response header and the value of **host** in the response body.

Constraints
-----------

None

URI
---

POST /v2/manage/utils/secret

.. table:: **Table 1** Query parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                         |
   +=================+=================+=================+=====================================================+
   | projectname     | No              | String          | Project name. The default value is the region name. |
   |                 |                 |                 |                                                     |
   |                 |                 |                 | Example: **eu-de**                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                              |
   +=================+=================+=================+==========================================================================================================================================================+
   | Content-Type    | Yes             | String          | Message body type (format). The value can be **application/json** or **charset=utf-8 application/json**.                                                 |
   |                 |                 |                 |                                                                                                                                                          |
   |                 |                 |                 | Default value: **application/json**                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                          |
   |                 |                 |                 | The token can be obtained by calling the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response header parameter

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                           |
   +=======================+=======================+=======================================================================================+
   | X-Swr-Dockerlogin     | String                | Docker login command, for example:                                                    |
   |                       |                       |                                                                                       |
   |                       |                       | docker login -u ``********@``\ OW******FPUKBXI -p 6f0779072******863d1ae3ccef921b7f33 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+

.. table:: **Table 4** Response body parameter

   +-----------+---------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                        | Description                 |
   +===========+=============================================================================================+=============================+
   | auths     | Map<String,\ :ref:`AuthInfo <swr_02_0052__en-us_topic_0000001185755810_response_authinfo>`> | Authentication information. |
   +-----------+---------------------------------------------------------------------------------------------+-----------------------------+

.. _swr_02_0052__en-us_topic_0000001185755810_response_authinfo:

.. table:: **Table 5** AuthInfo

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   auth      String Base64-encoded authentication information.
   ========= ====== ==========================================

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/manage/utils/secret

Example Response
----------------

**Status code: 200**

Creation succeeded.

.. code-block::

   {
     "auths" : {
       "swr.xxx" : {
         "auth" : "Y24tbm9ydGg******hhMTgzMGVmN2RhZjJm"
       }
     }
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Creation succeeded.
400         Request error.
401         Authentication failed.
500         Internal error.
=========== ======================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
