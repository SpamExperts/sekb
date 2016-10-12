Exchange Journaling
===================

This page describes how to setup Journaling in Microsoft Exchange and
set-up processing of these message with SpamExperts. This pages
describes steps using Microsoft Exchange 2010.

To use the Microsoft Journaling option with SpamExperts, the domains you
are archiving for need to be already added to your cluster.

Steps to enable Journaling:
~~~~~~~~~~~~~~~~~~~~~~~~~~~

In Exchange 2010

Setup DNS lookup send connector:

-  Open **EMC**
-  **Organization Configuration**
-  **Hub Transport**
-  **Send Connectors**
-  Right click and select **New Send Connector**
-  Select "**Internet**\ " in the drop down
-  On the next page add new address space with **``*``** (representing
   all domains)
-  On the next page select "**Use domain name system (DNS) "MX" records
   to route mail automatically**\ "

Be Advised: Servers will most likely already have a send connector for
external emails, this should change according to local set-ups.

If the current server setup is too complicated instead of a catch-all
address space (``*``) the user can specify the exact domain and set the
cost as low as possible. This should prevent conflicts with other send
connectors.

Add new **External Mail Contact** for journaling address:

-  Open **EMC**
-  **Recipient Configuration**
-  **Mail contact**
-  Right click and select **New Mail Contact**
-  Select **New Contact**
-  Select "**Specify the Organizational unit**\ " and chose the
   "**/Users**\ " one
-  Edit "**External e-mail address**\ " and add your journaling email
   address, for example: \ ``journal@example.com``
-  Fill out the rest of the details form

Add **new Journal rule**:

-  Open **EMC**
-  **Organization Configuration**
-  **Hub Transport**
-  **Journal Rules**
-  Right click and select **New Journal Rule**
-  Select the mail contact added at step 1 at "**Send Journal reports to
   e-mail address**\ "
-  Select "**Internal**\ " Scope
-  Select "**Journal messages for recipient**\ " and select the
   **Dynamic Distribution Group** for this domain

Configure Journaling from the SpamExperts interface:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Log into the SpamExperts Control Panel as **Super-Admin**
-  **Overview**
-  Select your domain, for example: \ ``example.com``
-  **Archive > Settings**
-  Enable Journaling, if its current state is disabled
-  Add the journaling recipient

Be Advised: When you set the Journaling recipient, this will
automatically whitelist the recipient and blackhole it.
