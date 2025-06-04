:original_name: swr_03_0007.html

.. _swr_03_0007:

Notes and Constraints
=====================

Quotas
------

Quotas are imposed on the number of organizations a user can create. :ref:`Table 1 <swr_03_0007__table1038894018383>` lists the quotas imposed by SWR.

.. _swr_03_0007__table1038894018383:

.. table:: **Table 1** SWR resource quotas

   ============= =====
   Resource Type Quota
   ============= =====
   Organization  5
   ============= =====

Requirements on Images to Upload
--------------------------------

-  If you use a container engine client to push images to SWR, the total number of image layers cannot exceed 20 at a time.
-  If you use a container engine client to push images to SWR, each image layer cannot exceed 10 GB.
