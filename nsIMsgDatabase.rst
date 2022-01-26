==============
nsIMsgDatabase
==============

`mailnews/db/msgdb/public/nsIMsgDatabase.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIMsgDatabase.idl>`_


Properties
==========

dBFolderInfo
------------

``readonly attribute nsIDBFolderInfo dBFolderInfo``

databaseSize
------------

``readonly attribute long long databaseSize``

folder
------

``readonly attribute nsIMsgFolder folder``

lastUseTime
-----------

``attribute PRTime lastUseTime``

This is used when deciding which db's to close to free up memory
and other resources in an LRU manner. It doesn't track every operation
on every object from the db, but high level things like open, commit,
and perhaps some of the list methods. Commit should be a proxy for all
the mutation methods.

I'm allowing clients to set the last use time as well, so that
nsIMsgFolder.msgDatabase can set the last use time.

FirstNew
--------

``readonly attribute nsMsgKey FirstNew``

msgRetentionSettings
--------------------

``attribute nsIMsgRetentionSettings msgRetentionSettings``

msgDownloadSettings
-------------------

``attribute nsIMsgDownloadSettings msgDownloadSettings``

summaryValid
------------

``attribute boolean summaryValid``

lowWaterArticleNum
------------------

``readonly attribute nsMsgKey lowWaterArticleNum``

highWaterArticleNum
-------------------

``readonly attribute nsMsgKey highWaterArticleNum``

nextPseudoMsgKey
----------------

``attribute nsMsgKey nextPseudoMsgKey``

nextFakeOfflineMsgKey
---------------------

``readonly attribute nsMsgKey nextFakeOfflineMsgKey``

defaultViewFlags
----------------

``readonly attribute nsMsgViewFlagsTypeValue defaultViewFlags``

defaultSortType
---------------

``readonly attribute nsMsgViewSortTypeValue defaultSortType``

defaultSortOrder
----------------

``readonly attribute nsMsgViewSortOrderValue defaultSortOrder``

msgHdrCacheSize
---------------

``attribute unsigned long msgHdrCacheSize``

Methods
=======

Close
-----

``void Close(aForceCommit)``

Parameters
^^^^^^^^^^

* in boolean aForceCommit

Commit
------

``void Commit(commitType)``

Parameters
^^^^^^^^^^

* in nsMsgDBCommit commitType

ForceClosed
-----------

``void ForceClosed()``

clearCachedHdrs
---------------

``void clearCachedHdrs()``

resetHdrCacheSize
-----------------

``void resetHdrCacheSize(size)``

Parameters
^^^^^^^^^^

* in unsigned long size

GetMsgHdrForKey
---------------

