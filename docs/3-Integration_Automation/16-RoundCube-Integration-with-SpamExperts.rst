.. _3-RoundCube-Integration-with-SpamExperts:

RoundCube Integration with SpamExperts
======================================

SpamExperts customers can report emails as spam or not spam directly
from their RoundCube webmail account by employing the
`MarkAsJunk2 <https://plugins.roundcube.net/packages/johndoh/markasjunk2>`__
plugin. Please note this integration is not maintained by SpamExperts,
please let us know if you have further documentation improvements.

Install the Plugin
==================

To install the MarkAsJunk2 plugin follow these steps:

1. Go to the RoundCube plugins folder and download the
   `MarkAsJunk2 <https://plugins.roundcube.net/packages/johndoh/markasjunk2>`__
   plugin.
2. Edit configuration file - **config/config.ini.php**
3. Add the name of the plugin in that file, by using the following
   example:

::


        $config['plugins'] = array('MarkAsJunk2');

To disable the plugin, just remove that line from the configuration
file.

For more information check this `wiki
page <https://github.com/roundcube/roundcubemail/wiki/Plugin-API#installing-%20plugins-and-activating-plugins>`__
from RoundCube on how to install plugins.

Configure the Plugin with SpamExperts
=====================================

For the integration to work, you have to properly configure it, as
follows:

The first step is to rename the configuration file from
**"config.inc.php.dist"** to **"config.inc.php"**\ and open it with your
text editor/IDE.

Now you have to enable the email learning driver by editing the
**"config.inc.php"** file. Set the **"markasjunk2\_learning\_driver"**
option to **"email\_learn"**. After that, define the email addresses
where spam and legitimate emails marked as spam are reported to.
|image0|

SpamExperts has 2 special central reporting email addresses you can use,
which will (from the email headers) automatically process the reports
related to the user/domain/cluster that processed the emails (this is
identified from the email headers).

For reporting spam:

::


        $config['markasjunk2_email_spam'] = 'spamreport@spamrl.com';

For reporting legitimate emails (ham):

::


        $config['markasjunk2_email_ham'] = 'notspamreport@spamrl.com';

.. figure:: /_static/images/roundcube-conf2.png
   :alt: 

In the same file you can also specify if the email should be sent as an
attachment or what email subject should contain, by using the the
following:

::


        $config['markasjunk2_email_attach'] = true;

::


        $config['markasjunk2_email_subject'] = 'RoundCube report (%t)'; *

-  “%t” replaces the subject with the type of message (spam/ham)

For more information check the plugin’s GitHub
`repository <https://github.com/JohnDoh/Roundcube-Plugin-Mark-as-Junk-2/>`__.

.. |image0| image:: /_static/images/roundcube-conf1.png
