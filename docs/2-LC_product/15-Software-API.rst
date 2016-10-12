.. _2-Software-API:

Software API
============

Software API

All functionality of the SpamExperts Local Cloud setup is exposed via
the API. A full help listing all available commands can be accessed from
the Control Panel by going to **Server** > **Software API Calls** or via
the **api\_help()** call using the following URL:

::


        https://SERVERNAME/cgi-bin/api?call=api_help. 

The API is accessible via HTTPS and can be accessed using simple URL
calls. For example, from PHP this can be done using **libcurl**, it’s
also to execute a call from any browser. The commands executed on the
Software API are automatically executed on all relevant servers in your
Local Cloud setup, so there is no need for you to individually configure
the servers. These commands should not be executed from the SSH command
line on the SpamExperts system, they can be ran from any external
location.

Be advised that the API described on this page (Software API) is only
available on our Local Cloud product. For the Hosted Cloud/Control Panel
API please refer to the
:ref:`Control Panel API documentation <1-SpamExperts-Control-Panel-API>`.

Example calls
-------------

To add a domain to the filtering cluster, you can simply execute the
add\_incoming\_domain() from a web browser, or directly from a script:

::


        https://servername/cgi-bin/api?call=api_add_incoming_domain&domain=example.com&destination=mail.example.com

As it can be seen it’s very easy to integrate the adding/removing of
domains (and all other available features) in any existing provisioning
system or control panel.

Default settings
----------------

As Local Cloud administrator you can control the default settings for
all domains.

To modify the default domain settings, simply specify “default” as
domain.. If the default value is changed, then it will affect any
domains that are still set to using the default values. If a custom
value has been previously set for a domain, then that will override the
default, even if the custom value is the same as the default. To change
a domain setting back to use the default value, the special value
**‘default’** should be used as argument.

Mind the difference between **Domain Default** and **Value Default**.
**Domain Default** changes the setting for all domains using the default
values, whereas **Value Default** changes the setting for a specific
domain back to use the “default value”.

When retrieving from the API the value of a setting that has been
changed and it’s not default, a warning will be printed to indicate that
the setting value is not the default one. The warning will also include
the default value for that setting. This allows the caller to
distinguish between **"use the default"** and **the same value as the
default**.

Sample PHP script
-----------------

Sample Python script
--------------------
