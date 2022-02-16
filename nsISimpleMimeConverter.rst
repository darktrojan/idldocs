======================
nsISimpleMimeConverter
======================

`mailnews/mime/public/nsISimpleMimeConverter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsISimpleMimeConverter.idl>`_

nsISimpleMimeConverter provides an interface for rendering raw mime objects
as HTML. It's used to provide converters for mime types not handled
directly by the mime code.
"text/calendar" - see calendar/base/src/CalMimeConverter.jsm
"text/vcard"    - see mailnews/addrbook/modules/VCardUtils.jsm

Properties
==========

uri
---

``attribute nsIURI uri``

Methods
=======

convertToHTML
-------------

``AUTF8String convertToHTML(contentType, data)``

Render mime data into HTML.
NOTE: it is important that this function doesn't do anything which
would allows other events to processed on the thread (that means
calls to NS_ProcessNextEvent()). Using a synchronous XMLHttpRequest
is a prime example - it spins the thread queue, processing other
events while it waits.

It's an issue because it's likely that convertToHTML() is being called
in response to data coming in from an async inputstream. Letting other
events be handled on the thread means that more data might come in
from the stream, recursively calling the nsIStreamListener
onDataAvailable() handler we're already inside! And it's tricky to
track down this kind of problem - it only occurs if the data is big
enough that it comes through in multiple chunks.
See bug 1679299.

Parameters
^^^^^^^^^^

* in ACString contentType
* in AUTF8String data

Return value
^^^^^^^^^^^^

* AUTF8String
