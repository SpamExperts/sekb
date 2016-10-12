How to Proactively Block Dangerous Attachments
==============================================

With SpamExperts you can block a very large amount of malware, yet there
can sometimes be new Malware campaigns that are able to evade all
Antivirus and Anti-Spam filters. Due to this we would highly recommend
to enable the **"Block attachments that contain hidden executables"**
option by default for all your domains. On our Hosted Cloud this option
has been enabled already by default.

This is highly effective against so called 0-day malware. Once this is
enabled, messages that are sent with executables within a compressed
archive (.zip, .rar etc) are rejected and quarantined.

Be Advised: The **Block attachments that contain hidden executables**
option will only affect messages that contain an executable within a
compressed archive. The check is executed 3 layers deep into archives
for the following default list of file extensions:

::


        ('exe', 'bat', 'com', 'cmd', 'cpl', 'js','jse', 'msi', 'msp', 'mst', 'paf', 'wsh','wsf', 'vbs', 'vbe', 'psc1', ‘scr’, ‘lnk’)

**Block attachments that contain hidden executables** by default for all
------------------------------------------------------------------------

domains

To block dangerous by default for all your existing domains and future
domains that you will add, go to: **Super-Admin Dashboard** >
**Outgoing** > **Default Domain Settings**. From here on, click on the
**Attachment Restrictions** tab from the left hand side menu and tick
check the tickbox in front of **"**\ Block attachments that contain
hidden executables\ **"**.

Be advised that this will automatically enable the \ **Block attachments
that contain hidden executables** feature to all domains that have the
default value (and not a custom setting for this) and future added
domains. This can be overruled at domain level.

**Block attachments that contain hidden executables** at domain level
---------------------------------------------------------------------

To block dangerous attachments for a specific domain only, you will need
to, login as the domain user and go to: **Domain Dashboard** > **Email
Restrictions** > **Attachment Restrictions** and check the tickbox in
front of **"**\ Block attachments that contain hidden
executables\ **"**.

Block certain extensions
------------------------

It’s also possible to block messages based on their attachment. By
default SpamExperts already pre-fills a selected list of attachments
that are blocked. However you can of course add / remove any other
attachment file types that are deemed necessary.

Block Password Protected Archives
---------------------------------

Spammers often use a trick by sending password encrypted archives in the
hope to bypass some filters, and saying the “password” in the body of
the spam message. These messages can be blocked by enabling the “Block
Password Protected Attachments” feature. This can be enabled at both the
default level and domain level as mentioned above.

Further API calls (Local Cloud Only)
------------------------------------

It’s also possible to use some of our Filtering API calls to further add
more strictness to specific messages.

For example by using the **“api\_scanned\_linked\_extensions”** API call
you can set the size that should be downloaded. Usually we recommend a
maximum of 1.5MB as it should be more than enough and it’s unlikely that
malicious applications are larger than this.

::


        https://master.example.com/cgi-bin/api?call=api_set_message_link_size_limit&domain=example.com&size=1500000

Where **“master.example.com”** is the Master hostname, **“example.com”**
is your selected domain and “1500000” is 1.5 MB of maximum download
size.

Now you can use the **“api\_set\_scanned\_linked\_extensions”** call to
set the extension you want to scan. In the following example we added a
.zip:

::


        https://master.example.com/cgi-bin/api?call=api_set_scanned_linked_extensions&domain=example.com&extensions=bat:btm:cmd:com:cpl:dll:exe:lnk:msi:pif:prf:reg:scr:vbs:url:zip

Once this has been done, if a message arrives with a link in the body,
like “hxxp://example.com/badfile.zip”, the zip file will be downloaded
and scanned with the relevant engines. By default this option is
disabled.
