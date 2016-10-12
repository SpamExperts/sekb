.. _2-Backups:

Backups
=======

The SpamExperts email filtering service is fully redundant. For more
information, see our
:ref:`clustering  <2-Clustering>`
article.

To avoid data loss, the following information should be stored on
redundant storage. There is no backup of this data.

-  Logging data
-  Quarantine data
-  Locally queued emails due to destination server issues
-  Archiving data (unless you have configured mirrored storage)

**A copy of the following data is available in real-time on all
filtering nodes:**

-  All domains, their destination routes, and domain settings

**The following data is backed up daily from the master, and stored on a
different Local Cloud server in your setup:**

-  Web Interface data
-  All domains, their destination routes, and domain settings

In case data needs to be restored from backup, a (re)installation fee is
charged.

SpamExperts does not support the creation of snapshots of running
servers that would lock the filesystem. Please ensure that if an
external backup is created at storage level, the machine remains fully
responsive during the backup and does not get frozen in any way. In case
an external backup is restored, the re-installation fee to resync all
data with our central systems still applies, as the restore will not be
in-sync with the live environment.

Unfortunately we cannot allow the R1Soft CDP Agent to run on the
systems, as it's known to cause issues and interfere with processes. In
case you run a virtual server, you can run the agent on the physical
system as it won't run in our virtual environment. Please note that a
restore of a R1Soft CDP Agent backup likely breaks the live
synchronization, and hence will still require a (paid) manual restore by
our engineers to ensure the environment is fully operational again.
