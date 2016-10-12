.. _2-SSL-Certificates:

SSL Certificates
================

Introduction
============

By default a self-signed SSL certificate is installed on your server for
HTTP, SMTP, and IMAP. You can replace these certificates with a signed
certificate directly from the API, or from the Control Panel as a
Super-Administrator on the "Certificates" page.

If you already have a Certificate (CRT), and the certificate key (KEY),
the certificate signing request (CSR) and the Certificate Bundle (Root
Intermediary Certificate) you can skip the Generate a CSR step and go
directly to uploading Certificates in the SpamExperts Control Panel.

Be Advised: Before generating an SSL Certificate, there are a few things
that you should take into consideration:

-  Web interface SSL should match the full hostname used to access the
   SpamExperts Control Panel
-  Incoming certificate should match the MX records
-  Outgoing certificate should match the SMTP hostname used

Generate a Certificate signing requests (CSR)
=============================================

This step is mandatory in case you need a new certificate. If you
already have the certificate(s) please skip to the Uploading the
Certificate(s) step.

Creating Certificate Signing Requests
-------------------------------------

In order to request a certificate, you'll need to create a CSR
(Certificate Signing Request).You can do this with the commands below,
or via our Control Panel certificate function.

The CSR is needed to generate the real certificate issued by a CA
(Certificate Authority).

Generate a CSR with the SpamExperts Control Panel
-------------------------------------------------

First you need to complete a certificate signing request (CSR) and a RSA
private key. This can be achieved on the server by following our guide
or directly from the SpamExperts Control Panel:

1. Log in as **Super-Admin** in the **Control Panel**
2. Go to **Server** > **Certificates**
3. Click on the **Generate CSR & RSA Key** button
4. Fill in all the details and Click the **Generate** button
5. Copy the CSR and RSA key somewhere. You'll need the CSR for the
   certificate request, the RSA key will be used later on when importing
   the certificate.

The CSR is needed to generate the real certificate issued by a CA
(Certificate Authority).

Generate a KEY and CSR via a Terminal
-------------------------------------

Generate a KEY via a Terminal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure you have OpenSSL installed on that machine.

Now you need to create a key and sign the certificate with it, by using
the following command:

::


          openssl genrsa -out example.com.key 2048

You should replace "example.com" with the hostname the certificate is
intended for.

The output should be similar to this:

::


         Generating RSA private key, 2048 bit long modulus
          ......+++
          .........................+++
          e is 65537 (0x10001)
        

The process takes a few seconds, after which you continue the next part.

Keep in mind that this is the certificate’s private key and is essential
to keep it safe as without it you can’t generate the certificate signing
request (CSR).You will also need the key later when uploading the
certificate.

Generate the CSR via a Terminal
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After you have generated the private key, you can create the CSR by
using the following command:

::


         openssl req -new -key example.com.key -out example.com.csr

As above, don’t forget to replace “example.com”.

You will now be presented with a few questions.

::


          You are about to be asked to enter information that will be incorporated
          into your certificate request.
          What you are about to enter is what is called a Distinguished Name or a DN.
          There are quite a few fields but you can leave some blank
          For some fields there will be a default value,
          If you enter '.', the field will be left blank.
          -----
          Country Name (2 letter code) [AU]: NL
          State or Province Name (full name) [Some-State]: State
          Locality Name (eg, city) []: Cityname 
          Organization Name (eg, company) [Internet Widgits Pty Ltd]: Your Company Name
          Organizational Unit Name (eg, section) []: Department
          Common Name (eg, YOUR name/FQDN) []:example.com
          Email Address []:example@example.com
          Please enter the following 'extra' attributes
          to be sent with your certificate request
          A challenge password []:
          An optional company name []:
        

Be Advised: Don't set a challenge password. Just hit Enter when asked.

.. figure:: http://dev.spamexperts.com/sites/default/files/images/generate%20cert.jpg
   :alt: 

