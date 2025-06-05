:original_name: swr_faq_2008.html

.. _swr_faq_2008:

Logins
======

What Are the Differences Between Long-Term and Temporary Login Commands?
------------------------------------------------------------------------

-  Temporary login commands expire 6 hours after they are generated. A temporary login command can be used for temporary use or one-time authorization. For production clusters that require high security, it can be used with periodic refresh.
-  Long-term login commands are permanently valid. A long-term login command can be used for preliminary tests, CI/CD pipelines, and image pull to container clusters.
-  After you obtain a long-term login command, your temporary login commands can still be valid as long as they are in their validity periods.

-  Both long-term and temporary login commands can be used by multiple users at the same time.

-  :ref:`What Do I Do If the Temporary Login Command Expired? <swr_faq_0052>`

.. toctree::
   :maxdepth: 1
   :hidden: 

   what_do_i_do_if_the_temporary_login_command_expired
