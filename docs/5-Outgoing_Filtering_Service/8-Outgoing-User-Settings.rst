Outgoing User Settings
======================

Here you can configure the settings of the outgoing user. The image
below represents a user for a specifc domain. If you wish to see how to
setup an IP address for an outgoing user please see
`here. <https://my.spamexperts.com/knowledgebase.php?action=displayarticle&id=131>`__

.. figure:: https://my.spamexperts.com/images/kb/outgoingusersettings.png
   :alt: 

-  **Automatic lock enabled -** This setting will enable the automatic
   lock features.
-  **Identification method -** Here you can set the outgoing identification
   method you wish to use. More information can be found
   `here <https://my.spamexperts.com/kb/731/Outbound-Spam-Monitoring.html>`__
-  **User lock timeout -** Adjustable setting to change the user lock
   timeout.
-  **Maximum unlocks by timeout -** Adjustable setting to change the
   maximum number of unlocks per user timeout.
-  **Enable outgoing limits -** Adjustable setting activate
   /deactivate limits on outgoing connections.
-  **Outgoing limit per hour -** The amount of outgoing connections
   that can be opened per hour.
-  **Outgoing limit per minute -** The amount of
   outgoing \ *connections* that can be \ *opened* per minute
-  **Valid Sender address required -** Check this option if you wish
   to verify that it requires a valid sender address.
-  **DKIM Selector -** Here you can choose a selector you wish to use
   at domain level. The selector can be generated via the webpanel at
   domain level using the dkim generator tool. Once you have made the
   certificate, please remember to add the TXT to your DNS.
-  **Maximum number of recipients per day -** Adjustabe setting to
   configure the maximum number of recipients a sender can make per
   day.
-  **Invalid recipient limit -** Adjustable setting to configure the
   amount of invalid recipients a sender can make per day.
-  **Maximum days to retry -** Configurable setting to adjust the
   amount of days to retry with the Automatic retry Schedule.
-  **Quarantine response -** If you set it to Accept the message,
   then the SMTP response would be Accept and the message would still be
   blocked and show in the quarantine.
