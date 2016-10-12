.. _3-DirectAdmin-addon:

DirectAdmin addon
=================

About
~~~~~

SpamExperts Module For DirectAdmin is a module which allows you to
manage SpamExperts account directly from your DirectAdmin.

**Features:**

-  Module Configuration:

   -  Automatic Adding Of New Domains To SpamFilter
   -  Automatic Deletion Of Domains From SpamFilter
   -  Automatic Switching Of Domains MX Records
   -  Processing Domain Pointers
   -  Using Existing MX Records For Domains
   -  Protecting Remote Domains
   -  Adding Domain To The SpamFilter During Login (If It Does Not
      Exist)

-  Checking Filter Status For Domain
-  Toggle Protection For Domain
-  Log Into Domain SpamExperts Account
-  Enabling/Disabling Protection For Group Of Domains
-  Bulk Protection
-  Simple Update
-  Collecting Basic Information About Environment
-  Run Diagnostics Action
-  Reseller Access (Only Domain List Tab With Domains Of His Users)
-  User Access (Only Domain List Tab With His Domains)

**Additionally:**

-  Supports DirectAdmin 1.43.3 And Later
-  Supports PHP 5.4 And Later

Installation and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this section we will show you how to properly install and configure
your SpamExperts Module For DirectAdmin.

In order to proceed you should remove ‘exec’ from the disable\_functions
in your php.ini

| 1.
  `Download <http://download.seinternal.com/integration/files/directadmin/latest.tar.gz>`__
  and unpack SpamExperts Module For DirectAdmin.
| 2. Edit directadminapi.conf.new file as shown on the following screen
  and fill it with your DirectAdmin IP address, used port and API access
  details. Additionally, type 1 next to secure= if your API connection
  uses SSL.
| |Fig. 1: directadminapi.conf.new file|
| 3. Pack files and folders as presented on the following screen into
  .tar.gz format. **ATTENTION! The name you're going to use for the
  .tar.gz package will be used as the module ID and if you already have
  a module with such name the existing module's files will be destroyed
  by DirectAdmin's Plugin Manager. Please select a unique name!**
| |Fig. 2: SpamExperts Module For DirectAdmin files.|
| 4. Log in to your DirectAdmin and go to the Home tab.
| 5. In order to proceed, enter Plugin Manager under Extra Features
  category.
| 6. Afterwards, mark File checkbox and select a module pack by pressing
  Browse... button. Fill Password field with your password, mark Install
  after upload checkbox and press Add Plugin button.
| |Fig. 3: Add Plugin form at DirectAdmin panel.| 7. In the next step
  you need to set up a connection to the Spam Experts API. To do so, go
  back to Home tab and enter Professional Spam Filter under Extra
  Features category.
| 8. Switch to Configuration tab and fill the fields underlined on the
  screen below. Afterwards, press Save Changes button.
| |Fig. 4: SpamExperts Module For DirectAdmin, Configuration tab.|
| Congratulations! You have just finished the installation and
  configuration of the module.

Management
~~~~~~~~~~

Now we will show you how to manage your SpamExperts Module For
DirectAdmin. You can do this in Management section.

**Configuration**

| You can adjust the operation of the module at Configuration tab. As
  you can see on the following screen, the tab contains checkboxes owing
  to which you can easily configure the module and adapt its work to
  your own needs.
| |Fig. 5: Configuration of SpamExperts Module For DirectAdmin at
  Configuration tab.|

**Branding**

| You can adjust the module's branding at Branding tab. As you can see
  on the following screen, the tab contains information about current
  branding and it is possible to set up your own brand name and upload a
  custom logo.
| |Fig. 13: Branding configuration of SpamExperts Module For
  DirectAdmin.|

**Domain List**

| At Domain List you can view and manage all the domains. You can check
  whether they are present in the spam filter, toggle protection and log
  in to each spam filter account with just one click.
| |Fig. 6: Domain List tab with marked single domain actions.|

| Additionally, you can enable/disable protection to group of domains.
  To do so, simply mark checkboxes next to domains you wish to
  protect/unprotect and press Protect Selected/Unprotect Selected
  button.
| |Fig. 7: Domain List tab with marked group action available for
  domain.|

**Bulk Protection**

| Bulk Protection tab allows you to synchronize all (or depending on
  settings, only specific) domains existing on your DirectAdmin server
  with SpamExperts server. To start the synchronization process, press
  Execute bulkprotect button.
| |Fig. 8: Bulk Protection tab of SpamExperts For DirectAdmin module.|

As soon as you press the button, synchronization process will start. We
respect value of your time, therefore we implemented estimated time
counter that will show you estimated time needed to finish the
synchronization.

**Update**

| Our module allows you to easily update it to the latest version. To do
  so, simply go to Update tab and press Click to update button.
| |Fig. 9: Update tab.|

| Afterwards, mark checkbox next to your SpamExperts Module For
  DirectAdmin, fill password field and press Update button.
