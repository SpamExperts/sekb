.. _2-Monitoring:

Monitoring
==========

We constantly monitor the software on your Local Cloud servers. Any
issues related to hardware/resources/networking are not covered in this
article.

Update and maintenance period
=============================

SpamExperts releases a new software build every Tuesday around 12:30
CET. As Super Administrator, you can schedule the weekly update day/time
of your Local Cloud on the **"Server"** > **"Settings"** page.

.. figure:: /_static/images/updatetime-serversettings.jpg
   :alt: 

We keep interruptions during the update process at minimum, and they
will never result in loss of email, at worst email delivery is slightly
delayed.

Unexpected problems
===================

Whenever a software problem is detected, our engineers are automatically
notified and will investigate the problem.

Usually software issues are resolved during the next update and
maintenance period. If a software issue is detected that requires
immediate intervention, the problem will be directly resolved. Also if
problems have occurred to live services (such as the API, webinterface,
or quarantine), we will inform you via email.

If you would detect any issues with your servers, please always contact
us first at support@spamexperts.com before taking any actions. Also
ensure to always send an email before you phone, so our engineers can
handle your case optimally.

Load
====

It is important to have hardware resources (virtual) available at all
times, as we have no control over the availability of your resources.

Disk I/O throughput, available disk space, memory, and CPU resources all
affect the system load. Whenever the load would become too high on
average, please ensure to increase the available resources (either on
the existing servers or by adding more servers to the Local Cloud
setup). If you like to receive further details on the resource
bottleneck, please `contact our
support <mailto:support@spamexperts.com>`__ in order to analyze your
system.

Network/hardware problems
=========================

Customers are responsible for keeping their hardware and networks
operational, as such issues are not covered by our support due to the
hardware and network ownership. If any problems occur, the
**“maintenance mode”** will be triggered until they are resolved.

Always inform us 3 days prior any scheduled maintenance.

SNMP
====

Although you are officially not allowed to make any changes to the
software on the machine, it is not uncommon for customers to run the
SNMP daemon. This will not affect the SpamExperts monitoring. You can
`request <support@spamexperts.com>`__ our support to install the daemon.

We advise customers to monitor their server resources by querying the
Software API and retrieve the status of all resources/systems.

Using Nagios
============

It's possible to monitor your SpamExperts systems directly via a Nagios
monitoring system. Read more about our open-source script available
:ref:`here  <3-Nagios-Plugin-Script>`.

Monitoring your servers via the Software API
============================================

For monitoring purposes you can use our Software API. There are 2 API
calls available depending on what kind of format suits your
requirements:

::


        https://API_USER:API_PASS@MASTER_HOSTNAME/cgi-bin/api?call=api_get_server_status

::


        https://API_USER:API_PASS@MASTER_HOSTNAME/cgi-bin/api?call=api_get_json_server_status

Example usage:

1. Add a new Software API monitoring user from **Control Panel menu** ->
   **Server** -> **Software API users**
2. On your monitoring server create a cron script to call our API and
   feed the data to the monitoring software.

::


        curl -k "https://API_USER:API_PASSWORD@MASTER_HOSTNAME/cgi-bin/api?call=api_get_server_status"

Example on how to call the API in Bash:

You can find more information and description of these calls, including
what data they return, in the API help documentation at:

::


        https://API_USER:API_PASSWORD@MASTER_HOSTNAME/cgi-bin/api?call=api_help

An example script for monitoring “load avg1” across all the cluster's
servers. The data can be sent to your monitoring server.

::


        #!/bin/bash
        
        curl -k https://API_USER:API_PASSWORD@MASTER_HOSTNAME/cgi-bin/api?call=api_get_server_status | while read line; do
            data=( `echo $line | sed 's/,/ /g'` )
            echo HOSTNAME: ${data[0]} LOAD AVG1: ${data[1]}
        done
        

24x7 premium support contract
=============================

Clients with a 24x7 premium support contract receive extended
monitoring. Please `contact us <support@spamexperts.com>`__ for more
details.
