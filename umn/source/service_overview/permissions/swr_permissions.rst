:original_name: swr_03_0021.html

.. _swr_03_0021:

SWR Permissions
===============

By default, new IAM users do not have any permissions granted. You need to add them to one or more groups and attach permissions policies or roles to these groups. In this way, the users can inherit permissions from the groups and perform operations on specific cloud resources.

SWR is a project-level service deployed for specific regions. When you set **Scope** to **Region-specific projects** and select projects in specific regions, the users only have permissions for SWR resources in the selected projects. If you set **Scope** to **All resources**, the users have permissions for SWR resources in all region-specific projects. When accessing SWR, the users need to switch to the authorized region.

.. table:: **Table 1** System-defined permissions for SWR

   +------------------------+----------------------------------------------------------------------------------------------+---------------------+
   | Name                   | Description                                                                                  | Type                |
   +========================+==============================================================================================+=====================+
   | SWR Administrator      | SWR administrator permissions, including all SWR permissions.                                | System-defined role |
   +------------------------+----------------------------------------------------------------------------------------------+---------------------+
   | Tenant Administrator   | Administrator permissions for all services except IAM, including all SWR permissions.        | System-defined role |
   +------------------------+----------------------------------------------------------------------------------------------+---------------------+
   | Tenant Guest           | Read-only permissions for all services except IAM, including permissions such as image pull. | System-defined role |
   +------------------------+----------------------------------------------------------------------------------------------+---------------------+
   | ServiceStage Developer | ServiceStage developer permissions, including permissions such as image pull.                | System-defined role |
   +------------------------+----------------------------------------------------------------------------------------------+---------------------+

.. note::

   -  You can `grant permissions <https://docs.otc.t-systems.com/en-us/usermanual/swr/swr_01_0015.html>`__ (read, write, and manage permissions), to different users for them to access either a specific image or images in a specific organization.
