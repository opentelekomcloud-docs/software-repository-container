:original_name: swr_03_0005.html

.. _swr_03_0005:

Permissions
===========

If you need to grant your enterprise personnel permission to access your SWR resources, use Identity and Access Management (IAM). IAM provides identity authentication, fine-grained permissions management, and access control. IAM helps you secure access to your cloud resources.

With IAM, you can create IAM users and grant them permission to access only specific resources. For example, if you want some software developers in your enterprise to be able to use SWR resources but not be able to delete the resources or perform any other high-risk operations, you can create IAM users and grant permission to use SWR resources but not permission to delete them.

If your cloud account does not require individual IAM users for permissions management, you can skip this section.

IAM is a free service. You only pay for the resources in your account.

SWR Permissions
---------------

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and then attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

SWR is a project-level service deployed for specific regions. When you set **Scope** to **Region-specific projects** and select the specified projects in the specified regions, the users only have permissions for SWR resources in the selected projects. When accessing SWR, the users need to switch to the authorized region.

You can grant permissions by using roles and policies.

-  Roles: A coarse-grained authorization strategy that defines permissions by job responsibility. Only a limited number of service-level roles are available for authorization. Cloud services often depend on each other. When you grant permissions using roles, you also need to attach any existing role dependencies. Roles are not ideal for fine-grained authorization and least privilege access.
-  Policies: A fine-grained authorization strategy that defines permissions required to perform operations on specific cloud resources under certain conditions. This type of authorization is more flexible and is ideal for least privilege access. For example, you can grant IAM users only permission to manage a certain type of ECSs.

:ref:`Table 1 <swr_03_0005__en-us_topic_0000001880043537_table4990131931715>` and :ref:`Table 2 <swr_03_0005__en-us_topic_0000001880043537_table1409182914134>` describe all system-defined policies and roles of SWR.

.. _swr_03_0005__en-us_topic_0000001880043537_table4990131931715:

.. table:: **Table 1** System-defined policies of SWR (recommended)

   ================== ============================== =====================
   Policy             Description                    Type
   ================== ============================== =====================
   SWR FullAccess     Full permissions for SWR.      System-defined policy
   SWR OperateAccess  Operation permissions for SWR. System-defined policy
   SWR ReadOnlyAccess Read-only permission for SWR.  System-defined policy
   ================== ============================== =====================

.. _swr_03_0005__en-us_topic_0000001880043537_table1409182914134:

.. table:: **Table 2** System-defined roles of SWR

   +------------------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+
   | Role                   | Description                                                                                                              | Type                |
   +========================+==========================================================================================================================+=====================+
   | SWR Admin              | Administrator permissions for SWR. Users with this role can perform all operations on SWR resources.                     | System-defined role |
   +------------------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+
   | Tenant Administrator   | Administrator permissions for all services except IAM. Users with this role can perform all operations on SWR resources. | System-defined role |
   +------------------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+
   | ServiceStage Developer | ServiceStage developer permissions. For example, users with this role can pull images.                                   | System-defined role |
   +------------------------+--------------------------------------------------------------------------------------------------------------------------+---------------------+

:ref:`Table 3 <swr_03_0005__en-us_topic_0000001880043537_table129908203111>` lists the common operations supported by system-defined permissions for SWR.

.. _swr_03_0005__en-us_topic_0000001880043537_table129908203111:

.. table:: **Table 3** Common operations supported by system-defined permissions

   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Operation                    | SWR FullAccess | SWR OperateAccess | SWR ReadOnlyAccess | SWR Administrator | Tenant Administrator |
   +==============================+================+===================+====================+===================+======================+
   | Uploading/Pushing an Image   | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Downloading/Pulling an Image | Y              | Y                 | Y                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Adding a trigger             | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Modifying an image           | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Sharing an image             | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Assigning permissions        | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Deleting an image or a tag   | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Creating an organization     | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
   | Deleting an organization     | Y              | Y                 | x                  | Y                 | Y                    |
   +------------------------------+----------------+-------------------+--------------------+-------------------+----------------------+
