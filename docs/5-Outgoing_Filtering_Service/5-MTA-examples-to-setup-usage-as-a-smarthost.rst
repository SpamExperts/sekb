.. _5-MTA-examples-to-setup-usage-as-a-smarthost:

MTA examples to setup usage as a smarthost
==========================================

You can use the Outgoing Service as a default smarthost relay. This page
will describe how to setup various SMTP daemon to use a smarthost for
filtering.

In all examples we will use the hostname **SMARTHOST** on port **587**
as outgoing server. This should be changed to reflect your local setup.
Replace **SMARTHOST** with your filter hostname. You possibly want to
make **SMARTHOST** something like "outgoing.yourprovidername.com"
containing all the outgoing IPs of your filterservers. In case you use
our Hosted Cloud product you should contact support for the correct
smarthost hostname. Information on the trial Hostname for Hosted Cloud
users can be found
`here <https://my.spamexperts.com/kb/74/Get-started-with-the-Outgoing-Filter.html>`__

*All suggested commands/setups mentioned on this page are at your own
risk!*

Qmail
-----

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

   ::

       ```
            echo ":**SMARTHOST**:587" > /var/qmail/control/smtproutes 
       ```

*This will override any existing smtproutes. If you do not want this,
you can replace the single > with >>.*

Routing specific domain destinations via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

::

         echo "example.com:**SMARTHOST**:587" >> /var/qmail/control/smtproutes

This will route outgoing email TO "example.com" via the smarthost.

Postfix
-------

Routing all outgoing mails via the outgoing smarthost (IP Authentication):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

You should edit **/etc/postfix/main.cf** and make sure there is a line:

::


         relayhost = **SMARTHOST**:587

Then restart postfix.

Routing outgoing mails with Per Username Authentication:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To use an authenticated user, create a password maps file, for example
*/etc/postfix/relay\_passwd*:

::


        smtp.smarthostname.example.com USERNAME:PASSWORD"

Ensure the file has the correct permissions and to create the hash from
the maps file by executing:

-  ``chown root:root /etc/postfix/relay_passwd``
-  ``chmod 600 /etc/postfix/relay_passwd``
-  ``postmap /etc/postfix/relay_passwd``

Add the following line to **/etc/postfix/main.cf**

::


         relayhost = **SMARTHOST**:587

Finally add to /etc/postfix/main.cf below the "relayhost =" line:

::


        smtp_sasl_auth_enable = yes
        smtp_sasl_password_maps = hash:/etc/postfix/relay_passwd
        smtp_sasl_security_options = 
        

Restart Postfix for the changes to take effect: /etc/init.d/postfix
restart

Routing specific domain destinations via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to do this, you should add a line to
**/etc/postfix/transport**:

::


         example.com smtp:[**SMARTHOST**]:587

After you've made your changes, you should generate a postmap file
using:

::


         postmap hash:/etc/postfix/transport

In order for Postfix to use the transport file, you should add or edit a
line in **/etc/postfix/main.cf**:

::


         transport_maps = hash:/etc/postfix/transport

Afterwards you should restart Postfix and all mail or the mail for
selected domains should go trough the Smarthost.

Routing specific domain through own outgoing users:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| If you want to use a more fine-grained model you can choose to relay
  the outbound traffic for domains over separate users.
| This allows you to apply different settings per domain, but also
  provides the enduser access to their own logfiles.

To do this the following part has to be added to your main.cf:

::


        relayhost = [**SMARTHOST**]:587
        smtp_sasl_auth_enable = yes
        smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
        smtp_sasl_security_options =
        smtp_sender_dependent_authentication = yes
        sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay

Account should be configured in the sasl\_passwd file in this format:

::


        @example.com outgoing@example.com:THEPASSWORD

The sender\_relay file can be used to override the smarthost per-server
as well, the format for this file is:

::


        @example.com [SMARTHOST1]:587  
        @example.net [SMARTHOST2]:587

Don't forget to postmap the sasl\_passwd / sender\_relay files otherwise
they will not work.

