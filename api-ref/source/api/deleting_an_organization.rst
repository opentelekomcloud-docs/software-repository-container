:original_name: swr_02_0027.html

.. _swr_02_0027:

Deleting an Organization
========================

Function
--------

Delete an organization.

URI
---

DELETE /v2/manage/namespaces/{*namespace*}

For details about parameters, see :ref:`Table 1 <swr_02_0027__tae82a09e27434bef9a38b734d798ae6c>`.

.. _swr_02_0027__tae82a09e27434bef9a38b734d798ae6c:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =================
   Parameter Mandatory Type   Description
   ========= ========= ====== =================
   namespace Yes       String Organization name
   ========= ========= ====== =================

Request
-------

-  Request parameters

   N/A

-  Example request

   .. code-block:: text

      DELETE https://{Endpoint}/v2/manage/namespaces/group

Response
--------

N/A

Status Code
-----------

=========== ================================
Status Code Description
=========== ================================
204         Deleted successfully.
400         Request error.
401         Authentication failed.
404         The organization does not exist.
500         Internal error.
=========== ================================
