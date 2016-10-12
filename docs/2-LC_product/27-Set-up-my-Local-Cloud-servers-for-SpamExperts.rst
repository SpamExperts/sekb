Set up my Local Cloud servers for SpamExperts
=============================================

Setup Requirements
------------------

General Setup Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~

**HDD**: As processing email involves a lot of small read/writes, we
recommend fast storage.

**Virtualization**: Servers can be virtual. Check the `Virtualization
article <https://my.spamexperts.com/kb/138/Virtuozzo-or-OpenVZ-container-virtualization.html>`__
for more information.

**Root Access**: For the installation to work smoothly, direct SSH root
access to the default port (22) is required. No changes should be made
to the Debian default settings. SpamExperts will handle securing the
setup after the access details have been received.

**No external firewall should be active**: we already run a firewall
locally on the systems, and fully protect all services. No external
firewall should be active as this may interfere with the software. The
security is fully managed by SpamExperts, and we welcome any security
audit after the setup of the environment has completed.

**Software management**: SpamExperts will take full care of the software
management on the cluster. Customers should not change the configuration
of the OS / software (except for the networking settings).

**Load Balancing**: Round Robin DNS setup is recommended, for more
information check the following
`article <https://my.spamexperts.com/kb/753/Local-Cloud-MX-Records.html>`__.

**Recommendations**

Hard drives in RAID1 at least on the master/quarantine/logging server
for redundancy.

When choosing the disk size for the quarantine/logging server (generally
the master), take into account that the larger the available disk space
the more days you can store quarantine/logging data. This data can
optionally be stored on a secondary mountpoint.

Minimum Hardware Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The minimum requirements are as follows:

-  Two CPU Cores
-  CPU >= 1.8 GHz
-  4096MB RAM
-  80GB Diskspace (for the logging/quarantine role more disk space is
   recommended)
-  Storage type in order of preference:

1. SSD
2. SAS
3. SATA

Network Requirements
~~~~~~~~~~~~~~~~~~~~

-  A non-firewalled internet connection (or all `required
   ports <https://my.spamexperts.com/kb/37/Firewall-Usage.html>`__
   opened)
-  Each servername must resolve to one IPv4 (the primary server IP), and
   optionally in addition 1 IPv6 address (the primary server IPv6)
-  The primary IP of each server must have the reverse DNS set to the
   server hostname
-  All communication should be possible over the external IPs (in case
   of NAT), also communication between the servers in a SpamExperts
   setup.
-  Server hostnames must not be used as MX record hostnames, as they
   will be visible in the email headers and cannot be changed without a
   reinstallation. Instead, you can use separate MX record hostnames to
   easily control the mailflow.

Network Address Translation (NAT)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Please note we strongly recommend against using NAT, as from our
experience clients often experience issues with their NAT setup. Issues
with a wrongly set up internal networking are not supported. When using
the SpamExperts solution behind a Network Address Translation (NAT)
system you need to ensure the following requirements are met in full:

1. The server should only communicate on its primary external IP address
   that the server hostname is pointing to regardless of destination.
2. Servers should be able to communicate with each other on their
   external IP addresses.
3. The source IP address of connections made between servers should be
   the external primary IP address.
4. Hostnames must not resolve internally to private IP addresses.

Be Advised: Our solution is fully compatible with a NAT system when
properly configured. If you have any questions, please contact our
`support team <mailto:support@spamexperts.com>`__.

Operating System Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  Debian Linux (latest stable release) minimal installation with
   OpenSSH-Server, 64bit
-  Installation on a single partition (no separate partitions for /home,
   /boot etc). Only separate partition for swap.
-  There is no custom software installed
-  SSH is remotely accessible with the root user on port 22 (this will
   be secured by SpamExperts as part of the setup)

Debian server setup
-------------------

In order to use SpamExperts Local Cloud, you have to install the Debian
Linux distribution on your server. We support the latest `Debian stable
64bit <https://www.debian.org/releases/stable/>`__ operating system.

You can acquire the minimal required package from the official Debian
website:

-  Go to the `download
   page <https://www.debian.org/releases/stable/debian-installer/>`__
-  Download the amd64 "netinst CD image"

Note: Even though the 64-bits filename includes "AMD64", don't worry
about this as it will still work under 64 Bits Intel CPUs.

Please note that the screenshots below were made with Debian 5, but the
steps should (roughly) be the same.

Add SSH Keys for Passwordless SSH Connection
--------------------------------------------

After the Debian setup is completed, you need to add SSH Keys for the
SpamExperts Setup Operators in order to connect via SSH to your
SpamExperts server without a password.

To enable this, just run the following command in a terminal:

::


        wget https://download.seinternal.com/install/init.sh && bash ./init.sh

Manually installing Debian
--------------------------

If you have to install Debian yourself, simply boot your server with the
latest stable Debian ISO mounted or burned to a CD.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg01.png
   :alt: 

If your BIOS settings are correct to boot from the Debian CD, you'll see
the menu in the screenshot above displayed . Select the option "Install"
to start the Debian installation process.

Choose Language
~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg02.png
   :alt: 

Select English for the default system language.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg03.png
   :alt: 

Select the representative country/territory or area in question. In this
case we're in The Netherlands, which is located under Other.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg04.png
   :alt: 

