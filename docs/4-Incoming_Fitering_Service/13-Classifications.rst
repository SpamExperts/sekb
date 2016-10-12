.. _4-Classifications:

Classifications
===============

In the SpamExperts Control Panel we use different classifications to
describe why a message was rejected or temporarily rejected.

Temporarily Rejected (4xx SMTP response)
----------------------------------------

**TEMPORARILY REJECTED**

Messages which have been temporarily rejected, stay stored on the
sending mail server. Legitimate mail servers always automatically retry
delivery of such messages. Depending on the reason of the temporary
reject, the message could get accepted at a subsequent delivery attempt.
It's always possible to whitelist the sender to disable any checks and
to ensure that the message will get accepted as soon as it's retried by
the sending server.

Greylisted
~~~~~~~~~~

Temporary rejection due to
:ref:`greylisting  <4-Greylisting>`.
This technology is only applied to new IP addresses which do not have a
(good) reputation yet in our global systems. We do **not** apply
"**classical greylisting**\ " so this should not cause any delays on
your legitimate traffic. For new Local Cloud installations please allow
up to 72 hours for the systems to "learn" about your traffic.

You have been denied authentication
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This means that you have used incorrect outgoing authentication details
too often in a short period of time.  To resolve this, use the correct
authentication details and wait a few moments and try again.  This is to
protect against brute-force attacks on your SMTP credentials.

Unable to verify destination address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This means the destination server is unreachable or temporarily
rejecting the email traffic. You'll have to check the destination route
set to ensure delivery is attempted to the correct server. The logs on
the destination server should show why it is not accepting the delivery
attempts.

Internal error
~~~~~~~~~~~~~~

An internal error occurred, this should automatically resolve. If not,
please contact `support <mailto:support@spamexperts.com>`__.

Per-minute connection limit exceeded
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The sender has exceeded his/her per-minute limit.

Too Many Connections
~~~~~~~~~~~~~~~~~~~~

Too many connections from the sending server. Ratelimited.

Too Many Concurrent SMTP Connections
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is a hard-coded limit of 10 concurrent SMTP connections per IP to
protect the systems against attack. Please ensure that the sending mail
server only opens up a maximum of 10 concurrent connections to avoid
hitting this limit.

Too many messages. Please wait for a while and try again.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This indicates that the outgoing user has exceeded the maximum amount of
messages configured for that outgoing user to be sent. In case the
limits should be changed, they can be modified via the SpamExperts
Control Panel for the outgoing user. These limits can be entirely
disabled there as well.

Mail for this domain cannot be accepted right now; please retry (Unable to
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

handle in active connection.)

Within a single SMTP connection, it is possible to deliver a message to
different recipients. The SMTP protocol only allows you to either
"accept" OR "reject" the email, without distinguishing between the
different recipients. In case one of the recipients has different
filtering settings, we cannot "accept" or "reject" the message as the
classification may differ per- recipient. In such case we return a
**temporary rejection**, so the sending server will retry delivery
individually for the recipients allowing to classify each message
separately. Most SMTP servers retry immediately, and hence there will be
no delivery delay. If all recipients are sharing the same filtering
settings, the message will be immediately accepted for all recipients
(or rejected) without this temporary reject. In case a delay is
experienced, the sender can instead configure their server to either
immediately retry (to prevent such delay), or to open a separate
delivery connection for each recipient.

Rejected (5xx SMTP response)
----------------------------

**REJECTED**

Messages which have been rejected are blocked by the system. Generally
these messages can be reviewed in the "**Spam quarantine**\ ", from
where they can be released. It's always possible to whitelist the sender
to disable any checks and to ensure that the message will get accepted
as soon as it's resent by the sender.

Lines in message were longer than user maximum
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This means that line within the email is longer than the set maximum.
The RFC 5322 (SMTP 5321) specifies a maximum line length of **998**.
Normal email clients always enforce this limit to avoid delivery
problems. The problem should be resolved at the sender side, or the
check can be disabled.

Message had more parts than the user maximum (Too many MIME parts)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This refers to the amount of MIME parts that a message contains. The
default limit is set to **100**.  This can be de-passed and triggered
with excessive amounts of attachments or other MIME parts.

Sending server used an invalid greeting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The sender has used an invalid HELO/EHLO. This could be either because
an IP address is used for the HELO, or because the HELO contains an
invalid character, for example : underscore (\_). The RFC states that a
FDQN (Fully Qualified Domain Name) **MUST** be used.

Considered spam
~~~~~~~~~~~~~~~

Our systems considered this message as **SPAM** and quarantined the
message. Releasing the message from quarantine will report it as a
classification mistake to correct our systems.

SPF failure
~~~~~~~~~~~

