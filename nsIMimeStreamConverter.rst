======================
nsIMimeStreamConverter
======================

`mailnews/mime/public/nsIMimeStreamConverter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/mime/public/nsIMimeStreamConverter.idl>`_

This interface contains mailnews mime specific information for stream
converters. Most of the code is just stuff that has been moved out
of nsIStreamConverter.idl to make it more generic.

Properties
==========

forwardInline
-------------

``attribute boolean forwardInline``

This is used for forward inline, both as a filter action, and from the UI.

forwardInlineFilter
-------------------

``attribute boolean forwardInlineFilter``

This is used for a forward inline filter action. When streaming is done,
we won't open a compose window with the editor contents.

forwardToAddress
----------------

``attribute AString forwardToAddress``

Address for the forward inline filter to forward the message to.

overrideComposeFormat
---------------------

``attribute boolean overrideComposeFormat``

Use the opposite compose format, used for forward inline.

identity
--------

``attribute nsIMsgIdentity identity``

This is used for OpenDraft, OpenEditorTemplate and Forward inline (which use OpenDraft)

originalMsgURI
--------------

``attribute AUTF8String originalMsgURI``

origMsgHdr
----------

``attribute nsIMsgDBHdr origMsgHdr``

Methods
=======

SetMimeOutputType
-----------------

``void SetMimeOutputType(aType)``

Set the desired mime output type on the converer.

Parameters
^^^^^^^^^^

* in nsMimeOutputType aType

GetMimeOutputType
-----------------

``void GetMimeOutputType(aOutFormat)``

Parameters
^^^^^^^^^^

* out nsMimeOutputType aOutFormat

SetStreamURI
------------

``void SetStreamURI(aURI)``

This is needed by libmime for MHTML link processing...the url is the URL
string associated with this input stream.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aURI

SetMimeHeadersListener
----------------------

``void SetMimeHeadersListener(listener, aType)``

Used to extract headers while parsing a message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMimeStreamConverterListener` listener
* in nsMimeOutputType aType
