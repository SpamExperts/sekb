.. _3-SmarterTools-SmarterMail-integration:

SmarterTools SmarterMail integration
====================================

**SmarterMail 8.X  setup.**

The SmarterTools Email server can be used in coordination with
SpamExperts.

**INCOMING FILTER**

Simply add your domain in the SpamExperts solution, and point the route
to the SmarterMail server. After that you can change your MX records to
point to the SpamExperts MX records. SpamExperts will filter all your
incoming email, and delivers the not-spam messages to your SmarterMail
environment.

**OUTGOING FILTER**

To configure your outgoing filter through SmarterMail, use the following
steps:

Click the '**Settings**\ ' tab on the left hand side of the panel.

.. figure:: /_static/images/smarter_mail1.png
   :alt: 

Then navigate to the '**Routing**\ ' folder and click the '**Outgoing
Gateways**\ ' tab.

.. figure:: /_static/images/smarter_mail2.png
   :alt: 

A new window will open to the right of the screen. Click the '**New**\ '
button located at the top.

You should be presented with the image below:

.. figure:: /_static/images/smarter_mail3.png
   :alt: 

| Fill in your SpamExperts outgoing server details here, make sure you
  check both the "**Enabled**\ " and "**Enable authentication**\ "
  boxes.
| An example setup for the SpamExperts Hosted Cloud, would be:

| **Server address: ** smtp-trial.antispamcloud.com
| **Port:** 587
| **Username:** outgoing@example.com
| **Password:** xxxxxxx  (whatever password was used when creating your
  outgoing user in the SpamExperts interface)

Choose **TLS** as your encryption method.

Click "**Save**\ " when done.

Filtering on headers
~~~~~~~~~~~~~~~~~~~~

If you've disabled the quarantine system in SpamExperts, spam and
phishing that would normally be quarantined, will get delivered to the
SmarterMail environment. If you wish to filter based on the
classification, you can use the following header:

-  **X-Recommended-Action: reject**

To do this for SmarterMail, go to the **Domain level**. Click
**Settings**, then choose '**Content Filtering**\ ' from the '**Domain
Settings**\ ' tab.

.. figure:: /_static/images/smartdomainsetting.png
   :alt: 

Now click '**New**\ ' and put a check mark in the box '**Email
Header**\ ', then proceed by clicking '**Next**\ '.

.. figure:: /_static/images/chooseheadersmart.png
   :alt: 

In the '**Email Header**\ ' box, please add the following.
"**X-Recommended- Action: reject**\ " and click '**Next**\ '.

.. figure:: /_static/images/recectsmart.png
   :alt: 

Now place a checkmark next to the '**Move Message**\ ' box, then write
'**Spam**\ ' in the text box next to it.

.. figure:: /_static/images/rejectspamfolder.png
   :alt: 

Then click '**Save**\ ' and you're all done. Now all emails with this
header will be directed into your SmarterMail '**Spam**\ ' folder.
