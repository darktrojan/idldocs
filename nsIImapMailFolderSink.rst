=====================
nsIImapMailFolderSink
=====================

`mailnews/imap/public/nsIImapMailFolderSink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapMailFolderSink.idl>`_

nsIImapMailFolderSink provides a way for the IMAP system to communicate
with the local folder representation.

The IMAP system could poke folders directly, but going through this
interface has a couple of benefits:

1. It better defines the public coupling between the two systems.
2. It's easier to wrap with a proxy class so the IMAP system can safely
call the methods across thread boundaries (see ImapMailFolderSinkProxy).

Properties
==========

folderNeedsACLListed
--------------------

``attribute boolean folderNeedsACLListed``

folderNeedsSubscribing
----------------------

``attribute boolean folderNeedsSubscribing``

folderNeedsAdded
----------------

``attribute boolean folderNeedsAdded``

aclFlags
--------

``attribute unsigned long aclFlags``

uidValidity
-----------

``attribute long uidValidity``

folderQuotaCommandIssued
------------------------

``attribute boolean folderQuotaCommandIssued``

Whether we have asked the server for this folder's quota information.
If the server supports quotas, this occurs when the folder is opened.

shouldDownloadAllHeaders
------------------------

``readonly attribute boolean shouldDownloadAllHeaders``

onlineDelimiter
---------------

``readonly attribute char onlineDelimiter``

Methods
=======

setFolderQuotaData
------------------

``void setFolderQuotaData(aAction, aFolderQuotaRoot, aFolderQuotaUsed, aFolderQuotaLimit)``

Set FolderQuotaData information

Parameters
^^^^^^^^^^

* in unsigned long aAction
* in ACString aFolderQuotaRoot
* in unsigned long long aFolderQuotaUsed
* in unsigned long long aFolderQuotaLimit

OnNewIdleMessages
-----------------

``void OnNewIdleMessages()``

UpdateImapMailboxInfo
---------------------

``void UpdateImapMailboxInfo(aProtocol, aSpec)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in :doc:`nsIMailboxSpec` aSpec

UpdateImapMailboxStatus
-----------------------

``void UpdateImapMailboxStatus(aProtocol, aSpec)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in :doc:`nsIMailboxSpec` aSpec

getMsgHdrsToDownload
--------------------

``void getMsgHdrsToDownload(aMore, aTotalCount, aKeys)``

Used when downloading headers in chunks.

Parameters
^^^^^^^^^^

* out boolean aMore
* out long aTotalCount
* out Array<nsMsgKey> aKeys

parseMsgHdrs
------------

``void parseMsgHdrs(aProtocol, aHdrXferInfo)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in :doc:`nsIImapHeaderXferInfo` aHdrXferInfo

AbortHeaderParseStream
----------------------

``void AbortHeaderParseStream(aProtocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol

OnlineCopyCompleted
-------------------

``void OnlineCopyCompleted(aProtocol, aCopyState)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in ImapOnlineCopyState aCopyState

StartMessage
------------

``void StartMessage(aUrl)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aUrl

EndMessage
----------

``void EndMessage(aUrl, uidOfMessage)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aUrl
* in nsMsgKey uidOfMessage

NotifySearchHit
---------------

``void NotifySearchHit(aUrl, hitLine)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aUrl
* in string hitLine

copyNextStreamMessage
---------------------

``void copyNextStreamMessage(copySucceeded, copyState)``

Parameters
^^^^^^^^^^

* in boolean copySucceeded
* in :doc:`nsISupports` copyState

closeMockChannel
----------------

``void closeMockChannel(aChannel)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapMockChannel` aChannel

setUrlState
-----------

``void setUrlState(aProtocol, aUrl, isRunning, aSuspend, status)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in :doc:`nsIMsgMailNewsUrl` aUrl
* in boolean isRunning
* in boolean aSuspend
* in nsresult status

releaseUrlCacheEntry
--------------------

``void releaseUrlCacheEntry(aUrl)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aUrl

headerFetchCompleted
--------------------

``void headerFetchCompleted(aProtocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol

setBiffStateAndUpdate
---------------------

``void setBiffStateAndUpdate(biffState)``

Parameters
^^^^^^^^^^

* in long biffState

progressStatusString
--------------------

``void progressStatusString(aProtocol, aMsgId, extraInfo)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in string aMsgId
* in wstring extraInfo

percentProgress
---------------

``void percentProgress(aProtocol, aFmtStringName, aMailboxName, aCurrentProgress, aMaxProgressProgressInfo)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol
* in ACString aFmtStringName
* in AString aMailboxName
* in long long aCurrentProgress
* in long long aMaxProgressProgressInfo

clearFolderRights
-----------------

``void clearFolderRights()``

setCopyResponseUid
------------------

``void setCopyResponseUid(msgIdString, aUrl)``

Parameters
^^^^^^^^^^

* in string msgIdString
* in :doc:`nsIImapUrl` aUrl

setAppendMsgUid
---------------

``void setAppendMsgUid(newKey, aUrl)``

Parameters
^^^^^^^^^^

* in nsMsgKey newKey
* in :doc:`nsIImapUrl` aUrl

getMessageId
------------

``ACString getMessageId(aUrl)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aUrl

Return value
^^^^^^^^^^^^

* ACString
