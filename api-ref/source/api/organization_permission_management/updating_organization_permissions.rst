:original_name: swr_02_0044.html

.. _swr_02_0044:

Updating Organization Permissions
=================================

Function
--------

Update the organization operation permissions for certain users.

URI
---

PATCH /v2/manage/namespaces/{*namespace*}/access

For details about parameters, see :ref:`Table 1 <swr_02_0044__table73271639103420>`.

.. _swr_02_0044__table73271639103420:

.. table:: **Table 1** Parameter description

   ========= ========= ====== ==================
   Parameter Mandatory Type   Description
   ========= ========= ====== ==================
   namespace Yes       String Organization name.
   ========= ========= ====== ==================

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

      +-----------------+-----------+--------------------------------------------------------+------------------------------------------------------------+
      | Parameter       | Mandatory | Type                                                   | Description                                                |
      +=================+===========+========================================================+============================================================+
      | [Array element] | Yes       | Array of :ref:`objects <swr_02_0044__table6912142367>` | Information required for updating organization permissions |
      +-----------------+-----------+--------------------------------------------------------+------------------------------------------------------------+

   .. _swr_02_0044__table6912142367:

   .. table:: **Table 4** [Array element]

      +-----------------+-----------------+-----------------+-------------------------------+
      | Parameter       | Mandatory       | Type            | Description                   |
      +=================+=================+=================+===============================+
      | user_id         | Yes             | String          | User ID. Obtain it from IAM.  |
      +-----------------+-----------------+-----------------+-------------------------------+
      | user_name       | Yes             | String          | Username. Obtain it from IAM. |
      +-----------------+-----------------+-----------------+-------------------------------+
      | auth            | Yes             | Integer         | User permission               |
      |                 |                 |                 |                               |
      |                 |                 |                 | -  7: Manage                  |
      |                 |                 |                 | -  3: Write                   |
      |                 |                 |                 | -  1: Read                    |
      +-----------------+-----------------+-----------------+-------------------------------+

-  Example request

   .. code-block::

      PATCH https://{endpoint}/v2/manage/namespaces/{namespace}/access

      [ {
        "user_id" : "fb3f175c1fd146ab8cdae3272be6107b",
        "user_name" : "user01",
        "auth" : 7
      } ]

Response
--------

-  Response parameters

   N/A

-  Example response

   .. code-block::

      {}

Status Code
-----------

=========== ================================
Status Code Description
=========== ================================
201         Updated successfully.
400         Request error.
401         Authentication failed.
404         The organization does not exist.
500         Internal error.
=========== ================================

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
