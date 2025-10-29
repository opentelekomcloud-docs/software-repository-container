:original_name: swr_02_0070.html

.. _swr_02_0070:

Sharing an Image with an Account
================================

Description
-----------

Share an image with an account. After pushing a private image, you can share it with other users and grant them permissions to pull the image.

Constraints
-----------

None

URI
---

POST /v2/manage/namespaces/{namespace}/repositories/{repository}/access-domains

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
   +============+===========+========+=================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | namespace  | Yes       | String | Organization name. Enter 1 to 64 characters, starting with a lowercase letter and ending with a lowercase letter or digit. Only lowercase letters, digits, periods (.), underscores (_), and hyphens (-) are allowed. Periods, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed.                                                                              |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | repository | Yes       | String | Image repository name. Enter 1 to 128 characters. It must start and end with a lowercase letter or digit. Only lowercase letters, digits, periods (.), slashes (/), underscores (_), and hyphens (-) are allowed. Periods, slashes, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed. Replace a slash (/) with a dollar sign ($) before you send the request. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 3** Request body parameters

   +---------------+-----------+--------+-------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                 |
   +===============+===========+========+=============================================================+
   | access_domain | Yes       | String | Shared tenant name.                                         |
   +---------------+-----------+--------+-------------------------------------------------------------+
   | permit        | Yes       | String | Currently, only the read permission is supported.           |
   +---------------+-----------+--------+-------------------------------------------------------------+
   | deadline      | Yes       | String | Valid until (UTC). **forever** indicates permanently valid. |
   +---------------+-----------+--------+-------------------------------------------------------------+
   | description   | No        | String | Description                                                 |
   +---------------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/manage/namespaces/{namespace}/repositories/{repository}/access-domains

   {
     "access_domain" : "demo",
     "permit" : "read",
     "deadline" : "2018-10-01T16:00:00.000Z",
     "description" : "description"
   }

Example Response
----------------

None

Status Codes
------------

=========== ==================================
Status Code Description
=========== ==================================
201         Creation succeeded.
400         Request error.
401         Authentication failed.
409         The shared account already exists.
500         Internal error.
=========== ==================================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
