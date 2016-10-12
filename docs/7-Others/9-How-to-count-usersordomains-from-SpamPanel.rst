How to count users/domains from SpamPanel
=========================================

Often it's needed to see a count of both inbound and outbound mailboxes
and / or domains. This can be done via the SpamExperts interface.

Incoming
~~~~~~~~

| **Domain count**
| To check the amount of domains loaded to your license, you can easily
  use the web interface::

-  Log into SpamPanel
-  Click *Overview
   *

-  Fairly on top of the page it says "Total items: xxx", with xxx being
   the total number of domains on the platform. 

| **Valid recipient (mailbox) count**
| To check the amount of mailboxes/ valid recipients for a domain for
  which we processed email in the last 7 days you can either use the
  SpamPanel API or the web interface.
| The SpamPanel API command you need is the following:

::


        https://api.antispamcloud.com/api/domain/getvalidrecipientcount/domain/example.com/

To use the above call, you will need a valid SpamPanel API username and
password. Please replace example.com with the inbound domain you wish to
check.

To use the web interface:

-  Log into SpamPanel
-  Click *Overview
   *

-  Using the drop down menu on the left of the domain you are looking
   for choose "*Valid Recipient Count*\ "

Outgoing
~~~~~~~~

| **Sender "From:" count**
| To be able to count the number of "From:" domains that your outgoing
  user is sending from, you will need to use the outgoing log search and
  any speadsheet based program. (For example Excel).

-  Log into *SpamPanel*
-  Click "*Overview"*
-  Click on the outgoing authenticating domain that is being used
-  Click on "*Log Search*\ " in the Outgoing section.
-  Select the date frame you are looking to check
-  Select "*Accepted"* emails only
-  Use the "*Customize*\ " option and select "*From*\ " as the only
   column to show
-  Select "*search"*
-  When the results are returned, export these reports to a file.
-  Open the file in any spreadsheet based program
-  Remove the Duplicate lines

This will then show you for how many unique senders we have accepted
email for during the set time frame. The logs search can also be used to
show other colums, for example, if you wish to show the "Envelope-from"
instead of the from. Note: For the license match, "from domains" related
to email forwarders do not have to be included for the count. You'll
need to ensure your license matches the total number of domains you're
providing filtering for on your environment (a forwarding domain would
count as 1).
