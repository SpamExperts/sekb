.. _2-Hardware-Requirements:

Hardware Requirements
=====================

Hardware requirements strictly depend on how much traffic the solution
will filter, thus different configurations may apply to different
customers.

Determining required hardware
=============================

Since our Local Cloud solution runs on your own hardware, it is useful
to estimate in advance how much hardware you may need to have sufficient
capacity for a redundant environment. Estimating hardware requirements
can be difficult due to differences in email patterns across
countries/companies. For more information on the actual setup structure,
please see
`Clustering <https://my.spamexperts.com/kb/69/Clustering.html>`__.

With hardware there is always a bottleneck: CPU, memory, or disk IO. We
generally noticed that fast disks (SAS/SSD) greatly improve the
connection/email throughput per server. The amount of memory determines
the number of concurrent connections that can be processed, you
generally won’t need more than 64GB per server (and minimum 4GB). CPU is
used mainly for content/virus scanning and analyses, and when sufficient
memory/disk IO will likely be the next bottleneck.

**If you need help with your hardware requirements, provide us with the
following details:**

-  Total number of email/domains or hosting accounts
-  Average number of incoming connections per day (if available)
-  Average number of legitimate email (not spam) deliveries per day

Trial installation recommendations
==================================

Hardware recommendations for a trial installation of the SpamExperts
Local Cloud solution can be found
`here <https://www.spamexperts.com/resources/pdf-central>`__. Other
hardware configuration may be necessary, depending on your email
traffic.
