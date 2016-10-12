.. _4-Domain-aliasing:

Domain aliasing
===============

For users with multiple domains we offer our free domain aliasing
feature where domains can be added directly in the SpamPanel. This means
that every email sent to one of your domain aliases will be sent to the
same user on your main domain.

Users can access the **Domain Aliases** feature from the\*\* Domain
Level (Domains > Overview > Click on domain)\*\* by going to **Incoming
> Domain Aliases.**

.. figure:: https://dev.spamexperts.com/sites/default/files/pictures/Domain%20Aliases.png
   :alt: 

Example
-------

Assuming your main domain is **example.com**, the alias is
**example.org** and your destination mail server is **mail.example.org**
we will deliver any email sent to **myemail@example.org** to
**myemail@example.com** on the **mail.example.com SMTP server**.

Do note, the email headers will still show the original recipient,\ **
myemail@example.org**.

Control panel
-------------

Alias domains don't have separate access to the control panel, so you
must continue to log in as you normally do.

All SMTP traffic to the **alias domain** is automatically rewritten to
the **main domain**, so any changes or lookups on the **main domain**
will include the alias’ traffic as well.

Consequently, If you are searching for a specific email sent to a domain
alias using the log search, the recipient will therefore show as
**user@maindomain**.
