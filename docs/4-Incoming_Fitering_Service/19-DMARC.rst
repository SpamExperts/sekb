.. _4-DMARC:

DMARC
=====

What is DMARC
=============

DMARC (Domain-based Message Authentication, Reporting & Conformance) is
an email protocol designed to help prevent email spoofing when used in
conjunction with
:ref:`SPF  <5-Setup-a-SPF-record>`
and/or
:ref:`DKIM  <5-Generate-DKIM-certificate>`
and gives sending domain administrators the ability to act on messages
when the criteria is not met. DMARC also provides the tools for senders
to monitor the abuse of their domains.

We would highly recommend configuring DMARC DNS records on managed
domains especially if your domain is the target of spoofed emails and
enabling the functionality within SpamExperts where possible. If you are
unclear on how to setup DNS records please consult your DNS
administrator.

Does SpamExperts support DMARC
==============================

Yes, SpamExperts fully supports DMARC on all incoming email. This is
currently not enabled for any outgoing email on SpamExperts, so will not
affect any outgoing traffic.

How does DMARC work
===================

DMARC works by matching the "From" header to the "Envelope From" of the
sending email. It can prevent spoofing of the "From" headers which is
commonly used by spammers in phishing campaigns.

More information on how DMARC works can be found here:
https://dmarc.org/wiki/FAQ

How to setup a DMARC record
===========================

DMARC records are set up in the DNS of a domain. There are many online
tools that can help you here, for example:
http://kitterman.com/dmarc/assistant.html

Alternatively, there are other examples here:
https://dmarc.org/resources/deployment-tools/

Configuring DMARC actions in the SpamExperts systems
====================================================

To enable the DMARC check within the SpamExperts dashboard, you need to
do the folowing

1. Log into the interface
2. Click on the Filter Settings page
3. Tick the DMARC option in the Sender Checks section

Skipping certain domains from DMARC checks
==========================================

Sometimes it is needed to be able to skip this check for certain sending
domains. This can be done very much like the current SPF and DKIM skips.

1. Log into the interface
2. Click on the Filter Settings page
3. Click the "Manage list of domains and IP addresses with disabled SPF,
   DKIM, and DMARC checks" link
4. Navigate to the "Disabled DMARC Domains" tab
5. Add entry
6. Click save
