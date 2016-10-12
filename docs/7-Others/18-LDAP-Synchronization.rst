LDAP Synchronization
====================

LDAP Authentication
~~~~~~~~~~~~~~~~~~~

SpamExperts provides full integration with LDAP in order to allow all
your email users to log in to the SpamExperts Control Panel with their
existing email credentials (This is currently only available to AD
(Microsoft), and not OpenLDAP). This means that your users will no
longer have two sets of credentials, but only one.

Even though your users will employ LDAP for authentication, the 2FA will
still be functional but password changes and recovery will no longer be
covered by us since the credentials are managed on your LDAP server.
Usually there’s no usability in adding email users or just removing them
as they will be added again when LDAP is activated. The only reason to
add one or more email users is to prevent them from logging in the
SpamExperts control interface by setting its status as inactive.

The LDAP support is only available for email user level and access to
Super- Admin, Admin, Sub-Admin or Domain user levels is not available
via LDAP. Because of this, the username that is used needs to be an
email address Eg test@example.com . So the LDAP server needs to
authenticates an email address for the LDAP integration with our control
panel to work as expected and not a username of the form Eg test.

How to enable LDAP authentication
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Overview > Select your domain > Webinterface Users > Manage Email
Users**

On the **Manage Users** page you will find the LDAP authentication tab
where you will need to add your LDAP domain controller (server hostname)
alongside with the port it needs to connect on. For example if your LDAP
domain controller is located ldap.example.com and connects on port 389
(unsecure) or port 636 (secure - over TLS), the domain controller you
will have to add will be: “ldap.example.com:636”.

Click **Save** to activate the LDAP service. Now you’re all set.

Once  LDAP has been set up, when the email user will attempt to connect
for the first time, we will automatically check its credentials via
LDAP.

If  the server hostname and port are incorrect you will receive an error
when trying to log in. Please pay close attention when adding the server
hostname and port.

How to disable LDAP
^^^^^^^^^^^^^^^^^^^

To disable LDAP authentication just delete the server hostname and port
from the Manage Email Users page and click Save.

SpamExperts Also provides an easy to use
`single-sign-on <https://my.spamexperts.com/kb/440/Integrating-SpamExperts-into-your-own-software.html>`__
system which can be integrated in most environments to ensure your
clients do not need to login at different control panels. The "one click
login" system can for example be integrated with your LDAP user base to
grant your users direct access to the SpamExperts control panel from
your existing customer environment. If you're not using a control panel
that we already provide free integration for, we're `happy to
assist <mailto:support@spamexperts.com>`__ in this process.

Single-sign-on alternatives
~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  If you have the LDAP usernames/passwords it's easy to synchronize the
   logins with our API, or to simply provide the details to the API
   whenever a new mailbox is provisioned. 
-  We have a feature to automatically enable our reporting and send a
   welcome email with the required login details to new recipients. When
   enabling this option it will automatically add all the filtered
   domain users to the '`Periodic user
   report <https://my.spamexperts.com/kb/111/Periodic-user-based-protection-Reports.html>`__\ '
   page, and then once added, send them a daily or weekly digest on the
   spam received. It also will send the end user a welcome email once
   the first spam message has been seen to let them know their personal
   quarantine has been activated, and if they would like to log in to
   see this, they can do it using the login link in the email. Once they
   have logged in for the first time, the users will be added to the
   'manage email users' list.

LDAP user verification
~~~~~~~~~~~~~~~~~~~~~~

To prevent the requirement for data duplication, SpamExperts uses
advanced SMTP-based `recipient verification
calls <https://my.spamexperts.com/kb/26/Recipient-Callouts.html>`__.
Your SMTP server will handle the local LDAP lookup, to ensure our system
will always properly handle the email for your mailboxes. We include
advanced dictionary attack handling to protect your SMTP and LDAP server
from being flooded with queries. This system is fully automatic, no
credentials are required on our side.
