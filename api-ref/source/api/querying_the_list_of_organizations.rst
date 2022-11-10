:original_name: swr_02_0028.html

.. _swr_02_0028:

Querying the List of Organizations
==================================

Function
--------

Query the list of organizations.

URI
---

GET /v2/manage/namespaces?filter=namespace::{*namespace*}

For details about parameters, see :ref:`Table 1 <swr_02_0028__tae82a09e27434bef9a38b734d798ae6c>`.

.. _swr_02_0028__tae82a09e27434bef9a38b734d798ae6c:

.. table:: **Table 1** Parameter description

   ========= ========= ====== =================
   Parameter Mandatory Type   Description
   ========= ========= ====== =================
   namespace No        String Organization name
   ========= ========= ====== =================

Request
-------

-  Request parameters

   N/A

-  Example request

   .. code-block:: text

      GET https://{Endpoint}/v2/manage/namespaces?filter=namespace::group

Response
--------

-  Response parameters

   .. table:: **Table 2** Response body parameter description

      +------------+-----------------------------------------------------------+-------------------+
      | Parameter  | Type                                                      | Description       |
      +============+===========================================================+===================+
      | namespaces | Array of :ref:`objects <swr_02_0028__table1787854911167>` | Organization list |
      +------------+-----------------------------------------------------------+-------------------+

   .. _swr_02_0028__table1787854911167:

   .. table:: **Table 3** namespaces parameter description

      +-----------------------+-----------------------+-----------------------+
      | Parameter             | Type                  | Description           |
      +=======================+=======================+=======================+
      | ID                    | Integer               | Organization ID       |
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

-  Example response

   .. code-block::

      {
          "namespaces": [
              {
                  "id": 1343008,
                  "name": "group",
                  "creator_name": "username",
                  "auth": 7
              }
          ]
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
