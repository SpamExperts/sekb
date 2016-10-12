.. _2-Clustering:

Clustering
==========

The SpamExperts email filtering solution is always installed on at least
2 servers. All filtering nodes are fully synchronized and controlled
from the API/web interface.

Main services
=============

There are different services run by machines within the cluster, by
default the master server includes all services:

-  **API/Web interface**
-  **Logging**
-  **IMAP quarantine**
-  **Archive storage**
-  **Filtering**

**Extra machines** added only perform the role of filtering node and do
not contain the other mentioned services. These extra machines are
so-called "slave servers" and are synchronized in real time with the
data from the master machine. The physical location of the slave server
can be anywhere, and does not depend on the master location. If the
master would be unreachable/down, the "slave machines" will keep
processing the emails.

The specific master functionality is only available when the master is
reachable, as messages quarantined/logged are queued on the filtering
slaves whilst the master server is unreachable and will automatically
synchronize again as soon as it is back online. The
logging/quarantine/archive storage can be hosted on the master (default)
or be moved to any of the slave servers.

Primary/fallback usage
======================

Each filtering node can handle both primary and fallback email. The
distinction between primary email (lowest MX priority) and fallback
email (highest MX priority) is made automatically based on the IP
address used. Each server can be used only as primary server, only as
fallback server, or (with 2 IPs) both as primary server and fallback
server at the same time. **This last setup ensures optimal use of the
hardware resources available. For more information see :ref:`Local Cloud MX Records  <2-Local-Cloud-MX-Records>`.**

IP address change
=================

If the IP address of a server changes, this will break the
synchronization/authorization of the system as part of the cluster. 5
days prior to changing your IP address please inform us to schedule a
free IP change.

Hostname change
===============

It's currently not possible to change the hostnames of the servers. This
will require a reinstallation for which we charge a fee.

Cluster size and distribution
=============================

We recommend a minimum of 2 servers, and 50% of the servers to be
located in another network/datacenter (for redundancy). Please note that
although it's technically possible to run on a single machine, we
strongly recommend against that as an outage would mean the entire
mailflow would stop. As our backups are between the SpamExperts systems,
there is no backup in a single-machine setup and as the traffic cannot
be distributed we only provide limited monitoring/support for such
setups.
