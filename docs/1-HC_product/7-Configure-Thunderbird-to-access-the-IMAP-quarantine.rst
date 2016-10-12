.. _1-Configure-Thunderbird-to-access-the-IMAP-quarantine:

Configure Thunderbird to access the IMAP quarantine
===================================================

If you would like to use our IMAP quarantine and training system
directly from your mail client, some configuration is needed beforehand.

Use the following settings to configure your IMAP account in your email
client, for example:Thunderbird or Outlook. In case you are using the
SpamExperts Hosted Cloud, you have to use
**"quarantine.antispamcloud.com"** as IMAP server, use as username
"example.com" (**replace with your own domain name**), and the password
you have set for **the domain user.**

Open your **account settings**. Depending on whether you use Windows or
Linux the menu item can be in a different location:

**Windows:** Menu Extra -> Account Settings

**Linux:** Menu Edit -> Preferences -> Account Settings |image0|

Click on **"Account Actions"** and pick the option **"Email Account"**.
|image1|

Enter your information. |image2|

Click on **"Stop"** while it is performing the auto-configuration.
|image3|

Change the **"POP3"** option to **"IMAP"** and click on **"Advanced
config"** |image4|

In the server settings window, change the following fields:

-  Change the **"Server Name"** to: **quarantine.antispamcloud.com**
-  Change your username to: Your domain name (without the www.)
-  Change the port to **993**
-  Optionally, if this isn't selected automatically, change
   **"Connection Security"** to **SSL/TLS** and set **"Authentication
   Method"** to **"Normal Password"**
-  Uncheck the **"Check for new messages on startup"** and **"Check for
   new messages every .. minutes"**

.. figure:: https://dev.spamexperts.com/sites/default/files/images/thunderbird3.png
   :alt: 

On the **"Synchronization & Storage"** tab, uncheck the **"Keep messages
for this account on this computer"**.

You're all set. Now you can use the IMAP quarantine & training straight
from your Thunderbird email client!

.. |image0| image:: https://dev.spamexperts.com/sites/default/files/images/thunderbird6.png
.. |image1| image:: https://dev.spamexperts.com/sites/default/files/images/thunderbird4.png
.. |image2| image:: https://dev.spamexperts.com/sites/default/files/images/thunderbird1.png
.. |image3| image:: https://dev.spamexperts.com/sites/default/files/images/thunderbird5.png
.. |image4| image:: https://dev.spamexperts.com/sites/default/files/images/thunderbird2.png
