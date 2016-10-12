.. _2-Get-started-with-the-Local-Cloud:

Get started with the Local Cloud
================================

Prerequisites
=============

In order to have the Local Cloud software deployed on your servers, you
need to ensure the following steps have been covered:

1. **Trial** - The trial step is purely optional. Once you register for
   the Local Cloud trial, you don’t have to register again for
   installation. See more information about starting a Local Cloud trial
   :ref:`here  <2-Start-a-Trial-with-Local-Cloud>`.
2. **Register** - You have to create a SpamExperts account in order to
   place your order and proceed to the next steps. Click
   `here <https://my.spamexperts.com/register.php>`__ to Register. This
   step is mandatory in case you haven’t registered already by setting
   up a Local Cloud trial (step 1).
3. **Place an order for the Local Cloud filtering service** - On this
   step you will go to **Client Area > Order > and Request a Quote**. A
   billing ticket will be submitted. Please contact
   `sales <sales@spamexperts.com>`__ to ensure your billing request has
   been processed and receive confirmation of it.
4. **Fill in the Local Cloud Signup Form** - Download the `Local Cloud
   Signup form <https://www.spamexperts.com/resources/pdf-central>`__,
   fill in all the necessary information and send it to our Sales team.
   Preferably you can send it directly to your account manager who will
   give you all the contact details and necessary information.
5. **Proceed with the installation steps as detailed below.**

Installation Procedure
======================

This page applies to the installation of our Local Cloud product only.
If you do not want to setup your own servers but still use our software,
you might want to look at our `Hosted Cloud
product <https://my.spamexperts.com/shop.php>`__.

Setting up servers
==================

Our solution runs on Debian Linux. For redundancy reasons, we strongly
recommend that you set-up at least two servers. For single-server setups
downtime of the solution can be expected as it lacks the redundancy
configuration.

Server requirements
===================

You can run the solution on either physical hardware or in a VPS.

In all cases, the **minimum** requirements are as following:

-  Dual Core CPU
-  4096MB Memory
-  80GB Diskspace
-  Debian Linux (latest
   `stable <https://www.debian.org/releases/stable/>`__ release) minimal
   installation with OpenSSH-Server, 64bit
-  No modifications to the default Debian configuration
-  Installation on a single partition (no separate partitions for /home
   etc)
-  A non-firewalled internet connection or required ports
   :ref:`opened  <2-Firewall-Usage>`
-  No modification (in case of virtualization) of
   **/etc/network/interfaces**, **/etc/hosts**, **/etc/hostname**,
   **/etc/resolv.conf** after our setup. See more information on the
   :ref:`Virtualization KB    article  <2-Virtualization>`.

If you run a larger cluster, it might be desirable to either run the
solution on more servers or make sure the hardware specifications are
upgraded accordingly.

Be advised: The above minimum requirements are **mandatory** and more
resources should be allocated based on how many domains your solution
filters, as shown below:

.. figure:: https://dev.spamexperts.com/sites/default/files/images/hardware-requirements-Debian-Install-LC.png
   :alt: 

Installation of Debian
======================

Once you have the servers ready, they should be installed with a minimal
installation of Debian with OpenSSH-Server. The installation of Debian
is straightforward, even if you are not familiar with Linux or Debian.
In such case, you might want to use our Debian Install Instructions.

We advise that you connect to the server using SSH keys without using
password authentication. See the
:ref:`Debian installations instructions <2-Set-up-my-Local-Cloud-servers-for-SpamExperts>`
for more information.

Password Authentication
-----------------------

Note down the root password you set during the installation, as that can
be used for console access when required. SpamExperts will not modify
the SSH root password.

SSH Keys
--------

In case you want to connect via SSH to the remote server, you should
authorize your public SSH Key(s) as explained in the Debian Install
Instructions (/root/.ssh/authorized\_keys).

Verification of the servers
===========================

The SpamExperts installation team will verify whether the servers are
setup according to the system requirements. If this is not the case,
they will contact and inform you what should be changed before the
installation can proceed.

Installation of the solution
============================

Once everything is ready to go, the SpamExperts installation team will
install the servers. During this time, it is important that the servers
are online and reachable. Do not shut them down or reboot them during
the installation, since this may prolong the installation.

The installation can take up to 3 working days. Once this is done, you
will be provided with login details. We also offer an optional express
installation service which completes in 1 working day, your account
manager can provide pricing details.

Installation complete, now what?
================================

Once the installation is complete, and you have been provided with the
login credentials, you can start using the solution.
