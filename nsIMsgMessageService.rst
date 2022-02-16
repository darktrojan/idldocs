====================
nsIMsgMessageService
====================

`mailnews/base/public/nsIMsgMessageService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMessageService.idl>`_

nsIMsgMessageService provides higher-level, UI-oriented calls for
dealing with messages in a protocol-agnostic way.
Things the user would recognise as actions they initiated.
This covers things like displaying messages, copying them, saving them
to disk, saving attachments...

Methods
=======

CopyMessage
-----------

``void CopyMessage(aSrcURI, aCopyListener, aMoveMessage, aUrlListener, aMsgWindow, aURL)``

If you want a handle on the running task, pass in a valid nsIURI
ptr. You can later interrupt this action by asking the netlib
service manager to interrupt the url you are given back.
Remember to release aURL when you are done with it. Pass nullptr
in for aURL if you don't care about the returned URL.
Pass in the URI for the message you want to have copied.

Parameters
^^^^^^^^^^

* in AUTF8String aSrcURI
* in :doc:`nsIStreamListener` aCopyListener
* in boolean aMoveMessage
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow
* out :doc:`nsIURI` aURL

CopyMessages
------------

``nsIURI CopyMessages(aKeys, srcFolder, aCopyListener, aMoveMessage, aUrlListener, aMsgWindow)``

Copy multiple messages at a time

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> aKeys
* in :doc:`nsIMsgFolder` srcFolder
* in :doc:`nsIStreamListener` aCopyListener
* in boolean aMoveMessage
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  URI that's run to perform the copy

DisplayMessage
--------------

``void DisplayMessage(aMessageURI, aDisplayConsumer, aMsgWindow, aUrlListener, aAutodetectCharset, aURL)``

When you want a message displayed....

Parameters
^^^^^^^^^^

* in AUTF8String aMessageURI
* in :doc:`nsISupports` aDisplayConsumer
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener
* in boolean aAutodetectCharset
* out :doc:`nsIURI` aURL

openAttachment
--------------

``void openAttachment(aContentType, aFileName, aUrl, aMessageUri, aDisplayConsumer, aMsgWindow, aUrlListener)``

When you want an attachment downloaded

Parameters
^^^^^^^^^^

* in AUTF8String aContentType
* in AUTF8String aFileName
* in AUTF8String aUrl
* in AUTF8String aMessageUri
* in :doc:`nsISupports` aDisplayConsumer
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener

SaveMessageToDisk
-----------------

``void SaveMessageToDisk(aMessageURI, aFile, aGenerateDummyEnvelope, aUrlListener, aURL, canonicalLineEnding, aMsgWindow)``

When you want to spool a message out to a file on disk.
This is an asynch operation of course. You must pass in a
url listener in order to figure out when the operation is done.

Parameters
^^^^^^^^^^

* in AUTF8String aMessageURI
* in :doc:`nsIFile` aFile
* in boolean aGenerateDummyEnvelope
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in boolean canonicalLineEnding
* in :doc:`nsIMsgWindow` aMsgWindow

getUrlForUri
------------

``nsIURI getUrlForUri(aMessageURI, aMsgWindow)``

When you have a uri and you would like to convert that
to a url which can be run through necko, you can use this method.
the Uri MUST refer to a message and not a folder!

Parameters
^^^^^^^^^^

* in AUTF8String aMessageURI
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  a URL which can be run through necko

Search
------

``void Search(aSearchSession, aMsgWindow, aMsgFolder, aSearchUri)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSearchSession` aSearchSession
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgFolder` aMsgFolder
* in AUTF8String aSearchUri

streamMessage
-------------

``nsIURI streamMessage(aMessageURI, aConsumer, aMsgWindow, aUrlListener, aConvertData, aAdditionalHeader, aLocalOnly)``

This method streams a message to the passed in consumer. If aConvertData is true, it
will create a stream converter from message rfc822 to star/star. It will also tack
aAdditionalHeader onto the url (e.g., "header=filter").

@note If we're offline, then even if aLocalOnly is false, we won't stream over the
network

Parameters
^^^^^^^^^^

* in AUTF8String aMessageURI
* in :doc:`nsISupports` aConsumer
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener
* in boolean aConvertData
* in ACString aAdditionalHeader
* in boolean aLocalOnly

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  the URL that gets run

streamHeaders
-------------

``nsIURI streamHeaders(aMessageURI, aConsumer, aUrlListener, aLocalOnly)``

This method streams a message's headers to the passed in consumer.
This is for consumers who want a particular header but don't
want to stream the whole message.

@note If we're offline, then even if aLocalOnly is false, we won't stream over the
network

Parameters
^^^^^^^^^^

* in AUTF8String aMessageURI
* in :doc:`nsIStreamListener` aConsumer
* in :doc:`nsIUrlListener` aUrlListener
* in boolean aLocalOnly

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  the URL that gets run, if any.

isMsgInMemCache
---------------

``boolean isMsgInMemCache(aUrl, aFolder)``

Determines whether a message is in the memory cache. Local folders
don't implement this.
The URL needs to address a message, not a message part, all query
qualifiers will be stripped before looking up the entry in the cache.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUrl
* in :doc:`nsIMsgFolder` aFolder

Return value
^^^^^^^^^^^^

* boolean

  TRUE if the message is in mem cache; FALSE if it is not.

messageURIToMsgHdr
------------------

``nsIMsgDBHdr messageURIToMsgHdr(uri)``

now the the message datasource is going away
we need away to go from message uri to go nsIMsgDBHdr

Parameters
^^^^^^^^^^

* in AUTF8String uri

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

  nsIMsgDBHdr for specified uri or null if failed.
