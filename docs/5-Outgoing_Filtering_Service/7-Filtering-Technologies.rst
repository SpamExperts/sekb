Filtering Technologies
======================

| The filtering methods and system of SpamExperts have been specifically
  designed to avoid false positives. For that reason many different
  checks are performed to avoid making mistakes based on only a single
  classifier.
| Two levels of filtering can be distinguished. Filtering at the "SMTP
  level" and filtering at the "DATA level".
| Thanks to the combination of many different advanced filters and the
  compliance with the RFCs on how to handle connections, the
  technologies ensure email can never disappear. The sender is always
  informed by their sending server that the message was rejected and, in
  addition, messages blocked at the "DATA level" are usually available
  in the quarantine system.

SMTP level
~~~~~~~~~~

As much as possible the incoming email connections are not blocked until
after the "rcpt to:" SMTP command. This way we ensure the connection
belonging to the recipient domain in the logging server is properly
logged, to ensure an easy overview of all connections made to a certain
recipient.

| If the connection appears to be coming from an unknown source that is
  not yet ranked with a good  reputation  in our systems, it may be
  temporarily rejected with a 4xx code. In that case the sending server
  will queue the email, and automatically retry delivery.
| After 10 minutes the connection will be accepted by the cluster, on
  any of the filtering nodes, and the internal whitelists are adjusted
  to avoid causing such a delay in the email delivery the next time.
| This concept is also known as greylisting, however the SpamExperts
  implementation is a lot more complex than traditional greylisting
  systems since all nodes are fully synchronized, and only connections
  from servers that are unknown to SpamExperts network are temporarily
  delayed. Therefore email delays due to greylisting on active filtering
  clusters are quite uncommon and generally do not cause any problems
  for the recipients. If the connection appears to originate from a
  spamming source, it is also temporarily rejected with a 4xx code.
| This way, even if the server would have been wrongly listed (for
  example on an external blacklist) as a spamming source, or if the
  spamming problem has been resolved on the sending server, the email
  still does not get lost and will be delivered to the final recipient.
| Only if the connection is from a known, spam-only source, or if the
  behavior is in direct conflict with the RFC standards, a connection
  may be permanently rejected with a 5xx error code. If that would ever
  happen for a legitimate sender, the sender will always receive a
  bounce notification from their sending server. This issue only occurs
  when there are serious problems with the sending server that should be
  resolved at the sender's side.

DATA level
~~~~~~~~~~

After the "DATA level" is reached the system will scan the email content
of the message based on a combination of advanced statistical filtering
technologies, spam fingerprint databases, viruses, phishing, and
spyware. Email detected as spam is either temporarily rejected (4xx
error code) or permanently rejected (5xx error code) depending on the
total score. Email which is permanently rejected at this level as spam
is quarantined and available for release (except for viruses). In case a
legitimate email would have been permanently blocked, the sending server
will also always inform the sender that the email did not arrive.

Visual Filtering Diagram
~~~~~~~~~~~~~~~~~~~~~~~~

For a visual diagram of the filtering process please see
`here <http://download.spambrand.com/kb/Filtering-Diagram.pdf>`__

| The filtering methods and system of SpamExperts have been specifically
  designed to avoid false positives. For that reason many different
  checks are performed to avoid making mistakes based on only a single
  classifier.
| Two levels of filtering can be distinguished. Filtering at the "SMTP
  level" and filtering at the "DATA level".
| Thanks to the combination of many different advanced filters and the
  compliance with the RFCs on how to handle connections, the
  technologies ensure email can never disappear. The sender is always
  informed by their sending server that the message was rejected and, in
  addition, messages blocked at the "DATA level" are usually available
  in the quarantine system.
