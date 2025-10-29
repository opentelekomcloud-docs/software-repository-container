:original_name: swr_02_0121.html

.. _swr_02_0121:

Querying Tenant Resource Statistics
===================================

Description
-----------

Query tenant resource statistics.

Constraints
-----------

None

URI
---

GET /v2/manage/reports/{resource_type}/{frequency}

.. table:: **Table 1** Path parameters

   ============= ========= ====== ===============
   Parameter     Mandatory Type   Description
   ============= ========= ====== ===============
   resource_type Yes       String Resource type.
   frequency     Yes       String Frequency type.
   ============= ========= ====== ===============

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

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

.. table:: **Table 3** Response body parameter

   +-----------+----------------------------------------------------------------------------------------------------+-------------+
   | Parameter | Type                                                                                               | Description |
   +===========+====================================================================================================+=============+
   | *[items]* | Array of :ref:`ReportData <swr_02_0121__en-us_topic_0000002095992748_response_reportdata>` objects | Statistics. |
   +-----------+----------------------------------------------------------------------------------------------------+-------------+

.. _swr_02_0121__en-us_topic_0000002095992748_response_reportdata:

.. table:: **Table 4** ReportData

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   date      String Time point.
   value     Double Statistics.
   ========= ====== ===========

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v2/reports/{resource_type}/{frequency}

Example Response
----------------

**Status code: 200**

Query tenant resource statistics.

.. code-block::

   [ {
     "date" : "2024-09-01",
     "value" : 0
   }, {
     "date" : "2024-09-02",
     "value" : 0
   } ]

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

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
