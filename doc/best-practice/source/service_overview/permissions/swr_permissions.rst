:original_name: en-us_topic_0000001488156664.html

.. _en-us_topic_0000001488156664:

SWR Permissions
===============

By default, new IAM users do not have any permissions granted. You need to add them to one or more groups and attach permissions policies or roles to these groups. In this way, the users can inherit permissions from the groups and perform operations on specific cloud resources.

SWR is a project-level service deployed and accessed in specific physical regions. To assign AOM permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing SWR, the users need to switch to a Region where they have been authorized to use this service.

.. table:: **Table 1** SWR permissions

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

   -  `Granting user permissions <https://docs.otc.t-systems.com/en-us/usermanual/swr/swr_01_0015.html>`__ enables you to grant read, write, and management permissions to different users for them to access either a specific image or images of a specific organization.
