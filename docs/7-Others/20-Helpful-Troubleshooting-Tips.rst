.. _7-Helpful-Troubleshooting-Tips:

Helpful Troubleshooting Tips
============================

Troubleshooting Guidelines.
---------------------------

Sometimes, when clients request information on incorrectly blocked
messages, or spam messages that have passed the filters, there are a few
things that you can check first to resolve any issues:

Complaints about incoming email getting wrongly blocked:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Check the "Evidence" header in quarantine (this can be done by
   clicking on the raw tab of the message in the quarantine) to find out
   why it was blocked, more details can be found at:
   https://my.spamexperts.com/kb/136/Classifications.html
-  Ensure to release the blocked messages from quarantine (to get them
   delivered and reported as a classification mistake)
-  If messages continue to get wrongly blocked, open a support ticket
   with us providing the domain name so we can analyze the released
   messages for more details

Complaints about incoming spam getting through:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Ensure that the "Filter settings" of the domain are set to default
-  Ensure that the sender whitelist / recipient whitelist are empty
-  Verify that the spam was sent directly to a domain filtered by our
   system
-  If that's the case, have them report the message as spam to our
   systems: https://my.spamexperts.com/kb/77/Report-Spam.html
-  If spam continues to get through, open a support ticket with us
   providing a sample sender/recipient/date of a spam mail (ideally a
   few) so we can analyze the reported spam and logs

Complaints about outgoing email getting wrongly blocked:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Ensure that the "Filter settings" of the domain are set to default
   (to prevent high volumes of outbound forward spam negatively
   affecting their filtering)
-  Ensure that the sender whitelist / recipient whitelist are empty (to
   prevent high volumes of outbound forward spam negatively affecting
   their filtering)
-  Analyze the AFR report sent to abuse-address@example.com to view
   details why it was blocked, more details can be found at:
   https://my.spamexperts.com/kb/136/Classifications.html
-  

   -  Release any incorrectly blocked messages from quarantine (to get
      them delivered and reported as a classification mistake)

-  Open a support ticket with us providing the sender/recipient/date so
   we can release the message from quarantine to have it delivered and
   reported to our systems as a classification mistake

*\* This option is only available for our Local-Cloud users.  For Hosted
Cloud users, please open support ticket with us to investigate and
release the outbound blocked messages. *
