:original_name: swr_02_0032.html

.. _swr_02_0032:

Updating the Brief Information on an Image Repository
=====================================================

Description
-----------

Update the brief information on an image in an organization of a tenant, including the **category**, **is_public**, and **description**.

Constraints
-----------

None

URI
---

PATCH /v2/manage/namespaces/{namespace}/repos/{repository}

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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                           |
   +=================+=================+=================+=======================================================================================================================================================+
   | Content-Type    | Yes             | String          | Message body type (format). The value can be **application/json** or **charset=utf-8 application/json**.                                              |
   |                 |                 |                 |                                                                                                                                                       |
   |                 |                 |                 | Default value: **application/json**                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                       |
   |                 |                 |                 | The token can be obtained through the IAM API used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                                                                                                                                            |
   +=============+===========+=========+========================================================================================================================================================================================+
   | is_public   | Yes       | Boolean | Whether the repository is a public repository. When the value is **true**, it indicates the repository is public. When the value is **false**, it indicates the repository is private. |
   +-------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | category    | No        | String  | Repository type. The value can be **app_server**, **linux**, **framework_app**, **database**, **lang**, **other**, **windows**, or **arm**.                                            |
   +-------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String  | Brief description of the image repository.                                                                                                                                             |
   +-------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   PATCH https://{endpoint}/v2/manage/namespaces/{namespace}/repos/{repository}

   {
     "category" : "database",
     "description" : "this is a busybox repository",
     "is_public" : false
   }

Example Response
----------------

None

Status Codes
------------

=========== =====================================================
Status Code Description
=========== =====================================================
201         Brief information about the image repository updated.
400         Request error.
401         Authentication failed.
404         The image repository was not found
500         Internal error.
=========== =====================================================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
