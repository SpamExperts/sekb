.. _1-Accept-email-only-from-the-Hosted-Cloud-filter-nodes:

Accept email only from the Hosted Cloud filter nodes
====================================================

To avoid spammers being able to directly deliver the spam to your mail
servers without filtering it first, you have to make sure your mail
server only accepts emails originating from the Hosted Cloud filtering
system.

For redundancy reasons, our Hosted Cloud nodes are located in many
different datacenters. Therefore they do not share a single IP range and
since the Hosted Cloud is regularly expanded, new IP addresses may be
added at any time.

To only accept messages from the Hosted Cloud filtering nodes you need
to allow emails based on our delivery hostname
**"delivery.antispamcloud.com"**. This hostname contains all active
delivery IP addresses. Alternatively you can allow traffic from any IP
address with the PTR record \*.antispamcloud.com.

**Please make sure your firewall does not block port 53 TCP.**

Alternatively if allowing emails based on hostname is not an option, you
could change your destination mail server to listen on an alternative
one, such as port **2525** instead of the default 25 . The special port
can be set for delivery when editing the destination route for your
domain.

Exchange 2007/2010/2013
=======================

Microsoft has removed support for whitelisting based on reverse
DNS/hostname. You can however use the following Powershell script:

::


        Add-PSSnapin Microsoft.Exchange*
        #Start
        $ErrorActionPreference = "Stop"
        $ips = [System.Net.Dns]::GetHostAddresses("delivery.antispamcloud.com") | select IPAddressToString
        $ips = $ips | foreach-object {$_.IPAddressToString}
        Set-ReceiveConnector -Identity "Default SERVERNAME" -RemoteIPRanges $ips
        #End

Please note that this script is intended for Exchange 2010 on Windows
2008 Small Business but may also apply to Exchange 2007 on other
versions of Windows. Replace the “SERVERNAME” part of the script with
your receiving connector’s name that you want this script to modify.

You can retrieve this name through **Exchange Management Console ->
Server Name -> Server Configuration - > Hub Transport.**

This script retrieves all IP addresses listed in
**”delivery.antispamcloud.com”**\ strong> and whitelists them in the
Receive Connector to allow connections from our servers.

You can use the task scheduler to create a planned task and ensure the
IP addresses are updated frequently (hourly or at least once a day).
This can be done by creating a task with the following command:

::


        powershell -command "& 'C:\psscripts\exchangereceiveconnector.ps1' "

If you are using Exchange 2007 with SBS 2008, then you may need to
create this task with the following command instead:

::


        PowerShell.exe -PSConsoleFile "C:\Program Files\Microsoft\Exchange Server\Bin\ExShell.Psc1" -Command ". 'C:\psscripts\exchangereceiveconnector.ps1'

The user running the task needs privileges for "Log on as a batch job"
on the host running Exchange and needs to be a member of the
**"Microsoft Exchange Security GroupsManagement"**\ strong> group.

Be advised: If any assistance is required with the Powershell script,
`contact support. <mailto:support@spamexperts.com>`__

Optionally to add additional custom IP addresses you can add after the
line containing the **"foreach-object"**:

::


        $ips += "192.168.1.0/24"

Make sure you replace this IP with any IP addresses or subnets that
should also have permission to deliver directly. You can add this line
for each IP/subnet you want to include.

Microsoft Exchange 2003
=======================

Microsoft Exchange 2003 uses the whitelist based on reverse DNS,
therefore you can simply add \*\*"\*.antispamcloud.com"** to the
**\ "Domain"** field, which you find when following the instructions
**\ "How to Configure IP Address Restrictions"\*\*.

More information can be found on the Microsoft website.

cPanel
======

1. First create a new file: /opt/setest. You can name it anything you'd
   like, as long as you replace that in the Exim configuration as well.
2. Open the file and add this::

    #!/bin/bash host -t MX
   :math:`1 | sort -n -k1 | cut -d ' ' -f 7 | sed -e 's/\.`//' \| xargs
   \| sed -e 's/ /:/g' \| tr -d ''


3. Save the file.
4. Create a new file: **/opt/setestptr**

   ::

       ```
           #!/bin/bash
           host -t PTR $1 | cut -d ' ' -f5 | sed 's/\.$//g' | tr -d '\n'
       ```

5. Save the files
6. Chmod them.   (chmod +x /opt/setest  && chmod +x/opt/setestptr)
7. Open the **Exim Configuration Editor** and enable the **Advanced
   Mode.**

-  cPanel 11.30 or earlier: Search for "[% ACL\_PRE\_RECP\_VERIFY\_BLOCK
   %]" and add before OR
-  cPanel 11.32 or later: Search for "custom\_begin\_recp\_verify" and
   add into the box:

