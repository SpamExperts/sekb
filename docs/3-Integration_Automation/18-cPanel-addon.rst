.. _3-cPanel-addon:

cPanel addon
============

Recommended setup
=================

The optimal procedure to protect a cPanel server is the following:

1. Once logged in as 'Super-Admin' Create a admin account from the
   manage admins page for the cPanel server in SpamExperts (Local Cloud
   only)
2. Install the SpamExperts cPanel addon
3. Configure the correct API/MX/user details for the cPanel add-on
4. Disable incoming filters from the SpamExperts servers

-  For Local Cloud: Exim Configuration Manager > Basic Editor > Access
   Lists > "Only-Verify-Recipient"
-  For Hosted Cloud: :ref:`Ensure proper delivery from the filtering    servers  <7-Ensure-proper-delivery-to-my-destination-server>`

-  Run **bulk protect** from add-on in WHM
-  Restart Bind:

   ::


       /etc/init.d/named restart

-  For outbound filtering: Set `outbound
   smarthost <https://my.spamexperts.com/kb/40/Using-outgoing-as-a-smarthost.html#heading_toc_j_9>`__
   details

Installing the addon
====================

The addon installation is straightforward and requires root access to
the system.

System requirements
-------------------

To use the addon, you have to ensure your system is setup/configured
according to the following requirements:

