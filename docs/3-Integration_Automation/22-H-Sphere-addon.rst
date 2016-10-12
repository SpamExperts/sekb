.. _3-H-Sphere-addon:

H-Sphere addon
==============

The H-Sphere module is being maintained and supported by
`CPDevel <http://www.cpdevel.com/>`__.

This addon is free to use for all SpamExperts clients.

Be Advised: SpamExperts does **not** offer support for this add-on and
`support can be requested from
CPDevel <http://www.cpdevel.com/customer-support/>`__.

Features
--------

-  Protect domains and change their MX records
-  Billing clients (if included in plan)
-  Login to manage the SpamExperts settings

Installation
------------

The following commands can executed to install the addon:

::


        su - cpanel 
        wget http://download.spambrand.com/hsphere/SpamExperts-latest.hsp
        java psoft.hsp.tools.PkgInstaller --package=SpamExperts-latest.hsp
        exit
        service httpdcp restart
        

Upgrade
-------

The following commands can executed to upgrade the addon:

::


        su - cpanel
        wget http://download.spambrand.com/hsphere/SpamExperts-latest.hsp
        java psoft.hsp.tools.PkgInstaller --package=SpamExperts-latest.hsp --upgrade
        exit
        service httpdcp restart
        

Uninstall
---------

The following commands can executed to uninstall the addon:

::


        su - cpanel
        java psoft.hsp.tools.PkgUnInstaller --pkg-name=SpamExperts-latest.hsp
        exit
        service httpdcp restart

Using this addon on the Hosted Cloud
------------------------------------

| Hosted Cloud users are required to first request enabling of their API
  via SpamExperts support.
| Further instructions about configuring and enabling of the API on the
  Hosted Cloud can be
  found \ :ref:`here  <1-Using-addons-on-the-Hosted-Cloud>`.
