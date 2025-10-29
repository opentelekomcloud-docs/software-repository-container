:original_name: swr_02_0057.html

.. _swr_02_0057:

Querying Image Retention Records
================================

Description
-----------

Query image retention records.

Constraints
-----------

None

URI
---

GET /v2/manage/namespaces/{namespace}/repos/{repository}/retentions/histories

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
   +============+===========+========+=================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | namespace  | Yes       | String | Organization name. Enter 1 to 64 characters, starting with a lowercase letter and ending with a lowercase letter or digit. Only lowercase letters, digits, periods (.), underscores (_), and hyphens (-) are allowed. Periods, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed.                                                                              |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | repository | Yes       | String | Image repository name. Enter 1 to 128 characters. It must start and end with a lowercase letter or digit. Only lowercase letters, digits, periods (.), slashes (/), underscores (_), and hyphens (-) are allowed. Periods, slashes, underscores, and hyphens cannot be placed next to each other. A maximum of two consecutive underscores are allowed. Replace a slash (/) with a dollar sign ($) before you send the request. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================================================================+
   | limit           | No              | String          | Number of returned records. Parameters **offset** and **limit** should always be used together.                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | String          | Start index. The value must be **0** or a positive number.                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                     |
   |                 |                 |                 | Parameters **offset** and **limit** should always be used together.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | filter          | No              | String          | Set this parameter to **limit**::{*limit*}\|\ **offset**::{*offset*}. **limit** indicates the number of returned records. **offset** indicates the start index. Parameters **offset** and **limit** should always be used together. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

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

.. table:: **Table 4** Response header parameter

   +---------------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                                                |
   +===============+========+============================================================================================================+
   | Content-Range | String | *Offset* (Start index) - *Count* (Number of records on the current page)/*Total* (Total number of records) |
   +---------------+--------+------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** Response body parameters

   +---------------+--------------------------------------------------------------------------------------------------------+----------------------+
   | Parameter     | Type                                                                                                   | Description          |
   +===============+========================================================================================================+======================+
   | retention_log | Array of :ref:`RetentionLog <swr_02_0057__en-us_topic_0000001186074278_response_retentionlog>` objects | Image retention log. |
   +---------------+--------------------------------------------------------------------------------------------------------+----------------------+
   | total         | Integer                                                                                                | Total number.        |
   +---------------+--------------------------------------------------------------------------------------------------------+----------------------+

.. _swr_02_0057__en-us_topic_0000001186074278_response_retentionlog:

.. table:: **Table 6** RetentionLog

   ============ ======= ==========================
   Parameter    Type    Description
   ============ ======= ==========================
   created_at   String  Creation time.
   id           Integer ID
   namespace    String  Organization name.
   repo         String  Image repository name.
   retention_id Integer Image retention policy ID.
   rule_type    String  Policy.
   tag          String  Image tag.
   ============ ======= ==========================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/manage/namespaces/{namespace}/repos/{repository}/retentions/histories

Example Response
----------------

**Status code: 200**

Request succeeded.

.. code-block::

   {
     "retention_log" : [ {
       "created_at" : "2020-04-17T08:01:09.658309Z",
       "id" : 9088,
       "namespace" : "hwstaff_l00283074",
       "repo" : "experience_2048",
       "retention_id" : 91,
       "rule_type" : "{\"template\":\"tag_rule\",\"params\":{\"num\":\"7\"},\"tag_selectors\":[]}",
       "tag" : "4"
     } ],
     "total" : 1
   }

Status Codes
------------

=========== =================================================
Status Code Description
=========== =================================================
200         Request succeeded.
400         Request error.
401         Authentication failed.
404         The organization or the repository was not found.
500         Internal error.
=========== =================================================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