The Common Name is important and should match your server CNAME /
Control Panel Hostname settings.

If for example, your control panel is hosted at "server1.example.com",
you should enter that as "Common Name". **Do not enter HTTP:// or
HTTPS://**.

If you are using a different name for your control panel
(cp.example.com), you should enter this as Common Name.

Uploading the Certificate(s)
============================

If you already have a wildcard certificate for your domain, you can
upload this to your control panel. Ensure the certificate matches up
your Fully Qualified Domain Name (FQDN) or will display an error in the
browser stating that the certificate is invalid.

The Certificate(s)
------------------

When you have received the issued certificate(s), also ensure you get
their CA bundle. This will contain the intermediate certificate(s) (if
any) and root certs. You will need the full bundle, not only the
underlying root certificate as this will not be accepted by the panel.

You'll need to assemble three files in total:

1. **The full certificates**, which contain, in order:

The private key, the issued certificate, the intermediate
certificate(s), the root certificate(s). This will most likely be 4 to 5
certificates in total.

2. **Certificates only**

This will only contain the issued certificate, the intermediate
certificate(s) and the root certificate(s). This will most likely be 3
to 4 certificates in total.

3. **Key only**

This will only contain the private key. This will be a single entry.

If you need to cover SMTP and IMAP as well, the best choice as a
certificate might be a wildcard certificate. With this, all your
filtering servers and used services will be covered by the certificate
(\*.example.com instead of smtp.example.com). With SMTP it is generally
never needed to have a matching name as this will only print warnings in
transit. It will however give warnings in e-mail clients if submission
is done directly to the cluster from there (a wildcard will cover for
this). For HTTPS and Quarantine, the certificates should match the
actual hostnames, or use the before mentioned wildcard.

To upload the certificate, just follow the same path go to **Server** >
**Certificates** > click **Browse** and select the certificate file.

Be advised: The Certificate file should contain the Private Key, the
Certificate, and Issuer's (CA) root certificate(s). It will often also
contain one or more intermediate certificates. The order should be as
follows (in the same file):

1. Private Key
2. Issued Certificate
3. Intermediate Certificate(s)
4. Root Certificate(s)

A more detailed example on how the certificate assembly should look like
is as follows. In this example, the CA bundle contained one root
certificate and two intermediates. This format is used for the web
interface and quarantine.

::


        -----BEGIN PRIVATE KEY-----
        Private key saved earlier
        -----END PRIVATE KEY-----
        -----BEGIN CERTIFICATE-----
        The issued certificate will be here
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Intermediate certificate from CA bundle
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Intermediate certificate from CA bundle
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Root certificate from CA bundle
        -----END CERTIFICATE-----
        

For SMTP/IMAP we'll need to split up in two files to upload. One for the
private key:

::


        -----BEGIN PRIVATE KEY-----
        Private key saved earlier
        -----END PRIVATE KEY-----
        

And one only containing the certificates:

::


        -----BEGIN CERTIFICATE-----
        The issued certificate will be here
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Intermediate certificate from CA bundle
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Intermediate certificate from CA bundle
        -----END CERTIFICATE-----
        -----BEGIN CERTIFICATE-----
        Root certificate from CA bundle
        -----END CERTIFICATE-----
        

Upload via the Control Panel
----------------------------

Once you've created these files, you can use them to request a
certificate through your SSL certificate provider.

When you've received your certificate, you can upload it to the
**Control Panel** under **"Server"** -> **"Certificates"**.

Merge the Certificate and Private Key (Optional)
------------------------------------------------

Once you have obtained a valid Private Key (KEY) and Certificate (CRT),
you can submit them directly from the API. Depending on the call, both
files should be merged in 1 file with the .pem file extension.

To merge the two files use the following command in a terminal:

::


        cat example.com.crt example.com.key > example.com.includepvkey.pem

Where **example.com.crt** is your certificate, **example.com.key** is
your private key and the output is **example.com.includepvkey.pem**, the
.pem file you need to upload.
