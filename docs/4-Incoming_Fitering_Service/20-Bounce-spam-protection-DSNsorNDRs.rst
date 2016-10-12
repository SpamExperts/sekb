Bounce spam protection (DSNs/NDRs)
==================================

"Bounce spam" can be an annoying problem. The email SMTP protocol is a
very simple protocol that was defined in
`1982 <http://tools.ietf.org/html/rfc821%20"http://tools.ietf.org/html/rfc821">`__.
Spam was not yet a problem and to keep things as simple as possible, no
security measures were implemented in the protocol itself. The result of
this is that there is no verification whatsoever that the "From:"
address in an email message actually belongs to the sender.

To try and avoid spamfilters, spammers will typically use random email
addresses as fake senders. This way they can avoid any simple spamfilter
that blacklists based on the sender email address. It is important
however that the email address they use as a sender does exist, since
spamfilters can apply a "sender verification check" to ensure that the
sending address itself exists.

SpamExperts applies advanced methods to identify and block
"bounce-spam".

What causes Bounce
~~~~~~~~~~~~~~~~~~

Properly set up mail servers will not cause bounce spam and directly
reject the message with a 5xx error code when the spammer tries to
deliver it. Unfortunately there are many legitimate mail servers that
are incorrectly set up. The spammer tries to deliver a spam message with
your email address in the from to an unknown address, the bad mail
server accepts the messages for delivery, it then finds out that the
destination user does not exist, and it will send a bounce email to your
email address because it (wrongly!) believes you are the originating
sender. Because these bounces do not come from spamming servers, but
from legitimate servers, they are very hard to block by any spam
filters.

Catchall domains
~~~~~~~~~~~~~~~~

| If you have configured your email system to accept all email sent to
  any address @example.com, this is called a "catchall domain". The main
  advantage for you is that you won't have to create a separate mailbox
  for each address that should work.
| Be Advised: The problem however is that if spammers detect that your
  mail server claims to accept email for any address, they can easily
  generate random email address and end with @example.com (your domain
  name) to generate millions of different "valid" email addresses! It's
  therefore highly recommended to **disable the email catchall** to
  avoid spammers from abusing your domain and also generate fake senders
  for their spam messages.

SPF / DKIM
~~~~~~~~~~

By setting a `SPF
record <https://my.spamexperts.com/kb/117/Setup-a-SPF-record.html>`__
for your domain, you reduce the attractiveness for spammers to use your
domain for sending out email. Also signing your emails with a
`DKIM <https://my.spamexperts.com/kb/33/Generate-DKIM-certificate.html>`__
certificate should further reduce the attractiveness to spoof your
domain name for outgoing spam.

BATV signing
~~~~~~~~~~~~

A special "trick" to avoid bounce spam is to sign every outgoing email
with a special `Bounce Address Tag Validation
code <http://en.wikipedia.org/wiki/Bounce_Address_Tag_Validation%20"http://en.wikipedia.org/wiki/Bounce_Address_Tag_Validation">`__ (BATV).
If a bounce is generated from a destination server, the incoming filter
will check if it was originally signed. Only if the message was
originally signed, the bounce is accepted. If the message was not signed
when it was send out, the bounce is not accepted. SpamExperts supports
BATV signing for its outgoing email products.
