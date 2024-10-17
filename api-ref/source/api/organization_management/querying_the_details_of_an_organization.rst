:original_name: swr_02_0029.html

.. _swr_02_0029:

Querying the Details of an Organization
=======================================

Function
--------

Query the details of an organization by its name.

URI
---

GET /v2/manage/namespaces/{*namespace*}

For details about parameters, see :ref:`Table 1 <swr_02_0029__table05962819187>`.

.. _swr_02_0029__table05962819187:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =================
   Parameter Mandatory Type   Description
   ========= ========= ====== =================
   namespace Yes       String Organization name
   ========= ========= ====== =================

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

Response Parameters
-------------------

Status code: 200

.. table:: **Table 3** Response body parameter description

   +-----------------------+-----------------------+-----------------------+
   | Parameter             | Type                  | Description           |
   +=======================+=======================+=======================+
   | id                    | Integer               | Organization ID       |
   +-----------------------+-----------------------+-----------------------+
   | name                  | String                | Organization name     |
   +-----------------------+-----------------------+-----------------------+
   | creator_name          | String                | IAM username          |
   +-----------------------+-----------------------+-----------------------+
   | auth                  | Integer               | User permission       |
   |                       |                       |                       |
   |                       |                       | -  7: Manage          |
   |                       |                       | -  3: Write           |
   |                       |                       | -  1: Read            |
   +-----------------------+-----------------------+-----------------------+

Example Request
---------------

.. code-block:: text

   GET https://{Endpoint}/v2/manage/namespaces/group

Example Response
----------------

.. code-block::

   {
       "id": 1422,
       "name": "group",
       "creator_name": "username",
       "auth": 7
   }

Status Code
-----------

=========== ================================
Status Code Description
=========== ================================
200         Query succeeded.
400         Request error.
401         Authentication failed.
404         The organization does not exist.
500         Internal error.
=========== ================================

Error Codes
-----------

For details, see :ref:`Error Codes <swr_02_0024>`.
