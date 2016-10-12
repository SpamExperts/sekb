.. _2-Server-moves-and-IP-changes:

Server moves and IP changes
===========================

Server moves
------------

This is actually depending on whether you are simply moving them or if
you are also changing IP's. If this is "just a move", we suggest you to
move these servers one at the time starting with your slave server(s).
This ensures that your email flow is not affected by this move.

Step one
~~~~~~~~

| Inform us when (date & time) you are planning the move and which
  servers are involved.
| This is important because we have to make preparations and mark the
  planned downtime in our monitoring system.

Step two
~~~~~~~~

Follow the steps mentioned in IP Changes (see below), if your IP
addresses are being changed as well. If the IP addresses do not change,
you can skip this step and proceed.

Step three
~~~~~~~~~~

Shutdown your first server and move it to new location.

Step four
~~~~~~~~~

Startup your server and verify that it came up properly. This can be
tested by pinging it. If everything is correct, you can ask us to check
if everything is correct. Once everything is working properly, you can
move the next server.

IP Changes
----------

Changing the IP's of your server(s) involve a few steps. If all of your
servers are receiving new IP's it is best to do the slave first, test
(or let us test this for you) whether it is still working properly and
proceed with the next server(s). This ensures that your email flow is
not affected by this change.

Step one
~~~~~~~~

Inform us what the new IP(s) for your server(s) are going to be and when
you are planning to do the change. This is **very important** because we
have to make preparations and mark the planned downtime in our
monitoring system. In case the IP changes without informing us, this
will affect the operation of your SpamExperts cluster.

Lower the TTL (time-to-live) of your server DNS entries so the change
can be propagated faster. Make sure that the reverse DNS of the IP(s) is
set to the *primary hostname* of your server (this may differ from your
MX record setting!)

Step two
~~~~~~~~

You have to modify the network interfaces configuration (in
/etc/network/interfaces) and save the file. Do not restart networking or
reset your server just yet, we still have to make some changes.

Step three
~~~~~~~~~~

We make the required changes to your system (with the exception of the
/etc/network/interfaces file since this is your responsibility) and
inform you when this has been completed. If you gave us the green light
to reboot the server or restart networking, we will do this.

Alternatively, you have to restart networking yourself when you see fit.
You can also reboot your server to make sure that all services are
listening at the correct IP.

Step four
~~~~~~~~~

Change the DNS record for the primary hostname of your server and let it
point to the primary IP of the server (the one assigned to eth0) The
change now has been completed and you can proceed with the other
server(s).