This means that the SPF (Sender Policy Framework) has been broken. If
this is legitimate mail, then this could be due to a forwarding
construction. Please see our
:ref:`SPF <5-Setup-a-SPF-record>`
knowledgebase article for more information.

Pyzor
~~~~~

 Pyzor is a content related classifier based on collected/reported data
from our datasets. Releasing the message from quarantine will report it
as a classification mistake to correct our systems directly.

Sending server is missing DNS records
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The sending server is missing MX records or A records. Please note that
any DNS changes only take effect after the initially set TTL has
expired.

Destination address does not exist
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The destination server is rejecting the connection with a 5xx permanent
failure. The logs on the destination server will show why the message
was rejected. You'll have to resolve the problem on the destination
server to ensure it accepts the email.

Phishing attempt detected
~~~~~~~~~~~~~~~~~~~~~~~~~

Our systems detected a phishing attempt. Releasing the message from
quarantine will report it as a classification mistake to correct our
systems.

Date header far in the past or future.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This classification means that the date header of the email is more than
the default 7 days in the past or future. Releasing this will only
deliver the message to the recipient.  This is something the sender will
need to resolve.

Bad header count (Message incorrectly formed)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Emails should never contain duplicate headers such as "**Subject**\ " or
"**To**\ ". In case such duplicate headers are found, the message will
be rejected until the underlying bug is fixed in the email sending
software.

Blacklisted sending server
~~~~~~~~~~~~~~~~~~~~~~~~~~

The sending server has been blacklisted on the IP blacklist.

Sending server listed on multiple DNSBL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The sending server has been found on multiple blacklists. Releasing the
message from quarantine will report it as a classification mistake to
correct our systems. For a temporary override please see
`http://www.spamrl.com <http://spamrl.com>`__

Sending server attempted too many invalid addresses
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The email sending server has attempted to deliver email to too many
invalid email addresses in a certain time period. Please retry again
later.

Blacklisted sender
~~~~~~~~~~~~~~~~~~

The sender was added to the custom sender blacklist.

URLBL
~~~~~

A URL within the email has been listed on several blacklists. Releasing
the message from quarantine will report it as a classification mistake
to correct our systems. The rejection message contains more information
about the responsible list.

UCEPP
~~~~~

A token was detected in the message that has been seen in recent spam
(e.g. URL, IP, phone number, or other specific details). Releasing the
message from quarantine will report it as a classification mistake to
correct our systems.

External Pattern Match
~~~~~~~~~~~~~~~~~~~~~~

The layout & format of the email matches known spam emails already
listed. Releasing the message from quarantine will report it as a
classification mistake to correct our systems. The rejection message
contains more information about the responsible list.

User-specified blackhole address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A user specified /dev/null Address.  This email will not get delivered
anywhere.

Combined Score
~~~~~~~~~~~~~~

The "**combined**\ " result provides a weighted classification score of
the different classifiers. Depending on the configured "**quarantine
threshold**\ ", the message will be rejected as spam or accepted. A
quarantine threshold score of 0.9 is recommended. To be more tolerable
for senders using a wrong HELO/PTR/IP configuration, a score of 0.91 can
be set. The lower the quarantine threshold, the more messages will be
quarantined as spam. The SMTP message returned for this classification
is "**High probability of spam**\ " to the sender. Please ensure to
release the message from quarantine if it's legitimate, this will adjust
the scoring in our various databases.

CRM114
~~~~~~

CRM114 is a statistical content check. When a message gets blocked by
this classifier on our systems, then this mean there has been a close
match within the email that corresponds to an already seen spam
message. Releasing the message from quarantine will report it as a
classification mistake to correct our systems.

Subject contains invalid characters.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When a message is rejected with "**550 Subject contains invalid
characters**\ " the email subject will have non-ASCII characters, which
is not allowed by the RFC. To include non-ASCII characters in subjects,
the subject is required to be properly encoded, for example with UTF-8.
Any normal mail client will automatically handle that for you, so it's
likely a bug in a custom written script that generated the invalid
subject. The evidence header for this classification will show "**Badly
formed Subject header**\ ".

Tokens
~~~~~~

Global Tokens (Hosted cloud / Local Cloud)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

These are statistical content checks that are built based on data
collected from all our clusters and clients worldwide. Releasing the
message from quarantine will report it as a classification mistake to
correct our systems..

Cluster Tokens (Local Cloud Only)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This is similar to the global tokens, but based specifically on your
Local Cloud traffic and reports. Releasing the message from quarantine
will report it as a classification mistake to correct our systems.

Sanesecurity
~~~~~~~~~~~~

We make use of certain datasets from Sanesecurity. To decode
Sanesecurity signatures please check
`here <http://sane.mxuptime.com/>`__.

Safebrowsing
~~~~~~~~~~~~

