.. _7-Send-Email-Logs-to-Remote-Syslog-server:

Send Email Logs to Remote Syslog server
=======================================

The SpamExperts Local Cloud solution supports sending detailed logs of
message connections and status changes to a remote syslog server, which
can be enabled via the Software API. You can store the remote syslog on
a designated server of your own choice for however long you need.

To start receiving the data, first you have to set the location of the
remote syslog server where the data will be sent. This can be achieved
with the following API call:

::


        api_set_remote_syslog_server(host='', port='', facility='', socket_type='', message_template='', enabled='', level='', status_template='') -> "".
        https://example.com/cgi-bin/api?call=api_set_remote_syslog_server&host=HOST&port=PORT&facility=FACILITY&socket_type=SOCK

The following call can be used as an example:

::


        https://example.com/cgi-bin/api?call=api_set_remote_syslog_server&host=HOST&port=PORT&facility=FACILITY&socket_type=SOCKET_TYPE&message_template=MESSAGE_TEMPLATE&enabled=ENABLED&level=LEVEL&status_template=STATUS_TEMPLATE -> ""

Where host is the server you store the remote syslog, the port is in
most cases 514 (unless you have another port open to listen for this).
The message template represents the format you will receive the remote
syslog results when we process the message. Status template, similar to
message template, is sent when the message status changes, for example:
the message is released from quarantine.

If you wanted something more detailed, for example to show more delivery
details on the message, then you can use the following example:

::


        https://example.com/cgi-bin/api?call=api_set_remote_syslog_server&host=remote.example.com&enabled=True&message_template="%(id)s","%(filtering_host)s","%(sender)s","%(recipient)s","%(domain)s","%(timestamp)s","%(sender_host)s","%(helo)s","%(sender_ip)s","%(incoming_size)s","%(outgoing_size)s","%(status)s","%(classification)s","%(classification_details)s","%(from_header)s","%(to_header)s","%(cc_header)s","%(subject_header)s"&status_template="%(id)s","%(filtering_host)s","%(domain)s","%(recipient)s","%(status)s","%(delivery_date)s","%(delivery_ip)s","%(delivery_port)s","%(delivery_fqdn)s","%(delivery_data)s"

The SpamExperts API call for retrieving the remote syslog also supports
other arguments than the ones provided so far, such as:

-  id
-  filtering\_host
-  domain
-  sender\*
-  recipient\*
-  timestamp
-  sender\_host
-  sender\_ip
-  incoming\_size
-  outgoing\_size
-  bandwidth
-  from\_header
-  to\_header
-  cc\_header
-  subject\_header
-  status
-  classification
-  classification\_details
-  classification\_code
-  helo
-  auth\_user
-  identity

\*The “sender” and “recipient” arguments are actually the
“envelope-sender” and “envelope-recipient” that are retrieved within the
template. If you want to retrieve the email “from”, “cc” or “to” please
use the “from\_header”, “cc\_header” or “to\_header” arguments.

And optionally we can also support the following arguments for when the
message status changes:

-  id
-  status
-  filtering\_host
-  domain
-  recipient
-  delivery\_date
-  delivery\_ip
-  delivery\_fqdn
-  delivery\_port
-  delivery\_data\*

\*The delivery\_data argument contains the remote server’s response, as
for example: if the server rejects the message it will contain the
server’s reject reply. The reply could be as follows:

::


        SMTP error from remote mail server after end of data: 550 rbl-reject: Message rejected because 198.51.100.0 is blacklisted

To check the remote syslog server settings, you can use the following
API call:

::


        api_get_remote_syslog_server() -> ""

::


        https://example.com/cgi-bin/api?call=api_get_remote_syslog_server

After execution, the **api\_get\_remote\_syslog\_server** call will
return all the configuration set before with
**api\_set\_remote\_syslog\_server**.
