===============
nsIPgpMimeProxy
===============

`mailnews/mime/public/nsIPgpMimeProxy.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIPgpMimeProxy.idl>`_

nsIPgpMimeProxy is a proxy for a (JS-)addon for OpenPGP/MIME decryption

Properties
==========

decryptor
---------

``attribute nsIStreamListener decryptor``

the listener that receives the OpenPGP/MIME data stream and decrypts
the message

contentType
-----------

``attribute ACString contentType``

messageURI
----------

``readonly attribute nsIURI messageURI``

holds the URI of the message currently being processed

mimePart
--------

``attribute ACString mimePart``

The particular part number of the multipart object we are working on. The
numbering is the same as in URLs that use the form "...?part=1.1.2".

The value stored in mimePart is only the number, e.g. "1" or "1.1.2"

Methods
=======

setMimeCallback
---------------

``void setMimeCallback(outputFun, outputClosure, myUri)``

set the decoder callback into mimelib

Parameters
^^^^^^^^^^

* in MimeDecodeCallbackFun outputFun
* in voidPtr outputClosure
* in :doc:`nsIURI` myUri

removeMimeCallback
------------------

``void removeMimeCallback()``

init
----

``void init()``

init function

write
-----

``void write(buf, count)``

process encoded data received from mimelib

Parameters
^^^^^^^^^^

* in string buf
* in unsigned long count

finish
------

``void finish()``

finish writing (EOF) from mimelib

outputDecryptedData
-------------------

``void outputDecryptedData(buf, count)``

Pass the decrypted data back from the decryptor and onto to libMime.

Parameters
^^^^^^^^^^

* in string buf
* in unsigned long count
