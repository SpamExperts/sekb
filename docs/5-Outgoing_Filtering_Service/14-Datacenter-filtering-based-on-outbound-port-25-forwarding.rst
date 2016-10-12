.. _5-Datacenter-filtering-based-on-outbound-port-25-forwarding:

Datacenter filtering based on outbound port 25 forwarding
=========================================================

We regularly receive the request about possibilities to force all
outbound port 25 traffic at network level to the SpamExperts solution.
This article explains what can, and what cannot be done.

Port 25 redirection at the network level
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you operate your own networking, assuming your networking equipment
supports it you could add a port based ACL and policy based routing
(routers Layer-3+). Note that such port based ACL may take up quite some
CPU resources on the routing equipment. After authorizing your IP
range(s) as SpamExperts outgoing users, you should be able to forward
all port 25 outbound traffic for those ranges to the SpamExperts server
IPs (at port 587, or a custom port 25 outbound listener). The
SpamExperts servers will accept the connections, scan the email, and
deliver the legitimate messages to the internet.

Please note that with this setup, the delivery of legitimate messages
will be done from an IP address assigned to the SpamExperts server. You
can configure which IP the system should use for delivery (depending on
the source IP), however it's not possible to preserve the source IP of
the originating server for delivery. This also means that e.g. SPF
records would require to be updated to include the SpamExperts filter
server IP space.

Why the source IP cannot be preserved
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Without going into too much detail, technically it's not possible to
preseve the source IP for delivery as SpamExperts does not act as a
transparent proxy. There are solutions that do act as a transparent
proxy, however they can only do so by disabling TLS encryption (as
otherwise it cannot inspect the traffic). Any recipient mailserver will
still accept such unencrypted traffic, however it does mean that all
your customers' communication is delivered plain-text via the internet.
As a security company, we put great value on secure connectivity between
servers and hence have decided not to provide such transparent option in
our software (as it would enforce TLS encryption to be disabled). In
most countries, this also violates the data protection laws (e.g. in the
European Union transferring email with private data plain-text is not
allowed). If there would be a technical way to accomplish this without
violating the laws and keeping the email secure, we'd love to hear your
thoughts!

As a datacenter, how can I then best prevent ranges from getting blacklisted
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you operate a datacenter, it's very important you monitor your IP
space for abusive behavior. Many large mail company (such as Hotmail and
Gmail) can provide you a free "feedback loop" with spam complaints from
their users related to "your" IP space. It's easy to automatically
process such reports, e.g. using the opensource
`Abuse.io <https://www.abuse.io/>`__ tool. If you get too many
complaints about a specific IP, you can:

1. Block port 25 outbound for that IP until they've resolved the issue
2. Block port 25 outbound for that IP, and offer the client to relay
   their outbound email via the SpamExperts solution to identify/block
   spam (and delivery from a clean IP)
3. Force-redirect port 25 outbound for that IP to the SpamExperts
   solution, to analyze the spam and determine to e.g. terminate the
   account

As a software development company, we'd love to hear other suggestions
on how our technology can assist you in preventing these issues!