Routing only some domains via the outgoing filter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to only relay some outgoing domains from your server via the
outgoing filter, while having the rest deliver locally outbound, then
you can do the below. Assuming that you have already created an outgoing
per username authenticated user in your SpamExperts outgoing user
section. This example shows how to route outbound email for the domain
example.com using the outbound authentication smtp@example.com

Add the following to the main.cf

::


        smtp_sasl_auth_enable = yes   
        smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd   
        smtp_sasl_security_options =   
        smtp_sender_dependent_authentication = yes   
        sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay

Create the following file:

::


        /etc/postfix/sender_relay

With the contents:

::


        @example.com [RELAYHOSTHERE]:587

Create the following file:

::


        /etc/postfix/sasl_passwd

With the contents (The outgoing authenticated user created in the
SpamExperts interface):

::


        @example.com smtp@example.com:test123

postmap these files:

::


        postmap hash:/etc/postfix/sender_relay  
        postmap hash:/etc/postfix/sasl_passwd

Restart Postfix

Exim
----

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

For this you have to edit your Exim configuration file (e.g.
**/etc/exim/exim.conf**).

You have to add in the routers section (after **begin routers**):

::


         spamexperts_smarthost_router:
          driver = manualroute
          # Exclude null sender messages from relaying via the smarthost
          condition = ${if or {{!eq{$sender_address}{}} {!eq{$sender_host_address}{}}}}
          transport = spamexperts_smarthost_transport
          route_list = $domain **SMARTHOST**::587
          no_more

If you don't want local mail to be forwarded, then make sure the local
mail router is before this one.

You have to add in the transports section (after **begin transports**):

::


         spamexperts_smarthost_transport:
          driver = smtp
          hosts_require_tls = *

Finally restart Exim.

Extra: Using authentication to deliver
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you want to use this example using authentication, append the
following lines to the to "remote\_smtp\_smart\_dkim" and
"remote\_smtp\_smart\_regular" sections:

::


          hosts_require_auth = *
        

Add the following part after the "begin authenticators":

::


          begin authenticators
        
          spamexperts_login:
          driver = plaintext
          public_name = LOGIN
          client_send = : **username@example.com** : **yourUserPassword  
          
        **

Please ensure any special characters in the password require are
escaped. Finally restart Exim.

Extra: Routing specific domain destinations via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Put the domain in place of the $domain value in the route\_list (above).
For multiple domains you can use:

::


          route_list = domain.example.com **SMARTHOST**::587 ; domain.example.org **SMARTHOST**::587

Exim/cPanel
-----------

Routing all outgoing mails via the outgoing smarthost (IP authentication):
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Go to the "Exim Configuration Editor" in WHM. Choose "Advanced Editor".

You have to add in the "Section: ROUTERSTART" (replace SMARTHOST with
the correct SMTP hostname):

::


        smarthost_dkim:
          driver = manualroute
          domains = !+local_domains
          require_files = "+/var/cpanel/domain_keys/private/${sender_address_domain}"
          # Exclude null sender messages from relaying via the smarthost
          condition = ${if or {{!eq{$sender_address}{}} {!eq{$sender_host_address}{}}}} 
          transport = remote_smtp_smart_dkim
          route_list = $domain **SMARTHOST**::587
        
        smarthost_regular:
          driver = manualroute
          domains = !+local_domains
          # Exclude null sender messages from relaying via the smarthost
          condition = ${if or {{!eq{$sender_address}{}} {!eq{$sender_host_address}{}}}} 
          transport = remote_smtp_smart_regular
          route_list = $domain **SMARTHOST**::587
        
        

If you are looking to use the cPanel outgoing hourly domain limits
options, please add the above configuration in the "Section:
POSTMAILCOUNT" section instead.

You have to add in the "Section: TRANSPORTSTART" (ensure to remove the
line forcing authentication if no username/password is required)):

