Microsoft Exchange internal email archiving
===========================================

When using SpamExperts for both your incoming and outgoing email
filtering (using the smarthost setup), all external SMTP communication
will automatically be archived as part of the domain for which archiving
is enabled. However Microsoft Exchange does not relay internal
communication via the outgoing smarthost, therefore internal
communication will not be archived by default.

Archiving internal communication is simple however, and can be
accomplished with the Exchange journaling system. The journaling system
allows Exchange to automatically send a copy of all internal
communication to an external email address. As long as you've setup the
external email address with SpamExperts for archiving, the SpamExperts
incoming filter will simply process the message and archives it. You
should configure the destination address to which the journaling reports
are sent as a whitelisted blackholed recipient. This means for the
messages received, no filtering or delivery to an external server takes
place. SpamExperts support can help you accomplish this, or you can do
so directly via the Software API on our Local Cloud product.

Your Microsoft Exchange administrator will be able to activate
journaling for you and ensure a copy of each email is automatically sent
to the archived blackholed recipient.
