ISPs that are not supported
===========================

Since the SpamExperts systems fully operate at SMTP level, it is
compatible with any type of mail server. A few internet providers
however stop accepting email for a domain that does not have the MX
records pointed directly to the mail server. Below you can find a list
of such internet providers and instructions how to avoid problems.

1und1.de
~~~~~~~~

When using the 1und1 mail servers it is only possible to use the
SpamExperts filtering solutions if you run your own DNS (or use an
external DNS service). As soon as the MX records are changed in the DNS
of 1und1, they will stop accepting email for your domain.

inode.at / UPC
~~~~~~~~~~~~~~

Before changing your MX records you will have to request inode.at/UPC to
keep accepting email for your domain. They will manually resolve that
for free.

Fasthosts.co.uk
~~~~~~~~~~~~~~~

Currently fasthosts.co.uk does not allow to change the MX records to a
hostname, and their technical support indicated that the use of an
external antispam relaying service is not possible. We recommend you to
change to another webhosting company.

cPanel hosts
~~~~~~~~~~~~

When changing the MX records for a domain using cPanel, please ensure
that you always enable the "**Local Mail Exchanger**\ ". If you don't,
cPanel may stop accepting email completely for your domain.

TransIP DNS Provider
~~~~~~~~~~~~~~~~~~~~

Unfortunately the nameservers of "TransIP" are unsupported for private
label Hosted Cloud MX records.  TransIP runs an in-house built DNS
system, which wrongly returns the "aa" flag for any DNS lookup.
Therefore, the lookup does not properly follow the NS records. This bug
has been reported to TransIP already, although they confirmed the bug in
their nameserver response they unfortunately haven't resolved it yet.
