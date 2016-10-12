.. _2-Local-Cloud-Server-Changes:

Local Cloud Server Changes
==========================

Server Modifications
====================

Server modifications may be needed, and as SpamExperts provides it’s
services SaaS, actions may be required from our side before such changes
are applied to prevent issues with the setup.

Be aware that even though we never change the original root SSH
password, and you can authorize your IP address for SSH access via our
web interface, you should never modify files directly on the system to
prevent breaking the setup. We do not support any problems whatsoever
that result from a direct change you made, so please always reach out to
our support if you believe a change is required. A fee may be charged to
undo any changes that occurred as root on the system, and a
reinstallation may be required in such cases to ensure the software can
be updated and monitored.

We do allow customers to update **“/etc/network/interfaces”** directly
to troubleshoot network problems or to add extra IP addresses, as long
as the primary IP address remains the same (details below).

Changing the primary IP address
===============================

In case the primary IP address of the server changes, the system will no
longer be able to reach out central intelligence networks and as a
result will no longer be email to process email traffic or be monitored.
In case the primary IP address will change, please notify us at least 3
working days in advance, so we can pre-authorize the new IP address in
our central networks. There is no fee charged for such change. Please do
ensure the new primary IP address has the PTR set correctly to the
server hostname, to prevent any issues.

Read more on `changing the primary IP address and server
moves <https://my.spamexperts.com/kb/127/Server-moves-and-IP-changes.html>`__.

Changing hostnames
==================

The SpamExperts Local Cloud setup relies on the server hostnames to be
consistent. If the hostname would change, the system will no longer
process any email. If you wish to change your hostname, we’ll have to
reinstall the systems and restore the existing configuration/data. A fee
applies to such modification. For more information
`contact <mailto:support@spamexperts.com>`__ our support team.

Adding more memory/CPU cores
============================

Adding more memory or CPU cores to your servers can be achieved without
our help. If the software is running on a physical server, you can
simply shut it down over SSH (or using a PDU) before making the hardware
changes. For virtual machines, it is as easy as changing the CPU/memory
allocation and rebooting the server.

Please inform our support about the planned (hardware) maintenance
window so we can temporarily disable the monitoring process of your
system.

We suggest you to reboot/modify one system at a time to ensure the
availability of your cluster.

Maintenance
===========

If you're planning to perform general maintenance on your servers,
powerfeed(s), network or anything that may affect the correct operation
of the spam filters; please inform us in advance. We need this
information so we can keep track of warnings triggered by our monitoring
system regarding your server(s).
