Migration between Hosted Cloud & Local Cloud
============================================

When migrating to Hosted Cloud from Local Cloud or from Local Cloud to
Hosted Cloud, you simply need to export the domains from your overview,
then import the domains on to the new platform via the interface. Once
all the domains are moved, all you would need to do is change the MX
records of the domains to the new ones.

The sender Blacklist / Whitelist will **not** be moved automatically.
Generally you should not need to migrate sender white and blacklists (as
this could interfere with filtering), however if this is necessary then
you can use the Control Panel API to get the data,  and then use the
upload CSV, Control Panel API call to import this into your platform.

Also, the following will not be migrated:

-  Logging data
-  Quarantined data (spam messages)
-  Individual domain settings (for example: spam threshold settings that
   are not default values)
-  Email users (including protection reports)

It would be possible to export the logging data though from the
interface at the log search if this is required by your team, however
this would not be able to be incorporated into the new Cloud install.
