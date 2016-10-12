Delivery IP management
======================

The SpamExperts outbound filter uses by default the primary interface
(IP address) to deliver outbound emails to the destination MX records.
It may however be preferred to e.g. separate the outbound delivery IP
from the inbound delivery IP. Also to reduce per-IP delivery volume,
it's possible to setup a "pool of delivery IPs" which will be randomly
selected for delivering the outbound emails. That's generally not
recommended though, as recipients may start blocking email based on such
activity (in specific cases it can be used to reduce the delivery rate
per IP). Finally it's possible to specify different delivery IP
addresses for different outbound users.

NOTE: When using the API there is no advanced syntax checking, please
ensure to use the correct settings to prevent breaking the mailflows.
The call apply to both IPv4 and IPv6 addresses.

Adding IP addresses to the network configuration
------------------------------------------------

To add additional IP address, please contact SpamExperts support and
clearly describe which IP address(es) should be added to which
system(s). Our support will change the network configuration for you and
will restart our services to activate them. Alternatively, you may add
additional IPs directly yourself to /etc/network/interfaces as long as
the primary IP does not change. Please ensure to NOT list the new IP
addresses as part of the server hostnames, those should always resolve
only to the primary IP address.

Managing outbound delivery IP addresses
---------------------------------------

To retrieve a list of IP addresses that are currently active, you can
use the software API:

    https://demo1.spambrand.com/cgi-bin/api?call=api\_get\_outgoing\_interfaces&domain=DOMAIN&username=USERNAME

You can specify the outbound "domain" and "username" for which to
retrieve the details. Please ensure these exists as an outbound user in
the system. To retrieve the default values for all users please specify
as DOMAIN "default" and leave USERNAME blank. The default IP address is
0.0.0.0 for IPv4 and ::0 for IPv6, these refer to the primary interface
of the server.

In case you wish to overrule the default delivery address of a filtering
node, you can use the software API directly:

    https://demo1.spambrand.com/cgi-bin/api?call=api\_set\_outgoing\_interfaces&domain=DOMAIN&filtering\_host=FILTERING\_HOST&interfaces=INTERFACES&username=USERNAME

To change the default IP for a node, specify as DOMAIN "default" and
leave USERNAME empty. The FILTERING\_HOST refers to the server hostname
you wish to set the IP for, and the INTERFACES variable should contain 1
or more IP addresses separated by a semi-colon (%3B when posting
directly via the URL). In case an IP is blacklisted, you could change
the IP address used to a new IP which is not blacklisted until the
blacklisting issue has been resolved. Please do ensure to first remove
spam from the email queues if present, to avoid the new IPs from
immediately getting blacklisted.

Configuring IP addresses
------------------------

Please note that the IP address should have a valid PTR and forward
hostname, which are NOT a sub-domain of the server hostnames. When
adding an IP address, it's important to ensure the PTR of the IP address
resolves to that IP address and is also used in the HELO. By default,
the system will use the PTR hostname as HELO. To overrule the automatic
system and set a custom HELO for the IP address you can use:

    https://demo1.spambrand.com/cgi-bin/api?call=api\_set\_outgoing\_ehlo&ip=IP&ehlo=EHLO

Example
-------

For example, I have a 2 node cluster:

-  node1.example.com
-  node2.example.com

I'd like to configure node2.example.com to deliver all outbound emails
randomly via both 1.1.1.1 and 2.2.2.2.

1. Open a ticket with SpamExperts support to add 1.1.1.1 and 2.2.2.2 as
   additional IPs to node2.example.com (or add it directly to
   /etc/network/interfaces yourself)
2. Create A-records in your DNS for both IPs (e.g. out1.example.com for
   1.1.1.1 and out2.example.com for 2.2.2.2)
3. Set the PTR of both IPs to the A records (e.g. out1.example.com for
   1.1.1.1 and out2.example.com for 2.2.2.2)
4. Set the HELO of both IPs:

   ::

       https://node1.example.com/cgi-bin/api?call=api_set_outgoing_ehlo&ip=1.1.1.1&ehlo=out1.example.com  
       https://node1.example.com/cgi-bin/api?call=api_set_outgoing_ehlo&ip=2.2.2.2&ehlo=out2.example.com

5. Set the default of node2.example to use both IPs randomly for
   delivery:

   ::

       https://node1.example.com/cgi-bin/api?call=api_set_outgoing_interfaces&domain=default&filtering_host=node2.example.com&interfaces=1.1.1.1%3B2.2.2.2&username=

6. To revert back to the default primary interface, you can execute:

   ::

       https://node1.example.com/cgi-bin/api?call=api_set_outgoing_interfaces&domain=default&filtering_host=node2.example.com&interfaces=&username=

Please note, step 4 is not needed is the correct PTR is set, as by
default the HELO is set to the PTR. You only need to ue this if it's not
possible to set a correct PTR

Warning - Do not use underscores (\_) in your hostnames if you are using
the PTR as the HELO, as this is not permitted per RFC.

Warming up new IPs
------------------

Many destination server will by default ratelimit traffic from IPs they
have not seen traffic from before. To prevent newly added IPs to get
immediately ratelimited, it is recommended to periodically activate them
using the IP so they "warm up" and destination servers get familiar with
their traffic. This will prevent a queue build-up. It's generally
recommended to take at least 7 days to warm up new IPs, starting with
delivering just an hour per day and increasing that to 24 hours over
time.
