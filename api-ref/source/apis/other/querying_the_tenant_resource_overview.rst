:original_name: swr_02_0120.html

.. _swr_02_0120:

Querying the Tenant Resource Overview
=====================================

Description
-----------

Query the tenant resource overview.

Constraints
-----------

None

URI
---

GET /v2/manage/overview

Request Parameters
------------------

.. table:: **Table 1** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | Content-Type    | Yes             | String          | Message body type (format). Possible values:                                                     |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | application/json;charset=utf-8                                                                   |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | application/json                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                      |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   ============= ======= =====================================
   Parameter     Type    Description
   ============= ======= =====================================
   domain_id     String  Tenant ID.
   domain_name   String  Tenant name.
   namspace_num  Integer Number of namespaces of the tenant.
   repo_num      Integer Number of repositories of the tenant.
   image_num     Integer Number of images of the tenant.
   store_space   Double  Storage size of the tenant.
   downflow_size Double  Download traffic of the tenant.
   ============= ======= =====================================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/manage/overview

Example Response
----------------

**Status code: 200**

Query the tenant resource overview.

.. code-block::

   {
     "domain_id" : "08d35*********113760",
     "domain_name" : "",
     "namspace_num" : 36,
     "repo_num" : 20,
     "image_num" : 36,
     "store_space" : 99.21,
     "downflow_size" : 0
   }

Status Codes
------------

=========== ======================
Status Code Description
=========== ======================
200         Succeeded.
400         Request error.
401         Authentication failed.
500         Internal error.
=========== ======================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
