.. _1-Domain-migration-within-Hosted-Cloud:

Domain migration within Hosted Cloud
====================================

Domain Migration
~~~~~~~~~~~~~~~~

There is sometimes a need to transfer domains from one "Administrator
account" to another on our Hosted Cloud.  This will need to be done from
the existing administrator.   This can be done by:

1. Log in to the SpamExperts interface
2. Click **"Overview"**
3. Select the domains that need to be transferred by appliying a check
   to the domains
4. Use the drop down menu and choose "**Transfer"**
5. Click **"Apply"**
6. Add the new administrator's email address in the box provided. (the
   new administrators email address will need to be known in advance)

The new administrator will then see these domains in his own
**"overview"** page where they will need to be accepted. Once this is
done, the domains will be transferred.  All logging, quarantine and
settings will stay in place, and any custom branding will be removed.

Alternatively, the current administrator can remove the domain from
their account, so that the new administrator can add the domain(s) to
their own account. Please do note though, if the domain is removed, then
its highly recommended to change the MX records back to the original
ones before SpamExperts, otherwise this will likely cause mail delivery
issues.

In case the other party does not respond, or refuses to transfer the
domain:

1. Please contact our support to reach out and request the transfer
2. In case the other party still does not transfer the domain, please
   ensure the MX records of the domain are not pointing to our services
   and add a TXT record to the domain with the value
   "yyyy-mm-dd-transfer-to-CLIENTID" (replace "yyyy-mm-dd" with the
   current date, and "CLIENTID" with your SpamExperts CLIENTID
3. Within 5 working days our support will force-transfer the domain to
   your account

Please note we do NOT allow to "reserve" any domains in our systems that
are (1) not using our services, or (2) not controlled by the
administrator. In case of a transfer dispute, the domain will always be
assigned to the current domain administrator.
