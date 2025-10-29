:original_name: swr_02_0037.html

.. _swr_02_0037:

Querying Quotas
===============

Description
-----------

Query quota information.

Constraints
-----------

None

URI
---

GET /v2/manage/projects/{project_id}/quotas

.. table:: **Table 1** Path parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

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

.. table:: **Table 3** Response body parameter

   +-----------+--------------------------------------------------------------------------------------------------+-----------------+
   | Parameter | Type                                                                                             | Description     |
   +===========+==================================================================================================+=================+
   | quotas    | Array of :ref:`ShowQuota <swr_02_0037__en-us_topic_0000001207669790_response_showquota>` objects | List of quotas. |
   +-----------+--------------------------------------------------------------------------------------------------+-----------------+

.. _swr_02_0037__en-us_topic_0000001207669790_response_showquota:

.. table:: **Table 4** ShowQuota

   =========== ======= ============
   Parameter   Type    Description
   =========== ======= ============
   quota_limit Integer Quota limit.
   quota_key   String  Quota type.
   unit        String  Unit.
   used        Integer Used quota.
   =========== ======= ============

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/manage/projects/{project_id}/quotas

Example Response
----------------

**Status code: 200**

The quota information is returned successfully.

.. code-block::

   {
     "quotas" : [ {
       "quota_limit" : 15,
       "quota_key" : "namespace",
       "unit" : "",
       "used" : 1
     }
    ]
   }

Status Codes
------------

============ ======================
Status Codes Description
============ ======================
200          Succeeded.
400          Request error.
401          Authentication failed.
500          Internal error.
============ ======================
