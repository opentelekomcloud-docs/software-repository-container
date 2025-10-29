:original_name: swr_02_0072.html

.. _swr_02_0072:

Updating an Account An Image Is Shared With
===========================================

Description
-----------

Update an account an image is shared with.

Constraints
-----------

None

URI
---

PATCH /v2/manage/namespaces/{namespace}/repositories/{repository}/access-domains/{access_domain}

.. table:: **Table 1** Path parameters

   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
   +===============+===========+========+=================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | namespace     | Yes       | String | Organization name. Enter 1 to 64 characters, starting with a lowercase letter and ending with a lowercase letter or digit. Only lowercase letters, digits, periods (.), underscores (_), and hyphens (-) are allowed. Periods, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed.                                                                              |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | repository    | Yes       | String | Image repository name. Enter 1 to 128 characters. It must start and end with a lowercase letter or digit. Only lowercase letters, digits, periods (.), slashes (/), underscores (_), and hyphens (-) are allowed. Periods, slashes, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed. Replace a slash (/) with a dollar sign ($) before you send the request. |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | access_domain | Yes       | String | Name of the account used for image sharing.                                                                                                                                                                                                                                                                                                                                                                                     |
   +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------+-----------+--------+-------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                 |
   +=============+===========+========+=============================================================+
   | permit      | Yes       | String | Currently, only the read permission is supported.           |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | deadline    | Yes       | String | Valid until (UTC). **forever** indicates permanently valid. |
   +-------------+-----------+--------+-------------------------------------------------------------+
   | description | No        | String | Description. This parameter is left blank by default.       |
   +-------------+-----------+--------+-------------------------------------------------------------+

Response Parameters
-------------------

None

Example Request
---------------

.. code-block::

   PATCH https://{endpoint}/v2/manage/namespaces/{namespace}/repositories/{repository}/access-domains

   {
     "permit" : "read",
     "deadline" : "2018-10-01T16:00:00.000Z",
     "description" : "description"
   }

Example Response
----------------

None

Status Codes
------------

=========== =======================
Status Code Description
=========== =======================
201         Modification succeeded.
400         Request error.
401         Authentication failed.
500         Internal error.
=========== =======================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
