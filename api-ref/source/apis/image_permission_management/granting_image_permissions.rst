:original_name: swr_02_0046.html

.. _swr_02_0046:

Granting Image Permissions
==========================

Description
-----------

Grant permissions of an image to certain users so that they can manage, edit, and read the image.

Constraints
-----------

You can grant permissions to other users (excluding yourself) only when the organization permission is **Edit** or higher or the image repository permission is **Manage**.

URI
---

POST /v2/manage/namespaces/{namespace}/repos/{repository}/access

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

.. table:: **Table 3** Request body parameter

   +-----------+-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                          | Description                                          |
   +===========+===========+===============================================================================================+======================================================+
   | [items]   | Yes       | Array of :ref:`UserAuth <swr_02_0046__en-us_topic_0000001231313913_request_userauth>` objects | Information required for creating image permissions. |
   +-----------+-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _swr_02_0046__en-us_topic_0000001231313913_request_userauth:

.. table:: **Table 4** UserAuth

   +-----------+-----------+--------+-------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                 |
   +===========+===========+========+=============================================================+
   | user_id   | Yes       | String | User ID, which needs to be obtained from IAM.               |
   +-----------+-----------+--------+-------------------------------------------------------------+
   | user_name | Yes       | String | Username, which needs to be obtained from IAM.              |
   +-----------+-----------+--------+-------------------------------------------------------------+
   | auth      | Yes       | Long   | User permissions. **7**: Manage. **3**: Write. **1**: Read. |
   +-----------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   POST https://{endpoint}/v2/manage/namespaces/{namespace}/repos/{repository}/access

   [ {
     "user_id" : "fb3f175c1fd146ab8cdae3272be6107b",
     "user_name" : "user01",
     "auth" : 1
   } ]

Example Response
----------------

None

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
201         Request succeeded.
400         Request error.
401         Authentication failed.
404         The image was not found.
500         Internal error.
=========== ========================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