::


        remote_smtp_smart_dkim:
          driver = smtp
          hosts_require_tls = *
          interface = ${if exists {/etc/mailips}{${lookup{$sender_address_domain}lsearch*{/etc/mailips}{$value}{}}}{}}
          helo_data = ${if exists {/etc/mailhelo}{${lookup{$sender_address_domain}lsearch*{/etc/mailhelo}{$value}{$primary_hostname}}}{$primary_hostname}}
          dkim_domain = $sender_address_domain
          dkim_selector = default
          dkim_private_key = "/var/cpanel/domain_keys/private/${dkim_domain}"
          dkim_canon = relaxed  
          headers_add = X-AuthUser: ${if match {$authenticated_id}{.*@.*}\  
         {$authenticated_id} {${if match {$authenticated_id}{.+}\  
         {$authenticated_id@$primary_hostname}{$authenticated_id}}}}  
          # Uncomment the line below in case you use a login for authentication  
          #hosts_require_auth = *  
        
        remote_smtp_smart_regular:
          driver = smtp
          hosts_require_tls = *
          interface = ${if exists {/etc/mailips}{${lookup{$sender_address_domain}lsearch*{/etc/mailips}{$value}{}}}{}}
          helo_data = ${if exists {/etc/mailhelo}{${lookup{$sender_address_domain}lsearch*{/etc/mailhelo}{$value}{$primary_hostname}}}{$primary_hostname}}  
          headers_add = X-AuthUser: ${if match {$authenticated_id}{.*@.*}\  
          {$authenticated_id} {${if match {$authenticated_id}{.+}\  
          {$authenticated_id@$primary_hostname}{$authenticated_id}}}}
         # Uncomment the line below in case you use a login for authentication  
         #hosts_require_auth = *

In case you use  **per username authenticatio**\ n, you have
to uncomment the 2 "hosts\_require\_auth = \*" lines in the transport
section, and add in the "Section: AUTH" (replace "username@example.com"
with your username, and "yourUserPassword" with your password):

::


          spamexperts_login:
          driver = plaintext
          public_name = LOGIN
          client_send = : **username@example.com** : **yourUserPassword**

Please ensure any special characters in the password require are
escaped. Finally save the settings which will restart Exim.

| Save the configuration, and all of the outgoing mail will be relayed
  trough the filterserver, and will accept both DKIM signed emails and
  original ones. Please ensure the IP address is authorized to relay
  outbound email without authentication before enabling this.
  Furthermore to prevent our sender verification callouts being blocked,
  please ensure to whitelist all your SpamExperts IPs in: Exim
  Configuration Manager => Basic Editor => Access Lists -->
  "Only-Verify-Recipient".
| For Hosted Cloud users, please add your custom SPF hostname
  '**CLIENTID.submission.antispamcloud.com**\ ' and
  '**delivery.antispamcloud.com**\ ' instead.

Extra: Routing all outgoing emails via the outgoing smarthost with
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

individual outgoing accounts:

In some cases you might want to be able to set custom settings/limits
for outgoing users. For this you can use the information above (Routing
with SMTP Authentication) but with a small change. Instead of the
**client\_send** in the previous example you can use this:

::


        client_send = :  ${extract{user}{${lookup{$sender_address_domain}lsearch{/etc/exim_spamexperts}}}}  :  ${extract{pass}{${lookup{$sender_address_domain}lsearch{/etc/exim_spamexperts}}}}

You can then create a file called **/etc/exim\_spamexperts** with the
following structure:

::


        domain1.com:    user=user@domain1.com     pass=abc  
        domain2.com:    user=user@domain2.com     pass=xyz

**Please note: If authentication details for the sending domain cannot
be found in */etc/exim\_spamexperts*, the message cannot be delivered!**

Extra: Limiting Outgoing for certain sender domains
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the router you can add the following entry (underneath domains).

::


        senders = ^.*@domain1.com : ^.*@domain2.com

This option can be combined with the individual accounts configuration
to restrict outgoing only to specific domains.

It's also possible to read this from a file.  For example (assuming the
domains are in a the '/etc/spamexperts\_domains':

::


        senders = *@partial-lsearch;/etc/spamexperts_domains

Extra: Limiting Outgoing for certain senders
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In some cases you might want to be able to assign each sender his own
outgoing user. To do this, you need to:

Create a file called /etc/exim\_spamexperts with the following
structure:

::


        sender1@domain1.com: user=user1@domain1.com pass=abc
        sender2@domain1.com: user=user2@domain1.com pass=xyz

In the ROUTERSTART section (underneath domains) add:

::


        condition = ${lookup{$sender_address}lsearch{/etc/exim_spamexperts}{true}{false}}

