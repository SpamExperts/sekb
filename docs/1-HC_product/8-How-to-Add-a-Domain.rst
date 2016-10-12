.. _1-How-to-Add-a-Domain:

How to Add a Domain
===================

After you are successfully logged in, you will notice the Control Panel
Dashboard and several tables with buttons for all available features.

To add a domain, go to “\ **Domains**\ ” > “\ **Add Domain**\ ”. You
will be shortly redirected to a new page where you type in your domain
name.

After verifying that the typed domain name is correct make sure that the
destination server route is valid, as shown below.

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/add%20domain.jpg
   :alt: 

If you do not have a specific destination server route to add from the
start, the Control panel will automatically fill in a suggested
destination route for you, with a default destination port 25.

Hosted Cloud
------------

After setting the destination route, you need to modify your **MX
Records** in your domain **DNS Settings**, in order to point to the
SpamExperts routes. See our article on changing your :ref:`MX Records  <1-Hosted-Cloud-MX-records>`.

Local Cloud
-----------

Local Cloud users must first define their **MX Record hostnames** and
then update their domains to point to the Local Cloud solution. For more
information see Local Cloud MX Records.
