.. _5-Block-port-25-outgoing-traffic-to-force-smarthost-usage:

Block port 25 outgoing traffic to force smarthost usage
=======================================================

Spammers may abuse a script on your servers to send out spam directly to
port 25 destination email addresses, therefore bypassing the SpamExperts
smarthost filtering. There should be no legitimate reason for scripts to
communicate to port 25 on external servers, as all email should be
handled locally on port 25.

You can simply use the **iptables firewall** to block all outgoing
connections to port 25 and force all traffic to pass the SpamExperts
filtering:

IPv4
~~~~

**To add:**

::

    iptables -A OUTPUT -p tcp --dport 25 -j DROP

**To remove:**

::

    iptables -D OUTPUT -p tcp --dport 25 -j DROP

IPv6
~~~~

**To add:**

::

    ip6tables -A OUTPUT -p tcp --dport 25 -j DROP

**To remove:**

::

    ip6tables -D OUTPUT -p tcp --dport 25 -j DROP

Be Advised: You need to ensure the rules are automatically applied after
a reboot again.