In the AUTH section, you need to add:

::


        spamexperts_login:
        driver = plaintext
        public_name = LOGIN
        client_send = : ${extract{user}{${lookup{$sender_address}lsearch{/etc/exim_spamexperts}}}} : ${extract{pass}{${lookup{$sender_address}lsearch{/etc/exim_spamexperts}}}}

Extra: Rewriting invalid senders to pass sender verification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the TRANSPORT section you can add the following entry (underneath
domains).

::


        return_path = ${if \
        or { \
        { eq {$return_path} {do_not_reply@intuit.com} } \
        { eq {$return_path} {do_not_reply@appcenter.intuit.com} } \
        { eq {$return_path} {ac@bsgconsulting.com} } \
        { match {$return_path} {\Nprvs=.*=adpdonotreply@adp.com\N} } \
        } \
        {validsender@domain.ext}{$return_path} \
        }

Using cPanel's hourly limit option.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| If you wish to make use of cPanel's email limit options for outbound
  email. Then you need to remove the "**ROUTERSTART**\ " section and add
  the same entry in the "**POSTMAILCOUNT**\ " instead.
| The options; "**Maximum percentage of failed or deferred messages a
  domain may send per hour**." and "**Maximum Hourly Email by Domain
  Relayed**\ " are adhered to for outgoing email via a smarthost.

Exim/Directadmin

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

For this you have to edit your Exim configuration file (e.g.
**/etc/exim.conf**).

You have to add in the routers section (after **begin routers**):

::


        spamexperts_smarthost_router:
          driver = manualroute
          domains = ! +local_domains
          ignore_target_hosts = 127.0.0.0/8
          condition = "${perl{check_limits}}"
          # Exclude null sender messages from relaying via the smarthost
          condition = ${if or {{!eq{$sender_address}{}} {!eq{$sender_host_address}{}}}}
        transport = spamexperts_smarthost_transport   
        route_list = $domain **SMARTHOST**::587   
        no_more

You MAY have to comment "lookuphost:" router depending on your
configuration.

You have to add in the transports section (after **begin transports**):

::


        spamexperts_smarthost_transport:
          driver = smtp  
         # In-case your server continues to send outbound over port 25 please add the below line  
          port = 587
          hosts_require_tls = **SMARTHOST**

Finally restart Exim.

If you are signing with DKIM on your Direct Admin server you may need to
add the following line under hosts\_require\_tls

::


        .include_if_exists /etc/exim.dkim.conf

Extra: Using authentication to deliver
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Add after **"begin authenticators"**:

::


        spamexperts_login:
          driver = plaintext
          public_name = LOGIN
          client_send = : **username@example.com** : **yourUserPassword**

Add to "spamexperts\_smarthost\_transport":

::


          hosts_require_auth = *

Extra: Routing all outgoing emails via the outgoing smarthost with
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

individual outgoing accounts:

| In some cases you might want to be able to set custom settings/limits
  for outgoing users. For this you can use the information above
  (Routing with SMTP Authentication) but with a small change.
| Instead of the **client\_send** in the previous example (*extra: using
  authentication to deliver*) you can use this:

::


        client_send = :  ${extract{user}{${lookup{$sender_address_domain}lsearch{/etc/exim_spamexperts}}}}  :  ${extract{pass}{${lookup{$sender_address_domain}lsearch{/etc/exim_spamexperts}}}}

You can then create a file called **/etc/exim\_spamexperts** with the
following structure:

::


        domain1.com:    user=user@domain1.com     pass=abc  
        domain2.com:    user=user@domain2.com     pass=xyz

**Please note: If authentication details for the sending domain cannot
be found in */etc/exim\_spamexperts*, the message cannot be delivered!**

Extra: Limiting Outgoing for certain domains
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the router (spamexperts\_smarthost\_router) you can add the following
entry (underneath "domains = ").

::


        senders = ^.*@domain1.com : ^.*@domain2.com

This option can be combined with the individual accounts configuration
to restrict outgoing only to specific domains.

