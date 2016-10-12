.. _1-Periodic-based-Protection-Reports:

Periodic based Protection Reports
=================================

The Periodic Protection Reports enable you to automatically receive
User, Domain and On-demand Domain reports via email.

To access reports go to: **Overview > Select Domain;**

From the **Domain Dashboard** select your report type under the
**"Protection Report"** section.

Report Output
-------------

HTML Report
~~~~~~~~~~~

In the HTML report you can find a summary of the spam messages our email
security solution caught while filtering the email traffic.

The report allows you to release any message directly without having to
log in to the interface or IMAP.

PDF Report
~~~~~~~~~~

The PDF report outlines a summary of spam and malicious attachments
caught by the filtering service and it includes information about the
total volume of mail processed for a specific user.

The report also includes a detailed table ,used for auditing purposes,
of messages that were rejected but not quarantined. Likewise, a table
for messages that were quarantined, with links to release each message
directly, is included.

Periodic User Reports
---------------------

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/periodic%20user%20report.jpg
   :alt: periodic user report.jpg

   periodic user report.jpg

Periodic User Report

With this option you can enable periodic protection reports based on
users.

Users can be added individually or via the the .csv upload function for
multiple users.

Auto-Enable Reports
~~~~~~~~~~~~~~~~~~~

In order to automatically add new users not known to our systems, you
can use the "Automatically activate for all recipient" feature. This
way, when SpamExperts' blocks a spam messages to your user, the
recipient will be automatically added to the Periodic User Reports.

The moment users are added they will receive a "welcome" email, that
enables their personal quarantine.Newly added users will receive the
daily or weekly user reports with the full list of quarantined messages.

The welcome email will contain a login link, where recipients can
sign-in and set a password for their account. This gives them the option
to log directly into the interface (or via IMAP) and to access their own
log search and manage quarantined messages.

Please note: If your domain has
"`Catch-All <https://my.spamexperts.com/kb/44/Bounce-spam-protection-DSNsorNDRs.html#heading_toc_j_1>`__\ "
enabled, then this option will not be available to be enabled from the
interface, as this will cause many entries for non-existing users. If
Catch-all is disabled on your destination mailserver, but our system
detects it is still enabled, please see our article here - `Whitelist
Delivery Servers
section <https://my.spamexperts.com/kb/341/Ensure-proper-delivery-to-my-destination-server.html>`__

If you are unable to disable the "**Catch-All**\ " configuration on your
destination mail server for any reason, it is still be possible to
enable the "**auto-enable**\ " feature.

To use the "auto-enable" you either need to use the "**Add Local
Recipients**\ " feature or activate the "**Disable Catch All Check**\ "
feature.

The "**Local Recipients**\ " feature is located in the Control Panel
under: **Domain Dashboard > Incoming > Local Recipients**.

This feature allows you to add specific individual users who will act as
local recipients. This means that any genuine email addresses of the
associated domain that are not present in the "Local Recipients" list
won't be able to receive any incoming emails.

We advise customers who use this option to constantly update their list
so that no legitimate recipients get their incoming emails rejected.

The second way customers can bypass the server-side enabled "catch-all"
is by activating the "**Disable Catch All Check**\ " feature from
**Domain Dashboard > Incoming > Domain Settings > Advanced Settings**.

Be advised that this feature is only available for users with
Super-Admin privileges.

Periodic Domain Reports
~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/periodic%20domain%20report.jpg
   :alt: periodic domain report

   periodic domain report

Domain User Report

The Periodic domain report allows you to configure one address to
receive a daily or weekly PDF or HTML report for the entire domain.

On-Demand Domain Report
~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/on-demand%20domain%20report.jpg
   :alt: on-demand report

   on-demand report

On-demand Domain Report

The On-Demand Domain report enables you to generate a protection report
for a specific date range and send it immediately to a certain email
address.
