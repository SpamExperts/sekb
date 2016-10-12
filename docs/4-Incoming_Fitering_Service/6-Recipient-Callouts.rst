Recipient Callouts
==================

There's no point accepting mail if it is sent to a recipient email
address that doesn't actually exist on your destination mail server.
Thus the servers check the destination servers first to check if a
recipient email address is an existing email account for which the
destination server accepts email. The filtering systems internally keep
track of existing/non-existing email accounts at the destination server
to minimize the number of recipient callouts. These callouts are all
done using SMTP directly, and are compatible with any type of email
destination server. Hence it's not required to query for valid users
externally using LDAP, the SMTP server on the destination server will
handle such lookups locally.

5xx destination server rejects
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Whenever the destination server permanently rejected the email for a
certain recipient with a 5xx error code, the destination address is
considered invalid and all email sent to the recipient address will be
rejected. This information is cached locally on each filtering server
separately for up to 2 hours. You can clear the callout cache using the
webinterface or API.

Existing recipients
~~~~~~~~~~~~~~~~~~~

Existing recipients are cached for up to 96 hours.

Technical details
~~~~~~~~~~~~~~~~~

The filtering servers do a 'null sender' callout. This means that the
filtering server will connect to your destination server, using a sender
of "<>" (just as a bounce message does), and the real recipient. After
checking the recipient, the connection will be properly closed (i.e. no
message is actually sent). You need to ensure that your destination
servers will correctly verify addresses in this fashion.

Before verifying the actual address, the filtering server will check to
see if the domain will accept all email addresses (if a "catch all"
address is setup), using a randomly generated address at the domain. If
this succeeds, then there is no need to check individual addresses,
because they will always be accepted (either valid addresses or not
valid but directed to the "catch all" address). These checks are cached
just like regular checks, but mean that if the domain does have a "catch
all" address there will be few callouts.