Extra: Force Local deliveries though a smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you are looking for force all local deliveries as well though the
smarthost, then you will need to adjust your **"router"** section to
something like the following (replacing IPSERVER1 & IPSERVER2 with the
primary IP's of your filtering servers:

::


        spamexperts_smarthost_router:
          driver = manualroute
          ignore_target_hosts = 127.0.0.0/8  
          condition = ${if !inlist{$sender_host_address}{<; **IPSERVER1** ;** IPSERVER2**}}
          condition = "${perl{check_limits}}"
          # Exclude null sender messages from relaying via the smarthost
          condition = ${if or {{!eq{$sender_address}{}} {!eq{$sender_host_address}{}}}}
          transport = spamexperts_smarthost_transport
          route_list = $domain **SMARTHOST**::587
          no_more

Sendmail
--------

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

For this you have to edit **/etc/sendmail.cf** and add the following
line:

::


         DS**Smarthost**

Restart Sendmail and it should work.

Alternative Configuration with username authentication (un-tested)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Change directory to where your sendmail configuration files
(**sendmail.mc** and **sendmail.cf)** are located, usually
**/etc/mail/.**

2. Create a safe subdirectory (suggested name **auth/**):

::


            # mkdir auth
            # chmod 700 auth
        

Create a file with your authentication information (suggested filename:
**auth /client-info**).

::


                AuthInfo:**smtp-trial.antispamcloud.com**: "U:USERNAME" "P:PASSWORD"
        

Generate the authentication database and make both files readable only
by root:

::


           # cd auth
           # makemap hash client-info < client-info
           # chmod 600 client-info*
           # cd ..
        

Add the following lines to your sendmail.mc file

::


           define(`SMART_HOST',`[**smtp-trial.antispamcloud.com**]')dnl
           define(`RELAY_MAILER_ARGS', `TCP $h 587')
           define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
           FEATURE(`authinfo',`hash /etc/mail/auth/client-info')dnl
        

Generate sendmail.cf

::


           # m4 sendmail.mc > sendmail.cf
        

Restart the sendmail daemon

::


           # kill -HUP `cat /var/run/sendmail.pid`   (old-school)   -OR-
           # make restart                            (FreeBSD)      -OR-
           # /etc/init.d/sendmail reload             (debian Linux)  
          
        

For localCloud users, you will need to replace \*\*
smtp-trial.antispamcloud.com \*\*with your specific hostname.

Exchange 2000/2003
------------------

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

-  In the Exchange System Manager, expand the Administrative Groups
   container.
-  Expand the desired administrative group, and expand the Routing
   Groups container.
-  Expand the routing group you need to work with, right-click the
   Connectors folder, and select New.
-  Select SMTP Connector.
-  On the General tab, enter a name to identify the connector.
-  Select Forward All Mail Through This Connector To The Following Smart
   Hosts, and enter **SMARTHOST**
-  Default SMTP Server -> Properties -> Delivery Tab -> Outbound
   Connections -> TCP Port set to 587

Routing specific domain destinations via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For this to work, you should do the things mentioned under **Routing all
mails to a smarthost** and continue:

-  Under Local Bridgeheads, click Add, and select the SMTP server that
   will become the SMTP bridgehead for its routing group.
-  On the Address Space tab, click Add, select SMTP, and click OK.
-  In the E-Mail Domain box, add the name of the remote location's
   e-mail domain (e.g., **example.com**), and click OK.
-  Click OK three times to exit the SMTP connector configuration.
-  Restart the Microsoft Exchange Routing Engine service and the SMTP
   service.

Exchange 2007/2010
------------------

This may also apply on future versions

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

A Send Connector must already have been created and configured correctly
on the Hub Transport server.

-  Open Exchange Management Console
-  Click on the + next to Organization Configuration
-  Select Hub Transport and
-  select the Send Connectors tab:
-  Right-click on the existing Send Connector, select Properties and go
   to the Network tab.
-  Select "Route mail through the following smart hosts:" and click Add.
-  Enter **SMARTHOST ** (you need to use port 587)
-  If you have more then one Smarthost, repeat the previous two steps.

The changes you've made to the Send Connector will take effect straight
away without you having to reboot the server or restart any services.

In order to change the port to 587 you will have to issue the following
command in the Exchange Powershell Console:

::


        Set-SendConnector -identity "**NAME OF CONNECTOR**" -Port:587

Afterwards restart restart the transport service and relaying should
work.

Routing all outgoing mails via the outgoing smarthost with Username
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Authentication:

A Send Connector must already have been created and configured correctly
on the Hub Transport server.

-  Open Exchange Management Console
-  Click on the + next to Organization Configuration
-  Select Hub Transport and
-  select the Send Connectors tab:
-  Right-click on the existing Send Connector, select Properties and go
   to the Network tab.
-  Select "Route mail through the following smart hosts:" and click Add.
-  Enter **smtp-trial.antispamcloud.com** in the FQDN section. (Change
   this to the licensed paid hostname when you have purchased a license)
-  Click 'Change' under the smart-host authentication
-  Select '**Basic Authentication**\ '
-  Add your newly created username and password
-  Click OK

The changes you've made to the Send Connector will take effect straight
away without you having to reboot the server or restart any services.

In order to change the port to 587 you will have to issue the following
command in the Exchange Powershell Console:

Set-SendConnector -identity "NAME OF CONNECTOR" -Port:587

Afterwards restart restart the transport service and relaying should
work.

Exchange 2013
-------------

Routing all outgoing mails via the outgoing smarthost:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Ensure the IP address is added as an authorized smarthost (without
   authentication)
2. Ensure the outgoing user has correct limits set matching your traffic
   volumes
3. Update your configuration:

A Send Connector must already have been created and configured correctly
in Exchange Administration Center:

1.  Navigate to Mail Flow
2.  Select Send Connectors
3.  Add a new connector (click the + sign)
4.  Add a relevant name for this connector, Eg: SpamExpertsOutFiltering
5.  Select : Internet (For example, to send internet mail)and click Next
6.  Select Route mail through smart hosts
7.  Add the Hostname by clicking on the + sign ->Click Save
8.  Click Next
9.  If you are using an IP outgoing user leave None / If you are using
    an Authenticating user select Basic Authentication -> Input the
    Outgoing User and Password
10. Click Next
11. *Address space: - > Click the + sign and in the *\ Full Qualified
    Domain Name (FQDN): input \*
12. Click Save and Next
13. \*Source server: - Click on the + sign and select the server from
    the list
14. Click OK and Finish

You need to ensure that the port 587 is being used:

1. Open the Exchange Management Shell
2. Run the following:

 Set-SendConnector -identity "**NAME OF CONNECTOR**\ " -Port:587

MailEnable
----------

1. Using the MailEnable Administration program, Expand
   Servers\|localhost\|Connectors
2. Right click on the SMTP Connector and select Properties
3. Select the Smart host property sheet
4. Check Smart host Enabled
5. Enter the provided hostname of your SMTP server. For trials on our
   Hosted Cloud this is **smtp-trial.antispamcloud.com**
6. Ensure the port number is 587

To use the smarthost with authentication make sure you check the "*This
Server Requires Authentication*\ " box and provide the required
credentials.

Kerio
-----

1.  Ensure the IP address is added as an authorized smarthost (without
    authentication)
2.  Ensure the outgoing user has correct limits set matching your
    traffic volumes
3.  Update your configuration:

4.  Login to your Kerio Connect admin interface
5.  Expand Configuration, and click on SMTP Server, and then the SMTP
    Delivery tab
6.  Select the use relay SMTP server radio button
7.  Relay server hostname: **smtp-trial.antispamcloud.com**
8.  Relay server port: 587
9.  Be sure Relay server requires authentication is NOT checked.
10. Select the Use SSL/TLS if supported by remote SMTP server checkbox

IceWarp
-------

To configure IceWarp to be used for SpamExperts, please use the
following steps:

-  Click ***Mail***
-  Navigate to ***General*** >>  ***Delivery** *>>  ***Use Relay
   Server***
-  For "*Per Username Authentication*\ " add  
   user:pass@\ **SMARTHOST**:587
-  For "*IP based Authentication*\ " add  **SMARTHOST**:587

Please replace SMARTHOST should be the name of the smarthost server. If
you are using Hosted Cloud, then the trial Hostname is **smtp-
trial.antispamcloud.com**
