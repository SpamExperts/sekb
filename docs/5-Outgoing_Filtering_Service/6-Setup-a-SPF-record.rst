Setup a SPF record
==================

What is SPF
-----------

SPF (Sender Policy Framework)  is a way to restrict which mail servers
are allowed to send email for your domain name.

An example of an SPF would be : example.com. TXT "v=spf1 -all"

SPF records are TXT records placed into a domain's DNS settings. To
setup a SPF record we recommend using the following
`link <http://www.openspf.net/dns.html>`__.

Be advised that forwarding emails can sometimes break the SPF. If this
is the case we reccomend using SRS (Sender Rewriting Scheme). More
information about this can be found
`here <http://www.openspf.net/SRS>`__.

SPF usage with our Hosted Cloud and Outgoing Filter.
----------------------------------------------------

For clients on our hosted platform, who use our outgoing product, we
strongly recommend  to use the following setup:

-  Create a  TXT record for the outgoing sending domain with the
   following details, where \ *1234 should represent your client ID
   within SpamExperts, if you do not know this please contact
   support@spamexperts.com*:

::


        "v=spf1 a:1234.submission.antispamcloud.com a:release.antispamcloud.com -all"

-  If you clients already have an existing SPF, simply add
   ***a:1234.submission.antispamcloud.com a:release.antispamcloud.com***
   to their existing record. 

It's also possible to use the "include" option in case you wish to use
your own domain in your clients SPF records. To do this:

-  Create a subdomain for your domain you wish to add to clients SPF  
   ***spf.example.com***
-  Create a TXT record for ***spf.example.com*** with the following
   details:

::


        "v=spf1 a:1234.submission.antispamcloud.com a:release.antispamcloud.com -all"

-  Add the following to your clients SPF: 

::


        "v=spf1 include:spf.example.com -all"

Be Advised: Clients that have a Outgoing License of over 1000 domains.
Please contact our support team at support@spamexperts.com for other
instructions on our Premium service.

For  our Hosted Cloud Trial users, please use the following SPF:

***"v=spf1 a:submission-trial.antispamcloud.com
a:release.antispamcloud.com -all"***
