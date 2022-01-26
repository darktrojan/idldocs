============
nsIMailtoUrl
============

`mailnews/compose/public/nsISmtpUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsISmtpUrl.idl>`_


Properties
==========

fromPart
--------

``readonly attribute AUTF8String fromPart``

These attributes are available should mailnews or extensions want them
but aren't used by standard in mailnews.

followUpToPart
--------------

``readonly attribute AUTF8String followUpToPart``

organizationPart
----------------

``readonly attribute AUTF8String organizationPart``

replyToPart
-----------

``readonly attribute AUTF8String replyToPart``

priorityPart
------------

``readonly attribute AUTF8String priorityPart``

newsHostPart
------------

``readonly attribute AUTF8String newsHostPart``

Methods
=======

getMessageContents
------------------

``void getMessageContents(aToPart, aCcPart, aBccPart, aSubjectPart, aBodyPart, aHtmlPart, aReferencePart, aNewsgroupPart, aFormat)``

mailto: parse specific getters
All of these fields are things we can effectively extract from a
mailto url if it contains all of these values
Note: Attachments aren't available because that would expose a potential
security hole (see bug 99055).
These items are in one function as we only ever get them from the one
place and all at the same time.

Parameters
^^^^^^^^^^

* out AUTF8String aToPart
* out AUTF8String aCcPart
* out AUTF8String aBccPart
* out AUTF8String aSubjectPart
* out AUTF8String aBodyPart
* out AUTF8String aHtmlPart
* out ACString aReferencePart
* out AUTF8String aNewsgroupPart
* out MSG_ComposeFormat aFormat
