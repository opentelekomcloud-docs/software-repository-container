:original_name: swr_02_0049.html

.. _swr_02_0049:

Querying Image Permissions
==========================

Description
-----------

Query image permissions.

Constraints
-----------

None

URI
---

GET /v2/manage/namespaces/{namespace}/repos/{repository}/access

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------+------------------------------------------------------------------------------------------------+----------------------------------+
   | Parameter    | Type                                                                                           | Description                      |
   +==============+================================================================================================+==================================+
   | id           | Integer                                                                                        | Permission ID.                   |
   +--------------+------------------------------------------------------------------------------------------------+----------------------------------+
   | name         | String                                                                                         | Image name.                      |
   +--------------+------------------------------------------------------------------------------------------------+----------------------------------+
   | self_auth    | :ref:`UserAuth <swr_02_0049__en-us_topic_0000001231195475_response_userauth>` object           | Permissions of the current user. |
   +--------------+------------------------------------------------------------------------------------------------+----------------------------------+
   | others_auths | Array of :ref:`UserAuth <swr_02_0049__en-us_topic_0000001231195475_response_userauth>` objects | Permissions of other users.      |
   +--------------+------------------------------------------------------------------------------------------------+----------------------------------+

.. _swr_02_0049__en-us_topic_0000001231195475_response_userauth:

.. table:: **Table 4** UserAuth

   +-----------+--------+-------------------------------------------------------------+
   | Parameter | Type   | Description                                                 |
   +===========+========+=============================================================+
   | user_id   | String | User ID, which needs to be obtained from IAM.               |
   +-----------+--------+-------------------------------------------------------------+
   | user_name | String | Username, which needs to be obtained from IAM.              |
   +-----------+--------+-------------------------------------------------------------+
   | auth      | Long   | User permissions. **7**: Manage. **3**: Write. **1**: Read. |
   +-----------+--------+-------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/manage/namespaces/{namespace}/repos/{repository}/access

Example Response
----------------

**Status code: 200**

Query succeeded.

.. code-block::

   {
     "id" : 1422,
     "name" : "group",
     "self_auth" : {
       "user_id" : "3059e6b5562241fda3fa441cca6f228b",
       "user_name" : "user01",
       "auth" : 7
     },
     "others_auths" : [ {
       "user_id" : "fb3f175c1fd146ab8cdae3272be6107b",
       "user_name" : "user02",
       "auth" : 7
     } ]
   }

Status Codes
------------

=========== ========================
Status Code Description
=========== ========================
200         Query succeeded.
400         Request error.
401         Authentication failed.
404         The image was not found.
500         Internal error.
=========== ========================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
