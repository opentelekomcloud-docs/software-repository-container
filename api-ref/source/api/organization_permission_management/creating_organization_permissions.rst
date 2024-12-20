:original_name: swr_02_0042.html

.. _swr_02_0042:

Creating Organization Permissions
=================================

Function
--------

Grant permissions of an organization to certain users so that they can manage, edit, and read images from the organization.

Constraints
-----------

None

URI
---

POST /v2/manage/namespaces/{*namespace*}/access

:ref:`Table 1 <swr_02_0042__table1860452124716>` describes the parameters.

.. _swr_02_0042__table1860452124716:

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

   .. table:: **Table 3** Request body parameters

      +-----------------+-----------+----------------------------------------------------------+-------------------------------------------------------------+
      | Parameter       | Mandatory | Type                                                     | Description                                                 |
      +=================+===========+==========================================================+=============================================================+
      | [Array element] | Yes       | Array of :ref:`objects <swr_02_0042__table196185211479>` | Information required for creating organization permissions. |
      +-----------------+-----------+----------------------------------------------------------+-------------------------------------------------------------+

   .. _swr_02_0042__table196185211479:

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

   .. code-block:: text

      POST https://{endpoint}/v2/manage/namespaces/{namespace}/access

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

   .. code-block::

      None

Status Code
-----------

=========== ===========================================
Status Code Description
=========== ===========================================
201         Creation successful.
400         Request error.
401         Authentication failed.
404         The organization does not exist.
409         The organization permission already exists.
500         Internal error.
=========== ===========================================

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
