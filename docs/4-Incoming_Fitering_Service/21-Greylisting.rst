.. _4-Greylisting:

Greylisting
===========

Greylisting
===========

We apply an advanced form of greylisting to help and stop a significant
amount of spam with minimal resource usage. Although greylisting is a
controversial technology, it is still highly effective when applied
properly.

First of all it's important to mention that all nodes within the cluster
are synchronized, and aware of the connections made to each other. Thus
for the greylisting technology it does not matter to what node a
connection is made. We also keep track centrally of "reputable hosts" to
avoid any greylisting delays from known legitimate servers.

| Greylisting works based on the 'triplet' information consisting of
  "sending server IP /24 subnet"/"sender email address"/"recipient email
  address". Whenever we receive a connection from an unknown 'triplet',
  we will temporarily reject (SMTP code 4xx) the connection for 10
  minutes after seeing the first attempt.
| A temporary reject in this case means that the sending server is
  requested to temporarily queue the email, and automatically retry
  later. Any legitimate SMTP server is required by the
  `RFC <http://www.rfc-editor.org/rfc/rfc5321.txt%20"http://www.rfc-editor.org/rfc/rfc5321.txt">`__
  to support this, and it's a fully automatic process of which the
  original sender will not receive any notification. It does not matter
  how often the server retries within the 10 minute interval or to which
  node, only after the 10 minutes we will accept the email.
| This will result in a short delivery delay, therefore there is an
  advanced automatic system to minimize such delays. After accepting the
  email from an previously unknown 'triplet', the 'triplet' becomes
  'white' to avoid temporarily rejecting connections from such triplets
  in the future. Furthermore whenever we have seen (at least) 5
  different successful (white) triplets from the same IP /24 subnet or
  (at least) 2 different successful (white) triplets from the same
  subnet and sender email address, the subnet or subnet+address is added
  to an internal "greylisting whitelist" system to avoid greylisting
  connections from that IP.
| All active mail servers delivering email to the servers will therefore
  not be influenced by the greylisting technology, since they will be on
  the internal "greylist whitelist". The greylisting technology is only
  applied to new unknown servers. Servers that have been blacklisted for
  sending out spam, will lose their whitelisted entry again so may
  shortly be greylisted for new connections.

-  Greylisted triplets become white after 10 minutes.
-  IP subnets are added to the "greylisting whitelist" after 5 white
   triplets.
-  IP subnet + sender address pairs are added to the "greylisting
   whitelist" after 2 white subnet+address pairs.
-  Greylist grey entries are expired after 8 hours.
-  Greylist white entries are expired after 60 days (if they have not
   been seen again).
-  Greylist triplets only apply to individual recipient domains, but the
   "greylisting whitelist" is shared across all domains for a cluster.

**Be Advised:** Most support questions regarding temporarily rejected
connections are because customers see the temporary reject log entries,
and are not aware that the message was **NOT** **blocked/identified as
spam**. The message was only shortly delayed to verify that the sending
server is behaving correctly (in accordance with the requirement for
SMTP servers).

**T**\ he "sending server IP /24 subnet" is basically the first part of
the sending server's IP address. For example, if the server's IP was
222.153.243.117, then the string used in the 'triplet' would be
'222.153.243'. This includes up to 256 (.0 to .255) servers, almost
always within the same organisation. This means that if an organisation
has several sending servers (typically within the same subnet), it does
not matter which sending server makes the second attempt.

More information on the RFC and greylisting can be found at `Section
5.3.1.1 of RFC1123 <http://www.ietf.org/rfc/rfc1123.txt>`__
