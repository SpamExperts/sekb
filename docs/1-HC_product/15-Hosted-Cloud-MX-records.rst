.. _1-Hosted-Cloud-MX-records:

Hosted Cloud MX records
=======================

To route the incoming email for your domain through the SpamExperts
filtering cloud you have to change your **MX records**.

Prior to changing the MX records, it is best to check your TTL. We
recommend a maximum value of “\ **3600**\ ” in order to propagate any
DNS changes faster. Higher TTLs can lead to spam not being filtered by
our nodes yet.

Please edit the DNS settings for your domain:

**1. Add the following MX records:**

-  **mx.spamexperts.com.** (priority 10)
-  **fallbackmx.spamexperts.eu.** (priority 20)
-  **lastmx.spamexperts.net.** (priority 30)

**2. Remove the original MX records**

Some DNS control panels require you to use a trailing dot (.) after the
hostname. Please check with your DNS provider if this is the case for
you.

Removal of old MX records is required to make sure all emails are
filtered through the SpamExperts cloud, as spammers actively try
different MX records (such as with the highest numbered priority) to
bypass spam filters.

DNS changes may take some time before they are picked up by the DNS
resolvers world-wide, so email may continue to deliver directly to the
original MX records without filtering for 24 hours.

You can check using the SpamExperts log search or within the :ref:`email headers  <4-View-email-headers>` if
the message has passed through the SpamExperts filtering nodes.
