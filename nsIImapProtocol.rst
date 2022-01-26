===============
nsIImapProtocol
===============

`mailnews/imap/public/nsIImapProtocol.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapProtocol.idl>`_


Properties
==========

flagAndUidState
---------------

``readonly attribute nsIImapFlagAndUidState flagAndUidState``

Methods
=======

LoadImapUrl
-----------

``void LoadImapUrl(aUrl, aConsumer)``

Set up this connection to run a URL.
Called by nsImapIncomingServer to process a queued URL when it spots a
free connection.
Because nsImapProtocol is really a connection and doesn't follow the
usual nsIChannel lifecycle, this function is provided to allow reuse.
Over and over again.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUrl
* in :doc:`nsISupports` aConsumer

IsBusy
------

``void IsBusy(aIsConnectionBusy, isInboxConnection)``

IsBusy returns true if the connection is currently processing a URL
and false otherwise.

Parameters
^^^^^^^^^^

* out boolean aIsConnectionBusy
* out boolean isInboxConnection

CanHandleUrl
------------

``void CanHandleUrl(aImapUrl, aCanRunUrl, hasToWait)``

Protocol instance examines the URL, looking at the host name,
user name and folder the action would be on in order to figure out
if it can process this URL. I decided to push the semantics about
whether a connection can handle a URL down into the connection level
instead of in the connection cache.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aImapUrl
* out boolean aCanRunUrl
* out boolean hasToWait

Initialize
----------

``void Initialize(aHostSessionList, aServer)``

Initialize a protocol object.

Parameters
^^^^^^^^^^

* in :doc:`nsIImapHostSessionList` aHostSessionList
* in :doc:`nsIImapIncomingServer` aServer

NotifyBodysToDownload
---------------------

``void NotifyBodysToDownload(keys)``

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> keys

GetFlagsForUID
--------------

``void GetFlagsForUID(uid, foundIt, flags, customFlags)``

Parameters
^^^^^^^^^^

* in unsigned long uid
* out boolean foundIt
* out unsigned short flags
* out string customFlags

GetSupportedUserFlags
---------------------

``void GetSupportedUserFlags(flags)``

Parameters
^^^^^^^^^^

* out unsigned short flags

GetRunningImapURL
-----------------

``void GetRunningImapURL(aImapUrl)``

Parameters
^^^^^^^^^^

* out :doc:`nsIImapUrl` aImapUrl

GetRunningUrl
-------------

``void GetRunningUrl(aUrl)``

Parameters
^^^^^^^^^^

* out :doc:`nsIURI` aUrl

tellThreadToDie
---------------

``void tellThreadToDie(aIsSafeToClose)``

Tell thread to die - only call from the UI thread

Parameters
^^^^^^^^^^

* in boolean aIsSafeToClose

GetLastActiveTimeStamp
----------------------

``void GetLastActiveTimeStamp(aTimeStamp)``

Parameters
^^^^^^^^^^

* out PRTime aTimeStamp

pseudoInterruptMsgLoad
----------------------

``void pseudoInterruptMsgLoad(imapFolder, aMsgWindow, interrupted)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` imapFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* out boolean interrupted

GetSelectedMailboxName
----------------------

``void GetSelectedMailboxName(folderName)``

Parameters
^^^^^^^^^^

* out string folderName

ResetToAuthenticatedState
-------------------------

``void ResetToAuthenticatedState()``
