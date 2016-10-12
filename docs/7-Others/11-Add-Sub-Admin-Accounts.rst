Add Sub-Admin Accounts
======================

A Sub-Admin account is basically the same type of account as the Admin.
The only difference between the two is that the Sub-Admin is directly
subordinated to an Admin.

This means that the Admin has full control over the Sub-Admin from the
moment he creates this type of user. For example, amongst other
settings, he can choose how many domains a Sub-Admin can manage, if that
account will have access to Control Panel API, or what products
(incoming / outgoing filtering / archiving) the Sub-Admin will use.

To add a Sub-Admin account you need to follow the steps below:

1. Log in the SpamExperts web interface with your Admin username and
   password
2. Go to **Manage Admins**, under Web interface Users tab
3. Click **Add**
4. Select the username, password and email address for your Sub-Admin
5. Review the Sub-Admin privileges, as follows:

.. figure:: https://dev.spamexperts.com/sites/default/files/images/sub-admin-add.png
   :alt: 

**Allow Sub-Admins** - this determines if the Sub-Admin can add
Sub-Admins himself.

**Allow release of outgoing spam messages** - select this to allow the
Sub-Admin to release outgoing spam messages.

Be advised that for our Hosted Cloud Clients this is currently limited,
even if the option is set to Enable.

**Allow Control Panel API usage** - this will allow the Sub-Admin to use
Control Panel API calls or not.

**Available products** - this determines what products the domains of
this admin can have - Incoming / Outgoing filtering and/or Archiving.

Be advised: this influences what products the Sub-Admin can enable on
the domains that he owns. For example, if you only enable incoming
filtering, the domains of the Sub-Admin will only have Incoming
filtering.

**Private label** - select to enable or disable private label for the
Sub-Admin

**Domains limit** - this specifies how many domains this admin can add.
If you only want him to handle 2 domains, then you can set the limit to
2 domains, otherwise use 0 for unlimited domains.

Be Advised: The limit is shared with your own limit. For example, if
your license is of 20 domains, you cannot set the limit to 0 for the
Sub-Admin. You can set it to 20, however this means that you will be
unable to add domains on your Admin account and all new added domains
will be attributed to the Sub- Admin account.

6. Click **Save**.

You're all set! Now the Sub-Admin account can be used.
