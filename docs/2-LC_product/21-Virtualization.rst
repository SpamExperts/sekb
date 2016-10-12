Virtualization
==============

Our solution works well on both physical and/or virtual machines. We do
recommend hypervisors that use full virtualization instead of
paravirtualization (or containers), so we can ensure the environment
including the kernel remains secure and up-to-date.

Be Advised: In case of paravirtualization **the customer is responsible
to ensure the latest stable kernel is available to the system**, and no
customizations are applied to the environment.

Also the customer is required to ensure the latest stable Linux kernel
is at all times supported without any restrictions.

A SpamExperts managed server must be able to be rebooted without the
host system "interfering" in this in any kind of way. So it’s critical
that files such as “\ **/etc/hostname**\ ”, “\ **/etc/hosts**\ ” and
“\ **/etc/resolv.conf**\ ” are not modified when the system is rebooted,
as that will break the filtering of the system.

Xen
===

When using a Xen-based environment, please ensure it always supports
running the latest stable Linux kernel. In addition, when using Xen with
PyGrub, you’ll have to ensure that you keep the boot configuration
up-to-date as that cannot be managed by the operating system.

**We do not provide support for this, as it should be handled by the Xen
server administrator.**

Xen is also known to modify system files, so please ensure it does not
touch any system files (as mentioned above) after the setup completed.

Virtuozzo / OpenVZ container virtualization
===========================================

You’ll need to ensure the latest Linux kernel is presented to the guest,
as well as prevent system files are being modified inside the guests.
It’s required for the environment to support "**systemd**\ ".
Furthermore there should not be any overcommitment or restrictions on
resources.

In case you choose to run the system in a container, it is very
important to constantly check the underlying settings to avoid any
problems. We will not be able to support issues caused by the underlying
virtual configuration.

user\_beancounters
------------------

The container restrictions can be evaluated in
"**/proc/user\_beancounters**\ " on the virtual machine. A
"**failcnt**\ " higher than 0 means that a resource limit was hit.
You'll need to ensure that no resource limits are hit. The number will
be increasing if it's a problem at the moment of checking. SpamExperts
does not monitor for such issues, so please ensure this is monitored
from the physical node.

cpulimit
--------

When setting the
`cpulimit <http://wiki.openvz.org/Resource_shortage#cpulimit>`__, you
need to ensure the configuration is set to use all CPU cores. With 4 CPU
cores you need to set the limit to 400%.

/etc/hosts, /etc/resolv.conf, /etc/hostname
-------------------------------------------

It is very important that after a reboot, these files are **NOT
modified**. Please ensure that they are not rebuilt on every reboot.
