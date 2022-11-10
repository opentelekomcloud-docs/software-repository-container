:original_name: swr_faq_0013.html

.. _swr_faq_0013:

SWR Overview
============

How Many Images Can Be Stored in SWR?
-------------------------------------

SWR has no limit on the number of images. You can upload any number of images.

Can I Push Arm-based Container Images to SWR?
---------------------------------------------

SWR has no restriction on the kernel architecture of images. There is no difference between pushing an Arm-based image and an x86-based image to SWR.

What Protocol Is Used to Push Images to SWR When I Run the docker push Command?
-------------------------------------------------------------------------------

HTTPS is used.

Will an Image Be Overwritten If I Push an Image That Have the Same Name and Tag with it?
----------------------------------------------------------------------------------------

Yes, the original image will be overwritten.
