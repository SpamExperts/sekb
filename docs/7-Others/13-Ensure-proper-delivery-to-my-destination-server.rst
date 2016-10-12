.. _7-Ensure-proper-delivery-to-my-destination-server:

Ensure proper delivery to my destination server
===============================================

In some cases configuration changes are required to the destination
server to ensure the SpamExperts servers can deliver to your destination
server without interruption. Please ensure your destination server
always accepts every message from our systems (only null sender callouts
should be rejected if the recipient address does not exist).

Disable spamfiltering on the destination server
-----------------------------------------------

| We highly recommend you disable the spamfiltering on your destination
  server, as this would mean that both our platform as your server still
  scans it.
| This might lead to your destination server rejecting, blocking or
  removing messages that it considers to be spam, which passed our
  system.

Having multiple layers of spamfiltering is generally a waste of system
resources and a source of issues.

Disable SPF checking
--------------------

| When a message is delivered to a SpamExperts Filtering server it will
  check for SPF.
| If the delivering server is allowed to deliver, we will accept it
  (given other parts of the Spamfiltering process also indicates its not
  spam)

When we are however delivering the scanned messages to your destination
server, your server will most likely reject/block/delete it because it
sees our servers as the delivering servers which is not listed in the
SPF records as valid delivery system. To stop this behaviour from
happening we highly recommend you to disable SPF checking. In most cases
this needs to be done on server level and cannot be done on domain-level

Whitelist delivery servers
--------------------------

Microsoft Exchange
~~~~~~~~~~~~~~~~~~

When using Microsoft Exchange, there are a few things to keep in account
when using:

-  For Hosted Cloud: Our delivery nodes should be able to connect to
   your server
   (see:ref:`this  <1-Accept-email-only-from-the-Hosted-Cloud-filter-nodes>`
   article)
-  Your Receiver Connector should have the "Permission Group" of
   "Anonymous users" allowed to relay.

cPanel
~~~~~~

When using cPanel, there are a few things to keep in account:

1. | Make sure your Email Routing is set to Local Mail Exchanger and not
     at Auto Mail Exchanger.
   | If cPanel detects non-local hostnames it will consider the domain
     remote and will stop accept email for it!

2. Disable POP before SMTP Authentication to ensure mails can be
   delivered properly

Whitelist delivery servers
^^^^^^^^^^^^^^^^^^^^^^^^^^

| Its also generally a good idea to whitelist the delivery servers.
| This allows us to bypass sender/recipient/spam and relaying checks and
  ensure proper delivery.

For Hosted Cloud users, please either **ONE** of the following options:

-  Add our current delivery IP's  to the "**Only-Verify-Recipient**\ "
   in WHM (Exim Configuration Manager => Basic Editor => Access Lists)
   section. This list can be found at https://noc.spamexperts.net. To
   keep up to date on our listings please sign up for alerts when IP's
   are added.

Or complete the following steps:

-  Add delivery.antispamcloud.com to the  "Only-Verify-Recipient" in WHM
   (Exim Configuration Manager => Basic Editor => Access Lists) section
-  Navigate to the advanced Editor tab
-  Find the **hostlist trustedmailhosts** option in the **Section:
   CONFIG** and  replace **lsearch;/etc/trustedmailhosts** with
   **+selist : lsearch;/etc/trustedmailhosts**
-  Scroll down to the bottom of the **Section CONFIG** and click  **Add
   additional configuration setting**
-  Add the following **hostlist selist = ${lookup dnsdb{>:
   a=delivery.antispamcloud.com}}**
-  Click save

For Local Cloud you can simply add the server IP's to same section or
directly in the file it stores to: /etc/trustedmailhosts

**Note: **\ Make sure that the IPs are **not** present in
/etc/skipsmtpcheckhosts , but \*\* only\*\* in etc/trustedmailhosts as
otherwise the status of the domain can appear to be catch-all. If this
is correct, however the catch-all still appears to be enabled, please
check /etc/remotedomains to make sure the domain is not there.

ConfigServer Firewall (CSF)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

In case you use CSF on your machine its generally also recommended to
whitelist us there, to ensure we are not blocked accidentally. For this
you can use the following bash script (Please back up any previous lists
in case of any problems):

::


        #!/bin/bash
        ## THIS SCRIPT IS PROVIDED AS-IS NO WARRANTY IS GIVEN ON PROPER OPERATION.
        ## USE AT YOUR OWN RISK!
        #
        ## Version 1.1 - 01-08-2015 - CSF EDITION - IPv4 Only
        
        CURRENT_IPS=`cat /etc/csf/csf.ignore`
        CLEAN_IPS="127.0.0.1"
        SE_DELIVERY_IPS=`host delivery.antispamcloud.com | grep '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' | awk {'print $4'} | sort`
        echo $CURRENT_IPS $CLEAN_IPS $SE_DELIVERY_IPS | xargs -n 1 | sort | uniq | xargs -n 1 > /etc/csf/csf.ignore
        /etc/init.d/lfd restart
        

This script can (like the cPanel whitelist script above) also be added
to your cron. The steps to do this would be:

1. Create a file with the above script
2. Save it in the /etc/ directory with the name se.sh
3. execute **chmod +x se.sh**
4. Add the following line to CRON to be executed every 6 hour:

\*\*\* */6 * \* \* /etc/se.sh >/dev/null 2>&1\*\*

Postfix & Amavis
~~~~~~~~~~~~~~~~

| In case you are using Postfix with Amavis there is an easy solution to
  allow our servers to bypass any filtering on your destination server.
| In your Postfix configuration you need to add this line (or append it
  to your already existing smtpd\_client\_restrictions):

::


        smtpd_client_restrictions = check_client_access hash:/etc/postfix/amavis_bypass

Then create a new file /etc/postfix/amavis\_bypass with content:

::


        # Bypass amavis entirely for emails originating from
        # SpamExperts' delivery cloud by immediately re-inserting
        # into Postfix
        #
        delivery.antispamcloud.com FILTER smtp:[127.0.0.1]:10025
        

Save the file and postmap it by issueing:

::


        postmap /etc/postfix/amavis_bypass

| Restart Postfix and all of the deliveries originating from our
  platform will bypass any virus-, spam- and spf checks initiated by
  Amavis.
| This will not affect any of your other domains on this destination
  server, only connections originating
  from \ **delivery.antispamcloud.com**

Kerio Connect

| We have a multi-purpose script for Kerio which creates/updates an IP
  Address Group with our delivery IP's.
| This list can be used to disable various limits/filters such as
  spamfiltering, SPF checking and the Spam Repellant.

More information on this script can be found on the Kerio Section of our
page on how to :ref:`Accept email only from the Hosted Cloud  <1-Accept-email-only-from-the-Hosted-Cloud-filter-nodes>`

DirectAdmin
~~~~~~~~~~~

To prevent your DirectAdmin system from rejecting our deliveries you can
add it to the whitelist by appending the following to
**/etc/virtual/whitelist\_hosts**:

::


        delivery.antispamcloud.com
        
