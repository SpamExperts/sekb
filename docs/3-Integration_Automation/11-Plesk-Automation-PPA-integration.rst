.. _3-Plesk-Automation-PPA-integration:

Plesk Automation (PPA) integration
==================================

Add-on integration
~~~~~~~~~~~~~~~~~~

Plesk Automation (PPA) has support for the APS 1.2 standard. You'll need
to verify with your Parallels regional account manager that the APS
license has been activated for your PPA setup.

1. Login as PPA administrator, go to ***Services,** **External
Applications***, import the `SpamExperts APS 1.2
package <http://dev.apsstandard.org/apps/>`__

.. figure:: /_static/images/3.png
   :alt: 

2. After the installation has completed (this takes a few minutes),
click the "***SpamExperts Integration***\ " package name, go to
***Resource types***

3. You have to Create the following resources:
==============================================

| **Resource class**: Application
| **Name:** SE: SpamExperts

| **Spampanel URL**: https://demo1.spambrand.com/ (please ensure to use
  https and not http)
| **Spampanel API** hostname: demo1.spambrand.com
| **Spampanel API** super administrator name: admin
| **Spampanel API** super administrator password: password
| **Enable SSL**: no
| **Primary MX:** demo1.spambrand.com
| **Interface enabled**: 1
| **Amount of domains allowed**: 100
| **Amount of serviceusers allowed**: 100
| **Enable incoming**: 1
| **Enable outgoing**: 0
| **Enable archiving**: 0

| **Provision application on account's domain**: yes
| **Provision application on vendor's domain**: no
| **Auto host domain**: yes
| **Bind domains to application instance**: yes
| **Automatically provision application**: yes
| **Prohibit service users with custom UPN**: no
| **Prohibit application instance deinstallation**: no
| **Mandatory for service user**: yes
| **Show application in navigation menu**: yes
| **Embed application user interface**: 

Do not associate an attribute.

| After this resource has been added, you need to:
| 1. Edit the resource SE: SpamExperts
| 2. Go to "Activation parameters"
| 3. Go to the sub-heading "Services"
| 4. Edit the "Application service 'Email Level Account'"
| 5. Turn off "Show in control panel" and "Show in instances list"

| ===============
| **Resource class**: Application service
| **Name**: SE: Email account

**Service**: Email level account
================================

| **Resource class**: Application counter (unit)
| **Name**: SE: Interface Enabled (with corresponding resource on next
  page)
| ===============
| **Resource class:** Application counter (unit)
| **Name**: SE: # of domains (with corresponding resource on next page)
| ===============
| **Resource class**: Application counter (unit)
| **Name**: SE: # of users (with corresponding resource on next page)
| ===============
| **Resource class**: Application counter (unit)
| **Name**: SE: Incoming (with corresponding resource on next page)
| ===============
| **Resource class**: Application counter (unit)
| **Name**: SE: Outgoing (with corresponding resource on next page)
| ===============
| **Resource class**: Application counter (unit)
| **Name**: SE: Achiving (with corresponding resource on next page)
| ===============

.. figure:: /_static/images/2.png
   :alt: 

4. Go to ***Products, Service Templates, Add Shared Hosting Template***

| **Name**: Mail + SE (default settings)
| Add the newly created SE: resources to this template

| **SE: # of domains**: unlimited
| **SE: # of users**: unlimited
| **SE: Archiving**: 0
| **SE: Email account**: unlimited
| **SE: Incoming**: 1
| **SE: Interface enabled**: 1
| **SE: Outgoing**: 0

.. figure:: /_static/images/1.png
   :alt: 

For domain to be registered automatically in SpamExperts, you have to
change its registrar status to Ready. A customer can add any of its
domains from the customer panel, the registrar status is not important
in this case.

If you get the error "License overuse for item 'Hosted APS applications'
(hosted-aps-applications).", it means there is no APS license active on
your PPA install. A Parallels regional sales manager can activate this
for you.