::


        ######################################################################################
        ## Start SpamExperts verification
        defer
        !condition = ${if match_domain{${run {/opt/setestptr $sender_host_address}}}{*.antispamcloud.com}}
            set acl_m_mx_records = ${run {/opt/setest $domain}}
            condition   = ${if eq{$acl_m_mx_records}{mx.spamexperts.com:fallbackmx.spamexperts.eu:lastmx.spamexperts.net}}
            message = Please deliver mail to the address specified in the MX records for this domain.
        ## End SpamExperts verification
        ######################################################################################

1. Save the configuration and you're all set. This configuration does
   the following:

-  If the MX records of the domain are exactly set to those in the
   condition:

   -  Accept mails if they originate from the hosts listed in the
      "hosts" variable: **"delivery.antispamcloud.com"** or localhost
   -  Reject direct deliveries not originating from the "safe" hosts

-  If the domain does not have their MX records configured as in the
   Exim configuration, it is assumed that they are not behind the filter
   and direct deliveries are accepted (given it passes the default ACL
   settings).

Exim
====

To configure Exim to only allow email from the filter servers for
certain domains, you have to set in the RCPT ACL:

::


        defer
            domains = +spamexperts_domains
            !hosts = delivery.antispamcloud.com : localhost
            message = Please deliver mail to the address specified in the MX records for this domain.

You can set up the **“spamexperts\_domains”** list earlier, reading it
from a file, or database, or even hard-coding it.

You can also use the configuration outlined in the cPanel section of
this guide.

DirectAdmin
===========

For DirectAdmin, the above ACL from the Exim section can be used. It
should be included before “ #local source whitelist” in the DirectAdmin
Exim file.

Postfix
=======

1. Create a file /etc/postfix/access with the content: antispamcloud.com
   OK
2. Create the hash-file used by Postfix: postmap /etc/postfix/access
3. Add the following to **/etc/postfix/main.cf**

::

    smtpd_client_restrictions = check_client_access
    hash:/etc/postfix/access, permit_mynetworks, reject

Or, if you already have smtpd\_client\_restrictions defined, insert
"check\_client\_access hash:/etc/postfix/access" at the beginning of
your definition, and replace permit with reject and the end of
definition.

You'll need to ensure the string smtpd\_access\_maps is not listed in
the Postfix parent\_domain\_matches\_subdomains configuration setting
(postconf -d \| grep parent\_domain\_matches\_subdomains). If it is
present you need to add this configuration line to main.cf without the
smtpd\_access\_maps variable.

1. Restart Postfix:  /etc/init.d/postfix restart

::


    ## Per domain setup

    It's also possible with Postfix to configure the MTA to only allow connections
    from the SpamExperts servers for certain protected domains. To do this you
    need to do the following:

      * Add this to the main.cf

::

    smtpd_restriction_classes = spamexperts
    spamexperts = check_client_access hash:/etc/postfix/antispam, reject
    smtpd_recipient_restrictions = check_recipient_access hash:/etc/postfix/protected_destinations, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

::


      * Create the following file:

::

     /etc/postfix/spamexperts

::


      * with the following content:

::

    antispamcloud.com OK 

::


      * Create the following file:

::

    /etc/postfix/protected_destinations

::


       * Add the domains that you want to configure:

::

    example.com spamexperts

::


       * Postmap both files
       * Restart Postfix

    # Kerio Connect

    Kerio Connect does not support hostname or reverse DNS whitelisting. Therefore
    we have created a script that will create/update your IP Address Group so it
    always contains the list of up-to-date addresses.

    The script can be [downloaded](http://download.spambrand.com/kerio/kerio-
    ipsync.zip) from our website.

    Please make sure you read the included readme.txt which will provide usage and
    configuration instructions.

    PHP is required for execution, it does not matter whether this is via a web
    server or the command line.

    It can run from the local Kerio Connect machine or any other server that has
    network access to your Kerio Connect system.

    # Qmail

    ## Qmail - TCPServer

    If you're running Qmail using tcpserver to spawn the qmail-smtp process, you
    can add a rule to your /etc/tcp.smtp file telling it to accept connections
    based on the reverse DNS of the connecting host:

::

    =delivery.antispamcloud.com:allow,RELAYCLIENT=""



Qmail - Inetd
-------------

If you're running Qmail as an inetd service by using tcp-env then all
SMTP access configuration is done from the following files:
**/etc/hosts.allow** and **/etc/hosts.deny**. Don't forget to add your
own SMTP clients to **/etc/hosts.allow.**

1. Add the following line to **/etc/hosts.allow**

   ::

       ```
            tcp-env: .antispamcloud.com: setenv = RELAYCLIENT

       ```

2. Add the following line to **/etc/hosts.deny **. This will deny access
   from all hosts except those in **/etc/hosts.allow **\ for the inetd
   service qmail

   ::

       ```
            tcp-env: ALL

       ```
