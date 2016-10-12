Outbound Spam Monitoring
========================

The filters are very effective at blocking a large percentage of
outbound spam/viruses, to prevent issues with your network reputation.
It is very important however to pro-actively suspend any spamming
customers/accounts, to stop the abuse at its source. If such accounts
are not suspended/blocked, eventually there will always be a spam run
which our engines could miss. You can prevent any such spam escalations
(or other type of attacks from abusive customer accounts), by ensuring
the account is locked down before it starts to cause real issues. Our
systems allow you to quickly and easily identify such abusive accounts,
before any third-party issues occur.

There are a number of ways that spammers can be monitored via our
systems, the best method depends per-customer.

Best practise for smarthost users:

1. Ensure all your smarthost authentication users are grouped as part of
   a single administrative domain (e.g. out.yourcompany.com)
2. Configure your sending MTA to always include an end-user
   identification header
3. Set your outgoing SpamExperts user account to use this identity
   header
4. Manually/automatically locate abusive identities and shutdown the
   main spam source (and temporarily lock down the identity via our
   identity management as an immediate measure)

Spampanel
---------

If you have administrator access to Spampanel (Local Cloud only), you
can review the blocked outgoing spam emails on the "Spam quarantine"
page in the Outgoing section as Super Administrator. Although the number
of daily spam emails you find there can be overwhelming at start, simply
spending 15 minutes a day to analyze/block the source of the most
frequent messages you can find there will quickly result in a
significant drop of overall spam traffic. This is strongly recommended
when starting to use our filtering, so your administrators can easily
pinpoint the top spam causes and get more familiar with tracking
down/blocking the spam sources.

Identification header configuration at sending MTA
--------------------------------------------------

cPanel/Exim Identification headers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

