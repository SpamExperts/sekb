General problems with specific Routers/Firewalls/Mail Servers
=============================================================

Cisco intrusion detection issues
--------------------------------

Sometimes there may be delivery issues resulting in messages getting
queued with the following reason:

::


        Connection timed out: SMTP timeout while connected to destinationserver.example [1.1.1.1] after sending data block (49135 bytes written)
        

This issue only seems to affect emails with a certain message size, and
can be caused by a Cisco Firewall at the recipient side with Intrusion
Detection enabled. Disabling Intrusion Detection solves the issue.

ASA 5505 ESMTP inspection problems
----------------------------------

The ASA 5505 has an ESMTP inspection rule that may wrongly block certain
emails from being delivered. Please ensure to disable this rule and/or
to update the firmware.

Outdated Zyxel firmware issues
------------------------------

| Sometimes there may be issues delivering emails to a destination
  server using a Zyxel router. A telnet to the destination server from a
  Linux machine shows no 220 greeting is returned.
| A telnet to the destination from a Windows machine does show the
  greeting. This is a known bug in the Zyxel firmware and updating the
  Zyxel router resolves the issue,

Exchange 2003 Small Business NAT problems
-----------------------------------------

There appears to be a bug in the Exchange 2003 Small Business local NAT
setup when redirecting traffic to an alternative SMTP port. Random
timeouts after RCPT TO: may occur which is not reproducible from Telnet.
Changing Exchange to listen directly on the alternate port, bypassing
the NAT port forwarding resolves this.

Exchange 2007 and missing SpamExperts X-Headers
-----------------------------------------------

If when looking at the source of your message you do not see our
'X-Headers', then this could be an issue with the default
HeaderPromotionModeSetting settings that Microsoft Exchange has in
place. By default Microsoft Exchange 2007 sets these to 'NoCreate'. To
see our X-Headers when using IMAP and POP then you should change this to
'MayCreate'.  This can be achieved from the Microsoft Exchange Shell by
typing:

set-transportconfig -HeaderPromotionModeSetting MayCreate

Lotus Domino Notes outbound SSL issue
-------------------------------------

Older versions of Lotus Notes maybe be wrongly configured to send
outbound mail by default to port 465 instead of port 25. This is a
severe security issue since port 465 has never been defined as an
official port for incoming email delivery. Instead, email uses STARTTLS
to handle encryption. To avoid email getting rejected from Lotus Notes
servers, it's important to configure Lotus Notes to correctly deliver
outbound mail to port 25 directly instead.

`The SSL port status should be set to "Disabled"
(default) <http://www.codestore.net/help/help6_admin.nsf/f4b82fbb75e942a6852566ac0037f284/9bc80eb9af693ad985256c1d00395b88?OpenDocument>`__.

Please ensure the outbound port is set to port 25 and `negotiated
SSL <https://www-304.ibm.com/support/docview.wss?uid=swg21108352>`__.

More information is also available in the `official
documentation <http://publib.boulder.ibm.com/infocenter/domhelp/v8r0/index.jsp?topic=/com.ibm.help.domino.admin.doc/DOC/H_SUPPORTING_THE_STARTTLS_COMMAND_STEPS.html>`__.

Hotmail rejects with bad nameserver setup
-----------------------------------------

Hotmail may bounce delivery attempts with the following unclear message:

::


        Reporting-MTA: dns;snt0-omc3-s14.snt0.hotmail.com  
        Received-From-MTA: dns;SNT402-EAS413  
        Arrival-Date: Wed,  
        17 Oct 2012 13:40:58 -0700  
          
        Final-Recipient: rfc822;info@motorkledingwinkel.nl  
        Action: failed  
        Status: 5.5.0  
        Diagnostic-Code: smtp;550 authentication"

This is NOT a rejection from the SpamExperts system. Hotmail has the
unusual behavior of delivering to the A-record instead of the MX-records
if the nameservers are not set up 100% correctly. Please `check your
nameservers <http://dnscheck.sidn.nl/>`__ to determine if there are
wrong settings and to verify once that has been resolved.

OpenDNS Nameservers
-------------------

Due to some lookup issues we do not recommend using OpenDNS nameservers
in your setup (resolv.conf). We would recommend either using your own
nameservers or Google's namerservers as backup. If you are in doubt,
please contact support@spamexperts.com

Rewriting sender addresses in Exim
----------------------------------

Sometimes it is needed to rewrite the sender address in Exim due to
sender verification issues and incorrectly set up email addresses. This
can be achieved by:

::


        return_path = ${if eq {$return_path}{member@paypal.com}{good-address@example.com}{$return_path}}  
          
          
        

Resolving SRS issue with Direct admin Exim - SpamBlocker 4.4\*
--------------------------------------------------------------

In the newer versions of Exim SpamBlocker (4.4\*) for Direct Admin,
there are some issues with SRS, when using sender verification on
outbound emails with SpamExperts. To resolve this, simply move the
**srs\_router** above the **virtual\_aliases** router. Once you do this,
you will be able to enable SRS on the sending mail-server and continue
to use sender verification on the SpamExperts side. So the config should
then look like this:

::


        srs_router:
        driver = redirect
        srs = reverseandforward
        data = ${srs_recipient}
        
        virtual_aliases:
        driver = redirect
        .include_if_exists /etc/exim.srs.forward.conf
        allow_defer
        allow_fail
        condition = ${if eq {}{${if exists{/etc/virtual/${domain}/aliases}{${lookup{$local_part}lsearch{/etc/virtual/${domain}/aliases}}}}}{yes}{no}}
        data = ${if exists{/etc/virtual/$domain/aliases}{${lookup{$local_part}lsearch*{/etc/virtual/$domain/aliases}}}}
        file_transport = address_file
        group = mail
        pipe_transport = virtual_address_pipe
        retry_use_local_part
        #include_domain = true
