.. _5-Generate-DKIM-certificate:

Generate DKIM certificate
=========================

Why should I use DKIM?
----------------------

There are several advantages to using DKIM to sign your outgoing emails:

-  The recipient is able to verify that the message did come from the
   specified sender;
-  The recipient is able to verify that the message content (and
   important headers, like the subject) has not been altered;
-  It lowers the chance of the email being identified as spam, although
   this is not the primary reason to sign.

If a spammer is trying to abuse your domain or email address, using DKIM
the changes of spam getting through will decrease. Many email servers
(e.g. Yahoo!, Gmail, SpamExperts) will check for a valid DKIM signature
on incoming email.

How does it work?
-----------------

DKIM adds a special DKIM Signature to the email headers. This signature
contains a hashed value of the content (both important headers and the
body). When a server that is checking for DKIM receives an email, it
will do the following:

-  Retrieve the public key from the DNS of the sending domain.
-  Use the key to decrypt the signature.
-  Verifies the content.

The exact actions a mail server takes when it discovers an invalid
signature depend on the configuration of that server.

How can I set it up via the interface?
--------------------------------------

Go to the domain in the interface that's being used for outgoing
authentication and click on generate DKIM

| 1: Choose a DKIM selector, (this can be anything), in this case we
  will select 'test' as the selector.
| 2: Choose the Length (generally advise to take the 2048 one - if your
  DNS can accept that)
| 3: Generate key

Once the key has been generated, then you will need to add this to the
DNS to the sub domain:

For example in:

::


         test._domainkey.example.com

Then save this in your DNS as a TXT record.

Then in the outgoing user settings for the outgoing users you need to
add the word test in the DKIM selector box. (test is the selector from
above)

Then any domain sending with that outgoing authentication that has this
selector should sign with this (assuming they dont have their own DKIM).

How can I set it up via command line?
-------------------------------------

Setting up DKIM involves a few steps.

Requirements:

-  Python
-  OpenSSL
-  Access to your DNS
-  `SpamExperts Outgoing <http://outgoing.spamexperts.com/>`__ enabled
   for your cluster.

Create keys
-----------

DKIM uses a pair of public and private keys - the private key is known
only to you (and SpamExperts, since we are signing the mail on your
behalf) and is used to create the signature. The public key is available
to anyone, and can be used to verify that the correct private key was
used.

**Generate a private key**

::


         openssl genrsa -out domainname.com.key 2048
        

**Generate a public key**

::


          openssl rsa -in domainname.com.key -out rsa.public -pubout -outform PEM
        

Create a DNS record
-------------------

In order for the receiving mail server to obtain your public key, you
must create a DNS record for the specified domain.

::


         dkim._validation         TXT     "k=rsa; p=[_public key in one line_];"
        

The name "validation" can be anything (this is called the "selector",
and you can use it to have different keys with the same domain). Make
sure you use the same name in the next steps.

Configure the keys
------------------

In order to use the keys for all outgoing mails for a certain user,
there are a few steps to take to implement this in to your SpamExperts
Filtering Cluster.

Create a file "makepriv.py" and enter the following content:

::


          s = """-----BEGIN RSA PRIVATE KEY-----
         YOUR 
         KEY
         HERE
         -----END RSA PRIVATE KEY-----"""
         import urllib
         print urllib.quote(s)
        

Replace the YOUR KEY HERE part with the contents of your private key.
Execute this:

::


         python makepriv.py
        

It will return a your key in a single line.

Input the name of the selector into the api. To do so, you should
replace a few values in the URL:

`https://SERVERNAME/cgi-bin/api?call=api\_set\_dkim\_certificate&domain=DOMAINNAME&certificate=VALUE&selector=SELECTOR <https://servername/cgi-bin/api?call=api_set_dkim_certificate&domain=DOMAINNAME&certificate=VALUE&selector=SELECTOR>`__

-  Replace **SERVERNAME** with the hostname of your primary server or
   the used CNAME
-  Replace **DOMAINNAME** with the domainname you want to be using DKIM
-  Replace **VALUE** with the value the Python script earlier produced.
-  Replace **SELECTOR** with the desired selector you've chosen earlier.

To finish things up, the desired outgoing user should be DKIM enabled:

`https://SERVERNAME/cgi-bin/api?call=api\_set\_dkim\_selector&domain=DOMAINNAME&selector=SELECTOR&username=USERNAME <https://servername/cgi-bin/api?call=api_set_dkim_selector&domain=DOMAINNAME&selector=SELECTOR&username=USERNAME>`__

-  Replace **SERVERNAME** with the hostname of your primary server or
   the used CNAME
-  Replace **DOMAINNAME** with the domainname you want to be using DKIM
-  Replace **SELECTOR** with the desired selector you've chosen earlier.
-  Replace **USERNAME** with the username of the outgoing user.

Your outgoing emails which are being sent through the "Outgoing Service"
will now be signed with your DKIM key.

Further reading
---------------

Want to learn more about DKIM? Here are some sites you could check out.

-  `RFC4870 <http://tools.ietf.org/html/rfc4870>`__
-  `RFC4871 <http://tools.ietf.org/html/rfc4871>`__
-  `RFC5322 <http://tools.ietf.org/html/rfc5322>`__
-  `Wikipedia <http://en.wikipedia.org/wiki/DomainKeys_Identified_Mail>`__