Select the corresponding continent or region which the desired country
is located, for instance Europe.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg05.png
   :alt: 

Select the country, territory or area in question. For instance: The
Netherlands.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg06.png
   :alt: 

Pick the correct keymap. This should probably be American English

Network Setup - Part 1
~~~~~~~~~~~~~~~~~~~~~~

It's time to configure the network settings. If your server does not get
an IP address automatically assigned via DHCP, there are a few extra
steps to take. If you're using DHCP, you can skip the first part of the
Network Setup and continue with the second part.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg07.png
   :alt: 

You'll get a nice "warning" that the server couldn't reach the DHCP
server. No problem, since it will present an option to setup a static IP
address.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg08.png
   :alt: 

Select Configure Network Manually.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg09.png
   :alt: 

Enter the IP address of the server.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg10.png
   :alt: 

Enter the subnet address.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg11.png
   :alt: 

Enter the gateway address.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg12.png
   :alt: 

Finally, it's time to enter the nameservers. If you have more than one,
you can enter them in this field as well by separating the entries with
a **space**. There is a maximum of 3 nameservers.

Network Setup - Part 2
~~~~~~~~~~~~~~~~~~~~~~

In the previous step you either let the server acquire an automatic IP
address using DHCP or you've set it up manually by giving it a static
IP. Either way, this second part is the same for both static and dynamic
IP addresses.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg13.jpg
   :alt: 

First enter the hostname of the server. This could be something such as
**“server1.example.com”** if this is the first spamfilter.

Please note that the server hostnames will need to be **FQDN** that have
an **A record** pointing to the **primary IP address** of the server and
should not be used for the MX records of your domains.

Partitioning
~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg14.png
   :alt: 

Choose for Guided - Use entire disk.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg15.png
   :alt: 

Choose the hard disk you want to install the system on. This is probably
the first, and maybe the only one in the list.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg16.png
   :alt: 

Pick the first option: **All files in one partition**.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg17.png
   :alt: 

Hit **Finish partitioning and write changes to disk** to wrap things up.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg18.png
   :alt: 

If you're sure to apply the partitioning scheme selected earlier, select
Yes. Be aware that already existing partitions will be removed, thus
wiping out all data.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg19.png
   :alt: 

The system is now partitioning the selected hard disk.

Installing base system
~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg20.png
   :alt: 

The system is now installing the base system.

Set up users and passwords
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg21.png
   :alt: 

You need to setup a password for root. We suggest you generate a strong
password in order to make the system more secure. You could use a random
password generator to create one. Do not forget this password, since
this is something you have to give to support in order to finish the
installation process. Please note that the root password must be ASCII
characters.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg22.png
   :alt: 

Confirm the password.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg23.png
   :alt: 

The setup requires you to add a user to the system. This value should be
*maint*.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg24.png
   :alt: 

This value is identical to the previous step.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg25.png
   :alt: 

This user requires a password. It doesn't matter what you enter since
this user is going to be deleted.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg26.png
   :alt: 

Confirm the password.

Configure the Package Manager
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg27.png
   :alt: 

To receive updates, the setup asks you to select the nearest country. In
this case, we select The Netherlands since that is where our server is
located.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg28.png
   :alt: 

Select a mirror, this can be anyone you'd like. In this example we chose
the official Debian mirror atftp.nl.debian.org.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg29.png
   :alt: 

If a proxy is required for accessing the internet (which is fairly
unlikely) you can enter its settings here.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg30.png
   :alt: 

Select "No" when asked to join the "Popularity Contest".

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg31.png
   :alt: 

Deselect all items that have been selected automatically. This is an
important step, because the default settings include a "Desktop System"
which we don't need (or want). The only option you should select is
**Standard system**.

Installing the bootloader
~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg32.png
   :alt: 

In order to make the system boot correctly, a bootloader should be
installed. Select Yes when asked if you want to install GRUB to the
master boot record.

When the installation is finished the server reboots. Don't forget to
remove any CD/DVD or ISO image from the system and make sure the Boot
Sequence is set-up correctly. If all goes well, you should see your
freshly installed Debian system.

Reboot
~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg33.png
   :alt: 

You'll be presented with the "GRUB Bootloader". The system should
continue automatically, but if it doesn't, select the option without
"Single User Mode" and press Enter.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg34.png
   :alt: 

During the boot process you will see a lot of information. Afterward you
will be presented with a text based login prompt. You should login with
root as username and the earlier configured root password.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg35.png
   :alt: 

In order to be able to access your server to finish the rest of the
setup, you should install **openssh-server**. This can be done by
entering:

::


        apt-get install openssh-server

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg36.png
   :alt: 

You will be presented with a request for confirmation, Type Y and press
enter. OpenSSH-Server will now be installed and configured.

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg37.png
   :alt: 

OpenSSH-Server is now installed and has been started.

Removing the "maint" user
~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://dev.spamexperts.com/sites/default/files/images/debinstallimg38.png
   :alt: 

Earlier in the setup you were asked to create a user. Because we don't
need/use this user, it should be deleted. You can do this by entering:

::


        userdel maint

If you used a different username than the suggested maint, replace the
**maint user**\ in command with the correct username.
