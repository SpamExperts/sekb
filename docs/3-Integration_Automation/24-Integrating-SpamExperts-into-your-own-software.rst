.. _3-Integrating-SpamExperts-into-your-own-software:

Integrating SpamExperts into your own software
==============================================

We offer several pre-built implementations ready to install and
integrate SpamExperts with `various control
panels <https://my.spamexperts.com/kb/13/3%20-Integration-and-automation>`__.
If you'd like to implement our solution into your own/proprietary
application, control panel or any automation on your end you can use the
following guidelines and implement it in a correct way.

Step 1: Determine the target audience
=====================================

It's important to decide what the application should do. Should it
create resellers, admins, domains, email users or something else?

We offer two APIs with common but also different functionalities:

Software API
------------

-  Available to: Software API users, Super Administrators [Only on Local
   Cloud]
-  Provides: All low/high level API calls with the exception of Control
   Panel specific functionality
-  Usage: via HTTP GET
-  Returns: Plaintext
-  Note: Actions done may take a few minutes to show up in the web
   interface due to caching

`This
API <https://admin:demo@demo1.spambrand.com/cgi-bin/api?call=api_help>`__
offers most control, however it's only recommended for one-time actions
as for general automation the Control API is recommended.

Control Panel API
-----------------

-  Available to: Super Administrator, Administrator, Domain and Email
   users [Both Local- and Hosted Cloud]
-  Provides: Most-used functionality and Administrator functions
-  Usage: via HTTP GET
-  Returns: Plain-text or JSON (append /format/json/ to call)

Note: Since `this API <https://demo1.spambrand.com/api/help/>`__
integrates directly into the frontend, cache will be cleared
automatically when required.

In our own integrations we make use of the Control Panel API since we
need to have it functional on the Hosted Cloud as well and it needs to
be able to work under a Administrator-level user.

If you do not require special API calls and if the Control Panel API is
sufficient, it's recommended to use it instead.

**Be advised: Mixing calls is possible but not recommended.**

Step 2: Familiarize yourself with the API
=========================================

Both API's work slightly different and have their own documentation
available.

The documentation always contains a (short) description of the
functionality of the API call and an example link.

A public demo server is available to test your integration:

-  **Hostname**: demo1.spambrand.com
-  **Username**: admin
-  **Password**: demo
-  **Software API help**:
   https://demo1.spambrand.com/cgi-bin/api?call=api\_help
-  **Control Panel API help**: https://demo1.spambrand.com/api/help/
-  **One-click-login**: Access the webinterface demo1.spambrand.com, go
   to "Settings" and download the script.

Step 3: Decide what to implement
================================

Once you have familiarised yourself with the APIs and determined which
one you'd like to use, it's time to decide which API calls are required.

For normal domain-automation and integration purposes we'll show you
some examples on how it works.

In our example we'll be adding domain "example.com" as a real domain and
"example.net" as an alias.

Adding a domain
---------------

**Control Panel API:**

::


        /api/domain/add/domain/example.com/destinations/%5B%22mail.example.com%22%5D

**Software API:**

::


        /cgi-bin/api?call=api_add_incoming_domain&domain=example.com&destination=mail.example.com

Removing a domain
-----------------

**Control Panel API:**

::


        /api/domain/remove/domain/example.com/

**Software API:**

::


        /cgi-bin/api?call=api_remove_domain&domain=example.com

Adding a domain alias
---------------------

**Control Panel API:**

::


        api/domainalias/add/domain/example.com/alias/example.net/

**Software API:**

::


        cgi-bin/api?call=api_add_domain_alias&domain=example.com&alias=example.net

Removing a domain alias
-----------------------

**Control Panel API:**

::


        api/domainalias/remove/domain/example.com/alias/example.net/

**Software API:**

::


        cgi-bin/api?call=api_remove_domain_alias&domain=example.com&alias=example.net

One-click login / SSO
---------------------

If the request was done succesfully you'll get a 40-character hash you
can append to the URL of the control panel
(**control.example.org/?authticket=CODEHERE**). From the web interface
you can download an example SSO PHP script on the "**Settings**\ " page
as super administrator or administrator.

**Control Panel API:**

::


        /api/authticket/create/username/example.com/

Step 4: Configuration
=====================

To make your application communicate with the API, it needs to know some
of the required settings.

At least this would require:

-  API / Control Panel URL
-  Username
-  Password

In case you also want to automate DNS (MX) changes you should also ask
for:

-  Primary MX Record
-  Secondary MX Record (optional)
-  Tertiary MX Record (optional)

Making API calls
================

You can make API calls with any HTTP-aware library/scripting language or
application. It does not matter whether this is something as simple as
**wget** or more complex such as **PHP** or **Python**.

The latter two are better since they are also able to parse the
output/JSON and determine whether the call succeeded.

For PHP you can make use of the **file\_get\_contents call**:

::


        $result = json_decode(file_get_contents( "https://api.example.com/api/domain/add/domain/example.com/destinations/%5B%22mail.example.com%22%5D/format/json/" ));

The **$result** parameter will then contain the array of resulting
content which can be further parsed/processed.

Flows / Procedures
==================

Some actions require changes on both sides: local (the hosting server)
and remote (SpamExperts).

Adding a domain
---------------

-  Add the domain to the system using one of the API's
-  Parse the output, verify that it was successfully added
-  Execute any required additional changes (for example: setting owner
   email address)
-  Change the MX records for the domain to the configured
   primary/secondary/tertiary MX records

In case you allow the customer to add/remove domains themselves, you
should make sure that the input is validated and verified that they have
access to their respective domain(s).

Removing a domain
-----------------

-  Revert the MX records to the local server (IP/hostname),
   mail.example.com or the domain name
-  Remove the domain through the API

In case you allow the customer to add/remove domains themselves, you
should make sure that the input is validated and verified that they have
access to their respective domain(s).
