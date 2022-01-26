==============
nsIMsgCompType
==============

`mailnews/compose/public/nsIMsgComposeParams.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgComposeParams.idl>`_


Constants
=========

New
---

**Type**: ``long``

**Value**: ``0``


Reply
-----

**Type**: ``long``

**Value**: ``1``


ReplyAll
--------

**Type**: ``long``

**Value**: ``2``


ForwardAsAttachment
-------------------

**Type**: ``long``

**Value**: ``3``


ForwardInline
-------------

**Type**: ``long``

**Value**: ``4``


NewsPost
--------

**Type**: ``long``

**Value**: ``5``


ReplyToSender
-------------

**Type**: ``long``

**Value**: ``6``


ReplyToGroup
------------

**Type**: ``long``

**Value**: ``7``


ReplyToSenderAndGroup
---------------------

**Type**: ``long``

**Value**: ``8``


Draft
-----

**Type**: ``long``

**Value**: ``9``


Template
--------

**Type**: ``long``

**Value**: ``10``


MailToUrl
---------

**Type**: ``long``

**Value**: ``11``


ReplyWithTemplate
-----------------

**Type**: ``long``

**Value**: ``12``


ReplyToList
-----------

**Type**: ``long``

**Value**: ``13``


Redirect
--------

**Type**: ``long``

**Value**: ``14``

Will resend the original message keeping the Subject and the body the
same, and will set the Reply-To: header to the sender of the original
message.  This gets the redirector "out of the loop" because replies
to the message will go to the original sender.  This is not the same
as the Resent mechanism described in section 3.6.6 of RFC 2822, and
so therefore does not use Resent-* headers.

EditAsNew
---------

**Type**: ``long``

**Value**: ``15``

Used to compose a new message from an existing message. Links
are sanitized since the message could be from external sources.

EditTemplate
------------

**Type**: ``long``

**Value**: ``16``

Used to edit an existing template.
