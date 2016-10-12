Spam Quarantine (web/IMAP)
==========================

| The quarantine system can be accessed directly via IMAP or the
  SpamExperts Control Panel.
| Messages that are rejected with a 5xx SMTP rejection code at SMTP
  level are quarantined.  So legitimate sending servers will have
  informed the sender about the rejection.  Enabling the quarantine is
  optional. If you do not want to use the SpamExperts quarantine , it's
  possible to configure the systems to deliver all messages to the
  destinaion mail-server and use "Subject Notation" instead. This will
  tag messages on the subject , so that filters can be used directly on
  the destination mail-server.

 By default, SpamExperts stores the quarantined spam for 14 days,
however on a Local Cloud setup customers may overrule this value. Spam
messages that were temporarily rejected at SMTP level are not listed in
the quarantine, and will be automatically retried by legitimate sending
servers

Webinterface access
~~~~~~~~~~~~~~~~~~~

From the Control Panel you can either **Release**,\*\* Release &
Train\ **,** Blacklist & Remove\ **, **\ Release and Whitelist\ **, or
**\ Remove\*\* messages blocked as spam. In case an email has been
incorrectly blocked, clicking '**Release & Train**" will result in
delivery of the false positive to the original recipient. It will also
trigger a report about the wrong classification to our systems to
further improve the filtering.

.. figure:: /_static/images/quarantine1.png
   :alt: 

It's also possible to do all the above actions directly from the log
search page. Using the drop down menu next to the blocked message will
give you the available options.

.. figure:: /_static/images/quarantine2.png
   :alt: 

IMAP access
~~~~~~~~~~~

| The quarantine system is powered by an IMAP backend. The backend is
  accessible as super-administrator (using the special "global"
  account), domain (using the domainname), and recipient (using the
  email address). Customers using the SpamExperts hosted cloud can
  connect to \ **quarantine.antispamcloud.com**.
| Users on a SpamExperts Local Cloud can use the hostname of the primary
  server in that cluster (or a CNAME associated with it). We have
  instructions available for
  `Thunderbird <https://my.spamexperts.com/kb/28/Configure-Thunderbird-to-access-the-IMAP-quarantine.html>`__
  and
  `Outlook <https://my.spamexperts.com/kb/88/Configure-Outlook-to-access-the-IMAP-quarantine.html>`__.
  Using IMAP you can also apply mass actions to specific emails by
  dragging to specific folders.

For Local Cloud users there  is also a special "global" account which
can be used to retrieve IMAP access to all quarantined messages. This is
for super administrators only.

IMAP folders
~~~~~~~~~~~~

There are several special folders present in the IMAP account:

-  Caught: All incoming messages which have been quarantined can be
   found in this folder. It's not necessary to report these emails as
   Spam again, as they have already been classified as such. These
   emails will automatically expire.
-  Caught (Outgoing): All outgoing messages which have been quarantined
   can be found in this folder (optional). It's not necessary to report
   these emails as Spam again, as they have already been classified as
   such. These emails will automatically expire.
-  Training Requested: This is only relevant if a special option as been
   activated via the Software API to store a copy of unsure
   classifications in this folder. These messages have been delivered,
   but can be manually dragged/dropped to "Not Spam" or "Spam" to
   further fine-tune the systems. Please contact support@spamexperts.com
   if you would like more information on this one.
-  Release & Train: This is a write-only folder (which cannot be
   accessed by the email client). Emails drag/dropped from "Caught" to
   this folder will be delivered to the recipient and reported as a
   classification mistake to our central systems
-  Release: This is a write-only folder (which cannot be accessed by the
   email client). Emails drag/dropped from "Caught" to this folder will
   be delivered to the recipient only.
-  Not Spam: This is a write-only folder (which cannot be accessed by
   the email client). Emails drag/dropped from "Caught" or "Training
   Requested" to this folder will be reported as a classification
   mistake to our central systems (it will not be delivered to the
   recipient)
-  Spam: This is a write-only folder (which cannot be accessed by the
   email client). Emails drag/dropped to this folder will be reported as
   a Spam to our central systems (it will not be delivered to the
   recipient). This is useful to report spam which was not blocked
   correctly directly from the email client.
