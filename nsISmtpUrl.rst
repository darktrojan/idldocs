==========
nsISmtpUrl
==========

`mailnews/compose/public/nsISmtpUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsISmtpUrl.idl>`_


Constants
=========

DEFAULT_SMTP_PORT
-----------------

**Type**: ``int32_t``

**Value**: ``25``


DEFAULT_SMTPS_PORT
------------------

**Type**: ``int32_t``

**Value**: ``465``


Properties
==========

recipients
----------

``attribute string recipients``

SMTP Parse specific getters.
These retrieve various parts from the url.
This list is a list of all recipients to send the email to.
Each name is NULL terminated.

PostMessage
-----------

``attribute boolean PostMessage``

postMessageFile
---------------

``attribute nsIFile postMessageFile``

The message can be stored in a file, to allow accessors for getting and
setting the file name to post.

requestDSN
----------

``attribute boolean requestDSN``

dsnEnvid
--------

``attribute ACString dsnEnvid``

The envid which is used in the DSN.

sender
------

``attribute string sender``

The sender of this mail (can be different from identity).

senderIdentity
--------------

``attribute nsIMsgIdentity senderIdentity``

SMTP Url instance specific getters and setters
Information the protocol needs to know in order to run the url.
These are NOT event sinks which are things the caller needs to know.
By default the url is really a bring up the compose window mailto url.
You need to call this function if you want to force the message to be
posted to the mailserver.
The user's full name and user's email address are encapsulated in the
senderIdentity.
(the user's domain name can be glopped from the user's email address)

NOTE:  the SMTP username and SMTP server are in the smtp url
smtp://sspitzer@tintin/...

prompt
------

``attribute nsIPrompt prompt``

authPrompt
----------

``attribute nsIAuthPrompt authPrompt``

notificationCallbacks
---------------------

``attribute nsIInterfaceRequestor notificationCallbacks``

smtpServer
----------

``attribute nsISmtpServer smtpServer``

verifyLogon
-----------

``attribute boolean verifyLogon``
