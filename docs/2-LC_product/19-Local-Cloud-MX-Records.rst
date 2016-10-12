.. _2-Local-Cloud-MX-Records:

Local Cloud MX Records
======================

To route the incoming email for a domain through the **SpamExperts Local
Cloud** solution, you’ll have to replace the existing\*\* MX records\*\*
with records pointing to the SpamExperts solution.

It’s important to think in advance of the structure that best fits your
organization. As it’s generally complicated to update the MX record for
all domains, you’ll want to do it right the first time.

To ensure your MX record hostnames are future proof, we recommend to
define 4 MX record hostnames. Even if you only have 2 filtering servers,
that may change in the future and if you directly provide 4 records to
your customers, you won’t run into any issues when you continue to grow
in the future. Of course you can also choose to just use 1 MX record
hostname, 2, 3 or more than 4. The decision is in the end up to you!

It’s very important to ensure the “\ **MX record hostnames**\ ” are
different from the “\ **server hostnames**\ ”. The server hostnames
should only point to the **primary IP of the server**, and this cannot
be (easily) changed. By using separate “\ **MX record hostnames**\ ”,
you ensure you’re always flexible to make updates when required, without
affecting your infrastructure. The MX record hostnames can be based on
ANY domain, and doesn’t have to be part of the domain used for your
server hostnames.

When you have decided on the MX record hostnames, you can either point
them to a **loadbalancer** or use “\ **DNS round-robin**\ ”. In case you
do use a loadbalancer, we still recommend to apply “\ **DNS
round-robin**\ ” to one of your “\ **MX record hostnames**\ ”, so email
will continue to be handled even if your loadbalancer infrastructure
would be down.

When using DNS-round-robin, you can simply update the **MX record
hostname A-records** to add/remove servers or to change the mail flow
direction. That’s why it’s so important not to use the server hostnames
for this, as those cannot be modified and hence you lose the opportunity
to influence the mail flow direction and distribution.

We recommend to\*\* set the TTL for the A records as low as
possible\ **, for example just **\ “60” seconds\*\*, to increase the
randomness and hence the spread of connections across your
infrastructure. That way, in case a node would be unavailable, the
chance of hitting an available server is much larger.

In case you do have a physical load-balancer, we recommend:

-  mx1.example.com. > A-record to loadbalancer
-  mx2.example.com. > A-record to loadbalancer
-  mx3.example.com. > DNS-round-robin A-records (see below)
-  mx4.example.com. > A-record to loadbalancer

DNS-round-robin is a really simple trick to distribute traffic across
your Local Cloud filtering nodes, and to make sure that the senders try
multiple nodes in case you’d have temporary issues with a server.

For example:

-  Server 1 primary IP: 1.1.1.1
-  Server 1 secondary IP: 1.1.1.2

-  Server 2 primary IP: 1.1.2.1
-  Server 2 secondary IP: 1.1.2.2

-  Server 3 primary IP: 1.1.3.1
-  Server 3 secondary IP: 1.1.3.2

**This is how we recommend to setup your MX records:**

-  **mx1.example.com. A 1.1.1.1 (TTL 60)**
-  **mx1.example.com. A 1.1.2.1 (TTL 60)**
-  **mx2.example.com. A 1.1.1.2 (TTL 60)**
-  **mx2.example.com. A 1.1.2.2 (TTL 60)**
-  **mx3.example.com. A 1.1.1.2 (TTL 60)**
-  **mx3.example.com. A 1.1.2.2 (TTL 60)**
-  **mx4.example.com. A 1.1.1.2 (TTL 60)**
-  **mx4.example.com. A 1.1.2.2 (TTL 60)**

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/dns%20round%20robin.jpg
   :alt: 

\*\* Then you will add in your DNS Settings the MX Records, as
follows:\*\*

-  **yourdomain.ext. MX 10 mx1.example.com.**
-  **yourdomain.ext. MX 20 mx2.example.com.**
-  **yourdomain.ext. MX 30 mx3.example.com.**
-  **yourdomain.ext. MX 40 mx4.example.com.**

Note that we recommend to point the secondary/tertiary/quaternary to the
secondary IP address, as spammers often skip the primary MX record to
try and bypass spam filters. By pointing your “non-primary-MX-records”
to the secondary IP, we can actually recognize that the connection order
is wrong and we can use such information for the email classification
process. This is not required though, it’s just a recommendation. If
there is just 1 IP address available, all MX record-hostnames can point
there.

If you later add a third server, all you need to do is add the primary
IP (1.1.3.1) to the mx1 hostname, and the secondary IP (1.1.3.2) to the
mx2/mx3/mx4 hostnames. That way it’s easy to grow the filtering cluster,
without the need to make any changes to the domains you’re filtering.

Users should of course **remove their old MX records**, to make sure all
emails are filtered through the SpamExperts Local Cloud Solution. Note
that spammers sometimes send spam to the old A records, thus we
recommend customers to only accept emails from the SpamExperts servers,
for more information see the following
`article <https://my.spamexperts.com/kb/31/Change-my-mailserver-to-only-accept-from-the-filter-systems.html>`__.

Be advised that DNS changes may take some time before they are resolved,
therefore emails may be delivered to the original MX records for 24
hours.

You can check using the SpamExperts log search or within the :ref:`email headers  <4-View-email-headers>` if
the message has actually passed through the SpamExperts filtering nodes.
