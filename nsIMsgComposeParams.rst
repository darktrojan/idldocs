===================
nsIMsgComposeParams
===================

`mailnews/compose/public/nsIMsgComposeParams.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgComposeParams.idl>`_


Properties
==========

type
----

``attribute MSG_ComposeType type``

format
------

``attribute MSG_ComposeFormat format``

originalMsgURI
--------------

``attribute AUTF8String originalMsgURI``

identity
--------

``attribute nsIMsgIdentity identity``

composeFields
-------------

``attribute nsIMsgCompFields composeFields``

bodyIsLink
----------

``attribute boolean bodyIsLink``

sendListener
------------

``attribute nsIMsgSendListener sendListener``

smtpPassword
------------

``attribute AString smtpPassword``

origMsgHdr
----------

``attribute nsIMsgDBHdr origMsgHdr``

htmlToQuote
-----------

``attribute AUTF8String htmlToQuote``

HTML-formatted content to quote in the body of the message.
Set this to get different content than what would normally
appear in the body, e.g. the original message body in a reply.
