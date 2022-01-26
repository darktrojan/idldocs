===========
nsIMsgQuote
===========

`mailnews/compose/public/nsIMsgQuote.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgQuote.idl>`_


Properties
==========

quoteListener
-------------

``readonly attribute nsIMimeStreamConverterListener quoteListener``

quoteChannel
------------

``readonly attribute nsIChannel quoteChannel``

streamListener
--------------

``readonly attribute nsIMsgQuotingOutputStreamListener streamListener``

Methods
=======

quoteMessage
------------

``void quoteMessage(msgURI, quoteHeaders, streamListener, autodetectCharset, headersOnly, aOrigHdr)``

Quote a particular message specified by its URI.

Parameters
^^^^^^^^^^

* in AUTF8String msgURI
* in boolean quoteHeaders
* in :doc:`nsIMsgQuotingOutputStreamListener` streamListener
* in bool autodetectCharset
* in boolean headersOnly
* in :doc:`nsIMsgDBHdr` aOrigHdr
