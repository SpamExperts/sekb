.. _1-Changelog-2015:

Changelog 2015
==============

Build 95168 (2015-12-29)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Messages that are both quarantined and queued previously had a
   “quarantined” status, and changed to a “queued” status in the
   previous update. The prior behavior is restored in this update;
   further changes are likely in the future (#26657)

Front-end / GUI:

-  Resolved an issue with Control Panel API calls for Non-Latin/UTF8
   International Domains (#26618)

Plugins & Integration tools:

-  No new updates this week

Build 95072 (2015-12-22)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Improved documentation around dates in the software API methods
   relating to the quarantine (#95003)
-  When a message is rejected because it is considered a virus, the
   Classification will now show a 'Rejected' status rather than an empty
   one (#26602)
-  It is no longer possible to white or black list a sender address that
   begins with a '/' (#95061)

Front-end / GUI:

-  Resolved issue with invalid domains that could have been added in the
   sender white/blacklist (#26523)
-  Resolved issue when getting error details for Non-Latin/UTF8
   International Domains (#26525)

Plugins & Integration tools:

-  cPanel: Resolved syntax issue on panels using PHP versions older than
   5.4 (#26590)
-  Plesk: Resolved Plesk warnings for specific setups (#26574)
-  Plesk: Resolved syntax issue on panels using PHP versions older than
   5.4 (#26590)

Build 94839 (2015-12-15)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue with archive search in 'all' mode with special
   characters (#26380)

Front-end / GUI:

-  Resolved issue with Telnet check with IPv6 destinations (#26446)
-  Resolved accessibility issue with require / unrequire and enable /
   disable 2Factor Authentication (#25951)
-  Improved User Experience when archiving email for a single recipient
   (#26489)
-  Improved the Mange Products option for multiple domains with
   different products available (#26495)

Plugins & Integration tools:

-  cPanel: Improved processing for parked, addon domains and subdomains
   as alias (#26075)
-  cPanel: Resolved issue with specific domain provisioning when MX
   records were not being correctly changed (#26506)
-  Plesk: Improved processing for parked, addon domains and subdomains
   as alias (#26075)
-  Plesk: Resolved issue with specific domain provisioning when MX
   records were not being correctly changed (#26506)

Build 94674 (2015-12-08)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved rollout issue with Software API documentation page (#26311)
-  Improved the Software API documentation section (#26385)

Front-end / GUI:

-  Resolved issue with search by recipient / sender with non-ASCII
   domain in log search pages (#26390)
-  Resolved issue with branding color scheme selectors remaining active
   when changing selection (#26411)
-  Resolved issue with creation of protection report when activating
   Branding services for an Administrator that did not previously have
   this service (#26377)

Plugins & Integration tools:

-  WHMCS: WHMCS Addon is now fully compatible with WHMCS v6 (#24832)
-  cPanel: Resolved issue with bulkprotect procedure adding the domains
   that are already added (#25024)
-  cPanel: Resolved API communication issues (#26231)
-  Plesk: Resolved issue with bulkprotect procedure adding the domains
   that are already added (#25024)
-  Plesk: Resolved API communication issues (#26231)

Build 94470 (2015-12-01)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Add new API methods api\_list\_admins(), api\_count\_admins(),
   api\_add\_admin(), api\_remove\_admin(), api\_rename\_admin(),
   api\_set\_admin(), api\_get\_admin(), api\_set\_admin\_parent(), and
   api\_get\_admin\_details(). These methods may be used to group sets
   of domains for more convenient use with other methods.Note that the
   web interface API should continue to be used to manage web interface
   admins (#94237)
-  Remove deprecated API methods
   api\_set\_disabled\_rfc\_compliance\_domains(),
   api\_get\_disabled\_rfc\_compliance\_domains(),
   api\_get\_protection\_report\_enabled(),
   api\_set\_block\_outgoing\_spam(), api\_get\_block\_outgoing\_spam(),
   api\_get\_estimated\_outgoing\_user\_count(), api\_server\_status(),
   and api\_get\_recipient\_error\_details() (#94238)
-  Remove deprecated functionality from API methods: the
   include\_aliases argument for api\_list\_domains() no longer accepts
   the value "true" (#94238)
-  Remove deprecated functionality from API methods: the
   skip\_size\_check argument for api\_whitelist\_ip() has been removed
   (#94238)
-  Remove deprecated functionality from API methods: the “true” and
   “force” values for include\_in\_progress are no longer valid for
   api\_count\_messages() and api\_count\_outgoing\_messages (#94239)
-  Adjust the restrictions around domains that may be used with the
   api\_transfer\_domain method (#94241)
-  The MX record of the archiving domain is no longer checked when
   executing most archiving API methods. Instead, the record is checked
   when queuing mail to be archived for the domain (#25898)

Front-end / GUI:

-  Added progress bar to "domain removal" part (#22067)
-  Resolved issue with "Remove and blacklist" option in the Incoming
   Spam quarantine page (#26230)
-  If a user is logged in as an admin or sub-admin, searches for lower
   level admins and logs out, the search term will be saved and kept in
   the search bar on the manage admins page (#26248)
-  Resolved issue with simultaneous removal of an admin alongside a
   sub-admin (#26215)
-  Resolved issue with 'api/user/list/role/email/domain' returning
   incorrect results (#26244)
-  Resolved search bar issue on Chrome browser (#26268)
-  Added information about sub-admin domains to the admin overview page
   (#22375)
-  Added message status as filter/column in log search pages (#20563)
-  Added permission option for admins to have access to the submission
   quarantine and release messages via the log search (#25567)
-  When the web interface API is used with software API credentials, a
   web interface user will be automatically created and used for future
   log-ins with those credentials (#25853)

Plugins & Integration tools:

-  No new updates this week

Build 94080 (2015-11-24)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 93858 (2015-11-17)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Allow wildcard subdomains when blacklisting or whitelisting senders
   for Incoming or Outgoing Filtering (#25325)
-  The RFC1413 idents on Outgoing connections are now disabled (#26156)

Front-end / GUI:

-  Updated Twitter Bootstrap to the latest version (#22054)
-  Resolved issue with response parsing that could prevent the outgoing
   whitelisted IPs from being displayed in Spampanel (#26158)
-  Resolved issue with count option on 'API calls history' page as it
   could incorrectly display +1 (#26165)
-  Resolved issue with Sort by date option in 'API calls history' page
   (#25993)
-  The link for Microsoft Authenticator (Windows Phone) was updated to
   the current version in their app store (#26167)
-  Resolved Legacy API admin cleanup on Spampanel API admin/remove
   method (#26143)

Plugins & Integration tools:

-  No new updates this week

Build 93523 (2015-11-10)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  The 'date' column in 'api\_find\_messages' now also works for in
   progress messages (#25965)
-  Added a new optional argument to
   'api\_statistics\_earliest\_timeframe' 'filter\_by' that allows
   filtering the results (#25070)
-  Added support for 'username=\*' in the
   'api\_lock\_outgoing\_identity' to lock an identity for all outgoing
   users for a domain (#24405)
-  Blocking hidden executable in zip files with
   'api\_set\_block\_hidden\_executable' will now check 3 levels deep in
   zip files (#20835)
-  Added the ability to restrict Archive API users by a list of IP or
   networks (#25344)
-  A new argument "callback" is now available in
   'api\_clear\_callout\_cache', that adds the ability to set a callback
   URL where the success or failure of API will be posted (#23256)
-  Improved the speed of the Software API call: 'api\_remove\_domain'
   (#18803)

SpamPanel

-  Resolved issue with API calls history sorting by date not working
   correctly (#25993)
-  Resolved issue with 'Unable to enable Archiving product' error when
   trying to edit an Administrator (#25980)
-  Resolved issue with Administrators being able to unassign domains
   making these un-manageable (#25817)
-  Resolved issue with 'api/domain/getowner' not returning the correct
   Administrator ID (#26008)
-  Resolved issue with Administrators not being able to create
   Authtickets for domain or email users that belong to their
   Sub-Administrator (#25970)
-  Visual Adjustments made to the Manage Permissions page for domain
   users (#24761)
-  'api\_rename\_admin' no longer works with an empty 'admin\_id' value
   (#26037)

Addons:

-  No new updates this week

Build 92900 (2015-11-03)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering / performance updates only

SpamPanel

-  No new updates this week

Addons:

-  No new updates this week

Build 92893 (2015-10-27)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  When processing Exchange Journal reports for archiving the CC and BCC
   metadata are also recorded (#25910)
-  IMAP Accessing the Outgoing Quarantine now works with IPv6 (#25892)
-  It is now possible to assign / unassign domains in the
   'api\_transfer\_domain' software API (#25937)

SpamPanel

-  Resolved issue with Super-Admins being able to add / edit
   administrator's brands with duplicate hostnames (#25879)
-  Resolved issue with \*@domain.com appearing in Recipient Whitelist
   Section when unsuspending an account (#25571)
-  The Users are no longer asked if they want to override the catch-all
   check when this is not available at their level (#25848)
-  Resolved issue with Retry Time showing different values at
   Super-Administrator Level and Domain Level (#25916)
-  Resolved issue with domain un-assignment by administrators (#25817)

Addons:

-  cPanel: The reason why a domain cannot be protected manually is now
   exposed (#12118)
-  cPanel: The destination routes are used as MX records when a domain
   is unprotected (#14843)
-  Plesk: The reason why a domain cannot be protected manually is now
   exposed (#12118)
-  Plesk: The destination routes are used as MX records when a domain is
   unprotected (#14843)
-  POA2.0: During the domain provisioning the domains are directly set
   up to speed up the process (#24153)
-  WHMCS: Added support for disabling End User's options in WHMCS Addon
   (#22272)

Build 92543 (2015-10-20)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering / performance updates only

SpamPanel

-  Resolved issue with Control Panel API 'api/admin/update' (#25641)
-  Resolved issue with Periodic User Report error 'selected language of
   template is not available' (#24907)

Addons:

-  cPanel: Cleanup add-on installation files in /usr/src/prospamfilter
   (#25448)
-  cPanel: Resolved issue with 'Cannot remove hook prekillacct! More
   content discovered not belonging to us' error when installing cPanel
   addon (#25540)
-  cPanel: Resolved issue with domain that are already filtered not
   being skipped when running Bulk Protect (#25024)
-  Plesk: Cleanup add-on installation files in /usr/src/prospamfilter
   (#25448)
-  Plesk: Resolved issue with uninstall failing to finish due to
   "mysql\_connect(): Access denied for user ..." (#25375)
-  Plesk: Resolved issue with Parse error syntax error, unexpected '['
   in /usr/local/prospamfilter/library/Plesk/Driver.php on line 67
   (#25845)

Build 92173 (2015-10-13)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Change outgoing recipient callout to only accept or permanently
   reject recipients. Messages that have recipients with temporary
   issues are now being queued on the filtering server (#25794)
-  It is now possible to restrict Software API users by IP or IP ranges
   (#24941)
-  The MX records check for the Archiving product is no longer performed
   when api\_set\_outgoing\_archive\_sender is active on the outgoing
   authenticating domain. Sender must still have the MX records
   correctly set in order for the message to get archived under the
   correct domain (#25064)
-  Blacklisting an outgoing sender using username=\* now also works on
   the enveloper sender (#25733)
-  Correctly handle different local time zones when storing Submission
   quarantine messages (#25736)
-  Correctly specify whether messages where rejected because of the
   recipient or sender callout in the outgoing log search (#25660)
-  Expose all logging variables to the remote syslog feature. It's also
   possible to set a new template to receive and log update when the
   message is delivered (#25252)

SpamPanel

-  Resolved issue with 'api/domailist/get' wrongly returning 404 error
   (#25715)
-  Resolved issue with disabling Archiving changing the 'real time
   indexing' (#25481)
-  Resolved issue with non-ASCII domain names not being decoded in the
   Interface (#25332)
-  Resolved issue with Sender and Recipient being wrongly displayed when
   the domain had '0' as the first character (#25778)
-  The Outgoing statistics are now displayed in the Interface (#23075)
-  The 'Retry' column is no longer available in the queue pages (#23769)
-  Resolved issue with 'api\_calls\_history' showing incorrect
   time-stamp in the Interface (#25770)

Addons:

-  No new updates this week

Build 91776 (2015-10-06)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added a new parameter to 'api\_whitelist\_outgoing\_ip' that allows
   skipping the limit of maximum number of concurrent connections from
   an IP address or IP range (#25006)
-  Different local timezone are now correctly handled in the Archive
   Search API (#25697)
-  Optimized 'api\_set\_quarantine\_days' to better handle changing the
   default value (#91674)

SpamPanel

-  Resolved issue with APS2 returning error 'Email exists, but the Email
   user was not found in SpamExperts' (#25646)
-  The interface now uses the API to determine which quarantine server
   to use (#25153)
-  Resolved issue with the Add domain section showing the incorrect
   number of domains allowed (#25589)
-  The translation of get\_lock\_reason is now handled by the interface
   (#22033)
-  Resolved issue with the Index rebuild failure not being processed
   (#25579)

Addons:

-  No new updates this week

OS X Apple Mail:

-  Resolved issue with reporting multiple messages from the mail client
   overview

Build 91414 (2015-09-29)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolved issue causing the 'api\_list\_local\_part\_quarantine' to
   return all local parts with quarantined messages instead of only the
   ones that have IMAP access enabled (#25200)
-  Different local time-zones are now correctly handled when building
   the on demand index for Archive Searches (#25478)
-  Resolved issue causing caught Outgoing messages from Authenticating
   IP ranges to only be stored at global level, instead of both global
   and user level (#25569)
-  It is now possible to set the 0 value for
   "api\_set\_additional\_training\_days", which disables the feature
   (#25556)
-  Messages that are 'released' or 'released and trained' from the
   quarantine system are now also archived if the relevant account has
   archiving enabled (#23477)
-  Added support for the 'api\_list\_locked\_identities' API to show all
   locked identities cluster wide (#24407)
-  Optimized the on demand index building for larger archive system by
   batching the messages in smaller sizes (#25103)
-  Blacklisting a sender address for all Outgoing users of a single
   domain with 'api\_blacklist\_outgoing\_sender', by setting the
   username parameter to \* is now possible (#25105)
-  Adjusted handling of Exchange journaled reports sent for Archiving to
   work at email user level if the recipient's domain from the original
   message matches the journaled address recipient domain (#22421)

SpamPanel

-  Resolved issue with branding hostname not being synced correctly
   (#25173)
-  Resolved issue with 'api\_list\_domains' being executed by Control
   Panel API (#25546)
-  Resolved issue with Server Usage 'idle / uptime' bar showing
   incorrect output (#25564)
-  Adjusted the documentation for 'api/admin/add/username' (#25565)
-  Adjusted the error message returned when trying to add a TLD to the
   Sender Blacklist section (#25588)
-  Report Spam / Report not spam now supports .msg format (#6474)
-  Global 'local disk storage' remaining disk space is no longer
   available for end users / domain users (#22715)

Addons:

-  No new updates this week

Build 90943 (2015-09-22)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  When processing an outgoing messages that has a null sender, the
   recipient will now be checked using a callout at the destination
   server. This enhancement prevents large queue build-ups of messages
   that are frozen because there is no sender and the recipient is not
   valid. (#24434)
-  Resolved issue that prevented the optimization of delivering outgoing
   messages locally when the recipient's domain was also handled by the
   same cluster, for domains that had multiple custom MX records
   (#25445)
-  Two new APIs methods are now available
   'api\_get\_trusted\_xclient\_list' and
   'api\_set\_trusted\_xclient\_list'. These methods expose the ability
   to manage a set of IPs that are authorized to use the XCLIENT SMTP
   extension (#16275)

SpamPanel

-  Resolved issue with on screen error messages when using the
   ControlPanel API 'getbandwidthusage' method for admins (#25434)
-  Optimized internal systems to handle bulk domain removal more
   efficiently (#24704)
-  Added a new 'no dictionary words' password policy that prevents
   passwords that are dictionary words (in any of the supported
   languages) (#22390)
-  'Message ID' is now a link to the View Page on the Incoming /
   Outgoing Delivery Queue pages (#23770)
-  Added 'Per-day' limit to outgoing user options (#24651)
-  Resolved issue with error response 'Domain exists, but the Domain
   user was not found in SpamExperts' when using the ControlPanel API
   (#25383)
-  Resolved issue with option 'Download as .eml' only partially
   downloading the message in the Quarantine page (#25488)

Addons:

-  No new updates this week

Build 90373 (2015-09-15)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering / performance updates only

SpamPanel

-  Remove "Invalid recipient limit" option from the outgoing user
   settings page (#24780)
-  Resolved issue with specific non-ascii characters not visible in the
   Archiving search page (#25395)
-  Resolved issue with whitelisted sender discrepancy between API and
   GUI (#25351)

Addons:

-  cPanel: Added support for command line "Bulk-Protect" (#16908)
-  cPanel: Resolved issue with an incorrect cPanel cron entry (#24937)
-  Plesk: Added support for command line "Bulk-Protect" (#16908)
-  Plesk: Resolved issue with an incorrect cPanel cron entry (#24937)

Build 90089 (2015-09-08)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Messages that are sent to black-holed recipients are now correctly
   archived for domains that are using a specific list of local parts.
   (#25363)

SpamPanel

-  Resolved issue with absent error message for an inactive user on
   Overview page and Add Domain page (#25281)
-  Resolved issue with an invalid date period with Archive search index
   creation (#25308)
-  Resolved issue with Outgoing User editing for non-ASCII domains
   (#25305)
-  Added further speed optimizations to the Overview page (#22604)

Addons:

-  cPanel: Resolved issue with diagnostics wrongly confirming API access
   is working (#22536)
-  cPanel: Resolved issue with "error: No file found" during
   installation (#25328)
-  cPanel: Resolved issue with Bulk protect not displaying the last
   execution date correctly (#25079)

-  Plesk : Resolved issue with diagnostics wrongly confirming API access
   is working (#22536)
-  Plesk :Resolved issue with "error: No file found" during installation
   (#25328)
-  Plesk: Resolved issue with Bulk protect not displaying the last
   execution date correctly (#25079)
-  Plesk: Resolved issue with domains not showing in List Domains when
   unable to determine the server's hostname (#25134)
-  Plesk: Resolved issue with client level domain list (#24994)

Build 89622 (2015-09-01)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Fixed default value for the remote syslog server template (#25251)

SpamPanel

-  No new updates this week

Addons:

-  No new updates this week

Build 89193 (2015-08-25)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added support to spamreport@spamrl.com for processing forwarded
   messages from Apple Mail, that were sent with rich text (25130)
-  When delivering messages with the Outgoing Filtering product, we
   optimize the processes to see if the recipients domain is also
   handled by the cluster and try to deliver locally first. This will
   now also work even if the domain's MX records do not have the same
   name as the local server hostnames (#25157)

SpamPanel

-  Resolved issue with language icon missing from the Periodic User
   Report -> Enable for recipient page (#25179)
-  Improved the time it takes to run the Control Panel
   api/admin/binddomains (#25184)
-  Resolved issue with SpamPanel session expiry blocking login after
   migration (#25171)

Addons:

-  No new updates this week

Build 88872 (2015-08-18)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Submission users can now use a default sender blacklist, this works
   just like the "default" system for the Delivery sender blacklist
   (#25017)
-  Temporary SMTP delivery errors are now logged correctly in the
   delivery details logs, and will be available in the
   api\_get\_delivery\_errors API (#24500)

SpamPanel

-  Resolved issue with ``Your IP or internet browser has changed`` error
   when using Safari (#24958)
-  Resolved issue with Javascript scroll down error in the Incoming /
   Outgoing Queue pages (#25007)
-  Resolved issues with Control Panel API
   ``sender / recipient whitelist / blacklist`` (#25015)
-  Adjusted the Log Search text to no longer mention the ``now`` option
   that was previously removed (#25040)
-  Adjusted classification text for ``Badly formed From header`` to
   provide more details (#24685)
-  Resolved issue with manage pages not validating the specified users
   at super-admin level (#25118)
-  Resolved issue with SpamPanel not handling properly the index rebuild
   (#25099)
-  Adjusted the configuration fields size in ``User Settings`` page
   (#25129)
-  Resolved issue with same email address allowed to be set as email
   alias (#24948)

Addons:

-  cPanel: Resolved issue where the Reseller access was disabled by
   default (#25089)
-  cPanel: Resolved issue where SpamExperts is available to Resellers
   even if it is disabled (#24546)
-  Plesk: Resolved issue where SpamExperts is available to Resellers
   even if it is disabled (#24546)

Build 88640 (2015-08-11)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering / performance updates only

SpamPanel

-  No new updates this week

Addons:

-  No new updates this week

Build 88125 (2015-08-04)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolved issue with ``api_unblacklist_outgoing_sender`` when no
   USERNAME is provided (#24989)
-  It is now possible to use default value for days argument in Software
   API ``api_set_additional_training_days`` when the domain is default
   (#24976)
-  Adjusted the error message when trying to rename an admin to a name
   that already exists (#87904)
-  Adjusted releasing messages from the protection report to handle any
   differences between local and UTC time (#25012)
-  The sender blacklist for the From: header check now correctly follows
   the case sensitive option for the domain (#24995)
-  Added support for GB2312 encoding (#16883)
-  Reverted old API behavior where a giving no value for a argument
   would be the same as in no argument was given at all. For example, a
   call like ``/cgi-bin/api?call=api_method&arg=`` would be equivalent
   to ``/cgi-bin/api?call=api_method``

SpamPanel

-  Resolved issue with login / change password conflict caused by having
   the same Administrator / Email User address (#24835)
-  Resolved issue with the pagination breaking when selecting Incoming /
   Outgoing in the Archive Search (#24897)
-  Resolved issue with error: ``This account is inactive`` being
   displayed when disabling Archiving Product for one or more domains
   (#24949)
-  Resolved issue with Control Panel API \`/senderwhitelist/ not
   returning the same results as the Software API (#24986)

Addons:

-  DirectAdmin: Resolved issue with DirectAdmin uninstaller not removing
   the hook scripts (#24786)
-  DirectADmin: Resolved issue with Plugin Logo link pointing to
   forbidden: /CMD\_PLUGINS\_ADMIN/se at user and administrator levels
   (#24808)

Build 87545 (2015-07-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  It is now possible to blacklist outgoing senders with a series of new
   software API methods: ``api_blacklist_outgoing_sender``,
   ``api_unblacklist_outgoing_sender``,
   ``api_get_outgoing_sender_blacklist``,
   ``api_set_outgoing_sender_blacklist`` (86452)
-  Resolved issue with local part characters regex containing a colon
   (#24743)
-  When browsing the quarantine as a domain user using an IMAP client,
   you are now able to see and manage messages for all email users for
   that domain that have the local part quarantine enabled (#22075)

SpamPanel

-  Resolved issue with auto-suggest domains being empty when trying to
   move from one domain dashboard to another (#24638)
-  The Local Part Aliases are now also shown in the Control Panel
   (#19878)
-  The user is now notified when a message is removed from the Outgoing
   / Incoming Delivery Queue by using the option
   ``Delete and notify user`` (#20982)
-  Adjusted text for the Archive Search page (#21415)
-  Improved performance when using ``Bulk Domain Removal`` (#24704)
-  Resolved issue with Control Panel API ``domainalias/list/domain//``
   returning incorrect results (#24760)
-  Resolved issue with the Protection Report template being reset when
   Unbinding a domain (#24833)
-  Resolved issue with the Log Search section returning the error
   ``Error Occurred`` and not returning to the Log Search (#24806)
-  Resolved issue with suggested MX records not working for non-ASCII
   domains (#24812)
-  Resolved issue with ``/api/admin/unbinddomains/`` unbinding all
   domains when an Admin only uses it for one domain (#24847)
-  Resolved issue with ``api/admin/unbinddomains/`` wrongly triggering
   an error message when used by a Super-Admin (# 24846)
-  Resolved issue with API user's password length (#24801)
-  Resolved issue with removing allowed API methods for an API user if
   that option was previously activated (# 24799)
-  It is now possible for Admins and Domain Users to set the recipients
   which will have their messages archived (#23483)
-  Resolved issue with Route Ports being wrongly updated when the
   Destination(s) (Overview) are changed (# 24894)
-  We have now added the Control Panel API
   ``/api/domain/addlocalrecipient/domain/`` which allows you to add
   Local Recipients (# 22004)

Addons:

-  No new updates this week

Build 86989 (2015-07-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolved possible caching issue preventing weekly/monthly outgoing
   limits from being properly enforced (#13509)

Addons:

-  cPanel/Plesk: Resolved issue with add-on showing Insecure File Rights
   errors (#24640)
-  cPanel/Plesk: The add-on auto-update schedule is now set to weekly
   (#24064)
-  cPanel/Plesk: Resolved issue with class ``cmfcDirectory`` not
   existing (#24455)
-  Plesk: Resolved issue with
   ``Invalid argument supplied for foreach()`` error during trunk
   install (#24709)
-  DirectAdmin: Resolved issue with DirectAdmin plugin potentially
   wiping out the configuration after update (#24753)
-  DirectAdmin: Resolved issue with SUID binary not supporting custom
   plugin directory (#24770)
-  DirectAdmin: Resolved issue with wrong paths in the Hook scripts
   (#24810)

Build 86418 (2015-07-14)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Two new API methods are available, ``api_set_blocked_tld``,
   ``api_get_blocked_tld``, that enable blocking messages based on
   senders TLD (#19529)
-  It's now possible to set a per-day limit on outgoing users via
   Software API (#13509)
-  Two new API methods are available exposing a history of outgoing user
   locking and unlocking: ``api_find_outgoing_user_locking``,
   ``api_count_outgoing_user_locking`` (#8633)

SpamPanel

-  Resolved issue with Admins not being able to access the domain Add
   and Overview pages (#24559)
-  The Delivery Queue page Headers are now Bold formatted (#24541)
-  Resolved issue with not being able to set a value of ``0`` to the Per
   Hour Limit in the Edit Outgoing User page (#24529)
-  Resolved Pop-up menu issues on narrow screens (#24547)
-  Resolved issue with Nginx blocking Super-Admin because of IP
   restrictions (#24573)
-  Resolved issue with Main Panel content not being visible when moving
   from Overview page to the Add Domain page (#24111)
-  You can now see the progress when transferring domains (#14131)
-  The long email subject will now be truncated in the Spam Quarantine
   pages (#22515)
-  It is now possible to download badly formatted messages from the Spam
   Quarantine (#22478)
-  Resolved issue with ``Restore Permissions`` to default value not
   working (#24572)
-  Resolved issue with filtering Domains by multiple criteria in
   Overview page (#24586)
-  Resolved issue with Spam Report using template from different domain
   (#24570)
-  Resolved issue with ``api_update_incoming_message_status`` not
   updating the status correctly after removing a message from the
   quarantine (#24532)
-  Renamed ``Submit Index`` button in Search Page when real-time
   indexing is disabled (#24618)
-  Updated the Password policies text (#24564)
-  Added help information for ``Number of days available`` in the Log
   Search when Real Time search is disabled (#24617)
-  Updated the ``Real-Time`` search label in Archive Search (#24615)

Addons:

-  cPanel: Resolved issue with cPanel sending double forward slashes
   ``//`` to SpamPanel API (#23263)
-  cPanel: Resolved issue with SpamExperts being available to resellers
   even if the ``Enable Addon in cPanel for reseller accounts`` is
   disabled (#24546)
-  Plesk: Resolved issue with Plesk sending double forward slashes
   ``//`` to SpamPanel API (#23263)
-  Plesk: Resolved issue with receiving ``Output from your job 48``
   messages when adding a domain (#24527)
-  Plesk: Resolved issue with:
   ``Cannot use string offset as an array error`` after installing Plesk
   Addon (#24602)
-  Plesk: Resolved issue with the corrupted icons in the List Domains
   section (#24519)
-  Plesk: Resolved issue with SpamExperts being available to resellers
   even if the ``Enable Addon in Plesk for reseller accounts`` is
   disabled (#24546)

Build 85865 (2015-07-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  The Archive logging system now stores the Archive ID and the
   api\_find\_messages and api\_find outgoing messages support an
   addition column: archive\_id (#21584)
-  The welcome email (auto-enable protection reports now has the
   "Content-Type header set (#24397)
-  The logging data may now be configured to be sent to a remote syslog
   server, as well as stored in the internal logging system (#21535)

SpamPanel

-  Adding a duplicate IP to SSH access now return an error message
   (#24112)
-  The Archive Search now has the option for Real Time searching
   (#21588)
-  We now have a modular system of passwords policies (#22398)
-  Improvements to the CSR generated output (#16478)
-  The 'api\_find\_messages' and 'api\_find\_outgoing' messages now
   returns a translated string for the classification information
   (#22034)
-  A super-admin can now add domains over the limit that the Admin has
   (#24357)
-  Resolved issue with sorting by username on the Manage Admins page
   (#24458)
-  Resolved issue with Bulk Actions options being wrongly displayed when
   multiple users are selected (#24140)
-  Resolved issue with Control Panel API '/api/admin/list/' not
   returning the domains of the admins (#24445)
-  Improved loading speed of the control panel for Admin users (#24499)
-  Resolved issue with 'Invalid, skipping' error when trying to remove
   Blacklisted Senders uploaded via CSV (#24490)
-  Improved SpamPanel error response text (#23411)
-  Resolved issue with empty menu under Permissions Page - Domain
   section (#24502)
-  Resolved issue with Admin Settings page being available only when
   incoming mail product is available (#24531)
-  Resolved issue with Control Panel API '/api/reseller/setproduct/'
   returning error: 'You have no permission to call this method'
   (#24539)

Addons:

-  cPanel: Resolved issue with PSF installer brand setup (#24508)
-  Plesk: Resolved issue with email for Admin account failing to be
   gathered (#24368)
-  Plesk: Added support for sub-domains (#23094)
-  Plesk: Resolved issue with ATD not executing domain addition command
   as PSAADM (#24469)
-  Plesk: Resolved issue with Undefined variable: converted domain
   (#24473)
-  Plesk: Resolved issue with 'There are no domains on this server'
   error (#24488)
-  Plesk: Resolved issue with Plesk add-on failing to install on PHP
   5.2: syntax error, unexpected ':' in
   /usr/src/prospamfilter/bin/install.php (#24497)
-  Plesk: Resolved issue with update failing on Plesk for Linux (#24521)
-  Plesk: Resolved issue with PSF installer brand setup (#24508)
-  DirectAdmin: Resolved issue with upgrade failing (#24319)

Build 85380 (2015-06-30)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  The logging system now stores the decoded version of the
   'To/CC/From/Subject' headers (#23203)
-  The logging system now distinguishes recipient rejection that is the
   result of a cached lookup rather than a fresh callout (#16480)
-  The 'api\_set\_administrator\_callout' API call now allows setting a
   blank email (i.e. removing any contact) (#22489)

SpamPanel:

-  Admins can now manage sub-admins using Control Panel API:
   '/api/admin/update' ; '/api/admin/wipe' ; '/api/admin/binddomains' ;
   '/api/admin/unbinddomains' ; '/api/domain/getowner' (#24195)
-  Resolved issue with 'Release and Train' option not working from the
   Log Search (#24276)
-  You are now able to assign an Admin under a sub-admin (#22245)
-  Increased the speed of transferring domains (#22602)
-  Changed the Bandwitdth Overview so it is now showing if a domain
   belongs to a sub-admin (#23543)
-  Admins are now able to remove Sub-Admins via API :
   '/api/admin/remove/username/' (#23391)
-  Resolved issue with: "Invalid request parameters" error when trying
   to view the Error Details for a message in the Log Search (#24366)
-  The Control Panel API '/api/domainslist/get/' can be extended to
   provide information about available services for each domain (#21596)
-  The SpamPanel now recommends using a Password Manager when creating
   custom passwords (#22393)
-  Improvements to the SpamPanel API '/api/domaincontact/set/domain/'
   (#24452)
-  Updated error messages when using setting cluster update times and
   allowed SSH IP's (#22030)

Addons:

-  cPanel: Resolved issue with erros showing in log when terminating an
   account (#24389)
-  Plesk: Resolved issue with PHP Warning: "Illegal string offset id"
   when clicking the Domain List (#24399)

Build 84851 (2015-06-23)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  It is now possible to retrieve and release messages from quarantine
   via the API (#21713)
-  It is now possible to use the value "default" when setting the
   default value, which will change the default back to the value used
   when installing the cluster (#5100)
-  Default values may now be used with
   api\_set\_maximum\_messages\_per\_connection (#18614)

SpamPanel:

-  Resolved issue with Overview returning a blank page in Internet
   Explorer (#24196)
-  Add retry time as an action for log search results (#21935)
-  Resolved issue with Add Domain page not showing correctly (#24251)
-  Resolved issue with not being able to remove the ``&`` character in
   restricted local parts via the interface (#23860)
-  Resolved issue with "Authentication failed" error when trying to view
   / release quarantined messages (#24235)
-  Resolved issue with Manage Administrators page not loading list of
   administrators when French language is used (#24271)
-  Changed the way Outgoing Reports is showing to make it more clear
   (#24227)
-  Resolved issue Overview search field not searching for the following
   format ``.net`` (#24313)
-  Resolved issue with api/admin/add/username failing to add uppercase
   usernames (#24351)
-  Resolved issue with domain unbinding from an admin account (#24308)
-  Resolved issue with admin contact email address not being added
   correctly (#24361)
-  The SpanPanel API '/api/admin/transferdomains/' requires accepting
   the domain before it is assigned to the new admin (#24304)

Addons:

-  cPanel: It is now possible to enable / disable reseller access in
   cPanel plugin (#19245)
-  cPanel: Resolved issue with cPanel terminate account not removing
   addon domains (#24079)
-  cPanel: Resolved issue with cPanel not displaying domains and
   returning the error: "There are no domains on this server" (#24325)
-  Plesk: Resolved issue with Toggle Protection not adding the correct
   route (#24286)

Build 84419 (2015-06-16)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

Monitoring:

-  You can now choose which contact will receive the monitoring system
   notifications (#19510)

SpamPanel:

-  No new updates this week

Addons:

-  cPanel: It is now possible to enable / disable admin access in cPanel
   plugin (#19245)
-  cPanel: When using the "Terminate Account" option in cPanel, the
   domains are now removed from the filtering server (#24079)
-  Plesk: Resolved SecurityError: blocked a frame with origin (#24241)
-  DirectAdmin: It is now possible to use branding in DirectAdmin
   (#22918)
-  DirectAdmin: Removed the term "SpamPanel" from the plugin (#24043)

Build 83913 (2015-06-09)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  No new updates this week

Addons:

-  No new updates this week

Build 83705 (2015-06-02)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  "Cancel 2FA" is no longer available once the user set the 2FA
   (#23749)
-  Resolved issue with "Sender is invalid" response when trying to
   whitelist or blacklist a domain (#24133)
-  Resolved issue with "You have no permission to remove admins" error
   when using api/reseller/setproducts API (#24148)
-  The 2FA is no longer required the second time when the page Manage
   Email users is refreshed (#24142)
-  The labels no longer use the term "SpamPanel" (#24045)
-  The Admins are now able to get a list of their sub-admins via API
   call (#24169)

Addons:

-  No new updates this week

Build 83328 (2015-05-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  A new API method,
   api\_set\_recipient\_protection\_report\_template(), is available,
   for making bulk changes to protection report settings (#23822)
-  A new API method,
   api\_set\_recipient\_protection\_report\_language(), is available,
   for making bulk changes to language settings (#23979)
-  An error has been fixed that would cause the
   api\_get\_domain\_count() API method to return an incorrect value
   when domains had multiple destinations (#23989)
-  When a message expires from the delivery queue, the status (in the
   logging data) is now updated to either “bounced” (if a delivery
   status notification was generated) or “queue-expired” (#19762)
-  When a message is not fully processed (e.g. the sending server gives
   up before completing) the status of the message (in the logging data)
   is now set to “not-accepted” (#24003)
-  When a message is removed from the quarantine, the status of the
   message (in the logging data) is now set to “quarantine-removed”.
   This also prevents these messages from appearing as releasable in
   protection reports (#19763)

SpamPanel:

-  It is now possible do assign domains directly from the Overview
   (#13683)
-  It is possible to add Local recipients that contain only ascii
   characters (#24054)
-  Added option to export user defined white and blacklists (#22856)
-  Added option to search the user defined white and blacklists (#22855)
-  Added search option to use defined white and blacklists (#22854)
-  Removed the term "SpamPanel" from the interface (#24043)
-  Resolved issue with email user not having access to sender whitelist
   / blacklist (#24069)
-  Resolved issue with Archive search date option showing the wrong date
   (#24044)
-  'Download .eml' button is now displayed in the incoming\|outgoing
   delivery queue (#24085)

Addons:

-  POA2.0: MX record changes are handled in the instance settings
   (#23362)
-  POA2.0: It is now possible to handle auto protection on multiple
   subscriptions for one customer (#23929)
-  POA2.0: Resolved issue where unprotecting a domain enabled the
   original MX records of other domains as well (#23981)

Build 82808 (2015-05-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  Email Users are now able to access Sender Whitelist / Blacklist
   (#22552)
-  Optimized logging classification for "Connection Lost" emails
   (#23377)
-  Added certificate management for the quarantine server HTTPS (#21341)
-  Added "Logout URL" to the session time-out page (#21390)
-  Resolved issue with setting the restricted local part characters in
   the Domain Settings page (#23860)
-  Resolved issue with Upload CSV file not working in the Sender
   Whitelist / Blacklist pages at email user level (#23901)
-  Optimized classification search criteria on Log Search page (#23931)
-  Resolved issue with Raw Headers missing from the message Preview in
   the Outgoing Spam Quarantine (#23747)
-  Resolved issue with the SpamPanel displaying an incorrect message
   when domains were transferred from Super-Admin to Admin (#23918)
-  Resolved issue with MX verification tool not returning results for
   all domains (#23938)
-  Added the message "Accept required" in the overview when domains are
   being migrated between users to make the action more clear (#23951)

Addons:

-  cPanel: Resellers are now able to operate their customer's domains
   (#23837)
-  cPanel: Resolved issue with "404 - Not found" error when selecting
   the number of items per page in Domain List (#23898)
-  cPanel: Alias and sub-domain are now showing in the Domain List
   (#23810)
-  cPanel: Resolved issue with removing the domain from cPanel not
   removing it from Spam Panel (#23906)
-  Plesk: Resellers are now able to operate their customer's domains
   (#23837)
-  Plesk: Resolved issue with "404 - Not found" error when selecting the
   number of items per page in Domain List (#23898)
-  Plesk: Alias and sub-domain are now showing in the Domain List
   (#23810)
-  DirectAdmin: DirectAdmin addon no longer hard-codes routes (#20112)

Build 82370 (2015-05-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  When the default account is set to inactive, archive methods that
   deal with the default account or all accounts (e.g.
   /archive/accounts/) may now be used (#23921)

SpamPanel:

-  No new updates this week

Addons:

-  No new updates this week

Build 81946 (2015-05-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  Resolved issue with changing the branding from server-wide to a
   specific server creating a duplicate (#23725)
-  It is now possible for sub-admins to add sub-admins via API call
   (#22221)
-  Sub-admins are now able to use the API /api/reseller/binddomains/
   (#22242)
-  It is now possible to view the message in the quarantine by clicking
   the subject in the Log Search (#23422)
-  Resolved issue with autofilling the username / password in Manage
   outgoing user page (#20206)
-  It is now possible to use the /api/domainuser/status/ Spam Panel API
   using the domain name as well as the ID parameter. (#22069)
-  Resolved issue with login as newly created sub-admins (#23843)

Addons:

-  cPanel: Resolved issue with PHP warnings occurring when unsintalling
   the addon on cPanel servers (#23763)
-  cPanel: Resolved issue with searching, changing order and changing
   count of items per page not working in Internet Explorer (#23876)
-  Plesk: Resolved issue with "This domain does not belong to you" error
   when trying to log in (#23641)
-  Plesk: Resolved issue with adding an email address in "Configure the
   email address for this domain" in Plesk not adding the address to the
   interface (#23796)
-  Plesk: Resolved issue with searching, changing order and changing
   count of items per page not working in Internet Explorer (#23876)

Build 81544 (2015-04-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  Resolved issue with the SpamPanel API call:api/admin/list/ not
   returning the proper result(#23432)
-  Resolved issue with calendar from the Outgoing / Incoming log search
   being misplaced (#23752)
-  Resolved issue with the outgoing filtering being active even after
   disabling Outgoing mail from Manage Products (#23774)

Addons:

-  cPanel: Panel driver now catches the exceptions raised by the cPanel
   library (#13905)
-  cPanel: Resolved issue with the error Logout URL is not valid
   (#15901)
-  cPanel: Resolved issue with bulk-protect hanging (#23751)
-  cPanel: The diagnostics now checks if the hook is executable (#15242)
-  cPanel: You are now able to select the number of items you wish to
   see on a page (#22969)
-  cPanel: Resolved issue with Locales in addon not working (#23685)
-  Plesk: Resolved issue with the error Logout URL is not valid (#15901
-  Plesk: The diagnostics now checks if the hook is executable (#15242)
-  Plesk: You are now able to select the number of items you wish to see
   on a page (#22969)
-  Plesk: Resolved issue with Locales in addon not working (#23685)

Build 81022 (2015-04-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  No new updates this week

Addons:

-  cPanel: Resolved PHP Warnings during installation (#23688)
-  cPanel: Adjusted text for ``Check all domains`` option (#23601)
-  cPanel: Optimized retrieval of domain list / Check status page
   (#23395)
-  Plesk: Resolved PHP Warnings during installation (#23688)
-  Plesk: Adjusted text for ``Check all domains`` option (#23601)
-  Plesk: Resolved issue with ``This domain does not belong to you``
   error in Plesk 12 (#23641)

Build 80690 (2015-04-14)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improved the speed of simple API calls (#23475)
-  Improved the speed of the quarantine release system (from protection
   reports) (#23476)
-  Improved the speed of various API calls that interact with multiple
   filtering servers (#23300)
-  Added a new API method (api\_list\_lock\_notification\_templates) is
   available to list the configured lock notification templates (#23240)
-  The status of a message in the logging system now distinguishes
   between being queued and queued but frozen (#21933)

SpamPanel:

-  Resolved issue with the domain limit settings (#23438)
-  Resolved issue with the Apply button not working when removing the
   Software API Users (#23513)
-  Resolved issue with the Spam Panel API : "Error in exception handler"
   error (#23593)
-  Resolved issue with the IPv6 being incorrectly split when used as a
   Route (#23615)

Addons:

-  cPanel: It is now possible to Update SPF records (#21243)
-  cPanel: Added checkboxes in the Domain Overview section to easily
   select several domains (#11980)
-  cPanel: Resolved issue with the Configuration Validation not
   requiring a correct password (#23546)
-  Plesk: Added checkboxes in the Domain Overview section to easily
   select several domains (#11980)
-  Plesk: Resolved issue with the Configuration Validation not requiring
   a correct password (#23546)

Build 80229 (2015-04-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  When a destination mail server rejects an email address that error
   message will be passed back to the sending server. Note that this
   does not apply when the destination rejection is cached, which will
   be the majority of cases (#11866)
-  It's now possible to use multiple values for the “status” filter in
   api\_find\_messages and related calls (#23288)
-  Improvements to the efficiency of updating the archiving search
   index, particularly on very busy clusters (#21508)
-  The API has new methods that let users disable the domain-level
   quarantine, and the email-user level quarantine is now enabled by
   default for all addresses (it can be disabled for specific addresses
   as required)(#22136)

SpamPanel:

-  Resolved issue with setting default protection report template at
   admin level (#20204)
-  Added sub-admin information to the bandwidth overview pages (#22376)

Addons:

-  cPanel: Enhancements made to ``Bulk Protect`` process (#23283)

Build 79757 (2015-03-31)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolved issue with the archiving storage definitions, passing a
   datetime.date object as the timestamp value, rather than a
   datetime.datetime (#23346)
-  The api\_find\_call\_logs method is now returning UTC values, and the
   documentation was updated to show this (#23379)
-  The client\_username and client\_ip arguments for
   api\_find\_call\_logs and api\_count\_call\_logs have been renamed to
   search\_client\_username and search\_client\_ip (#23355)
-  When an outgoing message is destined for a filtered incoming domain,
   this will now always be routed to the local server rather than
   following normal delivery rules (#18200)
-  The api\_get\_delivery\_errors API method now sources all data from
   the logging server, which will considerably improve speed,
   particularly on large clusters (#21628)
-  Significant improvements in the efficiency of archiving messages
   (#21150)
-  Two new API methods, api\_get\_delivery\_queue\_count and
   api\_get\_outgoing\_delivery\_queue\_count have been added, that
   allow getting the number of messages in the delivery queue (#21465)
-  A new column, “delivery\_data” is available in the
   api\_find\_messages and api\_find\_outgoing\_messages methods
   (#23115)
-  Improvements to the efficiency of removing a domain (#23287)
-  The “True” and “force” values for the “include\_in\_progress”
   argument of the api\_count\_messages and
   api\_count\_outgoing\_messages API calls are now deprecated (#79625)
-  The api\_get\_recipient\_error\_details API method has been
   deprecated (#21628)
-  The “include\_in\_progress” argument of the api\_count\_messages and
   api\_count\_outgoing\_messages API calls now defaults to False
   (#79633)

SpamPanel

-  Optimized the text in the "Manage list of domains and IP addresses
   with disabled SPF check" page (#23253)
-  Added text to explain the "Identification Method" behavior in the
   Outgoing user settings page (#23221)
-  Optimized SpamPanel API error text when authenticating with unknown
   user (#23130)
-  Resolved issue with being able to upload invalid local parts via a
   CSV file (#23361)
-  Renamed the submission term in the Spam Panel to "Outgoing" (#23364)
-  Added the ability to release/view/remove quarantined messages in log
   search results (#19766)
-  Added text to clarify that the "Enable outgoing limits:" are related
   to connections and not messages in the Outgoing user settings page
   (#23170)
-  Added more support to archive storage changes (#11119)
-  SpamPanel is now compatible with Dovecot 2 (#22787)
-  Optimized the message returned when the outgoing user is added to the
   SpamPanel (#21830)
-  Resolved on screen error when submission report was generated at
   admin level (#23388)
-  Changed getvalidrecipientcount to not include data on the filtering
   servers (#22871)

Addons

-  No new updates this week

Build 79270 (2015-03-24)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improvements to the efficiency of sending ARF messages (#21337)
-  Fixes to archive message storage where the message date in the
   server's local time and the message date in UTC are not the same
   (#22976)
-  Add recognition of errors in the form "Message size exceeds fixed
   limit" to api\_get\_delivery\_errors() (#23259)
-  Improved the efficiency of removing queued messages (#21510)

SpamPanel:

-  Fixed the way the Condition is shown in the Error Details (Log
   Search) by changing the True / False response to Permanent /
   Temporary rejected (#23124)
-  Resolved issue with Archive Mail Preview not loading the message in
   Archive Search (#23180)
-  Resolved issue with the Spam Experts Logo showing when branding is
   disabled on sub-admins (admins) (#22596)
-  Resolved issue with error "×User ID should be a numeric value greater
   than 0" when logging out from the Administrator view (#23245)
-  Resolved issue with the Bandwidth Overview not displaying the usage
   when the domain name contains too many characters (#23200)
-  Added the option to generate custom submission spam reports (#21469)

Addons:

-  cPanel : Converted Hooks to new systems (#12896)
-  Plesk : Added the possibility to sort the domains from Z-A (#23137)

Build 78412 (2015-03-17)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  No new updates this week

Addons:

-  No new updates this week

Build 78377 (2015-03-10)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  An issue where generation of protection reports could fail when
   domains were removed during generation has been fixed (#23041)
-  The restriction preventing having API arguments that had the same
   value as the argument name has been removed (#22955)
-  The API help page no longer has clickable example links, to avoid
   accidental clicks (and therefore API calls) (#22955)
-  Increase logging of permanent delivery failures (#23114)

SpamPanel:

-  Resolved issue with Archive wrongly returning the error message:
   "404: Message not found." (#23047)
-  Resolved issue with Admins not being able to add sub-admins (#23004)
-  The Incoming Delivery Queue is now keeping selected search criteria
   when switching between pages (#23078)
-  Resolved issue with changing from "Mirroring" to "Stripping" in
   Archive Settings not registering the change (#23089)
-  Resolved issue with not being able to reset the password using the
   Retrieve Login Link (#22941)

Addons:

-  cPanel: Resolved issue with "Unable to retrieve configuration" error
   when trying to login (#22990)
-  cPanel: Search option added to the domain list page (#14361)
-  Plesk: Search option added to the domain list page (#14361)

Build 78049 (2015-03-03)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  The Authentication-Results header now also includes the
   authentication domain, as well as username (#23037)

SpamPanel:

-  Resolved issue with Archive search not showing encoded headers
   (#22830)
-  Resolved issue with the Domain Statistics not displaying the results
   correctly (#22977)
-  Resolved issue with incorrectly displaying of the characters: "<" and
   ">" when viewing raw messages in the Archiving Mail Preview (#23008)
-  Resolved issue with Header Value being wrongly moved to a new line
   when viewing the raw messages in the Archiving Mail Preview (#23007)

Addons:

-  P.O.A 2.0 - Initial Stable Release
   `here <https://my.spamexperts.com/kb/742/Aps-20.html>`__

Build 77754 (2015-02-24)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  TLS certificate verification has been re-enabled (#22804)
-  The local part of an email address (‘sam’ in ‘\ sam@example.com\ ’)
   is specified as being case sensitive. However, many systems treat it
   as case in-sensitive. There are new API methods to control whether
   the local part is treated as case sensitive or insensitive. Note that
   the default is case insensitive, which is a change from previous
   behavior. (#20581)
-  The "block hidden executables" setting now uses the same default
   system as other settings, where new domains will start with the "use
   the default" setting, rather than the option disabled (#22817)
-  Improvements to the efficiency of migrating log entries (#19970)
-  The api\_delivery\_queue() and api\_outgoing\_delivery\_queue() API
   methods now support paginated requests (#18406)
-  The IP whitelist/blacklist API methods now support paginated requests
   (#18406)
-  Improvements to the encryption mechanism in archiving (#11813)
-  The API method api\_list\_domains() is now able to filter the list of
   domains that are returned, and supports pagination. There is also a
   new API method api\_count\_domains() (#21102)

SpamPanel:

-  Added the ability to get ``recipient error`` details for more than
   just the previous two days (#19372)
-  Resolved issue with column alignment in Outgoing IP whitelist page
   (#22935)
-  Resolved issue with domain ordering via 'Upload CSV file' option
   (#22946)
-  Updated text when creating Software API users via the Software API
   user page (#22810)
-  Force lowercase username argument of the emailusers/add method
   (#22707)
-  Add support for sub-admins reseller list with '/api/reseller/list/'
   (#22247)
-  Hide deprecated calls from Spampanel API help (#21005)
-  Expanded permission system to allow granular access to create
   sub-admins (#22186)
-  Changed title description for add and edit pages at super-admin,
   domain and email level (#22811)
-  Resolved issue with ``Could not retrieve the Archiving REST API``
   Reference (#22750)

Addons:

-  cPanel: Resolved issue with 2 SpamExperts links in X3 theme (#22822)
-  cPanel: Resolved issue with ``Use IP as destination route`` option
   (#22936)
-  Plesk: Resolved issue with UI Updater (#22923)
-  Plesk: Resolved issue with ``Use IP as destination route`` option
   (#22936)

Build 77349 (2015-02-17)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only

SpamPanel:

-  No new updates this week

Addons:

-  cPanel: Resolved issue with 'per-package' enable/disable option
   (#8038)
-  cPanel: Added allowance for 4 MX records within configuration
   (#14588)
-  cPanel: Optimized domain refresh list with AJAX (#14589)
-  cPanel: Resolved issue with 2 SpamExperts links in X3 theme (#22822)
-  cPanel: Resolved issue with SpamExperts icon not shown in X3 theme
   (#22834)
-  cPanel: Resolved issue Paper Lantern theme not using the custom
   branding set in WHM (#22825)
-  cPanel: Resolved issue with SpamExperts branding shown in tit
