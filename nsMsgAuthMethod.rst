===============
nsMsgAuthMethod
===============

`mailnews/base/public/MailNewsTypes2.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/MailNewsTypes2.idl>`_

Defines which authentication schemes we should try.
Used by @see nsIMsgIncomingServer.authMethod
and @see nsISmtpServer.authMethod

Constants
=========

none
----

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``1``


old
---

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``2``


passwordCleartext
-----------------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``3``


passwordEncrypted
-----------------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``4``


GSSAPI
------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``5``


NTLM
----

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``6``


External
--------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``7``


secure
------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``8``


anything
--------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``9``


OAuth2
------

**Type**: ``nsMsgAuthMethodValue``

**Value**: ``10``

