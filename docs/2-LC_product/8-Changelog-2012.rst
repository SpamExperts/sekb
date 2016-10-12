.. _2-Changelog-2012:

Changelog 2012
==============

Build 52150 (2012-12-20)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Allow outgoing user passwords to be changed at the domain level
    (#16806)
-  Spampanel API improved handling of IDN domains (#16755)

Build 51968 (2012-12-13)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Authticket support for IDN domains (#16745)
-  Associate IDN domains added via Spampanel API with the appropriate
   reseller (#16746)
-  When searching the global log, the domain should not be lost when
   changing the sorting (#16783)
-  Weekly/monthly outgoing limits are now exposed from the frontend
   (#16715)

Plesk add-on:

-  Create a single button for the client- and domain login (#16379)
-  Force lower-case domains on login (#16676)
-  Improved validation of IDN domains (#16754)
-  Properly update custom brandname (#16717)
-  Plesk 9 work around to list domains for domain administrators
   (#16701)

Build 51788 (2012-12-06)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Archiving improved processing of re-deliveries for email with quoted
   fields (#16667)

Build 51590 (2012-11-29)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Improved documentation for uploading CSV to add users to the
   recipient periodic report (#16580)
-  Reload the queue after force retrying a message successfully (#16631)
-  Improved redelivery process of archived messages (#16618)
-  Reset archive search query when switching between user levels
   (#16613)

Build 51398 (2012-11-22)
~~~~~~~~~~~~~~~~~~~~~~~~

Software

-  Filtering CPU resource optimizations (#16514)

Spampanel:

-  Improved support for mass operations on large number of domains
   (#16461) 

Build 51261 (2012-11-15)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Fix in api\_clean\_dns\_cache to properly flush the DNS cache on all
   nodes (#16507)
-  Enhancement for the option to force deliver queued emails to ensure
   the message is immediately retried (#16521)

Spampanel:

-  DKIM key size generation increased to 2048 bits (#16345)
-  Greek language added (#16224)
-  Show disabled incoming filtering for domains in the domain overview
   (#16482)
-  Allow resizing of the columns for the log search / email queue table
   (#16481)
-  Allow adding punnycode domains by resellers (#16453)
-  Retain set values on reseller creation page when an error is returned
   (#16488)
-  Force lowercase domains during the CSV import (#16492)
-  Properly handle periodic user report entries with a comma in the
   username (#15782) 

Build 51109 (2012-11-08)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added new API calls api\_[g\|s]et\_maximum\_messages and
   api\_[g\|s]et\_excessive\_messages\_per\_connection\_behaviour to
   allow overruling the build-in variables for these settings (#12882)

Spampanel:

-  Improved custom session timeout handling (#16265)
-  Do not allow commas in per-user recipient report addresses (#15782)
-  Properly parse IP whitelist entries with additional options (#16425)
-  SpamExperts branding issue resolved at login for clusters without
   Private Label (#16446)

POA APS add-on:

-  Add incoming/outgoing/archiving product provisioning to APS, please
   read the `upgrade
   nodes <https://my.spamexperts.com/kb/49/Parallels-Automation-addon.html>`__
   (#13795)

Build 50943 (2012-11-01)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Prevent emails getting accepted for non-existing recipients when
   applying the Local Recipients feature (#16401)

Spampanel:

-  Do not start an automatic all-domain search after returning from a
   domain-level search (#16352)

Plesk add-on:

-  Expose all allowed domains to resellers (#16169)
-  Stop using the "at" command for command in Plesk (#16183)

Build 50778 (2012-10-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  A security update resolving a potential
   `vulnerability <https://lists.exim.org/lurker/message/20121026.080330.74b9147b.en.html>`__
   with Exim has been applied to all servers (#16342)

Build 50778 (2012-10-25)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Change to case-insensitive search on the domain overview page
   (#15417)
-  Improved handling of IDN/punny-code domains (#16295)
-  Show errors when domains have failed to be added as part of the CSV
   import (#16298)
-  Do not list disabled products as enabled, when editing domains'
   products (#16342)

Build 50554 (2012-10-18)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added new API calls api\_[g\|s]et\_valid\_helo\_characters to control
   allowed HELO characters (#11925)
-  Non-ASCII character handling in filename passed to
   api\_set\_https\_certificate API call (#16230)
-  Archiving search issue resolved for ".at" domains (#16258)

Spampanel:

-  One-click-login (authticket) branding issue resolved for unassigned
   domains  (#16141)
-  Archive re-delivery system improvement to preserve all original
   headers (#16118)
-  Issue resolved whitelisting IP address in French language (#16270)
-  Correct ordering of routes when adding new domains (#16276)

Build 50280 (2012-10-11)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Prevent against IPv6 addresses being added to the sender/recipient
   whitelist/blacklist (#16112)
-  Prevent administrators from adding outgoing users if the outgoing
   product is not enabled  (#16158)
-  Domain statistics date/time display issue fixed for custom timezone
   settings (#16177)

Plesk add-on:

-  The Plesk for Linux add-on has been fully rewritten. A `public
   beta <https://my.spamexperts.com/kb/469/Plesk-Addon.html>`__ is now
   available. (#14439)

Build 50155 (2012-10-04)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  If rule checks are disabled, also skip EHLO sender verifications
   (#16103)

Spampanel:

-  Prevent any header modifications when redelivering archived emails
   (#16118)
-  Added Spampanel API call to enable/disable archiving (#15306)
-  Enforce correct branding for authtickets (#16141)

Build 50046 (2012-09-27)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Ensure queue runners complete with large queue sizes (#15945)
-  Default PTR EHLO improved handling of temporary nameserver issues
   (#16053)
-  Delivery IP selection also use set IPs to SpamExperts' managed
   servers (#15507)
-  API call api\_get\_outgoing\_ehlo documentation update regarding
   default PTR setting (#16074)

Spampanel:

-  Increase session timeout / make it configurable (#12611)
-  Automatically apply reseller branding to newly added domains (#16091)
-  Add warning when setting very low email size limit (#14092)
-  Improved performance handling of quarantined emails with many To
   addresses (#15428)
-  Improved IPv6 validation for the IP whitelist (#15933)
-  Stop allowing IP addresses being added to the sender
   whitelist/blacklist (#16035)
-  Set correct protection report template for recipient reports (#16048)

APS add-on:

-  Switch the way we count domains, which is being used for resource
   reporting (#15922)

Build 49898 (2012-09-20)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Use reverse IP as default HELO (#14983) 

Spampanel:

-  Improved XSS protection (#16026)

Build 49743 (2012-09-13)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  New API calls api\_[g\|s]et\_recipient\_report\_template to retrieve
   the recipient protection report template (#9822)
-  Include SMTP conversation data in bandwidth recording (#13570)
-  Improved api\_get\_recipient\_error\_details to handle more cases
   (#14336)
-  Improved error handling api\_[g\|s]et\_filter\_status with bad input
   (#15514)
-  Added new feature
   api\_[g\|s]et\_block\_password\_protected\_attachments to manage
   blocking of password protected attachments (#15074)
-  Added new feature api\_[g\|s]et\_scanned\_linked\_extensions to
   manage extensions included in virus scanning (#12940)

Spampanel:

-  Recipient report enabling verification to prevent duplicate
   activation  (#15866)
-  Improved XSS protection (#15942)

Build 49542 (2012-09-06)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Disable access to the Apache2 icons folder (#15870)
-  Expose the invalid HELO used in log search results (#15853)

Spampanel:

-  Force create per-user quarantine box when enabling the user report
    (#15824)
-  Improved explanations quarantine settings page (#11538)
-  Case insensitivity mass destination route change option (#15850)

Build 49370 (2012-08-30)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Logging improvement to provide clear reason if a wrong SMTP sequence
   is used (#15750)
-  API call api\_find\_messages proper handling of multiple specified
   "classification" variables (#15738)
-  API call api\_disable\_recipient\_protection\_report improved to
   allow for recipients with non-ASCII characters (#15760)
-  API calls api\_set\_dkim\_certificate/api\_set\_dkim\_selector
   adjustment to support domain names with a dash (#15800)

Spampanel:

-  Improved handling of Japanese characters for the archiving product
   (#15743)

cPanel add-on:

-  Domain sorting for the list in WHM (#13298)
-  Handling for duplicate domains in cPanel (#14697)
-  Workaround for cPanel DNS update race-condition bug (#14566)
-  Proper handling of addon domains in case addon/parked domains are
   configured to be added as an alias (#14736)
-  Improved detection mechanism for cPanel "remote domains" (#14809)

Build 49228 (2012-08-23)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Change archive API recipient search to use an exact match (#15652)
-  Properly expire quarantine for per-user account (#15627)

Spampanel:

-  Bandwidth overview fix to include last 24 hours (#15741)

Build 49124 (2012-08-16)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Sanitise recipients when the auto-enabling of the user protection
   report is active (#15722)

Build 48938 (2012-08-09)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Protection report generation issues with non-ASCII data fixed
   (#15588)
-  Added new software API calls api\_count\_messages and
   api\_count\_outgoing\_messages to retrieve a count of matching log
   results (#13571)
-  Improved reverse DNS lookup handling for Local Cloud nodes when
   delivering locally (#15611)
-  Outgoing email handling speed improvements for bad/invalid From:
   headers (#15617)

Spampanel:

-  Overview domain search reset button fix for IE 9 (#15613)
-  Issue fixed saving IP addresses allowed for administrator access
   (#15536)
-  Always show upload form besides drag drop functionality to report
   spam (#15423)
-  Pagination issues solved for removal of entries on sender whitelist
   (#15532)
-  Allow to set the default domain email address to blank (#15581)
-  Archived message preview show scrollbar for long lines (#15538)

Build 48774 (2012-08-02)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  XSS vulnerabilities resolved (#15534)

Build 48698 (2012-07-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Password recovery bug with failing template resolved (#15433)

Build 48542 (2012-07-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Rewritten software API return errors to provide better understandable
   information (#11111)
-  When changing available services for a domain as reseller, ensure
   other domains remain unchanged (#15385)

Build 48437 (2012-07-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improved handling of DKIM signatures for whitelisted senders (#15307)
-  Proper error handling for non-ASCII sender hosts in
   api\_find\_messages (#13975)
-  New API call api\_retry\_time\_outgoing to retrieve the scheduled
   retry time of a queued outbound email (#12866)
-  API call api\_delivery\_queue speed improvements with larger queues
   (#12863)
-  API call api\_get\_queue\_reason\_outgoing speed improvements
   (#12916)
-  SPF fix to force a block in case of verification failure (#15349)
-  Speed up the outgoing filter by skipping sender verification if not
   enforced (#15358)
-  Prevent duplicate message logging with emails in same outgoing
   connection (#13807)
-  New API calls to control the HELO
    api\_set\_incoming\_ehlo, api\_get\_incoming\_ehlo, api\_set\_outgoing\_ehlo, api\_get\_outgoing\_ehlo
   (#14468)
-  API call api\_find\_messages now includes HELO information for
   connections rejected with invalid HELO (#13525)
-  API returns nice error if HTTP method GET is not used (#15357)
-  Message processing change not to rewrite the envelope-from for
   aliased domains (#15383)
-  API call api\_unblacklist\_sender improved handling of non-ASCII
   characters (#15402)

Spampanel:

-  Resolved error when disabling private label for a reseller (#15384)
-  Statistics bandwidth shown per classification group (#15405)

Build 48332 (2012-07-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Automatically add the protection report templates to new resellers
   (#12657)
-  Quarantine uncheck the "check all" selectbox in case individual
   messages are deselected (#12718)
-  Quarantine remove the option to bulk release messages (#15253)
-  Reseller bandwidth overview wrongly formatted date in calendar
   selection fixed (#15334)

Build 48162 (2012-06-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Additional pre-data recording to further improve filtering
   technologies (#13342)
-  API call api\_delivery\_queue improved with search functionality
   (#12179)
-  API calls api\_find\_messages/api\_find\_outgoing improved with
   option to search for message ID (#13651)
-  Logging of outgoing filtering traffic improved to record temporary
   issues verifying the sender (#15143)
-  API call api\_get\_recipient\_error\_details improved to handle
   messages with the same sender/recipient (#15272)

Build 47971 (2012-06-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improved error handling for the software API call
   "api\_set\_valid\_local\_part\_characters" when provided with wrongly
   encoded variables (#15224).

Spampanel:

-  Improved memory and error handling when editing the reseller
   permissions  (#14965).
-  Moving domains search results adjusted to also return partial search
   matches (#15209).
-  Adjustment to restricted outgoing user log search variables to allow
   email users to search the logs as part of an IP smarthost account
   (#12616).
-  Issue resolved where not all domains were available to attach to a
   reseller when editing the user (#15222).
-  The "Maximum days to retry" option removed from default domain
   settings (#15233).

Other:

-  New Thunderbird add-on released to allow for better
   statistics/tracking of emails (#15246).

Build 47849 (2012-06-14)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Protection report improved handling of non-ascii
   senders/recipients (#14977)
-  Software: Added additional encryption to replication (#14517)
-  Spampanel: Re-added non-partial log searching (#15153)

Build 47711 (2012-06-07)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Improved botnet detection (#15110)
-  Spampanel: Authticket additonal protection against XSS (#15108)
-  Spampanel: Removal deprecated report\_logo protection report variable
   (#15107)

Build 47574 (2012-05-31)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: SSH firewal IPv6 address verification bug fix (#15055)
-  Software: Archiving support non-ASCII SMTP senders/recipients
   (#14903)
-  Software: API deprecate api\_list\_all\_incoming and
   api\_list\_all\_outgoing (#12684)
-  Software: API deprecate api\_list\_all\_incoming\_bandwidth and
   api\_list\_all\_outgoing\_bandwidth (#12683)
-  Spampanel: Change destination handling cased values (#15066)

Build 47417 (2012-05-24)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Deprecation of the inaccessible logging feature. Only the
   accessible logging will be stored/available (#12619)
-  Software: Allow for non-ASCII subject notations (#10505)
-  Software: API add number of CPUs to api\_server\_status (#14480)
-  Software: API add ability to filter on message size with
   api\_find\_messages (#14480)
-  Software: Restrict maximum number of simultaneous accepted
   connections in total and per server (#11246)
-  Software: Quarantine performance improvements (#8305)
-  Spampanel: API return success for setproducts (#15035)

Build 47238 (2012-05-17)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Support image transparency in PDF protection report
   (#14963)
-  Software: Bug fix to properly skip DKIM check for wrongly configured
   senders (#14980)
-  Spampanel: Change destination route option moved (#14962)

Build 47119 (2012-05-10)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Domain statistics retrieval bug fix (#14878)
-  Software: Allow From: headers without domain (#14752)
-  Spampanel: Option added to retrieve delivery status from log results
   (#14335)
-  Spampanel: Return 503 header for error.php (#14364)
-  Spampanel: Allow to disable the webinterface for bridge-login
   (#12796)

Build 47015 (2012-05-03)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Spampanel: Uncheck the "Check all" checkbox when switching pages
   (#14784)
-  Spampanel: Removal of "required from domain" submission option
   (#14721)
-  Spampanel: Brand column added to branding management (#13418)
-  Spampanel: Quarantine caching issue fixed when switching domains
   (#14825)
-  Spampanel: Added IST (GMT+5:30) timezone (#14823)
-  Spampanel: Added GMT+0 timezone (#14696)
-  Spampanel: /api/domainuser/setpassword/username/ also update IMAP
   password (#14596)
-  Spampanel: Catch-all domain check before activation per-recipient
   automatic protection report (#12822)
-  Spampanel: Customization of emails sent out from Spampanel (#13843)
-  Spampanel: Archive search warning shown with results >1,000 emails
   (#11652)
-  Spampanel: Spampanel API application/json header with /format/json/
   (#14369)

Build 46882 (2012-04-26)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: SMTP rejection typo fix (adddress --> address) (#14750)
-  Software: Skip the blacklist check for From: header without email
   address (#14752)
-  Software: Logging add badly formed header rejection reason (#14758)
-  Software: Software API bandwidth list methods (#14728)
-  Spampanel: Added CSV import option on all user levels (#8973)
-  Spampanel: Added new Spampanel API call domainalias/list (#14573)
-  Spampanel: CSV import of new outgoing users bug fix setting default
   outgoing limits (#14771)

Build 46718 (2012-04-19)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Sender whitelist improved handling of DKIM passes (#14650)
-  Software: Removal "required from" outbound filtering feature (#14652)
-  Software: Added new URL filtering technology (#14641)
-  Spampanel: Bug fix log search export with specific criteria (#14728)

Build 46604 (2012-04-12)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Spampanel: Accept wildcard for CSR generation (#14636)
-  Spampanel: Trim spaces/dots from destination route (#11819)
-  Spampanel: Added support for domain aliases to
   /api/domain/add/domain/ (#13043)
-  Spampanel: Added export option for overview search results (#12263)
-  Spampanel: Added checkbox style to all pages with a list (#11939)
-  Spampanel: Added default settings for new resellers (#10636)
-  Spampanel: Show non-ASCII symbols in archive search results (#14661)

Build 46441 (2012-04-05)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Show invalid sender classification in log search results
   (#14613)
-  Spampanel: Memory optimizations (#14285)
-  Spampanel: Quarantine message deletion bug fix (#14600)
-  Spampanel: Quarantine allow for column sorting (#9678)
-  Spampanel: Quarantine search bug fix (#14568)
-  Spampanel: Protection report recipient CSV import auto-active user
   quarantine (#14622)

Build 46293 (2012-03-29)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: api\_add\_user\_method support for multiple methods (#7672)
-  Software: Improved handling of messages with many images (#14533)
-  Software: Statistics window fixed to include correct period (#14546)
-  Spampanel: Added option to report Not Spam (#10468)
-  Spampanel: Added option to disable spam rejection response at SMTP
   (#11996)
-  Spampanel: Added option to specify domain for log search as admin
   (#12966)
-  Spampanel: Server settings page restructuring (#12369)

Build 46081 (2012-03-22)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Bug fix for outgoing filter where IP addresses with a
   password set could send email without authenticating using that
   password (#14385)
-  Software: Add support for outgoing random delivery IP pool (#11325)
-  Software: Archiving add support for non-ASCII envelope senders
   (#14408)
-  Software: Bug fix for manual DNSBL whitelisting at
   www.spamrl.com/delist/ (#13609)
-  Spampanel: Add GMT-5 (#14374)
-  Spampanel: Refactoring of IMAP quarantine browser (#7162)
-  Spampanel: Force choice Block Spam / Automatic lock for outgoing
   users (#14136)
-  Spampanel: Add support for the .xxx domain extension (#14391)
-  Spampanel: Removal of the inaccessible logging days from the frontend
   (#14435)
-  Spampanel: Add option to flush DNS cache (#14035)
-  Spampanel: Spampanel API call added to retrieve the reseller owner of
   a domain (#14041)

Build 45642 (2012-03-15)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Temporarily stop mailserver during weekly update to ensure
   clean connection handling (#11891)
-  Software: Filtering process resource usage optimizations (#14281)
-  Software: Protection report logo size fix for Apple Mail OS X Lion
   (#13137)
-  Software: Archiving index only the first 8MB of indexable data
   (#13983)
-  Software: Improved protection against SSL BEAST attack (#11565)
-  Software: Improved handling for different encodings for the sender
   blacklist (#14332)
-  Software: Improved handling of protection report recipients with
   apostrophe in their local part (#14340)
-  Software: Allow whitelisting of invalid senders (#14353)
-  Spampanel: Removed unnecessary timezone queries (#14271)
-  Spampanel: Reduced memory usage at login (#14285)
-  Spampanel: Reduced memory during update (#14284)
-  Spampanel: Reduced memory usage when archiving is disabled (#14326)
-  Spampanel: Set default language for protection reports based on
   reseller setting (#14024)
-  Spampanel: Avoid "no such user" errors when using domain jump from
   user settings page (#14330)
-  Spampanel: Refactoring of the archiving redeliver feature to preserve
   original message formatting (#14221)

Build 45334 (2012-03-08)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Improved filtering of unknown IPv6 addresses (#14216)
-  Software: API added option 'append\_domain' to
   api\_list\_all\_outgoing\_users (#13844)
-  Software: Outgoing queue processing performance improvements (#14103)
-  Software: Outbound filtering improvements (#13457)
-  Spampanel: Spampanel API calls to manage the domain protection
   reports (#10891)
-  Spampanel: Show progress when uploading CSV (#11525)
-  Spampanel: Option to easily disable products for groups of domains
   (#12465)
-  Spampanel: Cache refresh after domain route update (#14250)
-  Spampanel: Apply reseller settings to reseller-specific access URL
   (#14197)
-  Spampanel: Outgoing max-days-to-retry moved to a cluster global
   setting (#14239)
-  Spampanel: Reseller option to select default protection report
   template for new domains (#14078)
-  Spampanel: Do not allow domain transfer to destination reseller if
   domain limit will be exceeded (#14201)
-  Spampanel: Bug fix reseller domains getting de-associated after
   search (#14186)

Build 45128 (2012-03-01)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: New improved system for virusscanner update definitions
   (#14036)
-  Software: Prevent lookup queries to non-used RBL lists (#14163)
-  Software: Reduced resource usage for large emails (#14174)
-  Software: Brandname improved handling of non-ASCII characters
   (#14168)
-  Software: Delivery queue reason improved handling of non-ASCII
   characters (#14169)
-  Software: Bug fix statistics recording leap days (#14180)
-  Spampanel: DKIM selector input verification (#11425)
-  Spampanel: Log search results timezone bug fix (#14133)
-  Spampanel: Domain export optimizations (#14122)
-  Spampanel: Bug fix IDN handling .dk domains (#14147)
-  Spampanel: Checkbox implemented on pages showing lists (#11939)
-  Spampanel: Removed wrong warning for unsupported brandname (#14155)
-  Spampanel: Domain overview page speed improvements (#13854)
-  Spampanel: Bug fix showing filtering status for pages >500 items
   (#14166)

Build 44970 (2012-02-23)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Filtering updates
-  Software: Improved support for non-ASCII domains
-  Software: Improved handling for non-ASCII variables passed to API
-  Spampanel: Spampanel API feature to allow service management per
   domain
-  Spampanel: Added "da" (Danish) language option
-  Spampanel: Added Japanese translation
-  Spampanel: Bandwidth overview for speed improvement
-  Spampanel: All domain list operations speed improvements
-  Spampanel: Improved handling of IDN domains
-  Spampanel: Improved detection for reported spam messages
-  Spampanel: Speed up of the domainuser/domain add Spampanel API calls
-  Spampanel: Add timezone UTC/GMT -4
-  Spampanel: IP whitelist show disabled IPs

Build 44818 (2012-02-16)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Bug fixed with recipient protection reports failing to
   generate
-  Software: Improved error handling for non-ASCII arguments
-  Software: Archiving improvement for indexing large emails
-  Software: IMAP quota handling deprecated in API
-  Software: API improved error handling to prevent bad timezones
-  Software: Support for "+" character in blacklisted/whitelisted
   senders/recipients
-  Spampanel: Status page refactoring to use less memory
-  Spampanel: Added option to delete protection report recipients
-  Spampanel: Custom timezone support for resellers and domains
-  Spampanel: Timezone bug fix with default language

Build 44672 (2012-02-09)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Bug fix maximum\_hourly\_bounces skipped with enforce\_batv
   set to the default
-  Software: Delivery queue retrieval performance improvements
-  Software: local\_part\_characters regexp validation improvements
-  Software: Improve performance statistics retrieval
-  Software: Outgoing sender verification only check SMTP mail from:<>
-  Software: Improved data verification
-  Spampanel: Redirect fix when setting invalid route
-  Spampanel: IP whitelist add support for skipping dnsbl check
-  Spampanel: Improved distinction between incoming and outgoing
   archived messages
-  Spampanel: Archive status page enhancements
-  Spampanel: Log search admin level fix for local-part
-  Spampanel: Bulk delete option for delivery queue
-  Spampanel: Feature to mass change destination routes
-  Spampanel: Allow to IP control admin access
-  Spampanel: Protection report recipient page enhancements
-  Spampanel: Confirmation when disabling filtering for a domain
-  Spampanel: MX verification set reseller sender details
-  Spampanel: Custom default items per page
-  Spampanel: Option to trade/transfer domain to different reseller
-  Spampanel: Enable API access by default for resellers
-  Spampanel: Archive mail preview improved support for foreign
   characters

Build 44523 (2012-02-02)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Spampanel: Admin domain overview caching improvements
-  Spampanel: Quarantine release/delete additional confirmation
-  Spampanel: Deprecated report logo removed
-  Spampanel: Route edit cache refreshing fixed

Build 44327 (2012-01-26)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Outgoing sender verification improvements
-  Software: Outgoing deliver only a single message per connection to
   local nodes
-  Software: Callout cache clearing improvements
-  Software: Filtering incoming IP whitelist feature to allow to skip
   all DNSBL
-  Software: API depreciation of api\_export\_domains and
   api\_add\_incoming\_domains in favor of webinterface methods
-  Software: Filtering improved handling of invalid filenames
-  Software: Recipient blackhole fix for messages without recipients
-  Software: API add\_incoming\_domain call internals modified to
   improve speed
-  Spampanel: API new call to retrieve available product list
   /api/productslist/get/
-  Spampanel: IMAP quota configuration removed
-  Spampanel: Permission option added to disable login-link retrieval
-  Spampanel: Auto-creation of admin user during first login
-  Spampanel: Feature added to export log search results
-  Spampanel: Sender whitelist/blacklist entry verification improved

Build 44075 (2012-01-19)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Report logo removed from API calls
-  Software: Deprecation of api\_get\_protection\_report\_template\_logo
-  Software: Protection report improved premium whitelabel handling
-  Software: Include rejected IP in DSN response
-  Software: Outbound filter sender verification fix
-  Software: Add get\_message\_info call for outgoing filter
-  Software: SSL CSR generation include State
-  Software: Filtering improved handling of encoded filenames
-  Software: Callout cache clearing permission fix
-  Spampanel: Set correct reseller brand when changing domain owner
-  Spampanel: Bug fix for logout redirect at email level
-  Spampanel: Feature resizeable columns in log search
-  Spampanel: Removal of raw log download (exposed via log search)

Build 43785 (2012-01-12)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Bug fix permission issue callout cache clearing
-  Software: Database rebuild IO usage adjustments
-  Software: Protection report generation bug fix default values
-  Spampanel: Branding management improvements
-  Spampanel: Infinite loop fix for missing domain

Build 43616 (2012-01-05)
~~~~~~~~~~~~~~~~~~~~~~~~

-  Software: Outgoing filter skips cluster training
-  Software: Filtering algorithm updates
