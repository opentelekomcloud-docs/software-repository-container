:original_name: swr_02_0036.html

.. _swr_02_0036:

Deleting the Image with a Specified Tag
=======================================

Function
--------

Delete the image with a specified tag in an image repository.

URI
---

DELETE /v2/manage/namespaces/{*namespace*}/repos/{*repository*}/tags/{*tag*}

For details about parameters, see :ref:`Table 1 <swr_02_0036__table05962819187>`.

.. _swr_02_0036__table05962819187:

.. table:: **Table 1** Parameter description

   ========== ========= ====== =====================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =====================
   namespace  Yes       String Organization name
   repository Yes       String Image repository name
   tag        Yes       String Image tag name
   ========== ========= ====== =====================

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

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/manage/namespaces/group/repos/busybox/tags/v1

Response
--------

N/A

Status Code
-----------

+-------------+------------------------------------------------------------------+
| Status Code | Description                                                      |
+=============+==================================================================+
| 204         | The image with a specified tag is deleted successfully.          |
+-------------+------------------------------------------------------------------+
| 400         | Request error. Error information is returned.                    |
+-------------+------------------------------------------------------------------+
| 401         | Authentication failed.                                           |
+-------------+------------------------------------------------------------------+
| 404         | The repository or the image with a specified tag does not exist. |
+-------------+------------------------------------------------------------------+
| 500         | Internal error. Error information is returned.                   |
+-------------+------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
