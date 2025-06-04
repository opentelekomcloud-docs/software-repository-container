:original_name: swr_faq_0039.html

.. _swr_faq_0039:

Image Push
==========

How Do I Push an Image to SWR by Calling an API?
------------------------------------------------

Currently, SWR does not provide an API for pushing images. You can push images using a container engine client or through the SWR console.

Can I Push Arm-based Container Images to SWR?
---------------------------------------------

SWR has no restriction on the kernel architecture of images. There is no difference between pushing an Arm-based image and an x86-based image to SWR.

What Protocol Is Used to Push Images to SWR When I Run the docker push Command?
-------------------------------------------------------------------------------

HTTPS is used.

Will an Image Be Overwritten If I Push an Image That Have the Same Name and Tag with it?
----------------------------------------------------------------------------------------

Yes, the original image will be overwritten.

What Is the Maximum Size of an SWR Layer?
-----------------------------------------

If you use the container engine client to push images to SWR, each image layer cannot exceed 10 GB.

What Is the Rate Limit for a Tenant to Push Images over the Internet?
---------------------------------------------------------------------

To avoid mutual interference between tenants when they push SWR images, the image push traffic for a single tenant is limited to 20 QPS. The traffic exceeding this value will be blocked. In this case, Docker will receive 503 and automatically retry traffic control requests.

Does SWR Support Resumable Image Push?
--------------------------------------

No.
