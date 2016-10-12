Message Queueing
================

Generally emails are directly delivered to the destination server and
not stored locally on the filtering machines. However if the destination
server is unavailable, all email sent to known destination recipients
are queued locally on the filtering servers for delivery. Emails which
have been permanently rejected by the destination server with a 5xx
error code, will NOT be queued and are rejected by the systems. If the
destination mailserver acts as catch- all for the domain, no recipients
will be cached and therefore email will only be queued if the valid
recipients have been explicitly set as Local Recipient in the
SpamExperts control panel.

**Queue Access**
~~~~~~~~~~~~~~~~

You can access the email queue from the webinterface, from which you can
also manually force-retry delivery of a queued message.

**Automatic Retry Schedule**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Messages queued for known valid recipients because of temporary problems
with the destination route (for example network problems) are
automatically retried for delivery at the following approximate
intervals:

-  During the first 2 hours, delivery is retried at a fixed interval of
   15 minutes.
-  During the next 14 hours, delivery is retried at a variable interval,
   starting at 15 minutes and multiplying by 1.5 with each attempt (e.g.
   after 15 minutes, then 22.5 minutes, then 34 minutes, and so on).
-  From 16 hours since the initial failure, until 4 days have passed,
   delivery is retried at a fixed interval of every 6 hours.
-  After 4 days we generate a bounce to the sender. If the bounce cannot
   be delivered immediately, it will be frozen. After this time,
   delivery of the message will have permanently failed. Optionally via
   the Software API the 4 days can be overruled to a longer (or shorter)
   period.

When a message is frozen,  (when a message can neither be delivered to
its recipients nor returned to its sender) no more automatic delivery
attempts are made. A super administrator can “thaw” ( force retry)  such
messages when the problem has been corrected.

SpamExperts caches valid recipients up to 4 days. When such entry has
expired, SpamExperts will not queue email for such recipients and
instead temporarily reject the message so it's queued on the sending
server. The sending server in such case will automaticallty retry
delivery. When using the "Local Recipients" feature, no caching is
involved and SpamExperts continues to accept and queue the emails for
all specified recipients.

**Messages Queued**
~~~~~~~~~~~~~~~~~~~

The `SMTP RFC
5321 <http://www.ietf.org/rfc/rfc5321.txt%20"http://www.ietf.org/rfc/rfc5321.txt">`__
specifies a sending server must queue messages which cannot be directly
delivered because of a temporary failure at the receiving end. Therefore
in case of temporary issues with the email infrastructure, emails will
not be bounced immediately but are instead queued on the sending
server(s) and automatically retried for delivery. In case of downtime of
the destination mailserver, messages are only accepted for delivery by
the filtercluster if the recipient is known to be valid. Valid
destination recipients are cached up to 96 hours.

When a destination server cannot be reached for 4 days, all messages
will be bounced after 4 days and no new email will be accepted/queued
until the destination server is back online. This 4 day period is
conform the SMTP RFC. The reason it's not longer than 4 days, is because
it's important for the sender to be aware that delivery of their message
has been failing for 4 days so they can try and contact the recipient in
another way.

Your own fallback server(s)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Please note that when you specify multiple destination routes, the
SpamExperts system will assume you run your own fallback system. If the
specified fallback server is not responding to recipient callouts, there
will be no database built up of valid recipients internally. We
recommend not to specify any fallback server(s) unless you've
specifically designed your infrastructure to handle outages of the main
destination server.

Troubleshooting messages in the queue
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If there are messages stored in the queue, this is always to to a
(temporary) error delivering to the destination server. To investigate
the issue:

1. Verify you have set a correct destination route (also ensure there
   are not multiple destination routes specified, normally there should
   just be 1 route)
2. Check the logs on your destination server to investigate why it's not
   accepting the delivery attempts
3. Run a `telnet
   test <https://my.spamexperts.com/kb/19/Test-my-server-is-correctly-accepting-mail.html>`__
   to check the response of your destination mailserver
4. If after following these steps you still have an issue, please
   contact SpamExperts support providing a sample sender/recipient/date
   to investigate

Using the Software API (Local Cloud Only)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It's possible to get the inbound or outbound queue data directly from
the API. There are 2 types of calls 'api\_get\_delivery' and
'api\_delivery' (for both inbound and outbound). Example's of their
output can be seen below:

::


        curl -k -s "https://user:pass@master.hostname/cgi-bin/api?call=api_get_delivery_queue&domain=example.com&include_retry_time=False"

This will produce the following:

::


        example.com,mx.example.com,1ZPhsl-0004Im-99,21887,3794,,devnull,True  
        example.com,mx.example.com,1ZPSrl-0007Pz-96,79609,3697,,devnull,True  
        example.com,mx.example.com,1ZPhsl-0004IK-0g,21887,3750,,devnull,True  
        example.com,mx.example.com,1ZPmWl-0000TD-5p,4031,3686,,devnull,False  
        example.com,mx.example.com,1ZPaPl-0006kV-Ip,50593,3727,,devnull,True

::


        curl -k -s "https://user:pass@master.hostname/cgi-bin/api?call=api_delivery_queue&domain=example.com&include_retry_time=False"

Produces the following:

::


        example.com  
        mx.example.com,1ZPhsl-0004Im-99,21932,3794,,devnull,True  
        mx.example.com,1ZPSrl-0007Pz-96,79654,3697,,devnull,True  
        mx.example.com,1ZPhsl-0004IK-0g,21932,3750,,devnull,True  
        mx.example.com,1ZPmWl-0000TD-5p,4076,3686,,devnull,False  
        mx.example.com,1ZPaPl-0006kV-Ip,50638,3727,,devnull,True  
        mx.example.com,1ZPe9l-0004nk-MD,36254,3691,,devnull,True  
        mx.example.com,1ZPkdl-00069b-54,11330,9869,,devnull,False  
        mx.example.com,1ZPkml-0003Mm-K9,10772,3765,,devnull,True  
        mx.example.com,1ZPlcl-0004Zq-K1,7548,9919,,devnull,False

There are any variables that can be used for these call's. Details on
all of these can be found in the "Software API calls" page of your Local
Cloud installation.

An example, of how to get the top outbound queued messages would be
something like this:

::


        curl -k -s "https://user:pass@master.hostname/cgi-bin/api?call=api_get_outgoing_delivery_queue&include_retry_time=False&frozen=false" | cut -d "," -f6 | sort | uniq -c | sort -nr | head -20
