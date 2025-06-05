:original_name: swr_faq_0016.html

.. _swr_faq_0016:

Why Does the Login Command Fail to Be Executed?
===============================================

Possible causes are as follows:

#. The container engine is not properly installed, in which case the following error is reported:

   **docker: command not found**

   **Solution**: Reinstall the container engine.

   -  To push images to SWR, the Docker version must be between 1.11.2 (included) and 24.0.9 (included).
   -  If the container engine client is in a private network, bind an elastic IP address (EIP) to the client. This EIP will allow the client to download installation packages from the website.

2. .. _swr_faq_0016__li1489599133814:

   The temporary login command has expired, or the regional project name, AK, or login key in the command is invalid. Error:

   **unauthorized: authentication required**

   **Solution**: Log in to the SWR console. In the navigation pane on the left, choose **My Images**. On the page displayed, click **Upload Through Client**. Then click |image1| to copy the login command.

3. The image repository address in the login command is incorrect, in which case the following error is reported:

   **Error logging in to v2 endpoint, trying next endpoint: Get https://{{endpoint}}/v2/: dial tcp: lookup {{endpoint}} on xxx.xxx.xxx.xxx:53 : no such host**

   **Solutions**:

   a. Change the image repository address in the login command.
   b. Generate a temporary login command. For detailed instructions, see :ref:`2 <swr_faq_0016__li1489599133814>`.

4. **x509: certificate has expired or is not yet valid**

   The preceding error is reported when the AK/SK in the login command with long-term validity is deleted. In this case, use a valid AK/SK to generate a login command.

5. **x509: certificate signed by unknown authority**

   **Possible Causes**:

   The container engine client communicates with SWR through HTTPS. The client verifies the server certificate. If the server certificate is not issued by an authoritative organization, the following error message is displayed: "x509: certificate signed by unknown authority"

   **Solutions**:

   If you trust the server and skip certificate authentication, manually configure Docker startup parameters as follows:

   -  CentOS:

      Modify the **/etc/docker/daemon.json** file. If the file does not exist, manually create it. Add the following content to the file:

      .. code-block::

         {
           "insecure-registries": ["{Image repository address}"]
         }

   -  Ubuntu:

      Modify the **/etc/default/docker** file and add the following content to **DOCKER_OPTS**:

      .. code-block::

         DOCKER_OPTS="--insecure-registry {image repository address}"

   -  EulerOS:

      Modify the **/etc/sysconfig/docker** file and add the following content to **INSECURE_REGISTRY**:

      .. code-block::

         INSECURE_REGISTRY='--insecure-registry {image repository address}'

   .. note::

      The image repository address can be a domain name or an IP address.

      -  To obtain the image repository address in domain name format, obtain a temporary login command by referring to :ref:`2 <swr_faq_0016__li1489599133814>`. The domain name at the end of the command is the image repository address.
      -  To obtain the image repository address in IP address format, ping the image repository address in the domain name format.

   After the configuration, run the **systemctl restart docker** command to restart the container engine.

6. **denied: Not allow to login, upload or download image**

   If you concurrently upload large numbers of images or frequently request access to the service, the system will blacklist you. As a result, you cannot log in to the system or upload or download images. Try again 30 minutes later.

.. |image1| image:: /_static/images/en-us_image_0168961239.png
