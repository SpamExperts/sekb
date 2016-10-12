Test my server is correctly accepting mail
==========================================

Incoming
~~~~~~~~

Using telnet you can manually test if the destination server is
correctly accepting the email. To do so, you have to lookup the
destination route in the SpamExperts Control Panel set for a domain, and
try delivery:

--------------

::


        demo1.spambrand.com:~$ telnet destinationserver 25
        Trying x.x.x.x...
        Connected to destinationserver.
        Escape character is '^]'.
        220 destinationserver ESMTP
        helo demo1.spambrand.com
        250 destinationserver at your service
        mail from:<>
        250 2.1.0 OK
        rcpt to: user@domain.tld
        250 2.1.5 OK
        quit
        221 2.0.0 closing connection
        Connection closed by foreign host.
        demo1.spambrand.com:~$  
          
        

--------------

Please note that for the recipient callout we always use an empty "mail
from:<>"

cPanel
~~~~~~

Please make sure that when manually changing your domain MX records, the
cPanel Email Routing settings are always set to "Local Mail Exchanger"
instead of "Automatically Detect Configuration". Otherwise the cPanel
server will reject all email to this domain, this will show in the log
search as "Recipient Rejected by destination server". Since it is a
permanent reject at the destination server, the mail will be permanently
rejected. Permanent failures, including failed `Recipient
Callouts <http://spamexperts.com/wiki/index.php?title=Recipient_callouts%20"Recipient%20callouts">`__,
are being cached up to two hours.

|File:CPanel\_mail\_routing.png|

Outgoing
~~~~~~~~

Using telnet you can manually test if a destination domain is correctly
accepting the email. To do so, you have to lookup the destination MX
record of the domain, and try a delivery:

--------------

::


          
        demo1.spambrand.com:~$ host destinationdomain
        destinationdomain has address x.x.x.x
        destinationdomain mail is handled by 10 destinationserver.
        demo1.spambrand.com:~$ telnet destinationserver 25
        Trying x.x.x.x...
        Connected to destinationserver.
        Escape character is '^]'.
        220 destinationserver ESMTP
        helo demo1.spambrand.com
        250 destinationserver at your service
        mail from:
        250 2.1.0 OK
        rcpt to: user@domain.tld
        250 2.1.5 OK
        quit
        221 2.0.0 closing connection
        Connection closed by foreign host.
        demo1.spambrand.com:~$  
          
        

--------------

.. |File:CPanel\_mail\_routing.png| image:: https://my.spamexperts.com/images/kb/CPanel_mail_routing.png
   :target: http://spamexperts.com/wiki/index.php?title=File:CPanel_mail_routing.png%20"File:CPanel_mail_routing.png"
