================
nsIMsgMessageUrl
================

`mailnews/base/public/nsIMsgMailNewsUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMailNewsUrl.idl>`_


Properties
==========

uri
---

``attribute AUTF8String uri``

messageFile
-----------

``attribute nsIFile messageFile``

AddDummyEnvelope
----------------

``attribute boolean AddDummyEnvelope``

canonicalLineEnding
-------------------

``attribute boolean canonicalLineEnding``

originalSpec
------------

``attribute AUTF8String originalSpec``

normalizedSpec
--------------

``readonly attribute AUTF8String normalizedSpec``

messageHeader
-------------

``attribute nsIMsgDBHdr messageHeader``

A message db header for that message.

@note This attribute is not guaranteed to be set, so callers that
actually require an nsIMsgDBHdr will need to use the uri attribute
on this interface to get the  appropriate nsIMsgMessageService and
then get the header from there.
