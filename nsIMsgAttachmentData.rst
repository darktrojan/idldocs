====================
nsIMsgAttachmentData
====================

`mailnews/compose/public/nsIMsgSend.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSend.idl>`_


Properties
==========

url
---

``attribute nsIURI url``

desiredType
-----------

``attribute ACString desiredType``

The type to which this document should be
converted.  Legal values are NULL, TEXT_PLAIN
and APPLICATION_POSTSCRIPT (which are macros
defined in net.h); other values are ignored.

realType
--------

``attribute ACString realType``

The type of the URL if known, otherwise empty. For example, if
you were attaching a temp file which was known to contain HTML data,
you would pass in TEXT_HTML as the realType, to override whatever type
the name of the tmp file might otherwise indicate.

realEncoding
------------

``attribute ACString realEncoding``

realName
--------

``attribute ACString realName``

The original name of this document, which will eventually show up in the
Content-Disposition header. For example, if you had copied a document to a
tmp file, this would be the original, human-readable name of the document.

description
-----------

``attribute ACString description``

If you put a string here, it will show up as the Content-Description
header. This can be any explanatory text; it's not a file name.

xMacType
--------

``attribute ACString xMacType``

xMacCreator
-----------

``attribute ACString xMacCreator``
