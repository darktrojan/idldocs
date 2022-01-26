=================
nsIMsgMailNewsUrl
=================

`mailnews/base/public/nsIMsgMailNewsUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMailNewsUrl.idl>`_


Constants
=========

eCopy
-----

**Type**: ``unsigned long``

**Value**: ``0``


eMove
-----

**Type**: ``unsigned long``

**Value**: ``1``


eDisplay
--------

**Type**: ``unsigned long``

**Value**: ``2``


Properties
==========

baseURI
-------

``readonly attribute nsIURI baseURI``

server
------

``readonly attribute nsIMsgIncomingServer server``

failedSecInfo
-------------

``attribute nsITransportSecurityInfo failedSecInfo``

Transport-level security information (if any), in the case of a security
error having occurred.
This value should be considered undefined if an NSS error has not
occurred. Read it as: "the secInfo that was being used when a failure
occurred", not: "the secInfo that failed".
Seems a bit ugly adding more state here, but the idea is that a
nsIUrlListener.OnStopRunningUrl() needs to be able to access a bad
certificate, so as to have the option of adding an exemption (See
Bug 1590473).

folder
------

``attribute nsIMsgFolder folder``

The folder associated with this url.

@exception NS_ERROR_FAILURE    May be thrown if the url does not
relate to a folder, e.g. standalone
.eml messages.

statusFeedback
--------------

``attribute nsIMsgStatusFeedback statusFeedback``

maxProgress
-----------

``attribute long long maxProgress``

The maximum progress for this URL. This might be a count, or it might
be a number of bytes. A value of -1 indicates that this is unknown.

msgWindow
---------

``attribute nsIMsgWindow msgWindow``

mimeHeaders
-----------

``attribute nsIMimeHeaders mimeHeaders``

loadGroup
---------

``readonly attribute nsILoadGroup loadGroup``

searchSession
-------------

``attribute nsIMsgSearchSession searchSession``

updatingFolder
--------------

``attribute boolean updatingFolder``

msgIsInLocalCache
-----------------

``attribute boolean msgIsInLocalCache``

suppressErrorMsgs
-----------------

``attribute boolean suppressErrorMsgs``

errorCode
---------

``attribute ACString errorCode``

Set after an error occurred.
It is not translated and contains no parameters.
It is unique to each different kind of error, i.e. the same
error has the same code, but a different error has a different code.
This allows to recover from specific errors programmatically,
or to keep error statistics.
If the error comes from a server, the implementor should make
efforts to pass on comparable server error identifiers and include
them here, e.g. as suffixes. Example: "imap-sasl-S474", where-as "S474"
comes from the server annd "imap-sasl-" is the prefix for where the
server reports appears.

errorMessage
------------

``attribute AString errorMessage``

Set after an error occurred.
An error message that can be displayed directly
to the end user without further processing.
It must have been translated.
It may contain contain values as part of the message.

memCacheEntry
-------------

``attribute nsICacheEntry memCacheEntry``

msgHeaderSink
-------------

``attribute nsIMsgHeaderSink msgHeaderSink``

isMessageUri
------------

``readonly attribute boolean isMessageUri``

Methods
=======

setFileNameInternal
-------------------

``nsresult setFileNameInternal(aFileName)``

Parameters
^^^^^^^^^^

* in ACString aFileName

Return value
^^^^^^^^^^^^

* nsresult

setSpecInternal
---------------

``nsresult setSpecInternal(aSpec)``

Parameters
^^^^^^^^^^

* in ACString aSpec

Return value
^^^^^^^^^^^^

* nsresult

setPortInternal
---------------

``nsresult setPortInternal(aPort)``

Parameters
^^^^^^^^^^

* in long aPort

Return value
^^^^^^^^^^^^

* nsresult

setQueryInternal
----------------

``nsresult setQueryInternal(aQuery)``

Parameters
^^^^^^^^^^

* in ACString aQuery

Return value
^^^^^^^^^^^^

* nsresult

setUsernameInternal
-------------------

``nsresult setUsernameInternal(aUsername)``

Parameters
^^^^^^^^^^

* in ACString aUsername

Return value
^^^^^^^^^^^^

* nsresult

RegisterListener
----------------

``void RegisterListener(aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aUrlListener

UnRegisterListener
------------------

``void UnRegisterListener(aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aUrlListener

SetUrlState
-----------

``void SetUrlState(runningUrl, aStatusCode)``

Parameters
^^^^^^^^^^

* in boolean runningUrl
* in nsresult aStatusCode

GetUrlState
-----------

``void GetUrlState(runningUrl)``

Parameters
^^^^^^^^^^

* out boolean runningUrl

IsUrlType
---------

``boolean IsUrlType(type)``

Parameters
^^^^^^^^^^

* in unsigned long type

Return value
^^^^^^^^^^^^

* boolean

getSaveAsListener
-----------------

``nsIStreamListener getSaveAsListener(addDummyEnvelope, aFile)``

Parameters
^^^^^^^^^^

* in boolean addDummyEnvelope
* in :doc:`nsIFile` aFile

Return value
^^^^^^^^^^^^

* :doc:`nsIStreamListener`

loadURI
-------

``void loadURI(docshell, aLoadFlags)``

Loads the URI in a docshell. This will give priority to loading the
URI in the passed-in docshell. If it can't be loaded there
however, the URL dispatcher will go through its normal process of content
loading.

Parameters
^^^^^^^^^^

* in :doc:`nsIDocShell` docshell
* in unsigned long aLoadFlags