| |Fig. 10: Plugin Manager with module ready to update.|

**Support**

| To shorten time needed by our Support Team to solve your problems with
  the module, we created the Support tab. It contains most of
  information that our Support Team may need. Additionally, in this
  section you can run module diagnostics that quickly checks environment
  configuration as well as connection to both DirectAdmin and
  SpamExperts APIs.
| |Fig. 11: Support tab|

**Limited Access For Resellers & Users**

| Access to SpamExperts Module For DirectAdmin for your resellers and
  users is restricted only to Domain List tab as shown on the following
  screen. Resellers will see only domains of their users while users
  will see only their own domains here.
| |Fig. 12: Resellers & users access to plugin.|

Tips
~~~~

1. It is possible that you will receive a following output during the
module installation:

::


        Adding hooks to DirectAdmin
        WARNING! - hook file .sh already exist
        WARNING! - hook file .sh already exist
        WARNING! - hook file .sh already exist
        WARNING! - hook file .sh already exist
        Plugin Installed! 

This warning is caused by attempt to install hook files which already
are installed. Its occurrence is not dangerous and will not disturb the
correct operation of the module. All required files are located on the
server so your module will run smoothly and seamlessly.

2. If you will receive a following error at Configuration tab of our
addon:

::


        Configuration file configuration.conf is not writable by the current user

Then you need to modify permission of configuration file. To do so, log
in to your DirectAdmin server via SSH, cd to
\_/usr/local/directadmin/plugins/ **Click on Professional Spam Filter**
> Go to the **Support** tab and notice the path to the debug logs.

::


        /usr/local/directadmin/plugins/PLUGINNAME/logs/prospamfilter_admin.log

::


        /usr/local/directadmin/plugins/PLUGINNAME/logs/prospamfilter_root.log

2. To activate **debug logs**, first login via SSH to your DirectAdmin
server and go to your plugin root directory, which should be the
following and create a file named **"debug"**:

::


        $ cd /usr/local/directadmin/plugins/PLUGINNAME/

::


        $ touch debug

Now the debug logs are enabled and you can check them in the
**“prospamfilter\_admin.log”** and **“prospamfilter\_root.log”** files.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/direct-admin-debug-ssh.png
   :alt: 

To check the logs just issue the following commands:

::


        $ cd /usr/local/directadmin/plugins/PLUGINNAME/logs/

::


        $ ls -l

::


        $ cat prospamfilter_admin.log

::


        $ cat prospamfilter_root.log 

To disable the debug logs, remove the **"debug"** file from the root
directory, by issuing the following commands:

::


        $ cd /usr/local/directadmin/plugins/PLUGINNAME/

::


        $ rm debug

Be Advised: As this feature should only be enabled when you are
experiencing issues with our DirectAdmin addon, we recommend to enable
it only when needed, as the debug logs a lot of information to the log
files and can consume valuable resources if it’s kept enabled all the
time.

.. |Fig. 1: directadminapi.conf.new file| image:: https://dev.spamexperts.com/sites/default/files/pictures/direct-admin-%20api-conf.jpg
.. |Fig. 2: SpamExperts Module For DirectAdmin files.| image:: https://dev.spamexperts.com/sites/default/files/pictures/direct-admin-%20filelist.jpg
.. |Fig. 3: Add Plugin form at DirectAdmin panel.| image:: https://my.spamexperts.com/images/kb/direct/3fu6.png
.. |Fig. 4: SpamExperts Module For DirectAdmin, Configuration tab.| image:: https://dev.spamexperts.com/sites/default/files/images/nzmw.png
.. |Fig. 5: Configuration of SpamExperts Module For DirectAdmin at Configuration tab.| image:: https://my.spamexperts.com/images/kb/direct/r8gr.png
.. |Fig. 13: Branding configuration of SpamExperts Module For DirectAdmin.| image:: https://dev.spamexperts.com/sites/default/files/images/FIuDKw.png
.. |Fig. 6: Domain List tab with marked single domain actions.| image:: https://dev.spamexperts.com/sites/default/files/images/cprg.png
.. |Fig. 7: Domain List tab with marked group action available for domain.| image:: https://dev.spamexperts.com/sites/default/files/images/yjzj.png
.. |Fig. 8: Bulk Protection tab of SpamExperts For DirectAdmin module.| image:: https://dev.spamexperts.com/sites/default/files/images/direct-admin-bulk-protect.jpg
.. |Fig. 9: Update tab.| image:: https://dev.spamexperts.com/sites/default/files/images/9kzn.png
.. |Fig. 10: Plugin Manager with module ready to update.| image:: https://my.spamexperts.com/images/kb/direct/4ajy.png
.. |Fig. 11: Support tab| image:: https://dev.spamexperts.com/sites/default/files/images/direct-admin-support.jpg
.. |Fig. 12: Resellers & users access to plugin.| image:: https://my.spamexperts.com/images/kb/direct/jtp6.png
