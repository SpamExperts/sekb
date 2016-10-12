Zimbra addon
============

Functionality
=============

The SpamExperts Zimbra addon, provides the following functionality:

-  Report a spam to our central reporting system
-  Automatically login to the SpamExperts Control Panel interface via a
   Zimbra tab

Compilation
===========

-  Download the addon files from
   `here <https://github.com/SpamExperts/zimbra-addon/archive/v1.0.zip>`__
-  Unpack the Zip file to a temporary location locally
-  Edit the *config\_template.xml* file to the appropiate values

   -  **reportSpamUrl** - this should remain unchanged
   -  **panelUrl** - The API hostname (for Hosted Cloud users this
      should be *https://api.antispamcloud.com*)
   -  **panelAdmin** - Your SpamExperts Admin username
   -  **panelPassword** - Your SpamExperts Admin password
   -  **allowedDomains** - This should contain *BOTH* your clusters
      hostname and \*.spamrl.com  (For Hosted Cloud users this should be
      **.antispamcloud.com,*.spamrl.com*)

-  Save the file
-  Remove the "**README.md**\ "
-  Pack the addon files back into a zip file called
   "**com\_zimbra\_spamexperts.zip**\ "  (do not include the folder
   "/zimbra-addon-master/")

Custom Branding
---------------

It's possible to re-brand our Zimbra addon. To re-brand the addon, this
will need to be done in the "Compilation" steps before re-packaging.

-  Replace the "**ZimletName**\ ", "**Label**\ " in the\_
   com\_zimbra\_spamexperts.properties\_ files.
-  Replace "*zimlet\_icon.gif*\ " with your own icon. This must be a GIF
   file and use dimensions 16px x 16px

Installation from command line
==============================

-  upload the recently packaged zip file  com\_zimbra\_spamexperts.zip
   to\*\* /opt/zimbra/zimlets/ \*\*directory of your server.
-  deploy the package using the following command

::


        /opt/zimbra/bin/zmzimletctl deploy /opt/zimbra/zimlets/com_zimbra_spamexperts.zip

You should see the following response on a successful installation

::


        INFO: Deploying Zimlet com_zimbra_spamexperts in LDAP.
        INFO: Installing Zimlet com_zimbra_spamexperts on this host.
        INFO: Upgrading Zimlet com_zimbra_spamexperts to 1.0
        INFO: Installing Zimlet config for com_zimbra_spamexperts
        INFO: Adding Zimlet com_zimbra_spamexperts to COS default
        INFO: Enabling Zimlet com_zimbra_spamexperts
        

Log in as user in Zimbra and check for the zimlet in Zimlet section.

Due to Zimbra Cache is possible to not see the zimlet immediately.

Install the addon from Zimbra Admin Area
========================================

-  log in to your zimbra as administrator (using port 7071)
-  go to **Configure**->**Zimlets** and deploy the zimlet
-  check "**Flush zimlet cache**\ " to be sure you will see the zimlet
   immediately

By default, the zimlet is available to all users, but from Zimbra
administration, for each user you can set if that user should have
access to this zimlet or not.

Support
=======

Extra logging
-------------

By default, zimbra debug mode for zimlets is enabled and all the
information can be found in\*\* /opt/zimbra/log/mailbox.log\*\*  If
debug mode is disabled, it can be enabled for an admin user, after
executing the following :

::


        su - zimbra
        zmprov addAccountLogger $email zimbra.zimlet debug

Forbidden Proxy issue
---------------------

If you are using mutiple COS (Class of Service ) objects then likely you
will need to add \*.spamrl.com to these. This can be done via command
line using:

::


        for i in `zmprov gac`; do zmprov mc $i +zimbraProxyAllowedDomains *.spamrl.com; done

Further support
---------------

Please contact support@spamexperts.com if you have any issues.
