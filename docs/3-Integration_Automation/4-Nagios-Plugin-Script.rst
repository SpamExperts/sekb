Nagios Plugin Script
====================

Using Nagios Monitoring with the API
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

As SpamExperts prohibits the use of the NRPE (*Nagios Remote Plugin
Executor*) on the Local Cloud installation, it is still possible to use
our API and a custom script to monitor the servers for certain services
and statuses.

All that we require is PHP on the Nagios monitoring server and a
Software API user with the correct credentials for the specific calls
you want to monitor. In this example we will use the
"api_get_json_server_status" call.

Steps to install
~~~~~~~~~~~~~~~~

-  Download the php script
   `here <http://download.spambrand.com/check_spamexperts.php.txt>`__
   and save it on your Nagios monitoring server at
   **/usr/local/nagios/libexec/**. (locations may vary)
-  Add the following code to the  commands file
   **/usr/local/nagios/etc/objects/commands.cfg** (locations may vary)

::


        define command{  
        command_name check_spamexperts  
        command_line php $USER1$/check_spamexperts.php -n $HOSTNAME$ -H api.domain.ext -u apiuser -p apipassword -w load5warninglevel -c load5criticallevel -i max_incoming_queue -o max_outgoing_queue  
        }

-  create a **host.cfg**

::


        define host{  
        use generic-host ; Name of host template  
        host_name node1.domain.ext  
        alias Spamexperts spam cluster  
        address 1.2.3.4  
        check_command check-host-alive  
        contact_groups critical-admins  
        max_check_attempts 20  
        notification_interval 60  
        notification_period 24x7  
        notification_options d,u,r  
        }  
        define host{  
        use generic-host ; Name of host template  
        host_name node2.domain.ext  
        alias Spamexperts spam cluster  
        address 1.2.3.5  
        check_command check-host-alive  
        contact_groups critical-admins  
        max_check_attempts 20  
        notification_interval 60  
        notification_period 24x7  
        notification_options d,u,r  
        }

-  Create a **services.cfg**

::


        define service {  
        use generic-service  
        host_name node1.domain.ext,node2.domain.ext  
        service_description spamexperts  
        is_volatile 0  
        check_period 24x7  
        max_check_attempts 3  
        normal_check_interval 5  
        retry_check_interval 1  
        contact_groups critical-admins  
        notification_interval 240  
        notification_period workhours  
        notification_options w,u,c,r  
        check_command check_spamexperts  
        }

-  edit the **nagios.cfg **\ file to include these new configuration
   files.

::

    cfg_file=/usr/local/nagios/etc/objects/host.cfg
    cfg_file=/usr/local/nagios/etc/objects/services.cfg


- Restart Nagios.
