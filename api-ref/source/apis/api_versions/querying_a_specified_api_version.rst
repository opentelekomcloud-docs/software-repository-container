:original_name: swr_02_0081.html

.. _swr_02_0081:

Querying a Specified API Version
================================

Description
-----------

Query a specified API version.

Constraints
-----------

None

URI
---

GET /{api_version}

.. table:: **Table 1** Path parameter

   =========== ========= ====== ============
   Parameter   Mandatory Type   Description
   =========== ========= ====== ============
   api_version Yes       String API version.
   =========== ========= ====== ============

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================+
   | Content-Type    | Yes             | String          | Message body type (format). The value can be **application/json** or **charset=utf-8 application/json**.                    |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | Default value: **application/json**                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+
   | X-Auth-Token    | Yes             | String          | User token.                                                                                                                 |
   |                 |                 |                 |                                                                                                                             |
   |                 |                 |                 | The token can be obtained by calling an IAM API. The value of **X-Subject-Token** in the response header is the user token. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameter

   +-----------+------------------------------------------------------------------------------------------------+-----------------------------+
   | Parameter | Type                                                                                           | Description                 |
   +===========+================================================================================================+=============================+
   | version   | :ref:`VersionDetail <swr_02_0081__en-us_topic_0000001185755798_response_versiondetail>` object | List of specified versions. |
   +-----------+------------------------------------------------------------------------------------------------+-----------------------------+

.. _swr_02_0081__en-us_topic_0000001185755798_response_versiondetail:

.. table:: **Table 4** VersionDetail

   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                         | Description                                                                                   |
   +=======================+==============================================================================+===============================================================================================+
   | id                    | String                                                                       | Version ID.                                                                                   |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | links                 | :ref:`Link <swr_02_0081__en-us_topic_0000001185755798_response_link>` object | API URL.                                                                                      |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | version               | String                                                                       | Maximum microversion. If microversions are not supported, the value is empty.                 |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | status                | String                                                                       | Version status. The value can be:                                                             |
   |                       |                                                                              |                                                                                               |
   |                       |                                                                              | -  **CURRENT**: The version is the primary version.                                           |
   |                       |                                                                              | -  **SUPPORTED**: The version is an earlier version, but it is still supported.               |
   |                       |                                                                              | -  **DEPRECATED**: The version is a deprecated version, which may be deleted later.           |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | updated               | String                                                                       | Version release time in UTC. For example, the release time of v1 is **2014-06-28T12:20:21Z**. |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | min_version           | String                                                                       | Minimum microversion. If microversions are not supported, the value is empty.                 |
   +-----------------------+------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+

.. _swr_02_0081__en-us_topic_0000001185755798_response_link:

.. table:: **Table 5** Link

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   href      String Link.
   rel       String Description.
   ========= ====== ============

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/{api_version}

Example Response
----------------

**Status code: 200**

Query succeeded.

.. code-block::

   {
     "version" : {
       "id" : "v2",
       "links" : {
         "href" : "https://swr-api.xxxx.mycloud.com/v2/",
         "rel" : "self"
       },
       "min_version" : "2.0",
       "status" : "CURRENT",
       "updated" : "2017-12-09T00:00:00Z",
       "version" : "2.26"
     }
   }

Status Codes
------------

=========== ================
Status Code Description
=========== ================
200         Query succeeded.
500         Internal error.
=========== ================

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
