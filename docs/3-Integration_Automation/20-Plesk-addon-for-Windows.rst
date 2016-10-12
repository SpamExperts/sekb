.. _3-Plesk-addon-for-Windows:

Plesk addon (for Windows)
=========================

Installing the addon:
=====================

The installation of the addon is very straightforward and can be done by
anyone with Administrator access rights to the system.

System Requirements:
====================

Administrator access to the Windows Plesk environment

Setup Instructions:
===================

Download the following file:

::


        http://download.seinternal.com/integration/installers/plesk-windows/installer.bat

From the command line run the following command:

::


        cmd /k installer.bat

Once the installation has completed, you can configure it through the
Plesk admin area.

.. figure:: /_static/images/plesk-win-01.png
   :alt: 

Configuration:
==============

The configuration page contains the full addon configuration and allows
you to configure the addon to act as desired. In most cases, the default
settings are enough but can be altered to suit your needs.

If you hover over an option, it will show you a tooltip describing the
option and what it entails.

.. figure:: /_static/images/plesk-win-02.png
   :alt: 

Configuration items described in detail
=======================================

SpamPanel URL
-------------

What URL is being used to manage the spam filter? This can be the
primary hostname of your cluster, or a CNAME you're using. To use HTTPS,
you will need to configure **SSL** support for **cpsrvd**.

This URL will be validated. If this is not a SpamExperts Control Panel
URL, you will be informed.

API hostname
------------

The hostname being used to interface with the API. This is the hostname
of your masterserver.

API username
------------

The API username should be either an administrator or super admin
account. We recommend you to use a separate user for this.

API password
------------

API password that belongs to the API user. The combination of hostname,
username, password and ssl enabled/disabled is being validated. If the
login fails, you will be informed so you can make the appropriate
adjustments. Your password is being hashed, salted and stored in an
encrypted format.

Primary MX
----------

The Primary MX record (MX10).

Secondary MX
------------

The Secondary MX record (MX20). Optional

Tertiary MX
-----------

The Tertiary MX record (MX30). Optional

Enable SSL for API requests
---------------------------

Use SSL for API requests. This checkbox will be unchecked/greyed out
when your PHP doesn't support OpenSSL.

Enable automatic updates
------------------------

Updates are being performed once a day to make sure the addon is running
the most recent version. If you tick this box, the addon will
periodically check for updates that will be automatically installed.

You can also update manually though the add-on's “Update” icon.

Automatically add domains to the SpamFilter
-------------------------------------------

If you want to automatically filter domains when adding new ones in
Plesk, tick this box

Automatically delete domains from the SpamFilter
------------------------------------------------

Tick this box to automatically remove filtered domains when removing
them from Plesk

Automatically change the MX records for domains
-----------------------------------------------

Tick this box to automatically change the MX records for domains. This
option uses the Primary/Secondary/Tertiary MX records to provision the
DNS for a new domain or when you're executing Bulk Protect.

Configure the email address for this domain
-------------------------------------------

Automatically set the contact address for the domain in the SpamExperts
web interface. Using this, customers can use the "Retrieve login link"
feature if they forget their password and will start receiving
Protection Reports for their domain. For protection reports, the default
settings are being used.

This function will work only if your account has an email-address
attached in Plesk.

Process aliases and subdomains
------------------------------

Tick this box to allow the addon to handle addon and parked domains.

Add aliases and subdomains as an alias instead of a normal domain.
------------------------------------------------------------------

If this box is unticked (and the previous one ticked) alias domains will
be added as normal standalone domains. If you tick this box (and the
previous one is ticked), alias domains will be added as aliases for the
root domain they belong to.

Use existing MX records as routes in the SpamFilter.
----------------------------------------------------

If you tick this box, instead of the server hostname the original MX
records for that domain will be used as destination hosts. You can use
this for specific server setups (such as Google Apps)

Redirect back to controlpanel upon logout
-----------------------------------------

Tick this box in case you want to have the user redirected back to Plesk
when they click the logout button in the SpamExperts interface.

Add the domain to the spamfilter during login if it does not exist

This function will add the domain to the filter, in case the domain does
not exist during login. This is useful to auto-protect domains during
login, in case they are not protected yet.

Force changing route & MX records, even if the domain exists.
-------------------------------------------------------------

This will change the route to this server and MX records in case the
domain already exists. This functionality can be used in case you are
frequently migrating domains between multiple Plesk boxes.

TTL to use for MX records
-------------------------

You can select which TTL the addon should use when creating MX records
for the domain it is protecting. We advise users to set a lower TTL,
such as 60 seconds. For more information see :ref:`Local Cloud MX Records  <2-Local-Cloud-MX-Records>`.

Branding
========

Using the branding option, you can change the appearance of the Plesk
icon to match your own branding. This functionality is only available if
you have purchased the Private Label (Whitelabel) or Premium Private
Label (Premium whitelabel).

.. figure:: /_static/images/plesk-win-03.png
   :alt: 

Domain List
===========

The domain list shows you all the local domains and offers you an option
to check if it is protected (if they are filtered by SpamExperts) and to
login to it.

.. figure:: /_static/images/plesk-win-04.png
   :alt: 

Clicking **“Check Status”** or **“Check all domains”** will check if the
domain is added to the filter. Using the **“Toggle Protection”** you can
either add or remove the domain from the spam filter.

Bulkprotect
===========

The Bulk Protect option allows you to protect all domains on the local
system.

.. figure:: /_static/images/plesk-win-05.png
   :alt: 

Clicking bulk protect will execute the bulk protect system. This may
take some time as it has to iterate through all domains (account, addon,
parked) and execute all of the various tasks involved in protecting the
domain, for example: adding it, changing MX records, setting email
address for reports.

Migration
=========

The migration page allows you change the username user and re-assign all
domains to that user (in case the destination user is an administrator):

.. figure:: /_static/images/plesk-win-06.png
   :alt: 

The migration process requires you to enter the new username and
password, to verify you have access to that account. During the
migration, the domains will be assigned to this new user.

Once the process is completed, it will update the username and password
for the addon configuration.

We strongly recommend each Plesk server to use its own Control Panel API
credentials. Whenever you move an account from one Plesk server to
another, you should first transfer the ownership of the domain from the
old Control Panel user to the new Control Panel user. That way, the old
Plesk server does not have access to the domain anymore (and won't
delete it), whilst the new server does have access (to allow the client
to login).

Update
======

The addon can auto-update itself to the latest version. On the update
page you can change what type of updates you'd like to receive, manually
update it or reinstalling the current version.

.. figure:: /_static/images/plesk-win-07.png
   :alt: 

Be Advised: We highly recommend you use the stable builds at all times,
as these are the tested and preferred builds. The testing and trunk
builds are updated more often but may contain bugs or untested changes.

Support
=======

The support page shows you basic information about which versions are
being used. Please run the diagnostics option and copy paste the output
of this whole page when requesting support.

.. figure:: /_static/images/plesk-win-08.png
   :alt: 

Troubleshooting
===============

There are two parts of enabling debug mode, one is enabling debug mode
for the addon and the other is to have your windows environment debug
enabled.

First, create the following file:

::


        C:\ProgramData\SpamExperts\config\debug

Then you will need to enable debug logging on your Windows environment
following the steps
`here <https://technet.microsoft.com/en-us/library/cc749492.aspx?f=255&MSPPError=-2147217396>`__

Uninstallation
==============

To remove the SpamExperts addon please use the following command:

::


        "%PLESK_BIN%\php.exe" -d open_basedir=C:\ -d safe_mode=0 "C:\Program Files (x86)\SpamExperts\Professional Spam Filter\bin\uninstall.php"
