==============
nsIMimeEmitter
==============

`mailnews/mime/public/nsIMimeEmitter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeEmitter.idl>`_


Properties
==========

outputListener
--------------

``attribute nsIStreamListener outputListener``

Methods
=======

initialize
----------

``void initialize(url, aChannel, aFormat)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` url
* in :doc:`nsIChannel` aChannel
* in long aFormat

complete
--------

``void complete()``

setPipe
-------

``void setPipe(inputStream, outStream)``

Parameters
^^^^^^^^^^

* in :doc:`nsIInputStream` inputStream
* in :doc:`nsIOutputStream` outStream

startHeader
-----------

``void startHeader(rootMailHeader, headerOnly, msgID, outCharset)``

Parameters
^^^^^^^^^^

* in boolean rootMailHeader
* in boolean headerOnly
* in string msgID
* in string outCharset

addHeaderField
--------------

``void addHeaderField(field, value)``

Parameters
^^^^^^^^^^

* in string field
* in string value

addAllHeaders
-------------

``void addAllHeaders(allheaders)``

Parameters
^^^^^^^^^^

* in ACString allheaders

writeHTMLHeaders
----------------

``void writeHTMLHeaders(name)``

Write the HTML Headers for the current attachment.
Note: Book case this with an EndHeader call.

Parameters
^^^^^^^^^^

* in AUTF8String name

endHeader
---------

``void endHeader(name)``

Finish writing the headers for the current attachment.

Parameters
^^^^^^^^^^

* in AUTF8String name

updateCharacterSet
------------------

``void updateCharacterSet(aCharset)``

Parameters
^^^^^^^^^^

* in string aCharset

startAttachment
---------------

``void startAttachment(name, contentType, url, aNotDownloaded)``

Parameters
^^^^^^^^^^

* in AUTF8String name
* in string contentType
* in string url
* in boolean aNotDownloaded

addAttachmentField
------------------

``void addAttachmentField(field, value)``

Parameters
^^^^^^^^^^

* in string field
* in string value

endAttachment
-------------

``void endAttachment()``

endAllAttachments
-----------------

``void endAllAttachments()``

startBody
---------

``void startBody(bodyOnly, msgID, outCharset)``

Parameters
^^^^^^^^^^

* in boolean bodyOnly
* in string msgID
* in string outCharset

writeBody
---------

``void writeBody(buf, amountWritten)``

Parameters
^^^^^^^^^^

* in AUTF8String buf
* out uint32_t amountWritten

endBody
-------

``void endBody()``

write
-----

``void write(buf, amountWritten)``

Parameters
^^^^^^^^^^

* in ACString buf
* out uint32_t amountWritten

utilityWrite
------------

``void utilityWrite(buf)``

Parameters
^^^^^^^^^^

* in string buf
