:original_name: swr_02_0031.html

.. _swr_02_0031:

Deleting an Image Repository from an Organization
=================================================

Description
-----------

Delete an image repository in an organization.

Constraints
-----------

None

URI
---

DELETE /v2/manage/namespaces/{namespace}/repos/{repository}

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

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v2/manage/namespaces/{namespace}}/repos/{repository}

Example Response
----------------

None

Status Codes
------------

=========== ==================================
Status Code Description
=========== ==================================
204         Image repository deleted.
400         Request error.
401         Authentication failed.
404         The image repository was not found
500         Internal error.
=========== ==================================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
