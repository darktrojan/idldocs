===============
nsMsgSocketType
===============

`mailnews/base/public/MailNewsTypes2.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/MailNewsTypes2.idl>`_

Defines whether to use SSL or STARTTLS or not.
Used by @see nsIMsgIncomingServer.socketType
and @see nsISmtpServer.socketType

Constants
=========

plain
-----

**Type**: ``nsMsgSocketTypeValue``

**Value**: ``0``


trySTARTTLS
-----------

**Type**: ``nsMsgSocketTypeValue``

**Value**: ``1``


alwaysSTARTTLS
--------------

**Type**: ``nsMsgSocketTypeValue``

**Value**: ``2``


SSL
---

**Type**: ``nsMsgSocketTypeValue``

**Value**: ``3``