::

    1. Full root/shell access to be able to install the addon
    2. cPanel running from stable/release/current versions only (we cannot support edge).[ LTS](https://documentation.cpanel.net/display/1144Docs/Update+Preferences) versions are not supported.
    3. Our “Local Cloud” or “Hosted Cloud” product and admin credentials
    4. The "Change mx" feature has to be enabled in the feature list. To enable this, go to: **Packages > Feature Manager**, click on **Edit Feature List** and tick the **“Ability to Change MX”** box.
    5. PHP 5.4 or above

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image11.png
   :alt: 

1. PHP support for:

-  cURL
-  OpenSSL (recommended, not mandatory)

Configuring PHP to support cURL and OpenSSL
-------------------------------------------

The addon relies on cURL to communicate with the API's it uses. You'll
need to ensure both cURL and OpenSSL are supported via EasyApache. The
activate this, login as super-administrator to **WHM**:

1. Go on the left to **"EasyApache (Apache Update)"**
2. Choose **"Start customizing based on profile"**
3. Continue with the next steps, until you can go to **"Exhaustive
   Options List"**
4. Ensure to select **"OpenSSL"** and **"CurlSSL"**, click **"Save and
   build"**

Setup instructions
------------------

To install (or update) the addon, issue the following command:

::


        wget -N http://download.seinternal.com/integration/installers/cpanel/installer.sh && bash installer.sh

This command will download the installer and install the latest (stable)
version of the addon.

Once the installation has completed, you can configure it through WHM. A
rerun of the installer will not overwrite the add-on configuration.

Addon: cPanel
=============

The cPanel part of the addon provides the enduser a (brandable) icon in
their control panel, allowing them to see their domains and login to
them.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/cpanel_image08.png
   :alt: 

If they click the icon, they are redirected to a page showing their
domains with login links.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image02.png
   :alt: 

Clicking “login” will automatically log them into the spam filter, and
allows the manage their full antispam settings for their domain.

Addon: WHM
==========

The WHM part of the addon includes all configuration and features for
the super-admin.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/cpanel_image07.png
   :alt: 

Clicking the icon will lead you to the mainmenu for the addon

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image10.png
   :alt: 

Configuration
-------------

The configuration panel contains all the necessary settings to allow
full flexibility for the addon.

In most cases, the default settings are sufficient but can be altered to
suit your needs.

On mouseover a tooltip with the option description will be displayed.

Be Advised: If you want to use this addon on our Hosted Cloud there are
some :ref:`additional steps  <1-Using-addons-on-the-Hosted-Cloud>`
required.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image04.png
   :alt: 

Configuration items described in detail
=======================================

SpamPanel URL
-------------

What URL is being used to manage the Spamfilter? This can be the primary
hostname of your cluster, or a CNAME you're using. Please note that if
you want to use **https://**, you will need to configure SSL support for
**cpsrvd**.

This URL will be validated. If this is not a Control Panel URL, you will
be informed.

API hostname
------------

The hostname is being used to interface with the API. This is the
hostname of your masterserver.

API username
------------

The API username should be a (sub)admin or admin account. We recommend
you to use a separate (sub)admin user for each cPanel server. For
security reasons, it’s not recommended to user Superadmin credentials.
Also please ensure not to use a “Software API” user.

API password
------------

API password is the one that belongs to the API user. The combination of
hostname, username, password and SSL enabled/disabled is being
validated. If the login fails, you will be informed so you can make the
appropriate adjustments.

Primary MX
----------

The Primary MX record (MX10).

Secondary MX
------------

The Secondary MX record (MX20). Optional

Tertiary MX
-----------

The Tertiary MX record (MX30). Optional

TTL to use for MX records
-------------------------

You can select which TTL the addon should use when creating MX records
for the domain it is protecting.

Enable SSL for API requests
---------------------------

Use SSL for API requests. Please note that this will require cpsrvd to
be compiled with OpenSSL. This checkbox will be unchecked/greyed out
when your PHP version/server doesn't support OpenSSL.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image00.png
   :alt: 

Enable automatic updates
------------------------

Updates are being performed once a week to make sure the addon is
running the most recent version. If you tick this box, the addon will
periodically check if updates are available. If there is an update, it
will be installed automatically.

You can also update manually through the addon's “Update” feature.

Automatically add domains to the SpamFilter
-------------------------------------------

If you want the addon to create new domains in the SpamExperts Control
Panel when it is being added to cPanel, tick this box.

Automatically delete domains from the SpamFilter
------------------------------------------------

If you want the addon to remove domains from the SpamFilter when they
are being removed from cPanel, tick this box.

Automatically change the MX records for domains
-----------------------------------------------

If you want the addon to change the MX records for your domains, tick
this box. This option uses the Primary/Secondary/Tertiary MX records to
provision the DNS for a new domain or when you're executing Bulk
Protect.

Configure the email address for this domain
-------------------------------------------

Automatically sets the contact address for the domain in the Spam
Filter. Using this, customers can leverage the "Retrieve login link"
feature if they forget their password and will start receiving
Protection Reports for their domain. For protection reports, the default
settings are used.

This function will work only if your account has an email address
attached in cPanel.

Process addon- and parked domains
---------------------------------

If you want the addon to handle addon and parked domains, tick this box.

Add addon- and parked domains as an alias instead of a normal domain.
---------------------------------------------------------------------

If this box is unticked, and the previous one ticked, domains will be
added as normal standalone domains. That is the recommended value. If
you tick this box (and the previous one is ticked), addon- and parked
domains will be added as special domain aliases for the root domain. We
strongly recommend to leave this feature unticked, as addon/parked
domains may have different mail rules setup and hence email may
malfunction as the account does not exist on the main domain.

Use existing MX records as routes in the SpamFilter.
----------------------------------------------------

If you tick this box, instead of the server hostname the original MX
records for that domain will be used as destination hosts. You can use
this for specific server setups, such as Google Apps.

Do not protect remote domains
-----------------------------

This will skip protecting domains that are set to “remote”. When a
domain is set to “remote”, the email handling is not done by this box.

By using this option and “use existing MX records as routes in the
SpamFilter” you can transparently have the domain protected since it
will then use the existing MX records, which point to the remote server,
to have the Spamfilter deliver mail to.

Redirect back to controlpanel upon logout
-----------------------------------------

Tick this box in case you want to have the user redirected back to
cPanel when they click the logout button in the SpamExperts interface.

Add the domain to the SpamFilter during login if it does not exist
------------------------------------------------------------------

This function will add the domain to the filter, in case the domain does
not exist during login. This is useful to auto-protect domains during
login, in case they are not protected yet.

Force changing route & MX records, even if the domain exists.
-------------------------------------------------------------

This will change the route to this server and MX records in case the
domain already exists. This functionality can be used in case you are
frequently migrating domains between multiple cPanel boxes.

Change email routing setting "auto" to "local" in bulk protect.
---------------------------------------------------------------

The “email routing” setting can be set to “local” (this server handles
email) in case the domain is set to “auto”. Auto is a dangerous setting
that may lead to issues in the email delivery. By ticking this box,
domains set to “auto” will be changed into “local”.

Add/Remove a domain when the email routing is changed in cPanel
---------------------------------------------------------------

When the email routing is being changed in the “Edit MX records”
setting, you can have the addon automatically remove the domain if it is
set to anything but local or add the domain if it is switched to local.

IP as Destination route instead of domain
-----------------------------------------

With this turned on all newly added domains should have destinations
represented with IP addresses. With the option turned off the
destinations should be hostnames.

Branding
========

Using the branding option, you can change the appearance of the cPanel
icon to match your own branding. This functionality is only available if
you have purchased the Private Label (White label) or Premium Private
Label (Premium white label)

.. figure:: https://dev.spamexperts.com/sites/default/files/images/cpanel_image13.png
   :alt: 

Domain List
===========

The domain list shows you all the local domains and offers an option to
check if it is protected, exists in SpamFilter, and to login to it.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image01.png
   :alt: 

Clicking “Check Status” or “Check all domains” will check if the domain
is added to the filter. Using the “Toggle Protection” you can either add
or remove the domain from the SpamExperts Control Panel.

Bulkprotect
===========

The Bulk Protect option allows you to protect all domains on the local
system.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image03.png
   :alt: 

Clicking bulk protect will execute the bulk protect system. This may
take some time as it has to iterate through all domains (account, addon,
parked) and execute all of the various tasks involved in protecting the
domain (for example: adding it, changing MX records, setting email
address for reports).

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image05.png
   :alt: 

On servers with big amount of domains (1000+) using the User  Interface
for running bulk protection for can be too resource-intensive. To better
handle big domains lists the addon provides a command-line utility for
running the bulk-protection procedure. It can be executed in root
sessions only by running the following commands:

::


        cd /usr/local/prospamfilter

::


        php bin/bulkprotect.php

Migration
=========

The migration page allows you change the username user and re-assign all
domains to that user, in case the destination user is an admin:

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image09.png
   :alt: 

The migration process requires you to enter the new user's username and
password, to verify you have access to that account. During the
migration, the domains will be assigned to this new user.

Once the process is complete, it will update the username and password
for the addon configuration.

We strongly recommend each cPanel server to use it's own Control Panel
API credentials. Whenever you move an account from one cPanel server to
another, you should first transfer the ownership of the domain from the
old web interface user to the new one. That way, the old cPanel server
does not have access to the domain anymore (and won't delete it), whilst
the new server does have access (to allow the client to log in).

Update
======

The addon can auto-update itself to the latest version. On the update
page you can change what type of updates you'd like to receive, manually
update it or reinstalling the current version.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image06.png
   :alt: 

We highly recommend you use the stable builds at all times, as these are
the tested and preferred builds.

The testing and trunk builds are updated more often but may contain
bugs.

Support
=======

The support page shows you basic information about which versions are
being used and generates a special code.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/cpanel_image12.png
   :alt: 

The special code contains a collection of data used by support to be
able to support you better. When asking support, please provide this
information.

Troubleshooting
===============

There are two parts of enabling debug mode, one is enabling debug mode
for the addon and the other is to have syslog save debug-level logs.
Both steps are required to successfully enable debug level logging.

You can enable the addon's debug mode by typing in a terminal:

::


        touch /etc/prospamfilter/debug

This feature should only be enabled when there is a problem and you want
to debug it.

To disable it again, just type:

::


        rm /etc/prospamfilter/debug

We recommend to enable debugging when there are problems (white pages,
unexplainable errors). This mode logs quite some information to the log
file and starts displaying more errors in the Control Panel.

Log Debug Level Data
--------------------

This is very important in the event of any issues you may encounter with
your installation. Please follow the below steps to log debug level
data:

First, you must change your syslog settings.

cPanel (or CentOS) has a default setup which ignores the "DEBUG"
entries.

To make them show up, you can add the following line to
**/etc/syslog.conf (or /etc/rsyslog.conf)** and **restart (r)syslog**
afterwards:

::


        *.debug                                                /var/log/debug

To restart syslog or rsyslog, depending on the case, just execute one of
the following commands:

::


        sudo service syslog restart

::


        sudo service rsyslog restart 

In case you want to keep this enabled for a longer period, you might
want to add it to the log rotation configuration.

The log will be stored on **/var/log/debug.**

cPanel v54 X3 Theme
-------------------

cPanel v54 has introduced some changes to the X3 theme which they have
officially deprecated and plan to remove by the end of 2016.
Unfortunately this can cause an issue with our plugin's icon for that
particular theme, which might no longer be displayed properly.

More details about X3 theme deprecation and scheduled removal can be
found in cPanel's blog post
`here <https://blog.cpanel.com/its-time-to-say-goodbye-%20to-x3/>`__.

We would strongly advise our customers to no longer use the X3 theme
starting with v54 and switch to the new default one that cPanel
recommends instead, for which they've also added a 'Retro' styling
option to make it look like X3.

However, if anyone still wants to use X3 theme on v54 for any reason and
has an issue with our plugin's icon not being displayed properly, the
following cPanel script can be used to fix the issue:
'/usr/local/cpanel/bin/rebuild\_sprites\`.

Upgrade Instructions
====================

The system automatically updates itself (when enabled), and can
optionally be updated manually via the web interface. If you experience
any issues using the web-based/automatic updater, please contact our
`support <mailto:support@spamexperts.com>`__. You can always run the
installation command as above to force a new install of the latest
version of the add-on, all settings will remain preserved.

Uninstall Instructions
======================

In case you want to remove the addon, you have to run the uninstaller
using the following command:

::


        cd /usr/local/prospamfilter/bin/ && ./uninstall.php

The above command will just uninstall the addon, but all added domains
will still be protected as mail will be routed through the SpamExperts
system and the MX Records will still point to your Local or Hosted Cloud
solution.

To remove all domains from the SpamExperts system and reset the MX
Records to their original state from before the add-on’s installation,
run the following command:

::


        cd /usr/local/prospamfilter/bin/ && ./uninstall.php --resetmx
