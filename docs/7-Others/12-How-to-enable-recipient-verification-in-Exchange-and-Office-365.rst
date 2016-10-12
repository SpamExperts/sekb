How to enable recipient verification in Exchange and Office 365
===============================================================

The Microsoft Exchange mail server does not reject by default emails to
non- existent users. When any mail server has recipient filtering
enabled, it will automatically reject emails to non-existent users and
reply to the sending server that the user isn't created, being the
sending server's job to send a Non-Delivery Report to the email sender.

The mechanism behind Exchange first accepts the email and then decides
if it will reject or accept the email, thus generating its own
Non-Delivery Report and try to send it back to the sender.

This can consume resources to generate the local NDR and send it back to
the original sender, which will then be flooded with Non-Delivery
Reports.

To avoid such situations, we recommend to enable the recipient
verification on your Exchange email server, as follows:

Exchange 2007
=============

The Recipient Filtering can be enabled or disabled in Microsoft Exchange
2007 email server via the Management Console or the Management Shell, as
follows:

Exchange Management Console
---------------------------

In the **Exchange Management Console**, go to **Edge Transport**.

Then in the work pane, select the **Anti-Spam tab**, and then choose
**Recipient Filtering**.

Now just **enable**\ the Recipient Filtering feature.

Exchange Management Shell
-------------------------

First open the Management Shell and issue the following command to
**enable the Recipient Filtering**:

::


        Set-RecipientFilterConfig -Enabled $true

To disable recipient filtering, issue the following command in the
Management Shell:

::


        Set-RecipientFilterConfig -Enabled $false

For more information, check this article from the `Exchange 2007
knowledgebase <https://technet.microsoft.com/en-us/library/bb125187(v=exchg.80).aspx>`__.

Exchange 2010
=============

The Recipient Filtering can be enabled or disabled in Microsoft Exchange
2010 email server via the Management Console or the Management Shell, as
follows:

Exchange Management Console
---------------------------

First open the **Management Console** on the **Edge Transport server**.

Click on **Edge Transport** from the console tree, and select the
**Anti-Spam tab** from the work pane. Now go to **Sender Filtering** and
click **enable**.

Be advised: You need the necessary permissions to access the anti-spam
features from Exchange 2010.

Exchange Management Shell
-------------------------

First open the Management Shell and issue the following command to
**enable the Recipient Filtering**:

::


        Set-SenderFilterConfig -Enabled $true

To disable recipient filtering, issue the following command in the
Management Shell:

::


        Set-SenderFilterConfig -Enabled $false

Be advised: You need the necessary permissions to access the anti-spam
features from Exchange 2010.

For more information, check this article from the `Exchange 2010
knowledgebase <https://technet.microsoft.com/en-us/library/bb124087(v=exchg.141).aspx>`__.

Please ensure that you are not using the default standalone installation
with no Edge Transport server, because the Anti-Spam function is not
installed. To enable it, see more details
`here <https://technet.microsoft.com/en-us/library/bb201691(v=exchg.141).aspx>`__.

Exchange 2013
=============

In Exchange 2013 Microsoft has changed the way it handles recipient
callouts, by doing this check post DATA. This means even if the
recipient validation is enabled on the mail server, any `recipient
callout <https://my.spamexperts.com/kb/26/Recipient-Callouts.html>`__
responds with a **"250 OK"** response for invalid recipients, therefore
leaving us with no valid way of checking if the recipient is valid or
not.

Fortunately there's a workaround for this issue. On a default
installation of Exchange 2013, a secondary port is open (**port 2525**).
If you enable “Anonymous Users” on the default hub transport then it is
then possible to use this secondary port (2525) for both deliveries and
correctly be able to verify recipients with a standard recipient
callout.“

**Please note that this setup has only been verified in a closed testing
environment, and may require testing before deploying on any live setup.
**

You will also as like other versions still need to make sure that the
following has been done.

First check if the **Anti-Spam Agent** is installed on the server via
the shell:

::


        Get-TransportAgent

Then ensure the\*\* Recipient Filter Agent\*\* is installed and enabled,
if not use the following command:

::


        & $env:ExchangeInstallPath\Scripts\Install-AntiSpamAgents.ps1

Now check if it is **enabled**:

::


        & $env:ExchangeInstallPath\Scripts\Install-AntiSpamAgents.ps1

Enable the **AddressBook** needed for all domains to check for
recipients:

::


        Get-AcceptedDomain | Format-List Name,AddressBookEnabled

If the **AddressBook is disabled**, use the following command:

::


        Set-AcceptedDomain example.com -AddressBookEnabled $true

\_\*Replace **example.com** with **your domain**\ \_

Now **restart** the **Exchange Transport service**.

To ensure the Recipient validation is enabled issue the following
command:

::


        Set-RecipientFilterConfig -RecipientValidationEnabled $true

And **restart** the transport service again.

Check if the Recipient Filtering actually works by opening a telnet
session on port 2525 of the mail server and issue the following:

::


        HELO example.com

::


        MAIL From:<test@example.com> 

::


        RCPT To:<nonexistent_user@example.com>

Now ensure SpamExperts uses port 2525 to verify recipients.

Office 365
==========

To enable **Recipient Verification** in Office 365 you need to have
**Exchange Online Protection** enabled on the server, as well as an
**Global Admin** or an **Exchange Company Administrator** account.

The **Directory Based Edge Blocking** (DBEB) feature from Office 365
enables users to reject messages for nonexistent recipients.

To configure and Enable DBEB, use the following steps:

Ensure the domain is set to **Internal Relay**, by going to **EAC** >
**Mail Flow** > **Accepted Domains** > **Select your domain** and click
**Edit** > check if the domain type is set to **Internal relay**, if not
change it to **Internal relay** and click **Save**.

Add your valid users to office 365 via **Directory synchronization**,
**remote Windows Powershell** or directly from the **Exchange Admin
Center** (EAC).

Now set your domain to **Authoritative**. Follow the same path as above,
**Mail Flow** > **Accepted Domains** > **select your domain** and set it
to **Authoritative**. After you click **Save**, please confirm that you
wish to enable "**Directory Based Edge Blocking**\ ".

Now you're all set!

For more information check this
`article <https://technet.microsoft.com/en-us/library/dn600322%28v=exchg.150%29.aspx>`__
from Microsoft.
