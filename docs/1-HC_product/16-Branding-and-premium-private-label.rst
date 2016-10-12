Branding & (premium) private label
==================================

SpamExperts offers Web Hosting companies the opportunity to brand the
email security solution with their private label.

Branding management (Hosted Cloud):
-----------------------------------

If you have purchased the **Private label** feature you are able to
brand several aspects of your account:

-  Set your own Spampanel webinterface logo/color scheme
-  Manage the protection report templates
-  Create your own Spampanel login URL
-  Choose your own custom MX records
-  Set the name of the classification tags included in the email header

Custom MX records
~~~~~~~~~~~~~~~~~

Custom MX records are not available for trial users on our Hosted Cloud

To create your own **MX-record hostnames**, you need to setup 4
NS-record hostnames in your DNS pointing to our nameservers:

-  mx1.example.com. NS dns1.spamrl.com.
-  mx1.example.com. NS dns2.spamrl.com.
-  mx1.example.com. NS dns3.spamrl.com.
-  mx1.example.com. NS dns4.spamrl.com.
-  mx2.example.com. NS dns1.spamrl.com.
-  mx2.example.com. NS dns2.spamrl.com.
-  mx2.example.com. NS dns3.spamrl.com.
-  mx2.example.com. NS dns4.spamrl.com.
-  mx3.example.com. NS dns1.spamrl.com.
-  mx3.example.com. NS dns2.spamrl.com.
-  mx3.example.com. NS dns3.spamrl.com.
-  mx3.example.com. NS dns4.spamrl.com.
-  mx4.example.com. NS dns1.spamrl.com.
-  mx4.example.com. NS dns2.spamrl.com.
-  mx4.example.com. NS dns3.spamrl.com.
-  mx4.example.com. NS dns4.spamrl.com.

Before adding the MX records to your domain, please open a support
ticket so that your hostnames will get added to the **spamrl.com**
nameservers, as they will only function once we create them at our end.
Only 1 set of custom MX- record hostnames is allowed per client. The
domain that you want to apply filtering to then can use your personal MX
records as follows:

-  yourdomain.ext. MX 10 mx1.example.com.
-  yourdomain.ext. MX 20 mx2.example.com.
-  yourdomain.ext. MX 30 mx3.example.com.
-  yourdomain.ext. MX 40 mx4.example.com.

Some DNS control panels do not require you to use a trailing dot (.)
after the hostname. Please check with your DNS provider if this is the
case for you.

Custom Control Panel login URL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

On the branding page you can configure or enter your own hostname which
will be associated with your branding. After defining your **hostname**,
simply create a **CNAME** in your DNS pointing to
**login.antispamcloud.com** to ensure your clients receive the correct
login page.

-  login.yourdomain.ext. CNAME login.antispamcloud.com.

Branding Management (Local Cloud):
----------------------------------

Private label versus premium private label
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the Control Panel we offer two branding options, **Private Label**
and **Premium Private Label **, as follows:The **Private Label**
branding allows you to replace the SpamExperts branding with your own
cluster-wide brand. The **Premium Private Label** option allows you to
have multiple brands within a cluster, each admin can define his/her own
branding, as detailed above for **Hosted Cloud**. You are able to brand
several aspects of your Local Cloud:

-  Set your own Control Panel webinterface logo/color scheme
-  Manage the protection report templates
-  Create your own Spampanel login URL
-  Set the name of the classification tags included in the email header

Custom MX records
~~~~~~~~~~~~~~~~~

If you wish your clients to use their own MX records, they can simply
define their own A-records in DNS pointing to the filtering servers. MX
records are technically not allowed to be a CNAME, therefore they must
use A records.

In case you wish to be flexible with your IP addresses, it's also
possible to define NS records similar to what we did for our Hosted
Cloud (see the `Hosted Cloud MX
record <https://my.spamexperts.com/kb/109/Hosted-Cloud-MX-%20records.html>`__
documentation).

Custom Spampanel login URL
~~~~~~~~~~~~~~~~~~~~~~~~~~

If your admins like to use their own login URL, they can simply create a
**CNAME** in their DNS pointing to your master server. If you have the
**Premium Private Label** feature, they are also allowed to define their
own branding for the URL.
