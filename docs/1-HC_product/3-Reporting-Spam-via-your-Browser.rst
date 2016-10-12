.. _1-Reporting-Spam-via-your-Browser:

Reporting Spam via your Browser
===============================

When using a browser based email client, it's sometimes needed to be
able to report spam to our systems. This can now be done by using a
simple script that can push the message to our systems if you can view
the whole source of the email via your browser.

Prerequisites:

-  Firefox or Chrome (Windows/Linux/OSX)
-  Addon -
   `Greasemonkey <https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/>`__

Please note this currently will only run on "**Google Mail** (Google
Apps)", "**Horde**\ ", "**RoundCube**\ " & "**OWA**\ "  (Exchange
Online).  If you have other web browsing mail-clients that you would
like to include, please contact support@spamexperts.com for more
information.

Installation steps:

1. Install and enable addon from above
2. Download the script
   `here <http://download.seinternal.com/mua/report_spam_browser.js>`__
   (this should automatically install the script.- If it does not please
   open the file, and select all, and copy to your clipboard.)
3. If automatic installation did not work, please click *"Greasemonkey >
   New User Script > Use script from Clipboard*".
4. Once the script is installed, please verify that the
   "*Greasemonkey*\ " icon is enabled.

Reporting Steps:

1. Login to your mail client via your preferred browser
2. Select the message you wish to report
3. View source of the message
4. A "**Report Spam**\ " button should appear on the page on the right.
   (If using OWA - this will show in the pop-up box when viewing the
   source)
5. Click "**Report Spam**\ "
6. If successful a pop-up box will appear confirming it was sent.
7. Close window

This script will not move, delete or change this message in anyway. This
will simply send those headers and body content to our training servers.