cPanel has an experimental feature for this
(http://docs.cpanel.net/twiki/bin/view/AllDocumentation/WHMDocs/EximMail#EXPERIMENTAL:
(Rewrite From: header). It does not have to be the envelope-from though,
and can be another header as well.

An example for Exim, (DirectAdmin / Cpanel), would be to add the
following line to the SpamExperts transport part:

::


        headers_add = X-AuthUser: ${if match {$authenticated_id}{.*@.*}\
         {$authenticated_id} {${if match {$authenticated_id}{.+}\
         {$authenticated_id@$primary_hostname}{$authenticated_id}}}}

Qmail Identification headers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To do this in Qmail, this requires a patch. To be able to add a
'X-Auth:' header, you need to do the following:

1. Apply qmailqueue patch: \ http://www.qmail.org/qmailqueue-patch.
2. Recompile qmail.
3. Install qmail-qfilter: \ http://www.untroubled.org/qmail-qfilter/.
4. Edit '/service/qmail-smtpd/run' and add the following line:
   export QMAILQUEUE="/var/qmail/control/filter.sh"

::


      5. Create the file /var/qmail/control/filter.sh, and make it executable and owned by the user qmail-smtpd

::

     #!/bin/sh  
    exec /usr/local/bin/qmail-qfilter /var/qmail/control/filter.pl

::


      6. Create the file /var/qmail/control/filter.pl and make it executable and owned by the user qmail-smtpd

::

     #!/usr/bin/perl  
    $usuario = $ENV{TCPREMOTEINFO};  
    print "X-Auth: $usuario\n";  
    while(<>) {  
    print;  
    }

::


      7. Restart qmail-smtpd.

    Please note, that this is unverified, and should be tested before rolling out
    to a live platform.

    ### Postfix Identification headers

    To do this in Postfix, you need to add the following line to your main.cf if
    not already there:  
      

::

     smtpd_sasl_authenticated_header = yes

::


    This will add a "Authenticated Sender" part to the received header  

    ### Zimbra Identification headers

    As Zimbra generally uses Postfix as it's MTA, you can apply the same option as
    the Postfix header above  
      

::

     smtpd_sasl_authenticated_header = yes

::


    This will add a "Authenticated Sender" part to the received header  

    ### SmarterMail Identification headers

      1. To enable the identification headers in SmarterMail, please do the following:
      2. Naviate to settings
      3. Protocol Setting
      4. SMTP Out
      5. Enable the "X-SmarterMail-Auth header" option

    ### Microsoft Exchange Identification headers

    Currently on Microsoft Exchange, to be able to add custom outgoing headers a
    XHeader transport agent must be built. For more information on how to do this
    please see their KB
    [here](https://msdn.microsoft.com/library/office/bb204064%28v=exchg.140%29.aspx)

    ## Configuring the Identity method via the Control Panel

    Once you have configured your MTA to set an "Identificaiton header", you need
    to configure the SpamExperts systems to be able to log and monitor these.  The
    easist way to do this is directly from withn the control panel. To do this
    please follow the steps below:  
      

      1. Login to your SpamExperts interface
      2. Navigate to the outgoing authenticating domain, (or for Local Cloud clients, you can also use the "**_default domain settings_**" in the outgoing section at Super Admin level - this sets it for all outgoing users that have default values)
      3. Click**_ Manage users_** in the **_Outgoing_** section
      4. Use the drop down menu at the_** Identification Method** _line, and choose "_**Header**_"
      5. Click _**Add New Header**_
      6. In the header name section add the header name that you are configuring, (for example **X-AuthUser **for Exim/cPanel)
      7. Uncheck the "**_remove after processing_**", assuming you do not want to remove this header. If you do, then you can keep this option enabled.
      8. Click **_Save_**

    If you have configured  more that one identity, then they will be processed in
    order. If both headers are in the same outgoing email, the top one will be the
    one that is processed.

      
    Once this has been set for your outgoing users, it's advised to verify some
    outgoing message in your outgoing Log Search page. Look for new messages that
    have the "User Identificatin" column. If you see data in here it is working
    correctly.  
      
    It's important to find a good identifier for your different mailstreams to be
    able to make effective use of this feature, there are other options on the
    _**Identification Method** _part, which are "**_Envelope-Sender_**" and
    "**_Authenticating User_"**. If you are not able to add an specifc outgoing
    header, we would recommend to set this to the "_Envelope-Sender_". As this
    means you will be able to continue to use the locking option (either via API
    or the Log Search) , and lock senders based on this identity instead.  
      

    ## Locking senders based on the Identity header within the Control Panel

    It is possible to lock senders based on their Identity header directly in the
    control panel. For this to work, there must first be a configured Identity. To
    lock a sender, currently you need to do this directly via the log search.
    Steps to lock a sender:  

      1. Login at domain level
      2. Navigate to Log Search
      3. Input your search criteria
      4. select "rejected" as classfication
      5. Locate sender with identity you wish to block
      6. Click the lock icon next to the identity

      
    The lock will turn blue, this indicates the identity is now locked. to unlock,
    simply re-click the lock icon.  
      

    ## Locking senders based on the Identity header via the API

    When using IP authentication, it's often needed to be able to lock specific
    senders without locking the whole IP.  This can be done by  locking senders
    via their Identification method (Envelope-sender, Authenticating User,
    Identification Header). To do this you need to execute the following API:  

::

    https://APIHOSTNAME/cgi-bin/api?call=api_lock_outgoing_identity&domain=DOMAIN&identity=bob@example.com&username=USERNAME

::


    To list the current locked users:  

::

    https://APIHOSTNAME/cgi-bin/api?call=api_list_locked_identities&domain=DOMAIN&username=USERNAME

::


    Please note, to be able to use this method, an Identification header must
    first be set as mentioned above.

      

    ## Lock & Unlock user identity script

    An exmaple user identity locking script  can be found
    [here](http://download.seinternal.com/support/lock_identity.py)  
      

::

    python lock_identity.py -h  
    Usage: lock_identity.py [options] hostname api_username [api_password]  
      
    Lock outgoing identities that are sending bad mail.  
      
    Options:  
      -h, --help            show this help message and exit  
      -n NICE, --nice=NICE  'nice' level [default: 10]  
      --unattended          run unattended (always answer 'yes')  
      -l LIMIT, --limit=LIMIT  
                            lock users over this limit [default: 50]  
      --hours-ago=HOURS     check behaviour over the last n hours [default: 2]  
      -q, --quiet           don't output anything in a successful run.  
      --client-username=CLIENT_USERNAME  
                            client username for API logging [default:  
                            lock_identity]

::


      
    An example user identity unlocking script can be found
    [here](http://download.seinternal.com/support/unlock_identity.py)  
      

::

    python unlock_identity.py -h  
    Usage: unlock_identity.py [options] hostname api_username [api_password]  
      
    Review and unlock outgoing identities.  
      
    Options:  
      -h, --help            show this help message and exit  
      -n NICE, --nice=NICE  'nice' level  
      -s SEARCH, --search=SEARCH  
                            Match only these identities  
      --client-username=CLIENT_USERNAME  
                            client username for API logging [default:  
                            lock_identity]

::


    The following example, shows how this can be run manually to check and block
    identities that have had 25 rejected messages in the last 1 hour:

::

    ~ % python lock_identity.py master.hostname.tld apiusername apipassword --hours-ago=1 -l 25
    XXX spam/virus/phish messages were sent by users with no identity.
    bob@example.com (10.0.0.1@smtp.example.com): sent 29 bad messages - Do you wish to lock this user? y

::


    To run this automatically via a CronJob for example, you can do the following:

::

    python lock_identity.py master.hostname.tld apiusername apipassword --hours-ago=1 -l 25 --unattended -q

::


    This will answer yes automatically to the locking question and not output any
    results.

    ##  
    Outbound Spam Reports via the Control Panel

    There is an option in the outgoing section to generate on-demand outgoing
    spam-reports. This can be generated per outgoing authenticating domain.  

      1. Login to the interface
      2. Click "_Outgoing reports_"
      3. In the domain field, add your outgoing authenticating domain
      4. Select the "_period_"
      5. Select the "_Classification_"
      6. Select the "_Group By"_ option.
      7. Click "_Show_"

      

    ## Outbound Spam Reports via CSV

    There is  an option to have a daily CSV report for outbound spam per outgoing
    user:  
      
    The API call to activate the daily report with spamming accounts is:  
      
    _**api_set_outgoing_report_recipient(domain, recipient='', username='') ->
    "".**_  
      
    _Set the address where the outgoing filter report should be sent to. If the
    'recipient' argument is omitted then disable this feature. Please note that
    this feature is in development and the format and content of the report are
    subject to change without our usual deprecation procedures._  
      

::

    https://MASTERHOSTNAME/cgi-bin/api?call=api_set_outgoing_report_recipient&domain=DOMAIN&recipient=RECIPIENT&username=USERNAME" 

::


      
    So this should be good for you in regards to the monitoring of outbound spam,
    and be able to see overall information. (please note , subject and body will
    not be shown here)  

    ##  
    Alternative Outbound Spam Reports via CSV based on "Identification header"

    There is another option to have a  CSV report for outbound spam per
    identification header sender that is sent every 2 hours to a specified email
    address  
      
    The API call to activate the daily report with spamming accounts is:  
      
    _**api_set_outgoing_report2_recipient(domain, recipient='', username='') ->
    "".**_  
      
    _Set the address where the outgoing filter report should be sent to. If the
    'recipient' argument is omitted then disable this feature. Please note that
    this feature is in development and the format and content of the report are
    subject to change without our usual deprecation procedures._  
      

::

    https://master.hostname/cgi-bin/api?call=api_set_outgoing_report2_recipient&domain=DOMAIN&username=USERNAME&recipient=RECIPEINT

::


    The report will contain counts of blocked spam per Identification and counts
    of invalid senders.  For example:  
      

::

    "Authentication Domain","Authentication User","User Identification","Spam Count","Invalid Sender Count"  
    example.com,,bob@example.com,100,0  
    example.net,,example.net,235,301  
    example.org,,example.org,0,2000

::


      
      
      

    ## IMAP quarantine access

    Rather than using any of the scripts, or the Spampanel webinterface, you can
    simply authenticate with your "global" administrator account (Local Cloud
    only) using any IMAP compatible email client for real-time access to the spam
    quarantine. Please contact our support in case you do not have the "global"
    credentials yet.  
      

    ### Global quarantine reporting script

    Rather than using Spampanel or direct IMAP quaratine access to review the
    quarantine, this is a simple script that will parse the outbound IMAP
    quarantine. (Local Cloud Only)  
      
    You can download this here:  
      
    <http://download.seinternal.com/tools/retrieve_quarantine_info.py>  
      

::

    Usage: retrieve_quarantine_info.py [options]  
       
     Output a list of quarantined outgoing messages.  
       
     Options:  
     -h, --help show this help message and exit  
     -c, --csv saves output to csv file  
     -d, --display displays the loglines as they pass by  
     -i, --incoming search the incoming quarantine  
     -o, --outgoing search the outgoing quarantine  
     -t, --today load results from today (otherwise yesterday)  
     -s IMAPHOST, --imaphost=IMAPHOST  
     The hostname of the imap server  
     -u IMAPUSER, --username=IMAPUSER  
     The username to check, usually 'global'  
     -p IMAPPASS, --password=IMAPPASS  
     The password for the 'global' user  
     -n, --no-bounce filters out mail originating from 'mailer-daemon'

::


      
    Please make sure you run this from a NON FILTERING server only. This will
    retrieve the quarantined messages either in an on screen format or saved to a
    csv.  
      
    For example you could do something like this:  
      
    $./retrieve_quarantine_info.py -d -o -n -s MASTERHOSTNAME  
      
    This will display on screen the messages that have been quarantined outbound
    in the last hour. You will be prompted for a "Global" password.  This is given
    out only on request. If this is requried please contact
    [support@spamexperts.com](mailto:support@spamexperts.com) for more details.  
      
    This will show you something like this:  
      

::

    $./retrieve_quarantine_info.py -d -o -n -s MASTERHOSTNAME (or quarantine server if applicable)   
     Please enter the password for the IMAP account 'global'.  
     Password:   
     #,From,To,Reply-To,Qmail UID,Invoked for,IP/Username,Evidence,PHP script,Auth.sender,Auth-User,Auth-Email  
     1,--DATA WILL BE HERE--   
     2,--DATA WILL BE HERE--   
     3,--DATA WILL BE HERE--   
     4,--DATA WILL BE HERE--   
     5,--DATA WILL BE HERE--   
       
     

::


    Here you can see the information on the blocked messages and some relevant
    details.  
      
    Alternatively it may be easier for you not to display the data and save it to
    a csv file, then you can open it in any excel like program and sort it on the
    specific field to group the data.  
      
    This should then give you a better idea of some of the clients that you can
    close down for spamming.  
      

    ## Using the Log Search API

    It's possble to use the api_find_outgoing_messages to be able to get for
    example a list of the top 50 spammers in X amount of time. A simple bash
    example can be seen below  

::

    curl -k -s "https://user:pass@master.hostname/cgi-bin/api?call=api_find_outgoing_messages&domain=DOMAIN&from_date=`date -d '12 hours ago' +'%s'`&to_date=`date +%s`&predicate=and&partial=False&sort_field=datestamp&classification=oversize%2Cblacklisted%2Clocked%2Cphish%2Cvirus%2Cspam%2Cdeferred&include_in_progress=False&id=&subject_header=&api_language=en&columns=sender" | sort | uniq -c | sort -nr | head -50

::


      
    It's also then possible to start automating actions. For example, you can use
    2 API's 'api_find_outgoing_messages' and 'api_blacklist_outgoing_sender' to be
    able to query the log API to find senders that have sent X amount of messages
    in X amount of time, and then take a further action. The example below shows a
    simple way to check the outgoing logs for the last 24 hours, and if the sender
    has sent more than 2000 messages then blacklist the sender.  

::

    curl -s -k "https://user:pass@master.hostname/cgi-bin/api?call=api_find_outgoing_messages&domain=DOMAIN&from_date=`date -d '12 hours ago' +'%s'`&to_date=`date +%s`&predicate=and&partial=False&sort_field=datestamp&include_in_progress=False&columns=sender" | sort | uniq -c | grep "@" | sort | awk '{if($1==$1+0 && $1>2000)print $2}' | xargs -I{} curl -k -s "https://user:pass@master.hostname/cgi-bin/api?call=api_blacklist_outgoing_sender&domain=DOMAIN&sender={}'

::


      
    While these are very basic examples, our API is very versatile, so these can
    be ammended or changed to suit your exact needs, for example, by locking
    specific senders based on the identification headers or more.  

    ## Blacklisting outbound senders via the API

    To be able to blacklist an outgoing sender, you need to use the API :  

::

    https://APIHOSTNAME/cgi-bin/api?call=api_blacklist_outgoing_sender&domain=DOMAIN&sender=SENDER&username=USERNAME

::


    To list the current blacklisted senders:  

::

    https://APIHOSTNAME/cgi-bin/api?call=api_get_outgoing_sender_blacklist&domain=DOMAIN&username=USERNAME

::


    Please note, to be able to use this method, you will always need to set the
    domain and username. This should be the outgoing authenticating user.

      

    ## Mass outbound message removal from outbound delivery queue

    Often it's needed to mass remove messages from the outgoing delivery queue
    (for example when ARF reports). This can already be done using the Interface
    and API, however we also have an open source script that can help facilitate
    this. This can be downloaded
    [here](http://download.seinternal.com/tools/queue_remove_emails.py). This
    script must NOT be run from a SpamExperts filtering server, and shoudl be run
    externally using the API credentials  
      
    Usage:  
      

::

    python queue_remove_emails.py   
      
    Please specify the API server hostname and your API username!  
      
    Usage: queue_remove_emails.py [options]  
      
    Options:  
      -h, --help            show this help message and exit  
      -f SENDER, --from=SENDER  
                            find and remove messages from the specified sender  
      -t RECIPIENT, --to=RECIPIENT  
                            find and remove messages from the specified recipient  
      -s SERVER, --server=SERVER  
                            API server hostname  
      -u USERNAME, --username=USERNAME  
                            API username

::


      
      
    An example, would be:  
      

::

    python queue_remove_emails.py -f bob@example.com -s master.hostname -u admin



ARF reports
-----------

A report that will be sent each time an outgoing spam message is
blocked, and will contain a copy of the original message including
headers.

Information on this and how to set up the ARF reports can be found here:

`https://my.spamexperts.com/kb/357/Abuse-Reporting-Format-ARF.html <https://my.spamexperts.com/kb/357/Abuse-Reporting-Format-ARF.html>`__
Many larger companies already process such ARF reports originating from
external sources such as AOL. You can simply set your administrator
address to point to your existing ARF parsing infrastructure, so your
existing abuse handling systems automatically receive and process our
datafeeds.

ARF parser
~~~~~~~~~~

If you do not have an ARF parser yet, we definitely recommend to setup a
system to handle your incoming ARF reports. We can recommend the free
opensource software \ `Abuse.IO <https://www.abuse.io/>`__ for this.

Alternatively you can e.g. use a simple python file that can parse the
contents of the ARF reports. Your sysadmins will know how best they can
utilize this and parse the data that they need. This can be found here:
`http://download.spambrand.com/arf\_parser.py <http://download.antispamcloud.com/arf_parser.py>`__\ Using
ARF automation also allows you to accept ARF feed from third-parties, to
further improve your abuse handling and to deal with abuse that does not
(yet) use our outgoing filter.
