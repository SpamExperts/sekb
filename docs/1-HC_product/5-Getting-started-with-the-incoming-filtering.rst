.. _1-Getting-started-with-the-incoming-filtering:

Getting started with the incoming filtering
===========================================

Getting started with Incoming Filtering on Hosted Cloud
=======================================================

The Incoming Filtering service on the SpamExperts Hosted Cloud can be
started by purchasing our product, or by beginning a free trial.

To log in to our Control Panel interface you need to go to the `control
panel <http://login.antispamcloud.com/>`__, available through your
user-account, or `my.spamexperts.com <https://my.spamexperts.com/>`__.
Go to **My Products** from the left panel, select your **Hosted Cloud**
product and click on **Login to Control Panel**.

After you are successfully logged in, you will notice the Control Panel
Dashboard and several tables with buttons for all available features.

To add a domain, please read the following knowledgebase article on :ref:`How to Add a Domain  <1-How-to-Add-a-Domain>`.

If you do not have a specific destination server route to add from the
start, the Control Panel will automatically fill in the destination
route for you, with a default destination port 25.

After setting the destination route, you need to add our **MX Records**
in your domain **DNS Settings**, in order to point to the SpamExperts
Hosted Cloud routes. See our article on changing your :ref:`MX Records  <1-Hosted-Cloud-MX-records>`.

Optionally, after completing this step, you can let the SpamExperts team
know you have switched the MX-records, so we can double-check everything
is set correctly.

Now you’re all done, within 24 hours you should be "Simply SpamFree"!

In case you are not 100% spam free within this timeframe, please read
the following :ref:`Knowledge-base article  <4-What-do-I-do-when-I-receive-Spam>`
or `contact <mailto:support@spamexperts.com>`__ our dedicated support
team.

Getting started with Incoming Filtering on Local Cloud
======================================================

Having received your access details from our System Administration team,
you are ready to start using the services on Local Cloud.

After you are successfully logged in, you will notice the SpamPanel
Dashboard and several tables with buttons for all available features.

To **add a domain**, please read the following knowledgebase article on
:ref:`How to Add a Domain  <1-How-to-Add-a-Domain>`.

Now you need to define your own domain **MX Records** and switch them to
point to the Local Cloud solution. See more information on :ref:`Local Cloud MX Records  <2-Local-Cloud-MX-Records>`.

For a full list of explanations for all control panel features at all
user levels, please see our SpamPanel Documentation manuals
`here <https://my.spamexperts.com/kb/44/SpamPanel-documentation>`__.

The system will automatically start learning/adjusting to the new
incoming email traffic. Read more on how this process works
:ref:`here  <4-Filtering-Technologies>`.

If you access the recipient whitelist located at the domain access
level, you’ll find two recipients already present. Conforming to **SMTP
RFC 5321**, the **"abuse@"** and **"postmaster@"** recipients are by
default whitelisted for all domains.

Spam sent to these two addresses will therefore, not be filtered. In
case you want these special accounts filtered by default, you can simply
delete the addresses from the **Recipient Whitelist** in the default
**Domain Settings** found at the **"Super-Admin"** access level.

We also recommend to set up a **Load-Balancer** or use **DNS
round-robin**, to help evenly spread the load over your cluster. More
information on this can be found
:ref:`here  <2-Load-balancer-configuration>`.
