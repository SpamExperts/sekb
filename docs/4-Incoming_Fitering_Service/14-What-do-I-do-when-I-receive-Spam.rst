What do I do when I receive Spam?
=================================

Even though you may using our anti-spam system correctly, it is possible
you are still receiving spam. This page explains the steps to determine
why you are still receiving spam messages, and how best to resolve this
issue.

**Check whether your MX records are correct**

To prevent spam effectively, your **MX records** should **ONLY** contain
those of the filtering servers, no other mail servers. If you leave the
old MX records pointing to your own mail server, spammers will attempt
to deliver spam directly, thus bypassing the spam filters. You can look
up your domain MX records `here <http://mxtoolbox.com/>`__.

**Analyze the spam email header**

Email headers show detailed information about the origin of a message
and the various systems it passed through. Simply `View email headers`_ in
your email client, and look for the line starting with
"X-Recommended-Action:", if it's present the message was processed by
our filters. You'll also see a "X -SpamExperts-Evidence:" header
(SpamExperts may be replaced with a private label name), if it says e.g.
"Whitelisted" it means that we did not check the message as the
sender/recipient was whitelisted in the control panel.

**X-SpamExperts-Class: line missing**

If you do not see a line starting with "**X-Recommended-Action:**\ " in
the email headers, this means the **spam message did NOT pass through
our systems**, and therefore could not be blocked. There are various
reasons why this might have occurred:

-  You might not be using the SpamExperts MX records, so please check
   the MX records for your domain. It's important that you only use the
   following SpamExperts MX records (for our Hosted Cloud):

   -  mx.spamexperts.com. (priority 10)
   -  fallbackmx.spamexperts.eu. (priority 20)
   -  lastmx.spamexperts.net. (priority 30)

-  You are using the correct MX records, but they have not had
   sufficient traffic pass through them, it being a fresh installation.
   After changing the MX records in your DNS, it may take up to 48 hours
   before this update reaches all DNS servers world-wide. During this
   period, email may still be delivered directly to your mail server and
   therefore may not be filtered yet by the SpamExperts servers.
   Spammers often use old DNS information, so for a short while you may
   still receive spam that was never scanned by our servers.
-  Somehow the spammer delivered directly to your destination mail
   server, to prevent this we recommend users to configure their
   firewall/mail server `to only accept messages from our
   servers <https://my.spamexperts.com/kb/31/Change-my-mailserver-to-only-accept-from-the-filter-systems.html>`__,
   to avoid this issue.

**X-SpamExperts-Class: line says "whitelisted"**

If the class line says "**whitelisted**\ ", this means that you must
have added the sender or recipient email address, to their respective
whitelist on your domain. Spammers always fake the sender, and try to
use senders that are likely to be put on whitelists by recipients.
Therefore, it's important to never whitelist your own email address as a
sender, since spammers will often send you messages that appear to
originate from yourself! The whitelists should only be used to overrule
the filtering technologies, if they are causing a problem for you, by
rejecting senders you know are safe but inherently look suspicious.
Generally our classifiers will not block your legitimate emails.

**X-SpamExperts-Class: line says "ham" or "unsure"**

SpamExperts combines many technologies to provide you optimal protection
from "**false positives**\ ", i.e. legitimate email, marked as spam.
Since we never want a legitimate email to be blocked, if you've received
a spam message classified as "**ham**\ " or "**unsure**\ ", our system
was not confident enough to block the message, and marked it as such,
giving you the opportunity to release and train the filters. This can
occur if the spam message appears to be from a legitimate source.

Policy concerning Forwarding-domains: if you have multiple domains that
act as email forwarders for the domain you want protected by our spam
filter, we will **NOT** block the spam messages since they originate
from a forwarding server. You will need to use our MX records for such
domains, and you are more than welcome to make use of our free domain
aliasing functionality to protect your forwarding domains. To check
which email address the message was originally directed to, please
inspect the "**Received:**\ " headers. These will specify what address
the message was delivered to.

**Check whether you have “catch all” enabled**

Spammers love to randomly generate recipients such as
ac3ijj@example.com, to try and deliver spam to your server. If your mail
server accepts all connections for any recipient, the chance of spam
getting through is significantly higher. We highly recommend you
**disable** such “\ **catch- all**\ ”, and instead create mailboxes
and/or forwarders for email addresses that do exist.

If you cannot disable the “\ **catch-all**\ ” behavior on your
destination server, you can use the "**Local Recipients**\ " feature to
specify which recipients are valid in our Control Panel.

You can test whether you have "**catch-all**\ " enabled by executing the
(check) "**Protection status**\ " function in the Control Panel
overview, from the drop down menu beside each domain:

|image0|\ \*\*

Still receiving spam?\*\*

It is also possible that our system simply did not detect the spam
message correctly. If this occurs, please `report the message to our
systems <https://my.spamexperts.com/kb/77/Report-Spam.html>`__ as spam,
so we can further train and improve our filtering technologies. All
reported messages are automatically processed centrally.

If you still receive large amounts of spam, even after using our
filters, and having checked all the steps mentioned above, please place
a copy of the spam messages in the "**Inbox**\ " folder of the **IMAP
quarantine account**, and send an email to support@spamexperts.com, with
the domain name used to report the messages. Our support staff can then
analyze the spam, and make adjustments to avoid it from getting through
in the future. This is why it's important to use the IMAP quarantine
system to report spam messages, to ensure no information is lost for
analysis. Alternatively you can email us a *.zip* file with all spam
messages in *.eml or .msg* formats for analysis. Please contact us for
the correct reporting address.

Finally, please make sure that the messages you report as spam are
indeed spam. We do not consider messages from senders that you have
subscribed to in the past, as spam, since they offer an unsubscribe
option. You should unsubscribe from such mailings instead, if they are
no longer desired. For more information check out our `how do I
quarantine and train
emails <https://my.spamexperts.com/kb/80/Spam-Quarantine-weborIMAP.html>`__
article.

.. |image0| image:: /_static/images/whatdoIdowhenreceivingspam.png
