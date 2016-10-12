Changelog 2013
==============

Build 61970 (2013-12-26)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Addons:

-  No new updates this week

Build 61968 (2013-12-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  If the api\_set\_outgoing\_interfaces() API call is used with an
   interface that is not part of the cluster, a warning is returned
   (#14413)
-  If a destination like "example..com" is used in an API call, it is
   rejected with an appropriate error message (#14602)
-  If a date earlier than 2000 is used with the various API statistics
   calls, an appropriate error message is generated (#15745)
-  If a destination that is too long is used in an API call, it is
   rejected with an appropriate error message (#17022)
-  If a duplicate address is provided as an argument to the
   white-/black-listing API calls, an appropriate error message is
   generated (#17189)
-  The api\_add\_local\_recipient() API method would accept a local part
   containing NULL characters.  This will now generate an error (#19254)
-  The api\_deliver\_queued\_message() API methods would show error
   messages even when the delivery was successful (#19262)
-  The api\_[outgoing\_]delivery\_queue() and API methods now treat an
   empty "frozen" filter as "True" (#19274)

Spampanel:

-  Delivery queue page scroll up after force-retry (#19119)
-  Add option to report spam from the queue pages (#15999)
-  Improve CSV import procedure and enhance error messages (#19177)
-  Expose option to add outging email to envelope sender's archiving
   account (#18369)
-  Improve the log search feature by using the new API pagination option
   (#18642)
-  Resolve issue with the quarantine/tag threshold bars not showing in
   Italian (#19217)
-  Redirect default domain settings button to proper page (#19216)
-  Resolve issue with "hide details" not working for domain CSV imports
   (#19186)
-  Show the user authentication level in Spampanel (#19107)
-  Improve SMTP output parsing when 'redelivering' an archived message
   (#19266)
-  Ensure correct activated services are shown for domains when using
   live search (#19241)

Addons:

-  POA: APS 1.2 Allow clients to upgrade the old 1.7 package to the
   latest (#18640)
-  POA: APS 1.2 return an error for provisioning duplicates (#18477)
-  POA: APS 1.2 resolve issues with domain limits not being obeyed
   (#18478)
-  POA: APS 1.2 fail provisioning of domains without MX record (#18402)

Build 61478 (2013-12-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Addons:

-  No new updates this week

Build 61475 (2013-12-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added more informative error messaging when
   api\_deliver\_queued\_message() fails to deliver the message (#19121)
-  Added further classification details when a message is blocked via
   'Google Safe Browsing' (#15816)
-  Adjusted delivery status wording when a message is deleted from the
   delivery queue (#19146)

SpamPanel:

-  Resolved issue with 'To:' column truncation in quarantine overview
   when mutiple 'To:' addresses are used (#19143)
-  Resolved issue with viewing of outgoing queued messages (#19165)
-  Resolved issue with log search classification when an alternate
   language is used (#19134)
-  Adjusted IP whitelisting to both Incoming & Outgoing sections when
   'Skip All Filters' is used (13094)

Addons:

-  No new updates this week.

Build 61180 (2013-11-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added Software API methods: api\_get\_delivery[outgoing]\_queue() for
   JSON or CSV retrieval (#18806)

SpamPanel:

-  Added search functionality to delivery queue (#10470)
-  Resolved issue with Spampanel's copyright when menu is collapsed
   (#19065)
-  Show commercial URL if control panel is disabled in APS (#13427)
-  Resolved error with Administrator email confirmation link(#19097)

Addons:

-  No new updates this week.

Build 60968 (2013-11-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolved issue with manually locked users automatically unlocking
   (#18247)
-  The Archive API's ``/usage/`` method now returns usage for all
   domains (#17081)
-  Added Archive API method ``/accounts/`` that returns a list of
   archiving accounts (#17081)
-  Use domain set delivery IP address if not the default for outgoing
   users (#16114)
-  Further enhancements to Protection Report generation (#18725)

SpamPanel:

-  Change Kbytes to MB in email size restriction in SpamPanel (#16420)
-  Added additional of timezone Brisbane GMT+10 (#18788)
-  Added missing Timezone GMT -6 (MST) (#18770)
-  Added domain alias support to CSV import (#14025)
-  Added MX verification tool for domain Aliases (#12145)
-  Server status page enhancements (#12368)
-  Added sort indicators to delivery queue table (#19025)
-  Added 2FA code immediate verification (#18433)

Addons:

-  Mac OS mail.app spam reporting tool updated

Build 60591 (2013-11-14)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added optional "ID" parameter to api\_count\_[outgoing\_]messages()
   (#18767)
-  Improved efficiency of API's api\_count\_[outgoing\_]messages()
   (#18870)
-  Improved efficiency of the Protection report generation (#18724)

SpamPanel:

-  Added subnet allowance when using 'Skip All filters' in the IP
   whitelist (#17170)
-  Improve English in various Spampanel pages (#18865)
-  Added a "trust this device" option for two factor authentication
   (#18432)
-  Expose option to make quarantining oversize messages optional
   (#18367)
-  Mass release restricted to administrators only to prevent bad mass
   releases negatively influencing the filtering (#17795)
-  Added Subject filter via the interface log search (#18362)
-  Added Archiving redeliver in batch option (#17070)
-  Added count of valid recipients (#17469)
-  Resolved Spampanel Quarantine - items per page not working (#18828)
-  Added change password option for outgoing user - domain level
   SpamPanel (#18902)
-  Resolved issue with Incoming/Whitelist IP's 'save' button in Italian
   language (#18923)
-  Resolved issue with oversized log search in Chrome browser (#18738)
-  Resolved issue with Spampanel Log-Search Subject decoding in Hebrew
   (#18420)
-  Resolved issue with Spampanel Quarantine Subject decoding in some
   languages (#18949)
-  Resolved issue with Outgoing and Archiving option showing at domain
   level when not enabled for the reseller (#18904)

Addons:

-  No new updates this week

Build 59978 (2013-11-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Addons:

-  No new updates this week

Build 59977 (2013-10-31)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added improved error messaging when setting update day/time fails
-  Corrected api\_find\_outgoing\_messages() output for entries where
   there is no username part of the submission user (#18698)

SpamPanel:

-  Added Spampanel API call to toggle domain/email user status (#16032)
-  Added Spampanel API call to enable/disable interface status (#16942)
-  Added Spampanel API call to disable/enable filtering (#16683)
-  Do not allow destination routes set to localhost (#18358)
-  Added option to choose what levels to expose "Include results from
   the last minutes:" (#18529)
-  Rename report templates when reseller username is changed (#16278)
-  Disable outgoing/archiving when product disabled for a domain
   (#16687)
-  Added Live search / filtering on domain overview (#9696)
-  Enhanced error messaging if data was not imported correctly (#14839)
-  Added pop-up warning when deleting resellers / domain users from
   interface (#18335)
-  Added search to local recipients in SpamPanel(#16880)
-  Added mass-destination change for resellers to SpamPanel(#16484)
-  Added SPF generator to SpamPanel (#9771)
-  Removed Brandname restriction when trying to set the brandname in
   Spampanel (#18759)
-  Resolved SpamPanel API call failing for newly added domains (#18760)
-  Expose sender/recipient whitelist/blacklist in Spampanel API (#17306)
-  Resolved Text on logon screen in Dutch/German language(#18763)
-  Resolved Total bandwidth count for all domains when showing an
   incorrect value (#18764)
-  Optimization added to speed up behavior with large amounts of
   domains(#18778)
-  Newly added domains not associated with the reseller account (#18766)
-  Disable vertical scroll for DKIM generated key (#16726)
-  Resolved Quarantine view in French Language (#18789)
-  Adjusted Logo in the new interface to a higher level (#18790)
-  Resolved the set route order in Spampanel API '/add/domain/' (#18818)
-  Implemented a truncated Subject column in the log search (#18835)
-  Resolved Quarantine not showing correctly when switching from domain
   user to email user (#18836)

Addons:

-  No new updates this week

Build 59510 (2013-10-24)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Addons:

-  No new updates this week

Build 59505(2013-10-17)
~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Corrected logging of "Rejected" messages when quarantine is disabled
   (#14290)
-  Improved language detection for messages with multiple language
   headers(#17250)
-  Added API method 'api\_get\_domain\_type' which can be used to check
   domain type details (#16092)
-  Added API method
   'get\_certificate\_info/api\_get\_[https\|smtp\|imap]\_certificate\_info'
   to get information about the TLS/SSL certificates that have been
   installed for IMAP/SMTP/HTTP (#14632)
-  Added API methods 'api\_set\_incoming\_smtp\_certificate' and
   'api\_set\_outgoing\_smtp\_certificate', which allow using different
   TLS/SSL certificates for the delivery and submission filters.
-  Improved API
   'api\_get\_queue\_reason\_incoming/api\_get\_queue\_reason\_outgoing'
   to allow querying a specific set of messages (#18428)
-  Added API method 'api\_set\_block\_hidden\_executables' to block all
   messages that contain an executable within a ZIP file. (#16101)
-  Improved efficiency in the API methods that work with the delivery
   queue (#18473)
-  The deprecated "domain=all" argument for api\_find\_messages() and
   api\_find\_outgoing\_messages() was removed
-  Added 'short day' variable to Periodic Report templates (#13929)
-  Improved error messages when using 'api\_get\_backup\_settings'
   (#14691)
-  Invalid domain names, which start with '-' or '.', are no longer
   accepted by the add\_incoming\_domain() API call (#17510)
-  Added possibility to use variants of "SpamExperts" as your brand name
   (#9991)
-  Enhanced brandname length limitation to 255 characters (#17154)
-  Improved efficiency when changing the quarantine expiry period.
-  Improved IPv6 support, if you're adding or removing IPv6 please
   contact SpamExperts support to active it(#9887)

SpamPanel:

-  Resolved issue loading the Delivery queue from IE8(#18696)
-  Added Spampanel branding color #ff4000 (#16874)
-  Vertical scroll for DKIM generated key has been disabled (#16726)
-  Added reseller field to CSV export feature (#15941)
-  Domain administrator contact for outgoing settings has been exposed
   (#18183)
-  Added support for skip\_ehlo\_check in IP whitelist (#16459)
-  Optimized performance of SpamPanel API 'domain/add' (#18688)
-  Removed the need to manually unbind domains when moving to another
   reseller (#15208)
-  Add sorting to the branding page (#12477)

Addons:

-  No new updates this week

Build 59205(2013-10-10)
~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Enhance the efficiency of the quarantine expiry (#14290)
-  Added argument to exclude frozen messages in the
   'api\_delivery\_queue' and api\_outgoing\_delivery\_queue'
   API(#13324)

SpamPanel:

-  Optimized syncronised deletion of quarantined messages (#18263)
-  Optimized '/add/domain/' SpamPanel API call (#18204)
-  Resolved issue parsing IDN domains when using SpamPanel API (#18647)
-  Resolved issue encoding passwords containing slashes with SpamPanel
   API (#18606)
-  Resolved delivery queue 'select all' issue with Chrome browser
   (#18611)
-  Performance optimizations for larger number of domains (#18638)

Addons

-  No new updates this week

Build 58810 (2013-10-03)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Addons

-  cPanel: Enhanced update mechanism (#18594)

Build 59056 (2013-10-02)
~~~~~~~~~~~~~~~~~~~~~~~~

Addons:

-  cPanel: A potential security issue has been found by a client
   (Rack911) and is resolved. Please ensure to (auto-)update to this
   release, or contact support for a workaround. (#18629)

Build 58798 (2013-09-19)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Software API protect against invalid username values for the default
   domain (#18398)

Spampanel:

-  Resolved bandwidth overview issue for resellers with IDN domains
   (#18555)
-  Optimization of error reporting when activating the Archiving service
   for a domain (#18528)

Addons

-  cPanel: Use cPanel provided local/remote domain detection (#17576)
-  cPanel: Resolved errors in automatic addon domains provisioning
   (#18508)
-  POA: Force lowercase domains when provisioning (#18360)
-  POA: Resolve provisioning of IDN domains (#18496)

Build 58598 (2013-09-12)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added ability to archive outgoing messages on a per 'Envelope-From:'
   basis (#17561)
-  Mail sent by submission filter users will be archived under the
   submission authentication domain if archiving is enabled for that
   domain. (#18196)
-  Added option to block all attachments with a password protected ZIP
   file (#15074)
-  Added support for paging in 'api\_find\_messages' and
   'api\_find\_outgoing\_messages' to limit the number of results
   (#15033)
-  Added new Softare API 'api\_get\_json\_server\_status()'. Similar to
   the 'api\_get\_server\_status()' method, but in a JSON format, using
   exact values rather than percentages. (#18161)
-  Optimization of API 'api\_delivery\_queue()' when filtering by
   frozen/not-frozen status (#11324)

SpamPanel:

-  New SpamPanel layout now available on demand for existing clients,
   please contact support if you wish to be upgraded already
   (#13541)** **
-  Added IP ranges to the Spampanel administrator IP restriction
   setting(#17523)
-  Added more informative errors when having problems with uploading
   certificates (#8906)
-  Added warning when DKIM selectors are invalid (#18048)\*
-  Added support for .sx TLD (#18381)\*
-  Added 2 Factor Login Authentication (#17847)
-  Removed "include results from the last few minutes" option from the
   interface, this is still available via the software API (#17687)
-  Added IDN decoding to the domain check for resellers via Spampanel
   API (#18394)\*
-  Resolved (recipient) & (domain) variable in welcome email for
   Protection Reports (#18416)
-  Resolved issue with 'Retry Time' variable for Outgoing Delivery Queue
   (#18452)
-  Resolved disabling the 'Auto-enable' option of a catch all domain
   when already enabled (#18457)
-  Resolved Subject encoding in human-readable form in the UI log search
   (#18420)
-  Resolved 'jump to Domain' auto fill for resellers (#18371)

\_\*\* Starred Items are also deployed to the old Spampanel Layout.
\*\*\_

Build 57866 (2013-09-05)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Build 57865 (2013-08-29)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Build 57864 (2013-08-22)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Build 57863 (2013-08-15)
~~~~~~~~~~~~~~~~~~~~~~~~

SpamPanel:

-  Enhanced protection against automatic enabled protection reports when
   routes cannot be reached (#18319)
-  Resolved message viewing in delivery queue (#18322)

Add-ons:

-  POA: Provisioning error 'Document not well-formed' resolved (#18268)

Build 57705 (2013-08-08)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Added hard disk S.M.A.R.T. monitoring (#12074)
-  Fix JSON error issue with user field in
   api\_find\_outgoing\_messages/api\_find\_messages (#18287)

SpamPanel:

-  Added message subject to log search results (#13779)
-  Resolved human-readable version of queue time/size (#18228)
-  Resolved delivery queue issue with Portuguese language (#18275)

Add-ons:

-  Resolved cPanel "root user does not see domains" (#18188)

Build 57525 (2013-08-01)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Add (hidden) option to BCC all ARF reports to the Local Cloud
   administrator email contact (#16785)
-  Added "colums" variable to Software API
   api\_find\_(outgoing\_)messages to limit search output (#17475)
-  Added Software API call
   api\_(get\|set)\_quarantine\_oversized\_messages to allow to disable
   quarantining such oversized emails (#14785)
-  Stop automatically unlocking outgoing user accounts which were
   manually locked (#18247)
-  Ensure Software API api\_find\_(outgoing\_) always returns all
   columns even for empty values (#18248)

Add-ons:

-  cPanel: Force-use priorities 10/20/30 when changing the MX records
   (#18214)

Build 57351 (2013-07-25)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improved handling of quarantine message migration when master server
   is unreachable (#17973)

Spampanel:

-  Increase the use of AJAX on pages that generally take longer to load
   (#9328)
-  Handle the situation where a reseller of a domain is missing (#18203)
-  Force restrict access to a reseller when updating its administrator
   contact (#18223)

Build 57120 (2013-07-18)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Resolve issue sorting Software API result by email subject for
   api\_find(\_outgoing)\_messages (#18176)

Spampanel:

-  Add Brazilian language translation (#18098)
-  Spampanel API expose domain archive storage size (#17563)
-  Spampanel API new call to set archive storage days per domain
   (#17564)

Add-ons:

-  cPanel/Plesk: Adjust behavior of the hook for /scripts/killact when
   domains are configured not to be removed (#18163)
-  Plesk: Disable access for service users (#18179)

Build 56989 (2013-07-11)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Improve handling of domain association for resellers with large
   quantities of domains (#18140)
-  Adjusted the MX verification tool only to return wrong domains
   (#18089)
-  Domain CSV import improvements to the success/fail output (#18103)
-  Add the ability to search the logs for the message ID (#16385)

cPanel add-on:

-  Improve cPanel API handling for responses with empty usernames
   (#18157)

Build 56863 (2013-07-04)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Domain CSV import speed improvements (#15698)
-  Do not allow enabling of automatic recipient protection reports for
   catch-all domains (#15628)
-  Permission issue resolved uploading CSV of report recipients without
   outgoing license (#18115)

cPanel/Plesk add-on:

-  Updater changes to work in async mode to prevent session deadlocks
   (#17929)

Webinar Q3 2013 (2013-06-27)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The recording can be found
`here <https://www.youtube.com/watch?v=-iBt4YmpGr4>`__.

Build 56755 (2013-06-27)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Issue resolved where untranslated strings were not showing in English
   for some languages (#18099)

cPanel add-on:

-  Force the cPanel routing setting to local during bulk-protect
   (#18108)
-  Exclude prospamfilter.gif from the self-diagnostics check (#18107)

Build 56678 (2013-06-20)
~~~~~~~~~~~~~~~~~~~~~~~~

cPanel add-on:

-  Updater refactoring due to recent cPanel backend changes, please run
   the installer from commandline if the update from the webinterface
   fails (#17929)
-  Correction of the domain counts returned during the bulk protect
   process (#17791)
-  Ensure the correct route is set after multiple bulk protect runs
   (#17895) 

Plesk add-on:

-  Show private label names in the page heading and titles (#16803)
-  Force-reload local cache after domain removal (#17898)
-  Error handle for systems with the system() call disabled (#17928)
-  Correction of the domain counts returned during the bulk protect
   process (#17791)
-  Ensure the correct route is set after multiple bulk protect runs
   (#17895)

Build 56557 (2013-06-13)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Handle concurrent calls to api\_set\_outgoing\_interfaces (#18011)

Spampanel:

-  Improve large reseller account multi-domain change handling (#18028)
-  CSV recipient upload only allow UTF-8 formatting (#17992)
-  Display reseller branding for domains using a wrong CNAME (#18029)

Build 56402 (2013-06-06)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Change to api\_get\_server\_status to return free space instead of
   blocks (#17984)
-  Software API change to stop accepting domain aliases containing a
   colon in the domain (#17966)
-  Disabling of SIZE advertising for the outgoing filter to allow for
   per-domain limits (#18013)

Spampanel:

-  Adjustments to quarantine raw message body loader to support more
   messages (#17994)
-  Archiving re-delivery improvements with multiple recipients (#16118)
-  New timezone added WST GMT+0800 (#17891)
-  Delivery queue time/size reformatted for a more human friendly
   representation (#16428)
-  Log search date sorting issue fixed (#18015)
-  Improved domain alias parsing (#17993)

Build 56218 (2013-05-30)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Properly format new "To:" header information in Software API
   find\_messages results (#17936)
-  Refactored Software API find\_messages to query servers concurrently
   rather than in serial (#17692)
-  Improved Software API find[\_outgoing]\_messages help documentation
   describing the new header/subject columns (#17692)

Spampanel:

-  Statistics graph generation correction of blacklisted/whitelisted
   counts (#17940)
-  Bandwidth sorting/graph localization issue resolved (#17953)

Build 55991 (2013-05-23)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Require the administrator contact to be verified (#17258)

cPanel/Plesk add-on:

-  Show IDN domains as normal during bulk-protect (#17888)
-  Show error details for domains with a wrong destination (#17901)
-  Force-refresh Spampanel cache after domain removal (#17898)

Build 55789 (2013-05-16)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Recording of email subjects added to the logging system (#9644)
-  Use hard-links for duplicate quarantine storage (#8732)

Spampanel:

-  Adjustment on Status page to show all values correctly (#17715)
-  Automatically apply reseller time-zone settings to newly added
   domains (#17731)
-  Include the Greek translation as optional language (#17772)
-  Periodic user report CSV import issue resolved with required product
   dependencies (#17775)
-  MX verification tool added further elaboration on failures (#13687)

cPanel/Plesk add-on:

-  Show custom brand name in page header and titles (#16803)

Build 55296 (2013-05-09)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

cPanel add-on:

-  Prevent showing a warning for the "current" tier (#17587)
-  Do not allow toggling protection for parked/addon domains if disabled
   in the settings (#17730)
-  Improved error handling in case Spampanel API access fails when
   migrating a domain (#17615) 

Plesk add-on:

-  Bug fix to allow protection toggling from the domain list (#17694)
-  Improved error handling in case Spampanel API access fails when
   migrating a domain (#17615)

Build 55295 (2013-05-02)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  This build includes general filtering/performance updates only.

Build 55294 (2013-04-25)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Added support for the ".cw" TLD  (#17643)
-  Auto-update total items on quarantine page after deleting/releasing
   messages (#15492)

cPanel add-on:

-  Added support for IDN domains during bulk protect (#17688)
-  Added Spampanel API validation check before bulk protect (#17704)

Plesk add-on:

-  Added support for IDN domains during bulk protect (#17688)
-  Added Spampanel API validation check before bulk protect (#17704)
-  Resolved updater syntax output in bad PHP environment (#17665)

Build 55067 (2013-04-18)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Periodically optimize tables for performance and reduced disk usage
   (#15859)
-  Software API call api\_get\_server\_status changed to return mount
   points instead of filesystem labels (#16347)
-  Software API improved error handling for invalid IPs (#15515)
-  Software API call api\_get\_recipient\_error\_details speed
   improvements (#16436)
-  Software API call api\_delivery\_queue speed improvements (#16304)
-  Software API increased maximum entries for
   api\_set\_disabled\_spf\_domains (#17155)
-  Software API increased maximum entries
   for api\_set\_disabled\_dkim\_domains (#17156)

Spampanel:

-  Ajaxification of the spam quarantine release/delete options (#15492)
-  Added support to delete protection report recipients with whitespace
   (#17609)

cPanel add-on:

-  Parked/add-on domains treated as domain aliases are now hidden from
   the domain list (#13275)
-  Proper error handling in case the configuration is missing (#13113)
-  Improved cPanel API communication/error handling (#17578)
-  Tooltip improvements on migration page (#17614)

Plesk add-on:

-  Parked/add-on domains treated as domain aliases are hidden from the
   domain list  (#13275)
-  Proper error handling in case the configuration is missing (#13113)
-  Tooltip improvements on migration page (#17614)

Build 54840 (2013-04-11)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Memory optimizations of IP whitelist/blacklist page for large
   quantities (#15804)
-  When using the Jump to domain feature force new domain in log search
   (#17509)

Build 54594 (2013-04-04)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Internal firewall changed to reject instead of drop traffic (#15934)

Spampanel:

-  Sanitize HTML content before previewing in quarantine (#17484)
-  New Spampanel API call to retrieve bandwidth usage for a domain
   (#15301)

Build 54423 (2013-03-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Allow for "Not Spam" reports at recipient level (#16051)
-  Ensure all AFR reports are sent for the outgoing filter when the
   quarantine response is set to the non-default "Accepted" (#17454)

Build 54259 (2013-03-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Added incoming/outgoing distinction to search for archiving (#11601)

cPanel add-on:

-  Modification of PHP binary used to support new 11.36 location
   (#17384)

Plesk add-on:

-  Unregulated CNAME removal resolved (#17422)

Build 54080 (2013-03-14)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Outdated SpamExperts logo replacement for protection reports (#17275)

Spampanel:

-  Added search on page to manage email users (#16657)
-  Added message size to log search (#15273)
-  Automatically disable services that are not available anymore for
   domains (#17287)

cPanel add-on:

-  Improved handling of domains with multiple destination routes
   (#17368)

Plesk add-on:

-  Support added for Plesk service users (#16832)

Build 53937 (2013-03-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Added sorting to the "Jump to domain" option for resellers (#17280)
-  Added CSV upload option for the whitelists/blacklists (#8453)

cPanel add-on:

-  Drop requirement of "makecpphp" (#17256)

Plesk add-on:

-  Automatically protect domain aliases when toggling protection for the
   main domain (#17238)
-  Show all domain aliases in domain list (#17237)

POA APS add-on:

-  Do not return a fatal error when the primary email address changes
   (#17032)

Build 53937 (2013-03-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Added sorting to the "Jump to domain" option for resellers (#17280)
-  Added CSV upload option for the whitelists/blacklists (#8453)

cPanel add-on:

-  Drop requirement of "makecpphp" (#17256)

Plesk add-on:

-  Automatically protect domain aliases when toggling protection for the
   main domain (#17238)
-  Show all domain aliases in domain list (#17237)

POA APS add-on:

-  Do not return a fatal error when the primary email address changes
   (#17032)

Build 53811 (2013-02-28)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Conversion of pre-2013 statistical size data to the bandwidth
   recording system (#17121)
-  Software API reject values exceeding allowed maximum (#17144)
-  Prevent creation of recipients with a space or newline for the
   automatic protection report activation, and purge bad entries
   (#12653)
-  Archive API fix to allow filtering based on outgoing email (#17273)

Spampanel:

-  Improvement to handle one-click-login for Safari users accessing from
   POA (#16860)
-  Periodic protection report user CSV upload improved error reporting
   for invalid languages (#17223)
-  Use bandwidth instead of size data when showing domain statistics
   (#17240)
-  Quarantine improved handling of messages with many To: entries
   (#17194)

Build 53664 (2013-02-21)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Improved email handling to different recipient domains in a single
   connection (#13875)

Spampanel:

-  Allow users to select DKIM key length (#16730)
-  Spampanel API feature allowing to unbind domains when removing
   resellers (#15337)

Plesk add-on:

-  Refactored user identification method (#17197)

Build 53417 (2013-02-14)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Software API documentation enhancement to include argument limits
   (#17141)

Plesk add-on:

-  PHP warning solved for the migration feature  (#17148)

Build 53211 (2013-02-07)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Spampanel API proper error handling for too long local parts (#17040)
-  Bandwidth calculation refactoring, data older than 3 weeks will be
   converted to the new system (#17110)

cPanel add-on:

-  PHP5 detection method improvement (#17036)

Build 53029 (2013-01-31)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Outgoing log search date selection restriction issue resolved
   (#17028)
-  Automatically refresh the delivery queue after force re-delivering
   all messages (#16989)
-  Added new Spampanel API method reseller/getoutgoingbandwidthusage
   (#15203)
-  Enforce the 64-chars-max-length restriction for user local parts in
   the Spampanel API (#17040)
-  Improved handling of Japanese encodings in the quarantine browser
   (#17057)
-  Refactoring of the SSL CSR generator country list (#16477)

cPanel add-on:

-  Refactoring of caching behavior and username detection for improved
   security (#17039)
-  Domain list layout issues resolved for some templates (#17050)

Plesk add-on:

-  Stable release of refactored add-on code (#14439)

Build 52837 (2013-01-24)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Do not attempt to process an empty delivery queue (#16976)
-  Do not attempt to delete all messages from an empty quarantine
   (#16977)
-  Allow resellers to disable the "User's profile" option for their
   domains (#16979)
-  Force-refresh the delivery queue page after forcing retry (#16989)

Build 52572 (2013-01-17)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Issue resolved viewing the email content of messages in the outgoing
   queue (#16932)

Plesk add-on:

-  Zend conflict solved when adding domains (#16938)

cPanel add-on:

-  Optimizations to the bulk protect method to reduce used resources
   (#16906)
-  Alpha transparency issue in icon resolved (#16914)
-  Prevent the bulk reset time to be cleared when updating the
   configuration (#14699)
-  When force changing is enabled, ensure to also force update existing
   domains (#15889)

Build 52409 (2013-01-10)
~~~~~~~~~~~~~~~~~~~~~~~~

Software:

-  Allow for single column output api\_get\_weekly\_statistics (#16884)

Spampanel:

-  Email queue page refactoring to improve speed and performance
   (#16881)

Build 52315 (2013-01-03)
~~~~~~~~~~~~~~~~~~~~~~~~

Spampanel:

-  Domain statistics fix to show count of whitelisted messages (#16762)
-  Show reseller email address on Settings page (#16867)

Plesk add-on:

-  Properly apply custom brandname when saving it (#16717)
-  Force lower-case domain names (#16676)
-  Work around for Plesk 9 issue to show all domains at domain level
   (#16701)
-  Prevent custom brandnames from being overwritten during the upgrade
   process (#16804)
-  Check if the correct version of PHP is present before setup (#15877)
-  Protect domain aliases on Plesk 9 (#16554)
-  Improved handling of IDN domains (#16755)

cPanel add-on:

-  Force change auto-routing to local to prevent issues with cPanel
   auto-detection (#15861)