In case your message has been rejected with "safebrowsing" in the
rejection message, it means it has been (recently) `listed by
Google <http://www.google.com/safebrowsing/diagnostic?site=google.com/>`__
as hosting malicious files.

Header is too long
~~~~~~~~~~~~~~~~~~

SpamExperts by default will reject emails with excessive large header
values, as this is a common indicator for non-legit emails.

Restricted characters in address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In case your message has been rejected with "**550 restricted characters
in address**\ " in the rejection message, it means that the recipient
address contains a character that is not accepted by the system, for
example: "&". You can control which characters are allowed for a domain
on the "**Domain settings**\ " page.

Relay not permitted
~~~~~~~~~~~~~~~~~~~

In case your message has been rejected with "**550 Relay not
permitted!**\ " in the rejection message, it means that delivery was
attempted to the incoming filtering service on port 25 to a domain which
has not (yet) been added to the filtering solution. To resolve this,
please add the domain to the incoming filtering service. If you're
trying to use the outgoing filtering service, please ensure to use the
outgoing filtering service port **587** instead.

Message submission is for authorised users only!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This indicates you're attempting delivery via our outgoing email filter
on port 465/587 (default). If you're receiving this response to an
incoming email delivery attempt, your mail server is wrongly set up (and
likely a misconfigured version of Lotus Domino). If you're trying to
send outgoing email, please ensure to provide a valid username/password
to authenticate.

Legitimate bounces are never sent to more than one recipient.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In case your message has been rejected with "**Legitimate bounces are
never sent to more than one recipient**\ " in the rejection message, it
means that the mail server was trying to deliver an email to multiple
recipients with an empty "MAIL FROM:<>" (return-path). The SMTP RFC
5.3.2.1 indicates that null sender emails (bounces) can never be sent to
multiple recipients, so there may be be a misconfiguration on the
mailserver.

Destination address is not configured.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This usually means that the filtered domain is using '**Local
Recipients**\ ' and that specific email address in not in their list of
approved recipients.

The content of this message looked like spam.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This indicates the message has been blocked based on our content
scanners, as similar messages have been reported as spam. In case the
message is legitimate, please ensure to release it from quarantine. This
will update the statistical filters to prevent such issues in the
future.

Unrouteable address
~~~~~~~~~~~~~~~~~~~

This error occurs if there is a (permanent) network error delivering to
the destination mail server. This issue is unrelated to the SpamExperts
software and indicates a network problem. Possibly the DNS servers of
the domain are broken, or they cannot be reached from the filtering
server. Alternatively it's possible the destination hostname or IP does
not exist, or is unreachable because of a permanent issue.  You can
check for DNS errors on the following page: http://dnscheck.sidn.nl/.
Please contact your network administrator to investigate any networking
issues.

We do not accept mail from this address
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This error occurs if the sender has been manually added to the "Sender
blacklist" for the receiving domain.

We do not accept message/partial messages here
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Before people had a permanent internet connection, sending larger emails
was time-consuming and often failed. Therefore older email clients
sometimes still break up large emails into separate parts for delivery.
This old email feature is not used anymore nowadays, and imposes a
severe risk as it makes detection of viruses impossible (as viruses
would be split over separate emails before being assembled again by the
destination email client). Please ensure to resolve your email client
settings to to split up larger emails.

DMARC - REJECT
~~~~~~~~~~~~~~

This error occurs if the sender's domain has a strict DMARC policy in
place. If the sender's DMARC record is set to "REJECT" and the messages
come from IP addresses that are not in the sender's SPF, then these are
rejected and not quarantined.

DMARC - Quarantine
~~~~~~~~~~~~~~~~~~

This error occurs if the sender's domain has a strict DMARC policy in
place. If the sender's DMARC record is set to "QUARANTINE" and the
messages come from IP addresses that are not in the sender's SPF, or
have a failed DKIM, then these messages are quarantined. Whitelisting
will not bypass this.

Accepted (2xx SMTP response)
----------------------------

**ACCEPTED**

Messages that display the 'Accepted' response have not necessarily been
delivered. It means the message has been accepted for delivery. If
immediate delivery fails, the message will be automatically retried. If
the destination server rejects the email, a bounce will be generated to
the sender.

Message looked like non-spam
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This message was accepted for delivery based on our content
checks. Reporting the message as spam will correct our systems.

Accepted, DNSWL
~~~~~~~~~~~~~~~

The sending server is listed on several DNS-Whitelists. This means no
spam has been seen recently from this sending server. Reporting the
message as spam will correct our systems.

Accepted, whitelist
~~~~~~~~~~~~~~~~~~~

The sender has been placed on a manual whitelist by the recipient.
Removing the sender/recipient from the whitelist will prevent spam
getting through.
