.. _2-Firewall-Usage:

Firewall Usage
==============

As SpamExperts offers SaaS managed email security service, it is very
important the servers are fully accessible at all times without external
(network) restrictions. Since SpamExperts is managing a large amount of
servers, it's important that the configuration is the same on all
systems to allow quick intervention when required. SpamExperts therefore
will take care of all security (updates) on the machines, and ensures
protection of the ports/services running on the environment. We also
collect data on external attacks and use this as part of our protection
service.

Ports that are open on the environment, are either publicly available
(SMTP, HTTP &amp IMAP for instance) or restricted based on IP by our
local firewall. This means that there is no need for an extra external
firewall, and we highly recommend to **DISABLE** any external firewall
to avoid conflicts with the software. We do of course welcome a full
security audit after we completed the setup of the systems.

If your network does not allow you to disable an external firewall
entirely, we strongly recommend to choose another network to host the
servers. If you nevertheless still wish to run an external firewall
besides the firewall we manage for you on the systems, a list of ports
that require to be open is available below. Please do note that between
version updates the required open ports may change, this will then be
shown in the :ref:`Dedicated Changelog  <1-Changelog>`. In case
the newly ports are not available within 5 working days, our software
may break and would be unsupported until the external issue is resolved.

As administrator of the hardware/network, you are responsible to keep
track and ensure the required ports are open before the
installation/upgrade is started. In the event of a disrupted service due
to an external firewall, a fee may be charged for handling the resulting
monitor warning/support. Please ensure that the required ports are
always open to avoid such situations. When using NAT (Network Address
Translation), which we strongly recommend against, please ensure that
the source IP address is identical to the external IP of the server and
not the primary IP of the subnet. See more information on the `Local
Cloud Installation procedure
page <https://my.spamexperts.com/kb/34/Set-up-my-dedicated-server-for-SpamExperts.html>`__.

Open ports
----------

There should be no firewall active that is obfuscating/altering/removing
any of the traffic to/from the SpamExperts servers (including e.g. the
SMTP welcome banner). For example certain Cisco devices are known to
interfere with SMTP by either having ESMTP inspection enabled, fixup
enabled or due to IDS being turned on. All these must be turned off. See
for more information on this
`here <https://my.spamexperts.com/kb/130/General-problems-with-specific-routersorfirewallsormailservers.html>`__.

As we have previously mentioned, we will manage the server’s local
firewall.

The following ports must be unfiltered and unrestricted:

In- & Outbound
--------------

All ports are TCP unless stated otherwise.

-  80
-  443
-  8443
-  25
-  143
-  123 (UDP)
-  993
-  3306
-  10050
-  873
-  30443
-  10045-10049 (TCP/UDP)

ICMP should be allowed.

Inbound
-------

All ports are TCP unless stated otherwise.

-  22 (SSH has been IP access restricted by our software already, see
   more details below)
-  465
-  587

Outbound
--------

All ports are TCP unless stated otherwise.

-  53 (TCP/UDP)
-  6568 (UDP)
-  6569 (UDP)
-  1600 (UDP)
-  4121
-  24441 (UDP)
-  10051
-  2703
-  61380-61399 (TCP/UDP)

SSH port 22
-----------

SpamExperts does not believe in security through obscurity, and hence we
run the SSH service on port 22. Our software restricts which IP
addressess can access the SSH service, and you can manage the authorized
IP address via our webinterface. We do not support an external firewall
blocking port SSH, as that prevents us from collecting data on external
attacks and in case of e.g. routing issues may block us from being able
to solve issues on the environment. If you do require as a company
policy to restrict SSH port 22 to specific IPs, you can use the
/etc/hosts.allow list from the server to do so. In addition, please
contact our support to provide a list of monitoring server IP(s) that
are in use which are required to be added as well. IMPORTANT: in case of
issues reaching the system please note that such problems will not be
supported by our team and our premium support contract services do not
apply to environments that have an external firewall interfering with
the connectivity. We do welcome any external security audit, and as a
security company follow the best practises in ensuring a secure
environment.
