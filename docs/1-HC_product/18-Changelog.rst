.. _1-Changelog:

Changelog
=========

Build 107062 (2016-10-04)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Optimized the whitelist sender disparate settings check (#28080)

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 106752 (2016-09-27)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue with the Outgoing Log Search not showing results for
   temporarily locked users (#29839)
-  Resolved issue with 'Latest Results' search where no result would be
   shown if one of the Filtering Servers was unreachable (#29846)
-  Resolved issue with checking for 2048 DKIM key when
   'api\_set\_dkim\_selector' was used (#29766)

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 106467 (2016-09-20)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added support for working with multiple quarantine server to
   api\_release\_outgoing\_messsage and api\_release\_messsage (#29807)

Front-end / GUI:

-  Resolved issue with invalid/conflicting filenames in archive download
   zip by switching to use the internal message ID instead of subject
   (#29804)
-  Resolved issue with puny-encoded domains in domain, or email-users'
   usernames (#29763)

Plugins & Integration tools:

-  No new updates this week

Build 106107 (2016-09-13)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  DMARC check is now enabled by default for new cluster setups (#13858)
-  Optimized the error returned when blacklisting or whitelisting an
   already listed sender from the protection report (#29739)

Front-end / GUI:

-  Exposed DKIM and DMARC disabling functionality (#27684)
-  Resolved issue with log searches ignoring the chosen filtering server
   for latest results (#29679)

Plugins & Integration tools:

-  cPanel: Added PHP 5.4 as ``RECOMMENDED_VERSION``. Older PHP versions
   are no longer actively supported by this addon and as such will be
   restricted to a new ``frozen`` update tier, which will only receive
   new fixes for issues deemed critical. It is highly recommended to
   upgrade to a newer PHP version to have access to all the latest
   features (#24924)
-  Plesk (Windows and Linux): Added PHP 5.4 as ``RECOMMENDED_VERSION``.
   Older PHP versions are no longer actively supported by this addon and
   as such will be restricted to a new ``frozen`` update tier, which
   will only receive new fixes for issues deemed critical. It is highly
   recommended to upgrade to a newer PHP version to have access to all
   the latest features (#24924)

Build 105717 (2016-09-06)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added support for blocking extensions that have dots in them (e.g.
   tar.gz) (#29632)
-  Resolved issue with erroneous warning displayed when setting the DKIM
   selector and the TXT record is valid (#29614)
-  Optimized speed of authentication checks for outgoing user (#29595)
-  Updated delivery data with the latest temporary rejections (#27515)
-  Expose the ability to dissallow releasing for messages containing
   certain attachments from the protection report (#29512)

Front-end / GUI:

-  Exposed option to disallow release of emails with specific
   attachments at email user level (#29155)
-  Added Spampanel API call to set grained permissions for an admin
   (#29204)
-  Optimized ``/api/admin/list`` when ran for a specific admin (#29602)
-  Resolved issue with log searches for IP ranges/matches (#29642)
-  Resolved issue incorrect classification shown when unable to verify
   sender address (#29643)

Plugins & Integration tools:

-  APS 2.0: Resolved issue when retrieving context resources (#29611)

Build 105391 (2016-08-30)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 105026 (2016-08-23)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue causing sender to wrongly show as whitelisted (#29443,
   #29498)
-  Resolved issue with Archive expiry when JSON was un-terminated
   (#29455)

Front-end / GUI:

-  Resolved issue with Continue button on Add domain page (#29242)
-  Resolved issue with incorrect username details when viewing
   quarantined messages from the log search (#29388)
-  Resolved issue when trying to transfer domains already pending
   transfer (#29505)
-  Improved handling on Overview of bandwidth usage page for admins
   (#28623)
-  Removed deprecated check for Software API user permissions when
   logging into the UI (#29531)

Plugins & Integration tools:

-  APS 2.0: Resolved issue with setting protected products on admin
   creation (#29296)

Build 104645 (2016-08-16)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Improved handling of duplicate archiving attempts and archiving
   storage deduplication run (#29418)

Front-end / GUI:

-  Enabled the columns 'filtering server / Message ID / Sender hostname"
   to be displayed by default on log search pages (#21202)
-  Resolved issue with toggling an admin's 'active' status on Manage
   admins page (#29476)
-  Resolved issue with broken API domain/getroute backward compatibility
   (#29428)
-  Removed 'Select all' check box wrongly showing in the 'Email
   notification templates' section (#29282)
-  Adjusted error message returned on the reseller Bandwidth Overview
   section (#29421)
-  Adjusted error message returned in Report Spam section, when the
   reported message is missing required headers (#28760)

Plugins & Integration tools:

-  No new updates this week

Extra:

-  We included an additional workaround to specifically protect against
   CVE-2016-5696 in this update. Please note that also without this
   workaround the SpamExperts servers do not appear vulnerable, so this
   is just an extra measure (#29483)

Build 104349 (2016-08-09)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Improve multiple quarantine server support in a cluster, by adding an
   IMAP proxy that will automatically direct IMAP connections to the
   correct servers based on the domain name. (#27965)
-  Add support for whitelisting sender domains like \*@example.com in
   api\_whitelist\_outgoing\_sender (#29315)
-  Increased daily statistics expiry period to 30 days (#29248)
-  Ensure that the message status is "released" and not "removed" when
   releasing messages from the log search. (#26290)

Front-end / GUI:

-  Added ability to perform actions on all search results (#17394)
-  Resolved issue with re-ordering routes on Edit routes page (#29287)

Plugins & Integration tools:

-  Plesk Linux: Add-on installation aborts for Plesk versions higher
   than 12.5 notifying the user that our Plesk extension should be used
   instead (#29043)
-  Plesk Windows: Add-on installation aborts for Plesk versions higher
   than 12.5 notifying the user that our Plesk extension should be used
   instead (#29043)
-  APS 2.0: Resolved issue with error detection for
   ``setDomainProducts`` method (#29296)

Build 104059 (2016-08-02)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 103732 (2016-07-26)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added support for IPv6 networks as outgoing users. (#21620)
-  Resolved unicode handling issue with the
   api\_set\_recipient\_protection\_report\_template Software API
   (#29047)
-  Skip BATV check when delivering outgoing messages to incoming
   domains. (#28996)
-  Add .docm to default list of blocked extensions for new cluster
   installations (#29165)
-  Resolved issue when calling OCR to index images (#29176)
-  Resolved usage of api\_set\_backup\_settings with empty string
   (#29172)

Front-end / GUI:

-  Improved Compose Email page loading times (#29140)
-  Resolved issue with Email reply page on clusters with multiple nodes
   (#29136)
-  Updated Log Search page template for latest results (#29179)
-  Resolved issue with quarantine status for latest results (#29133)
-  Optimized dashboard for languages with long translations for section
   headings (#29194)
-  Optimized overflow issues with long domain names displayed in modal
   headings on Overview page (#29138)
-  Improved layout for "Default MX host names" input field on smaller
   resolutions (#28439)

Plugins & Integration tools:

-  No new updates this week

Build 103490 (2016-07-19)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  No updates this week

Front-end / GUI:

-  Add Control Panel API method to add Outgoing Users (#27493)
-  Improved error handling for API calls that give an error or timeout
   (#29105)
-  Resolved issue with Telnet action on Overview page (#29107)
-  Resolved issue viewing messages on Outgoing delivery queue page
   (#29115)
-  Resolved issue with non-ASCII domain names on Outgoing reports page
   (#29116)
-  Resolved issue with non-ASCII domain names for the Administrator's
   contact field (#29119)

Plugins & Integration tools:

-  Plesk Linux: Resolved compatibility issue with php 5.2 (#29111)
-  Plesk Windows: Resolved compatibility issue with php 5.2 (#29111)

Build 103231 (2016-07-12)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Restructure submission logging to be more optimal for multi domain
   searches (#25419)

Front-end / GUI:

-  Exposed the ability to compose/send mail from Spampanel (#21189)
-  Resolved issue accessing quarantined outgoing messages that could
   sometimes trigger an error when trying to locate the message (#29030)
-  Optimized the 'Manage outgoing users' page at admin level for admins
   with large amount of domains (#28691)
-  Optimized the 'Global statistics' page at admin level for admins with
   large amounts of domains (#28995)
-  Resolved issue with a write callback wrapper mishandling json
   responses (#29059)

Plugins & Integration tools:

-  cPanel: Added better error reporting when toggle protection fails due
   to the domains limit from the license (#29016)
-  Plesk Linux: Added better error reporting when toggle protection
   fails due to the domains limit from the license (#29016)
-  Plesk Windows:Resolved login issue for alias domains in reseller
   interface (#29052)
-  Plesk Windows: Added better error reporting when toggle protection
   fails due to the domains limit from the license (#29016)

Build 102939 (2016-07-05)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added improvements to delivery when delivering to multiple recipients
   are using disparate blacklisted settings (#28079)
-  Resolved issue with camel-cased routes. (#28928)
-  Resolved issue with user column while doing an "in progress" search
   using api\_find\_outgoing\_messages (#28881)

Front-end / GUI:

-  Optimized Control Panel API to support providing data for sub-admins
   when called as an admin (#28523)
-  Added a new 'no common passwords' password policy (#22391)
-  Exposed the option to set the number of days that archived messages
   are kept for domain users, up to the limit configured at cluster
   level (#17620)
-  Updated ``/api/domain/exists`` to return correct status of aliases
   when called as an admin (#28855)
-  Optimized the procedure to update the profile for an admin with
   multiple sub-admins and domains (#28896)
-  Resolved issue with ``Toggle identity lock`` not working on outgoing
   log search page when viewing latest results (#28878)
-  Optimized domain ownership validation when transferring domain to a
   sub-admin for admins with mutiple domains (#28941)
-  Resolved redirect issue when moving from domain level back to admin
   level (#28944)

Plugins & Integration tools:

-  No new updates this week

Build 102688 (2016-06-28)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Optimizations to our update systems. (#26491)
-  A new parameter, sender\_flag, is now available for
   api\_whitelist\_sender, api\_whitelist\_local\_part\_sender,
   api\_blacklist\_sender, api\_blacklist\_local\_part\_sender.  This
   allows choosing where the list should be applied and can be either
   envelope sender, from header or both. (#28078)
-  Senders whitelisted or blacklisted from the protection report will
   now only apply on the envelope header instead of both the envelope
   sender and from header. (#28078)

Front-end / GUI:

-  Optimizations to the "Dashboard" page (#24409)
-  Fixed handling of invalid value provided for the ``domains`` argument
   for several Spampanel API calls (#28721)
-  Resolved specific permission issue on generated documentation
   (#28820)

Plugins & Integration tools:

-  APS 2.0: Resolved issue caused by incorrect case-sensitive usernames
   comparison (#28765)

Build 101985 (2016-06-21)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue with using multiple domains in
   api\_set\_outgoing\_interfaces. (#28669)

Front-end / GUI:

-  Resolved issue with inconsistent behavior when default activated
   admin products had not been configured (#28609)
-  Updated help text for ``Block potentially unwanted attachments``
   (#28660)
-  Resolved text alignment issue on 2FA auth page at lower resolutions
   (#28677)
-  Optimized ``/api/user/list/`` for admins with a lot of sub-admins and
   domains (#28642)

Plugins & Integration tools:

-  APS 2.0: Implemented automatic protection of all resources when the
   application is added to the existing account (#28504)
-  APS 2.0: Spampanel domain- and email user verification procedure has
   been optimized (#28643)
-  APS 2.0: Resource ID lists are sent in PUT request body instead of
   query string to avoid too long URLs (#28570)

Build 101619 (2016-06-14)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added IMAP support for training and releasing messages from Outlook
   2013+ (#27659)
-  Optimize usage of the api\_list\_domains API when using pagination
   (#28590)

Front-end / GUI:

-  Added a new archive usage page for admins (#10960)
-  Added lock/unlock identity as actions in log searches (#25558)
-  Improved the catch-all check to work more effectivley with Exchange
   2013+ servers (#25850)
-  Updated the 'Attachment restrictions' page (#27847)
-  Resolved issue with product indicators on 'Overview' page for domains
   using default server-wide settings (#28600)
-  Optimized ``/api/admin/list`` API method for admins on large servers
   (#28593)
-  Optimized account updates for admins with premium branding (#28608)

Plugins & Integration tools:

-  Plesk Linux: Resolved issue when incorrectly trying to check
   protection status on aliases that are not set to be processed as main
   domains (#28648)

Build 101357 (2016-06-07)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added Optimization to the on demand archive index building (#28459)
-  Resolved issue with the outgoing filter report (type 2) (#28561)

Front-end / GUI:

-  Updated "Search" option on the "Manage admins" page to also include
   sub-admins (#25421)
-  Optimized existing "Outgoing reports" to handle multiple domains
   (#22303)
-  Exposed archiving indexing options (#27767)
-  Added further Admin options ("Release and Train", View" and "Remove")
   when releasing outbound messages via the log search (#28041)
-  Resolved on-screen error when editing a brand for admins that have
   sub-admins with domains assigned (#28468)

Plugins & Integration tools:

-  APS2: Debug logging is turned off by default (#28527)

Build 101111 (2016-05-31)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added the ability to get the archive usage per storage node in the
   Archive API. (#25454)
-  Resolved issue that could cause recipients to be incorrectly
   temporarily rejected when sending multiple messages in the same
   connection. (#28454)

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 100828 (2016-05-24)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Removed the blacklist/whitelist option from the protection reports,
   for messages that have no sender. (#28407)
-  Generic improvements in handling connections from unverified sources.
   (#24096)

Front-end / GUI:

-  Exposed statistics page at the admin level. (#21736)
-  Removed the ability to log into Control Panel API with software API
   credentials. (#25854)
-  Optimised Control Panel API security checks for admins that have a
   large number domains. (#28393)
-  Resolved a script issue for the "On-demand domain report" page.
   (#28425)
-  Optimised error handling for the "Upload CSV" functionality. (#28402)

Plugins & Integration tools:

-  cPanel: Resolved an issue with “Add/Remove a domain when the email
   routing is changed in cPanel” configuration option (#28201)

Build 100500 (2016-05-17)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Add a new parameter "identity" to the api\_set\_outgoing\_interfaces
   API that allows setting a delivery interface to an identity. A new
   API is also now available api\_get\_outgoing\_interfaces\_json, that
   allows getting the list of configured delivery interfaces in a JSON
   format. (#20812)
-  The block hidden executables filter will now also block ".hta" files
   in compressed attachments. (#28308)

Front-end / GUI:

-  Added progress bar to the "Manage Products" page. (#23493)
-  Added a bulk "download" option for archived messages. (#25859)
-  Resolved issue with user not being logged-out after set to inactive
   in some case. (#28299)
-  Fixed vertical alignment for checkboxes and drop-down buttons on
   several Control Panel pages. (#28314)
-  Resolved an translation string issue on the Sender Whitelist page
   (#28260)

Plugins & Integration tools:

-  No new updates this week

Build 100147 (2016-05-10)
~~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue with unsure subject notation not being correctly
   added. (#28216)
-  Resolved issue with the unlock link from the lock notification email.
   (#28207)
-  Resolved issue with the wildcard domain check for black and white
   lists (#28248)
-  Resolved classification issue of outbound messages delivered to
   inbound filtered domains. (#27106)

Front-end / GUI:

-  Optimized the loading of jQuery progress bars. (#27157)
-  Added method to verify ownership of a domain. (#25411)
-  Resolved an issue with incorrect error message shown by
   ``/api/domain/add`` on clusters without archiving product. (#28218)

Plugins & Integration tools:

-  cPanel, Plesk (Linux), Plesk (Windows): Optimized add-on
   uninstallation procedure. (#25450)
-  APS2:Fixed wrong condition of the Login button availability for
   service users on customer level. (#27959)
-  APS2: Resolved the auto-provisioning issue of the first added domain.
   (#27740)

Extra

-  Patched OpenSSL for the following vulnerabilities: CVE-2016-2107,
   CVE-2016-2105, CVE-2016-2106 ,CVE-2016-2109, CVE-2016-2176. (#28253)

Build 99956 (2016-05-03)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolve issue in api\_clear\_retry\_hints causing the hints to be
   removed on the recipient and not the route (#28195)

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 99751 (2016-04-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  The Archiving MX record check is now skipped for incoming messages
   (#27421)
-  Fix usage of the optional size argument in
   api\_remove\_quarantined\_message and
   api\_remove\_outgoing\_quarantined\_message (#27223)
-  Domains set with api\_set\_outgoing\_sender\_check\_disabled\_domains
   are now case insensitive (#28134)

Front-end / GUI:

-  Added a search option to the Periodic User Report Section (#27261)
-  Allow for blank a Administrator contact (#26772)
-  Removed usage of deprecated api\_get\_recipient\_error\_details
   (#26415)
-  Control Panel API '/api/admin/add' now allows to create sub-admins
   directly (#26353)
-  Improved handling of archive index creation errors (#28105)
-  Resolved an issue with resetting an admin's password policies to
   default (#28117)

Plugins & Integration tools:

-  No new updates this week

Build 99451 (2016-04-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Resolved issue with specific outgoing abuse reports delivery when no
   incoming product is available. (#27818)
-  Optimized error response if a country code is provided that is the
   wrong length in api\_get\_csr\_and\_key. (#27836)
-  Resolve issue with displaying non-ASCII sender addresses in the PDF
   protection report. (#27875)
-  Improve rejection message for URLs blocked on Google SafeBrowsing.
   (#27992)

Front-end / GUI:

-  Resolved issue with super-admins not being able to enable a product
   for a domain at server level if that product was disabled by default.
   (#27817)
-  Optimized “Overview” and “Add Domain” pages for Domain and Email user
   levels. (#27991)

Plugins & Integration tools:

-  cPanel: Optimized alias handling for add/remove hooks, toggle
   protection actions and bulk protect (#27644)
-  Plesk for Linux: Optimized alias handling for add/remove hooks,
   toggle protection actions and bulk protect (#27644)
-  Plesk for Windows: Optimized alias handling for add/remove hooks,
   toggle protection actions and bulk protect (#27644)
-  DirectAdmin: Added optional debug logging. (#27835)
-  APS2.0: Resolved issue with protection status not being shown
   correctly for users with multiple subscriptions. (#27741)
-  APS2.0: Implemented button for service users to login at email user
   level. (#27778)

Build 98800 (2016-04-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week

Build 98781 (2016-04-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added optimisations to the block hidden executables filter. (#27801,
   #27799, #27797, #27809)
-  Resolved issue with api\_get\_outgoing\_blacklist where the username
   argument was “\*”. (#27832)
-  Resolved issue with protection report releases when using multiple
   quarantine servers. (#27791)

Front-end / GUI:

-  Resolved layout issue for language selector. (#27780)
-  Resolved issue with the ``Unbind from admin`` option incorrectly
   exposed at admin level. (#27770)
-  Resolved issue with Internet Explorer when reporting (non) spam
   messages via drag and drop from the UI. (#27823)

Plugins & Integration tools:

-  cPanel, Plesk for Linux: Resolved issue when reading the
   configuration using the binary, for a normal (non-root) user, which
   failed to properly parse quotes. (#27717)

Build 98505 (2016-03-29)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Blocked domain(s) will be added to the Evidence header for messages
   blocked because of bad URL reputation match. (#21801)
-  The api\_set\_locked\_identity\_response\_code API call can now also
   accept a "blackhole" code, which will blackhole all messages sent
   from locked identity. (#25315)
-  The .scr and .lnk extensions have been added to the list of blocked
   extension when the block hidden executable feature is active.
   (#27677)

Email Archiving (services):

-  A new Archive API call (/archive/select\_part/[domain]/) is now
   available that allows the selection of what messages parts should be
   indexed. (#21799)

Front-end / GUI:

-  Exposed email alias feature in SpamExperts Control Panel API.
   (#22636)
-  Added IE8 browser warning for users to update to a newer version.
   (#26545)
-  Resolved the incorrect creation of an authticket for an alias.
   (#27651)
-  Resolved issue with product selection when using the “Manage
   Products” option at Admin level. (#27689)
-  Resolved on screen error when accessing the outgoing log search from
   Admin level. (#27709)
-  Recipients or senders containing a colon will not be able to be
   whitelisted or blacklisted. (#27711)
-  Resolved an issue which prevented setting the 'Action for oversized
   messages' to 'reject'. (#27723)
-  Resolved erroneous response when adding domains with specific options
   enabled. (#27690)

Plugins & Integration tools:

-  cPanel: Resolved an issue with "Add subdomain as alias" option not
   working when creating a new account. (#26940)

Build 98121 (2016-03-22)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Additional actions are now available in the protection reports. The
   protection report now also includes option to: release and train,
   release and whitelist and remove and blacklist (#23957)
-  The delivery\_data column from api\_find\_messages and
   api\_find\_outgoing messages will now include the destination
   rejection messages when recipients are rejected because of a failed
   callout(#23530)
-  Added a new API for getting the IP whitelist in a JSON format:
   api\_get\_ip\_whitelist\_json (#27622)
-  Correctly include the last day of the interval when requesting an
   archive export (#27619)

Front-end / GUI:

-  Added more Control Panel API methods for managing local recipients
   (#25826)
-  Added Control Panel API method to set an admin as sub-admin for a
   different admin (#27182)
-  Updated domain archiving removal procedure to also set it to expire
   (#23973)
-  Resolved an issue when creating/removing new domain aliases not
   clearing the corresponding API cache (#27585)
-  Resolved 2FA generated codes' compatibility with Google's
   Authenticator (#27604)
-  Resolved an issue with archive export failing when real-time indexing
   is disabled (#27606)
-  Resolved an issue with '/api/domainuser/add\` allowing to create
   domain users for aliases (#27652)

Plugins & Integration tools:

-   cPanel: Resolved addon compatibility issue with PHP 5.2 (#27523)
-   cPanel: Updated error message when toggling protection for an alias
   domain (#27198)
-   Plesk (Linux): Updated installer to exit if the required 'at'
   package is not present (#27252)
-   Plesk (Linux): Resolved addon compatibility issue with PHP 5.2
   (#27523)
-   Plesk (Linux): Updated error message when toggling protection for an
   alias domain (#27198)
-   Plesk (Windows): Resolved addon compatibility issue with PHP 5.2
   (#27523)
-   Plesk (Windows): Updated error message when toggling protection for
   an alias domain (#27198)

Build 97774 (2016-03-15)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  Imposed a restriction against adding local recipients containing a
   comma character. (#27415)
-  Fixed issue with handling destination routes with duplicate hostnames
   and different ports. (#27488)
-  Fixed issue when transferring non-ASCII domains from an admin to
   another. (#27487)

Plugins & Integration tools:

-  No new updates this week

Build 97490 (2016-03-08)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  The Archive API documentation page will display both the domain
   endpoints and the default endpoints. For example both
   /archive/days/{domain}/ and /archive/days/ are now included in the
   help page. (#25535)

Front-end / GUI:

-  Optimized the procedure for retrieving all sub-administrators.
   (#27395)

Plugins & Integration tools:

-  No new updates this week.

Build 97254 (2016-03-01)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Handle protection reports for quoted local parts. (#25428)
-  Handle error when invalid input to the
   api\_get\_recipient\_error\_details Software API. (#26439)
-  Add a pair of new API calls api\_set\_predata\_reject and
   api\_get\_predata\_reject that allows enabling DNSBL rejections at
   RCPT time. The new API calls support both temporary and permanent
   rejections. Note that this should be used when absolutely necessary
   as these messages will not be quarantined. (#26965)
-  A new parameter (skip\_concurrent\_connection\_limit) has been added
   to api\_whitelist\_ip. This allows whitelisting certain IPs from the
   concurrent connection limit for incoming connections. (#26882)
-  Optimized the Archive indexing for large messages. (#22187)
-  Fix server statistics API call when there are no queued messages.
   (#27289)

Front-end / GUI:

-  Improved message preview from protection reports for admins and
   super-admins. (#27256)
-  Improved validation on the 'Sender whitelist' page. (#25626)
-  Resolved issue with ``admin/getarchivingdiskspaceusage`` on clusters
   with many of archiving accounts. (#27290)
-  Improved layout when adding destinations routes on 'Add domain' page.
   (#27110)

Plugins & Integration tools:

-  cPanel: Optimized handling of password update on the 'Configuration'
   page. (#27304)
-  Plesk (Linux): Optimized handling of password update on the
   'Configuration' page. (#27304)
-  Plesk (Windows):Optimized handling of password update on the
   'Configuration' page. (#27304)
-  cPanel: Improved cleanup when uninstalling the cPanel plugin.
   (#24706)
-  Plesk (Windows): Resolved issue with passwords containing special
   characters. (#27128)

Build 96945 (2016-02-23)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Add the ability to control various load settings with a new pair of
   API calls, api\_set\_load\_settings and api\_get\_load\_settings.
   These can be set for incoming/outgoing and for specific servers only.
   Some of these options only take effect after the next update.
   (#18356)
-  Expand the types of archive compressors checked when the "Block
   hidden executables" feature is activated
   (api\_set\_block\_hidden\_executables). Now includes: zip, 7z, rar,
   tar.gz, tar.bz2, tar, gz and bz2. (#26134)
-  Resolved archive index rebuilding issue for incorrectly encoded
   messages. (#27235)
-  Optimized the logo position in the PDF protection report. (#27214)

Front-end / GUI:

-  Optimized interface usability on the Periodic User Report page.
   (#26405)

Plugins & Integration tools:

-  No new updates this week

Build 96647 (2016-02-16)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Attachments with the ".js" extension are now included in the blocked
   extensions list for new cluster installations. Note that if you reset
   the value using the api\_set\_blocked\_extensions API, the ".js" will
   be included.(#27086)

Front-end / GUI:

-  Resolved concurrency issue which could have triggered an error when
   emptying the spam quarantine from the interface (#27129)
-  Fixed missing icons on the 'Edit routes' page description (#27109)

Plugins & Integration tools:

-  No new updates this week

Build 96454 (2016-02-09)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Add ability to set different SSL certificates for specific hostnames
   via a new API api\_set\_domain\_https\_certificate. Information about
   any existing certificate can be retrieved with another new API:
   api\_get\_domain\_https\_certificate\_info. (#26060)
-  Allow non-ASCII queries in the Archive API when searching messages.
   This is done via a charset table mapping. (#25831)
-  Stop quarantining messages that are rejected because they have
   restricted characters in their local-part recipient address. (#27071)

Front-end / GUI:

-  Resolved issue with admins not being able to access domains belonging
   to their sub-admins from the interface. (#27024)
-  Improved handling of multi domain transfers from the interface.
   (#26864)
-  Improved handling when loading the "Periodic user report" page when
   the destination mail server cannot be reached. (#26929)
-  Updated the "Quarantine" and "Unsure notation" thresholds sliders.
   (#25926)
-  Added Control Panel API support for adding local recipients. (#22004)
-  Updated /api/authticket/create to allow admins to generate an
   authticket for themselves or any of their sub-admins. (#27022)
-  Optimized layout of threshold fields on the "Filter settings" page.
   (#27079)
-  Updated all Spampanel API calls to allow admins to execute calls on
   domains that belong to sub-admins in their hierarchy. (#27068)
-  Adjusted "password" variable to be optional for Control Panel API
   /api/admin/add/username/. (#27055)

Plugins & Integration tools:

-  DirectAdmin: Resolved issue with automatic domain provisioning when
   “Do not Protect remote domains” was unchecked (#27001)

Build 96147 (2016-02-02)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Optimized error response when trying to whitelist an outgoing sender
   for an outgoing user that does not exist in
   ‘api\_whitelist\_outgoing\_sender’ (#26889)
-  Optimized classification for outgoing senders that cannot be verified
   because of temporary problems (#27021)

Email Archiving (services):

-  A new option ‘raw\_message’ is now available for the the Archive API
   when getting a message. This parameter allows getting the raw message
   instead of JSON (#25858)

Front-end / GUI:

-  Dashboard icons are now encoded in the main content and load faster
   (#24411)
-  Added wildcard support for sender white and blacklist pages. (#26200)

Plugins & Integration tools:

-  cPanel: Resolved installer issues on new servers (#26986)
-  cPanel: Improved cPanel API availability check (#26992)
-  DirectAdmin: Resolved issue with reverting MX records when ‘Toggle
   Protection’ is used (#26937)

Build 95900 (2016-01-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Two new Software API calls are now available
   api\_set\_outgoing\_sender\_check\_disabled\_domains and
   api\_get\_outgoing\_sender\_check\_disabled\_domains. These can be
   used to disable the callout verification done on the sender address
   for specific domains. (#20696)
-  SMTP connections rejected because of invalid recipients or sender
   addresses are now marked as "unknown" instead of "spam" in the log
   search. (#25640)

Front-end / GUI:

-  Make it possible for /api/authticket/create/username/ to create an
   auth ticket for super-admins (#25575)
-  Improved handling of ``/api/admin/update/`` (#26938)

Plugins & Integration tools:

-  cPanel: Add-on should return informative error if Spampanel API
   communication fails (#23126)
-  cPanel: Make installation procedure a driver-specific part (#24431)
-  Plesk: Add-on should return informative error if Spampanel API
   communication fails (#23126)
-  Plesk: Make installation procedure a driver-specific part (#24431)
-  DirectAdmin: Resolved compatibility issue with PHP versions lower
   than 5.5 (#26942)

Build 95660 (2016-01-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  Added a nicer error when blacklisting the same sender twice with
   api\_set\_outgoing\_sender\_blacklist.(#25498)
-  Added a nicer error when a invalid argument is passed to the
   filter\_by parameter of api\_list\_domains.(#26682)
-  Resolved issue with api\_set\_dkim\_certificate error when setting an
   new certificate (#26799)

Front-end / GUI:

-  Resolved issue with incorrect status code for missing resources
   (#25518)
-  Resolved issue with spam actions when viewing a quarantined email
   from the protection report (#26671)
-  Resolved incorrect brandname for sub-admins when having private label
   enabled (#23551)
-  Resolved validation issue when updating a server-wide brand (#26678)
-  Added better handling for alert messages containing HTML markup
   (#26624)
-  Resolved caching issue with domain search at admin level (#26706)
-  Resolved issue with filter by "All" option at admin level Overview
   page (#24586)
-  Resolved issue with the "Number of days available" input (#26805)
-  Resolved email validation for addresses at new TLDs (#26814)

Plugins & Integration tools:

-  cPanel: Resolved compatibility issue with cPanel v54 (#26723)

Build 95446 (2016-01-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  cPanel: Due to a possible compatiblity issue on the new v54 version
   of WHM, we have temporarily restricted access at user level for the
   latest cPanel version. We've contacted cPanel about this and we will
   release an update as soon as possible. Our apologies for the
   inconvenience. (#26723)
-  DirectAdmin: Resolved issue with the 'Process domain pointers' config
   option and updated hooks accordingly (#26656)

Build 95264 (2016-01-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Filtering (services):

-  This build includes general filtering / performance updates only

Front-end / GUI:

-  No new updates this week

Plugins & Integration tools:

-  No new updates this week
