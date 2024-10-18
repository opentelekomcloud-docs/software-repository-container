:original_name: swr_02_0032.html

.. _swr_02_0032:

Updating the Brief Information on an Image Repository
=====================================================

Function
--------

Update the brief information on an image repository in an organization, including the **category**, **is_public**, and **description**.

URI
---

PATCH /v2/manage/namespaces/{*namespace*}/repos/{*repository*}

For details about parameters, see :ref:`Table 1 <swr_02_0032__table16521054337>`.

.. _swr_02_0032__table16521054337:

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

.. table:: **Table 3** Request body parameters

   +-------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type    | Description                                                                                                                             |
   +=============+===========+=========+=========================================================================================================================================+
   | is_public   | Yes       | Boolean | Whether the repository is public. **true** indicates that the repository is public. **false** indicates that the repository is private. |
   +-------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | category    | No        | String  | Repository type. The value can be **app_server**, **linux**, **framework_app**, **database**, **lang**, **arm**, or **other**.          |
   +-------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String  | Brief description of the image repository.                                                                                              |
   +-------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------+

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

Status Code
-----------

+-------------+---------------------------------------------------------------------------+
| Status Code | Description                                                               |
+=============+===========================================================================+
| 201         | The brief information about the image repository is successfully updated. |
+-------------+---------------------------------------------------------------------------+
| 400         | Request error. Error information is returned.                             |
+-------------+---------------------------------------------------------------------------+
| 401         | Authentication failed.                                                    |
+-------------+---------------------------------------------------------------------------+
| 404         | The repository does not exist.                                            |
+-------------+---------------------------------------------------------------------------+
| 500         | Internal error. Error information is returned.                            |
+-------------+---------------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
