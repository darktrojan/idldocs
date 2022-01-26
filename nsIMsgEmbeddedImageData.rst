=======================
nsIMsgEmbeddedImageData
=======================

`mailnews/compose/public/nsIMsgSend.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSend.idl>`_

This interface is used by Outlook import to shuttle embedded
image information over to nsIMsgSend's createRFC822Message method via
the aEmbbeddedObjects parameter.

Properties
==========

uri
---

``attribute nsIURI uri``

cid
---

``attribute ACString cid``

name
----

``attribute ACString name``
