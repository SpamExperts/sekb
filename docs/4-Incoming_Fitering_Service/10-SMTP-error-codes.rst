.. _4-SMTP-error-codes:

SMTP error codes
================

Possible 5xx codes
~~~~~~~~~~~~~~~~~~

-  500 - The server could not recognize the command due to a syntax
   error.
-  501 - A syntax error was encountered in command parameters or
   arguments.
-  502 - This command is not implemented.
-  503 - The server has encountered a bad sequence of commands.
-  504 - A command parameter is not implemented.
-  550 - No mailbox by that name is currently available, for example
   because it was not found, or because the command was rejected due to
   policy reasons, such as a full mailbox. Please clear the
   :ref`callout cache <4-Recipient-Callouts>`
   after the mailbox has been emptied.
-  551 - The recipient is not local to the server. The server then gives
   a forward address to try.
-  552 - The action was aborted due to exceeded storage allocation.
-  553 - The command was aborted because the mailbox name is invalid.
-  554 - The transaction failed.
