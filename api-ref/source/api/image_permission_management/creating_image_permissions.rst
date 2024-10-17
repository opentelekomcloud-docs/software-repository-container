:original_name: swr_02_0046.html

.. _swr_02_0046:

Creating Image Permissions
==========================

Function
--------

Grant permissions of an image to certain users so that they can manage, edit, and read the image.

URI
---

POST /v2/manage/namespaces/{*namespace*}/repos/{*repository*}/access

For details about parameters, see :ref:`Table 1 <swr_02_0046__table73271639103420>`.

.. _swr_02_0046__table73271639103420:

.. table:: **Table 1** Parameter description

   ========== ========= ====== ==================
   Parameter  Mandatory Type   Description
   ========== ========= ====== ==================
   namespace  Yes       String Organization name.
   repository Yes       String Image name.
   ========== ========= ====== ==================

Request
-------

-  Request parameters

   .. table:: **Table 2** Request header parameters

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
      +=================+=================+=================+=============================================================================================================================+
      | Content-Type    | Yes             | String          | Message body type (format). The value can be **application/json** or **charset=utf-8 application/json**.                    |
      |                 |                 |                 |                                                                                                                             |
      |                 |                 |                 | The default value is **application/json**.                                                                                  |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
      | X-Auth-Token    | Yes             | String          | User token.                                                                                                                 |
      |                 |                 |                 |                                                                                                                             |
      |                 |                 |                 | The token can be obtained by calling an IAM API. The value of **X-Subject-Token** in the response header is the user token. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Request body parameter description

      +-------------------+-----------+--------------------------------------------------------+--------------+
      | Parameter         | Mandatory | Type                                                   | Description. |
      +===================+===========+========================================================+==============+
      | *[Array element]* | Yes       | Array of :ref:`objects <swr_02_0046__table6912142367>` | User list    |
      +-------------------+-----------+--------------------------------------------------------+--------------+

   .. _swr_02_0046__table6912142367:

   .. table:: **Table 4** *[Array element]* parameters decription

      +-----------------+-----------------+-----------------+-------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                         |
      +=================+=================+=================+=====================================+
      | user_id         | Yes             | String          | User ID.                            |
      +-----------------+-----------------+-----------------+-------------------------------------+
      | user_name       | Yes             | String          | Username.                           |
      +-----------------+-----------------+-----------------+-------------------------------------+
      | auth            | Yes             | Integer         | User permission that is configured. |
      |                 |                 |                 |                                     |
      |                 |                 |                 | -  7: Manage                        |
      |                 |                 |                 | -  3: Write                         |
      |                 |                 |                 | -  1: Read                          |
      +-----------------+-----------------+-----------------+-------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v2/manage/namespaces/{namespace}/repos/{repository}/access

      [ {
        "user_id" : "fb3f175c1fd146ab8cdae3272be6107b",
        "user_name" : "user01",
        "auth" : 1
      } ]

Response
--------

-  Response parameters

   N/A

-  Example response

   None

Status Code
-----------

=========== =========================
Status Code Description
=========== =========================
201         Creation successful.
400         Request error.
401         Authentication failed.
404         The image does not exist.
500         Internal error.
=========== =========================

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