``nsIMsgDBHdr GetMsgHdrForKey(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

getMsgHdrForMessageID
---------------------

``nsIMsgDBHdr getMsgHdrForMessageID(messageID)``

Parameters
^^^^^^^^^^

* in string messageID

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

GetMsgHdrForGMMsgID
-------------------

``nsIMsgDBHdr GetMsgHdrForGMMsgID(aGmailMessageID)``

Get a message header for a Gmail message with the given X-GM-MSGID.

Parameters
^^^^^^^^^^

* in string aGmailMessageID

  The ID of the message to find.

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

  the message, or null if not found (without throwing an error).

ContainsKey
-----------

``boolean ContainsKey(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

CreateNewHdr
------------

``nsIMsgDBHdr CreateNewHdr(aKey)``

Must call AddNewHdrToDB after creating. The idea is that you create
a new header, fill in its properties, and then call AddNewHdrToDB.
AddNewHdrToDB will send notifications to any listeners.

Parameters
^^^^^^^^^^

* in nsMsgKey aKey

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

AddNewHdrToDB
-------------

``void AddNewHdrToDB(newHdr, notify)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` newHdr
* in boolean notify

CopyHdrFromExistingHdr
----------------------

``nsIMsgDBHdr CopyHdrFromExistingHdr(key, existingHdr, addHdrToDB)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in :doc:`nsIMsgDBHdr` existingHdr
* in boolean addHdrToDB

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

listAllKeys
-----------

``Array<nsMsgKey> listAllKeys()``

Returns all message keys stored in the database.
Keys are returned in the order as stored in the database.
The caller should sort them if it needs to.

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

EnumerateMessages
-----------------

``nsIMsgEnumerator EnumerateMessages()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgEnumerator`

ReverseEnumerateMessages
------------------------

``nsIMsgEnumerator ReverseEnumerateMessages()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgEnumerator`

enumerateThreads
----------------

``nsIMsgThreadEnumerator enumerateThreads()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgThreadEnumerator`

getFilterEnumerator
-------------------

``nsIMsgEnumerator getFilterEnumerator(searchTerms, reverse)``

Get an enumerator of messages matching the passed-in search terms.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgSearchTerm`> searchTerms
* in boolean reverse

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgEnumerator`

  An enumerator to iterate over matching messages.

syncCounts
----------

``void syncCounts()``

GetThreadContainingMsgHdr
-------------------------

``nsIMsgThread GetThreadContainingMsgHdr(msgHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgThread`

MarkHdrRead
-----------

``void MarkHdrRead(msgHdr, bRead, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in boolean bRead
* in :doc:`nsIDBChangeListener` instigator

MarkHdrReplied
--------------

``void MarkHdrReplied(msgHdr, bReplied, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in boolean bReplied
* in :doc:`nsIDBChangeListener` instigator

MarkHdrMarked
-------------

``void MarkHdrMarked(msgHdr, mark, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in boolean mark
* in :doc:`nsIDBChangeListener` instigator

MarkHdrNotNew
-------------

``void MarkHdrNotNew(aMsgHdr, aInstigator)``

Remove the new status from a message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in :doc:`nsIDBChangeListener` aInstigator

MarkMDNNeeded
-------------

``void MarkMDNNeeded(key, bNeeded, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bNeeded
* in :doc:`nsIDBChangeListener` instigator

IsMDNNeeded
-----------

``boolean IsMDNNeeded(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

MarkMDNSent
-----------

``void MarkMDNSent(key, bNeeded, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bNeeded
* in :doc:`nsIDBChangeListener` instigator

IsMDNSent
---------

``boolean IsMDNSent(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

MarkRead
--------

``void MarkRead(key, bRead, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bRead
* in :doc:`nsIDBChangeListener` instigator

MarkReplied
-----------

``void MarkReplied(key, bReplied, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bReplied
* in :doc:`nsIDBChangeListener` instigator

MarkForwarded
-------------

``void MarkForwarded(key, bForwarded, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bForwarded
* in :doc:`nsIDBChangeListener` instigator

MarkRedirected
--------------

``void MarkRedirected(key, bRedirected, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bRedirected
* in :doc:`nsIDBChangeListener` instigator

MarkHasAttachments
------------------

``void MarkHasAttachments(key, bHasAttachments, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean bHasAttachments
* in :doc:`nsIDBChangeListener` instigator

MarkThreadRead
--------------

``Array<nsMsgKey> MarkThreadRead(thread, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgThread` thread
* in :doc:`nsIDBChangeListener` instigator

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

MarkThreadIgnored
-----------------

``void MarkThreadIgnored(thread, threadKey, bIgnored, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgThread` thread
* in nsMsgKey threadKey
* in boolean bIgnored
* in :doc:`nsIDBChangeListener` instigator

MarkThreadWatched
-----------------

``void MarkThreadWatched(thread, threadKey, bWatched, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgThread` thread
* in nsMsgKey threadKey
* in boolean bWatched
* in :doc:`nsIDBChangeListener` instigator

MarkHeaderKilled
----------------

``void MarkHeaderKilled(msg, bIgnored, instigator)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg
* in boolean bIgnored
* in :doc:`nsIDBChangeListener` instigator

IsRead
------

``boolean IsRead(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

IsIgnored
---------

``boolean IsIgnored(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

IsWatched
---------

``boolean IsWatched(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

IsMarked
--------

``boolean IsMarked(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

HasAttachments
--------------

``boolean HasAttachments(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

Return value
^^^^^^^^^^^^

* boolean

markAllRead
-----------

``Array<nsMsgKey> markAllRead()``

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

deleteMessages
--------------

``void deleteMessages(nsMsgKeys, instigator)``

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> nsMsgKeys
* in :doc:`nsIDBChangeListener` instigator

DeleteMessage
-------------

``void DeleteMessage(key, instigator, commit)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in :doc:`nsIDBChangeListener` instigator
* in boolean commit

DeleteHeader
------------

``void DeleteHeader(msgHdr, instigator, commit, notify)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in :doc:`nsIDBChangeListener` instigator
* in boolean commit
* in boolean notify

RemoveHeaderMdbRow
------------------

``void RemoveHeaderMdbRow(msgHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr

UndoDelete
----------

``void UndoDelete(msgHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr

MarkMarked
----------

``void MarkMarked(key, mark, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean mark
* in :doc:`nsIDBChangeListener` instigator

MarkOffline
-----------

``void MarkOffline(key, offline, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean offline
* in :doc:`nsIDBChangeListener` instigator

SetLabel
--------

``void SetLabel(key, label)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in nsMsgLabelValue label

setStringProperty
-----------------

``void setStringProperty(aKey, aProperty, aValue)``

Parameters
^^^^^^^^^^

* in nsMsgKey aKey
* in string aProperty
* in string aValue

setStringPropertyByHdr
----------------------

``void setStringPropertyByHdr(msgHdr, aProperty, aValue)``

Set the value of a string property in a message header

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in string aProperty
* in string aValue

setUint32PropertyByHdr
----------------------

``void setUint32PropertyByHdr(aMsgHdr, aProperty, aValue)``

Set the value of a uint32 property in a message header.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in string aProperty
* in unsigned long aValue

MarkImapDeleted
---------------

``void MarkImapDeleted(key, deleted, instigator)``

Parameters
^^^^^^^^^^

* in nsMsgKey key
* in boolean deleted
* in :doc:`nsIDBChangeListener` instigator

applyRetentionSettings
----------------------

``void applyRetentionSettings(aMsgRetentionSettings, aDeleteViaFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgRetentionSettings` aMsgRetentionSettings
* in boolean aDeleteViaFolder

HasNew
------

``boolean HasNew()``

Return value
^^^^^^^^^^^^

* boolean

ClearNewList
------------

``void ClearNewList(notify)``

Parameters
^^^^^^^^^^

* in boolean notify

AddToNewList
------------

``void AddToNewList(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

GetOfflineOpForKey
------------------

``nsIMsgOfflineImapOperation GetOfflineOpForKey(messageKey, create)``

Parameters
^^^^^^^^^^

* in nsMsgKey messageKey
* in boolean create

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgOfflineImapOperation`

RemoveOfflineOp
---------------

``void RemoveOfflineOp(op)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgOfflineImapOperation` op

ListAllOfflineOpIds
-------------------

``void ListAllOfflineOpIds(offlineOpIds)``

Parameters
^^^^^^^^^^

* in nsMsgKeyArrayPtr offlineOpIds

ListAllOfflineDeletes
---------------------

``void ListAllOfflineDeletes(offlineDeletes)``

Parameters
^^^^^^^^^^

* in nsMsgKeyArrayPtr offlineDeletes

ListAllOfflineMsgs
------------------

``Array<nsMsgKey> ListAllOfflineMsgs()``

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

setAttributeOnPendingHdr
------------------------

``void setAttributeOnPendingHdr(pendingHdr, property, propertyVal)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` pendingHdr
* in string property
* in string propertyVal

setUint32AttributeOnPendingHdr
------------------------------

``void setUint32AttributeOnPendingHdr(pendingHdr, property, propertyVal)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` pendingHdr
* in string property
* in unsigned long propertyVal

setUint64AttributeOnPendingHdr
------------------------------

``void setUint64AttributeOnPendingHdr(aPendingHdr, aProperty, aPropertyVal)``

Sets a pending 64 bit attribute, which tells the DB that when a message
which looks like the pendingHdr (e.g., same message-id) is added to the
db, set the passed in property and value on the new header. This is
usually because we've copied an imap message to a different folder, and
want to carry forward attributes from the original message to the copy,
but don't have the message hdr for the copy yet so we can't set
attributes directly.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aPendingHdr
* in string aProperty
* in unsigned long long aPropertyVal

updatePendingAttributes
-----------------------

``void updatePendingAttributes(aNewHdr)``

Given a message header with its message-id set, update any pending
attributes on the header.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aNewHdr

createCollationKey
------------------

``Array<octet> createCollationKey(sourceString)``

Parameters
^^^^^^^^^^

* in AString sourceString

Return value
^^^^^^^^^^^^

* Array<octet>

compareCollationKeys
--------------------

``long compareCollationKeys(key1, key2)``

Parameters
^^^^^^^^^^

* in Array<octet> key1
* in Array<octet> key2

Return value
^^^^^^^^^^^^

* long

getNewList
----------

``Array<nsMsgKey> getNewList()``

The list of messages currently in the NEW state.

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

getCachedHits
-------------

``nsIMsgEnumerator getCachedHits(aSearchFolderUri)``

Parameters
^^^^^^^^^^

* in AUTF8String aSearchFolderUri

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgEnumerator`

refreshCache
------------

``Array<nsMsgKey> refreshCache(aSearchFolderUri, aNewHits)``

Update search cache to ensure it contains aNewHits.

Parameters
^^^^^^^^^^

* in AUTF8String aSearchFolderUri
* in Array<nsMsgKey> aNewHits

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

  list of keys of messages removed from cache.

updateHdrInCache
----------------

``void updateHdrInCache(aSearchFolderUri, aHdr, aAdd)``

Parameters
^^^^^^^^^^

* in AUTF8String aSearchFolderUri
* in :doc:`nsIMsgDBHdr` aHdr
* in boolean aAdd

hdrIsInCache
------------

``boolean hdrIsInCache(aSearchFolderUri, aHdr)``

Parameters
^^^^^^^^^^

* in AUTF8String aSearchFolderUri
* in :doc:`nsIMsgDBHdr` aHdr

Return value
^^^^^^^^^^^^

* boolean
