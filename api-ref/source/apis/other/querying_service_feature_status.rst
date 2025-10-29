:original_name: swr_02_0122.html

.. _swr_02_0122:

Querying Service Feature Status
===============================

Description
-----------

Query service feature status.

Constraints
-----------

None

URI
---

GET /v2/manage/projects/{project_id}/feature-gates

.. table:: **Table 1** Path parameter

   ========== ========= ====== ===========
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===========
   project_id Yes       String Project ID.
   ========== ========= ====== ===========

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                      |
   +=================+=================+=================+==================================================================================================+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                      |
   |                 |                 |                 |                                                                                                  |
   |                 |                 |                 | It can be obtained by calling the IAM API (value of **X-Subject-Token** in the response header). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   ================== ======= ============================================
   Parameter          Type    Description
   ================== ======= ============================================
   enable_experience  Boolean Whether the experience center is enabled.
   enable_hss_service Boolean Whether interconnection with HSS is enabled.
   enable_image_scan  Boolean Whether image scanning is enabled.
   enable_sm3         Boolean Whether SM algorithms are enabled.
   enable_image_sync  Boolean Whether image synchronization is enabled.
   enable_cci_service Boolean Whether interconnection with CCI is enabled.
   enable_image_label Boolean Whether image tagging is enabled.
   enable_pipeline    Boolean Whether the pipeline service is enabled.
   ================== ======= ============================================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/manage/projects/{project_id}/feature-gates

Example Response
----------------

**Status code: 200**

Query service feature status.

.. code-block::

   {
     "enable_experience" : true,
     "enable_hss_service" : true,
     "enable_image_scan" : true,
     "enable_sm3" : true,
     "enable_image_sync" : true,
     "enable_cci_service" : true,
     "enable_image_label" : false,
     "enable_pipeline" : false,
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
