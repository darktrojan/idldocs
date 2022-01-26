============
nsIMsgFolder
============

`mailnews/base/public/nsIMsgFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolder.idl>`_


Constants
=========

nsMsgBiffState_NewMail
----------------------

**Type**: ``nsMsgBiffState``

**Value**: ``0``


nsMsgBiffState_NoMail
---------------------

**Type**: ``nsMsgBiffState``

**Value**: ``1``


nsMsgBiffState_Unknown
----------------------

**Type**: ``nsMsgBiffState``

**Value**: ``2``


nsMsgDispositionState_None
--------------------------

**Type**: ``nsMsgDispositionState``

**Value**: ``-1``


nsMsgDispositionState_Replied
-----------------------------

**Type**: ``nsMsgDispositionState``

**Value**: ``0``


nsMsgDispositionState_Forwarded
-------------------------------

**Type**: ``nsMsgDispositionState``

**Value**: ``1``


nsMsgDispositionState_Redirected
--------------------------------

**Type**: ``nsMsgDispositionState``

**Value**: ``2``


allMessageCountNotifications
----------------------------

**Type**: ``unsigned long``

**Value**: ``0``

Turn notifications on/off for various notification types. Currently only
supporting allMessageCountNotifications which refers to both total and
unread message counts.

Properties
==========

URI
---

``readonly attribute AUTF8String URI``

name
----

``attribute AString name``

prettyName
----------

``attribute AString prettyName``

abbreviatedName
---------------

``readonly attribute AString abbreviatedName``

parent
------

``attribute nsIMsgFolder parent``

messages
--------

``readonly attribute nsIMsgEnumerator messages``

folderURL
---------

``readonly attribute AUTF8String folderURL``

URL for this folder

showDeletedMessages
-------------------

``readonly attribute boolean showDeletedMessages``

should probably move to the server

server
------

``readonly attribute nsIMsgIncomingServer server``

this folder's parent server

isServer
--------

``readonly attribute boolean isServer``

is this folder the "phantom" server folder?

canSubscribe
------------

``readonly attribute boolean canSubscribe``

canFileMessages
---------------

``readonly attribute boolean canFileMessages``

noSelect
--------

``readonly attribute boolean noSelect``

imapShared
----------

``readonly attribute boolean imapShared``

canDeleteMessages
-----------------

``readonly attribute boolean canDeleteMessages``

canCreateSubfolders
-------------------

``readonly attribute boolean canCreateSubfolders``

does this folder allow subfolders?
for example, newsgroups cannot have subfolders, and the INBOX
on some IMAP servers cannot have subfolders

canRename
---------

``readonly attribute boolean canRename``

can you change the name of this folder?
for example, newsgroups
and some special folders can't be renamed

canCompact
----------

``readonly attribute boolean canCompact``

rootFolder
----------

``readonly attribute nsIMsgFolder rootFolder``

the phantom server folder

numPendingUnread
----------------

``readonly attribute long numPendingUnread``

These functions are used for tricking the front end into thinking that we
have more messages than are really in the DB.  This is usually after an
IMAP message copy where we don't want to do an expensive select until the
user actually opens that folder. These functions are called when
MSG_Master::GetFolderLineById is populating a MSG_FolderLine struct used
by the FE.

numPendingTotalMessages
-----------------------

``readonly attribute long numPendingTotalMessages``

hasNewMessages
--------------

``attribute boolean hasNewMessages``

does this folder have new messages


hasFolderOrSubfolderNewMessages
-------------------------------

``readonly attribute boolean hasFolderOrSubfolderNewMessages``

Indicates whether this folder or any of its subfolders have new messages.

firstNewMessage
---------------

``readonly attribute nsIMsgDBHdr firstNewMessage``

return the first new message in the folder


expungedBytes
-------------

``readonly attribute long long expungedBytes``

deletable
---------

``readonly attribute boolean deletable``

Can this folder be deleted?
For example, special folders and isServer folders cannot be deleted.

displayRecipients
-----------------

``readonly attribute boolean displayRecipients``

should we be displaying recipients instead of the sender?
for example, in the Sent folder, recipients are more relevant
than the sender

manyHeadersToDownload
---------------------

``readonly attribute boolean manyHeadersToDownload``

used to determine if it will take a long time to download all
the headers in this folder - so that we can do folder notifications
synchronously instead of asynchronously

relativePathName
----------------

``readonly attribute ACString relativePathName``

sizeOnDisk
----------

``attribute long long sizeOnDisk``

size of this folder on disk (not including .msf file)
for imap, it's the sum of the size of the messages

username
--------

``readonly attribute ACString username``

hostname
--------

``readonly attribute ACString hostname``

flags
-----

``attribute unsigned long flags``

Direct access to the set/get all the flags at once.

locked
------

``readonly attribute boolean locked``

biffState
---------

``attribute unsigned long biffState``

gettingNewMessages
------------------

``attribute boolean gettingNewMessages``

are we running a url as a result of the user clicking get msg?

filePath
--------

``attribute nsIFile filePath``

local path of this folder

summaryFile
-----------

``readonly attribute nsIFile summaryFile``

baseMessageURI
--------------

``readonly attribute AUTF8String baseMessageURI``

msgDatabase
-----------

``attribute nsIMsgDatabase msgDatabase``

Gets the message database for the folder.

Note that if the database is out of date, the implementation MAY choose to
throw an error. For a handle to the database which MAY NOT throw an error,
one can use getDBFolderInfoAndDB.

The attribute can also be set to another database or to null to force the
folder to reopen the same database when it is needed again.

@exception NS_MSG_ERROR_FOLDER_SUMMARY_MISSING If the database does not
exist.
@exception NS_MSG_ERROR_FOLDER_SUMMARY_OUT_OF_DATE If the database contains
out of date information.
@see nsIMsgFolder::getDBFolderInfoAndDB.

databaseOpen
------------

``readonly attribute boolean databaseOpen``

supportsOffline
---------------

``readonly attribute boolean supportsOffline``

retentionSettings
-----------------

``attribute nsIMsgRetentionSettings retentionSettings``

downloadSettings
----------------

``attribute nsIMsgDownloadSettings downloadSettings``

sortOrder
---------

``attribute long sortOrder``

used for order in the folder pane, folder pickers, etc.

dBTransferInfo
--------------

``attribute nsIDBFolderInfo dBTransferInfo``

lastMessageLoaded
-----------------

``attribute nsMsgKey lastMessageLoaded``

subFolders
----------

``readonly attribute Array<nsIMsgFolder> subFolders``

Returns an array containing nsIMsgFolder items that are
subfolders of the instance this is called on.

hasSubFolders
-------------

``readonly attribute boolean hasSubFolders``

Returns true if this folder has sub folders.

numSubFolders
-------------

``readonly attribute unsigned long numSubFolders``

Returns the number of sub folders that this folder has.

descendants
-----------

``readonly attribute Array<nsIMsgFolder> descendants``

customIdentity
--------------

``readonly attribute nsIMsgIdentity customIdentity``

msgStore
--------

``readonly attribute nsIMsgPluggableStore msgStore``

Pluggable store for this folder. Currently, this will always be the same
as the pluggable store for the server.

incomingServerType
------------------

``readonly attribute ACString incomingServerType``

Protocol type, i.e. "pop3", "imap", "nntp", "none", etc
used to construct URLs for this account type.

Methods
=======

Init
----

``void Init(uri)``

This method is called by the folder-lookup-service after constructing
a folder to initialize its URI. You would not normally
call this method directly.

Parameters
^^^^^^^^^^

* in AUTF8String uri

startFolderLoading
------------------

``void startFolderLoading()``

endFolderLoading
----------------

``void endFolderLoading()``

folderNamesReady
----------------

``void folderNamesReady(aReady)``

Parameters
^^^^^^^^^^

* out boolean aReady

updateFolder
------------

``void updateFolder(aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow

getFilterList
-------------

``nsIMsgFilterList getFilterList(msgWindow)``

Get the server's list of filters. (Or in the case of news, the
filter list for this newsgroup)
This list SHOULD be used for all incoming messages.
Since the returned nsIMsgFilterList is mutable, it is not necessary to call
setFilterList after the filters have been changed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

  The list of filters

setFilterList
-------------

``void setFilterList(filterList)``

Set the server's list of filters.
Note that this does not persist the filter list. To change the contents
of the existing filters, use getFilterList and mutate the values as
appropriate.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` filterList

getEditableFilterList
---------------------

``nsIMsgFilterList getEditableFilterList(aMsgWindow)``

Get user editable filter list. This does not have to be the same as
the filterlist above, typically depending on the users preferences.
The filters in this list are not processed, but only to be edited by
the user.
@see getFilterList

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilterList`

  The list of filters

setEditableFilterList
---------------------

``void setEditableFilterList(aFilterList)``

Set user editable filter list.
This does not persist the filterlist, @see setFilterList
@see getEditableFilterList
@see setFilterList

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilterList` aFilterList

ForceDBClosed
-------------

``void ForceDBClosed()``

Force close the mail database associated with this folder.

closeAndBackupFolderDB
----------------------

``void closeAndBackupFolderDB(newName)``

Close and backup a folder database prior to reparsing

Parameters
^^^^^^^^^^

* in ACString newName

  New name of the corresponding message folder.
  Used in rename to set the file name to match the renamed
  folder. Set to empty to use the existing folder name.

deleteStorage
-------------

``void deleteStorage()``

Delete the backing store of the folder, but not the folder itself.

deleteSelf
----------

``void deleteSelf(msgWindow)``

Delete this folder and its children, if any.
Note: this may mean moving it to trash and/or requesting confirmation
from the user, depending on implementation.
So the deletion may not take place immediately (or at all!)

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

propagateDelete
---------------

``void propagateDelete(folder, deleteStorage, msgWindow)``

Delete the given subfolder of this folder.
It does not need to be a direct child.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in boolean deleteStorage
* in :doc:`nsIMsgWindow` msgWindow

recursiveDelete
---------------

``void recursiveDelete(deleteStorage, msgWindow)``

Delete the folder and all of its subfolders.

Parameters
^^^^^^^^^^

* in boolean deleteStorage
* in :doc:`nsIMsgWindow` msgWindow

createSubfolder
---------------

``void createSubfolder(folderName, msgWindow)``

Create a subfolder of the current folder with the passed in name.
For IMAP, this will be an async operation and the folder won't exist
until it is created on the server.

Parameters
^^^^^^^^^^

* in AString folderName
* in :doc:`nsIMsgWindow` msgWindow

Throws
^^^^^^

* NS_MSG_FOLDER_EXISTS

addSubfolder
------------

``nsIMsgFolder addSubfolder(aFolderName)``

Adds the subfolder with the passed name to the folder hierarchy.
This is used internally during folder discovery; It shouldn't be
used to create folders since it won't create storage for the folder,
especially for imap. Unless you know exactly what you're doing, you
should be using createSubfolder + getChildNamed or createLocalSubfolder.

Parameters
^^^^^^^^^^

* in AString aFolderName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  The folder added.

createStorageIfMissing
----------------------

``void createStorageIfMissing(urlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` urlListener

compact
-------

``void compact(aListener, aMsgWindow)``

Compact this folder. For IMAP folders configured for offline use,
it will also compact the offline store, and the completed notification
will occur when the Expunge is finished, not the offline store compaction.

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

compactAll
----------

``void compactAll(aListener, aMsgWindow, aCompactOfflineAlso)``

Compact all folders in the account corresponding to this folder/
Optionally compact their offline stores as well (imap/news)

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow
* in boolean aCompactOfflineAlso

compactAllOfflineStores
-----------------------

``void compactAllOfflineStores(aListener, aMsgWindow, aOfflineFolderArray)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow
* in Array<:doc:`nsIMsgFolder`> aOfflineFolderArray

emptyTrash
----------

``void emptyTrash(aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener

rename
------

``void rename(name, msgWindow)``

change the name of the folder

Parameters
^^^^^^^^^^

* in AString name
* in :doc:`nsIMsgWindow` msgWindow

renameSubFolders
----------------

``void renameSubFolders(msgWindow, oldFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgFolder` oldFolder

generateUniqueSubfolderName
---------------------------

``AString generateUniqueSubfolderName(prefix, otherFolder)``

Parameters
^^^^^^^^^^

* in AString prefix
* in :doc:`nsIMsgFolder` otherFolder

Return value
^^^^^^^^^^^^

* AString

updateSummaryTotals
-------------------

``void updateSummaryTotals(force)``

Parameters
^^^^^^^^^^

* in boolean force

summaryChanged
--------------

``void summaryChanged()``

getNumUnread
------------

``long getNumUnread(deep)``

get the total number of unread messages in this folder,
or in all subfolders

Parameters
^^^^^^^^^^

* in boolean deep

Return value
^^^^^^^^^^^^

* long

getTotalMessages
----------------

``long getTotalMessages(deep)``

get the total number of messages in this folder,
or in all subfolders

Parameters
^^^^^^^^^^

* in boolean deep

Return value
^^^^^^^^^^^^

* long

changeNumPendingUnread
----------------------

``void changeNumPendingUnread(delta)``

Parameters
^^^^^^^^^^

* in long delta

changeNumPendingTotalMessages
-----------------------------

``void changeNumPendingTotalMessages(delta)``

Parameters
^^^^^^^^^^

* in long delta

clearNewMessages
----------------

``void clearNewMessages()``

clear new status flag of all of the new messages

setFlag
-------

``void setFlag(flag)``

Sets a flag on the folder. The known flags are defined in
nsMsgFolderFlags.h.

Parameters
^^^^^^^^^^

* in unsigned long flag

clearFlag
---------

``void clearFlag(flag)``

Clears a flag on the folder. The known flags are defined in
nsMsgFolderFlags.h.

Parameters
^^^^^^^^^^

* in unsigned long flag

getFlag
-------

``boolean getFlag(flag)``

Determines if a flag is set on the folder or not. The known flags are
defined in nsMsgFolderFlags.h.

Parameters
^^^^^^^^^^

* in unsigned long flag

Return value
^^^^^^^^^^^^

* boolean

  True if the flag exists.

toggleFlag
----------

``void toggleFlag(flag)``

Toggles a flag on the folder. The known flags are defined in
nsMsgFolderFlags.h.

Parameters
^^^^^^^^^^

* in unsigned long flag

onFlagChange
------------

``void onFlagChange(flag)``

Called to notify the database and/or listeners of a change of flag. The
known flags are defined in nsMsgFolderFlags.h
@note        This doesn't need to be called for normal flag changes via
the *Flag functions on this interface.

Parameters
^^^^^^^^^^

* in unsigned long flag

getFolderWithFlags
------------------

``nsIMsgFolder getFolderWithFlags(flags)``

Gets the first folder that has the specified flags set.

Parameters
^^^^^^^^^^

* in unsigned long flags

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  The folder or the first available child folder that has
  the specified flags set, or null if there are none.

getFoldersWithFlags
-------------------

``Array<nsIMsgFolder> getFoldersWithFlags(flags)``

Gets the folders that have the specified flag set.

Parameters
^^^^^^^^^^

* in unsigned long flags

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgFolder`>

  An array of folders that have the specified flags set.
  The array may have zero elements.

isSpecialFolder
---------------

``boolean isSpecialFolder(flags, checkAncestors)``

Check if this folder (or one of its ancestors) is special.

Parameters
^^^^^^^^^^

* in unsigned long flags
* in boolean checkAncestors

Return value
^^^^^^^^^^^^

* boolean

getUriForMsg
------------

``AUTF8String getUriForMsg(msgHdr)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr

Return value
^^^^^^^^^^^^

* AUTF8String

deleteMessages
--------------

``void deleteMessages(messages, msgWindow, deleteStorage, isMove, listener, allowUndo)``

Deletes the messages from the folder.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages
* in :doc:`nsIMsgWindow` msgWindow
* in boolean deleteStorage
* in boolean isMove
* in :doc:`nsIMsgCopyServiceListener` listener
* in boolean allowUndo

copyMessages
------------

``void copyMessages(srcFolder, messages, isMove, msgWindow, listener, isFolder, allowUndo)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in Array<:doc:`nsIMsgDBHdr`> messages
* in boolean isMove
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgCopyServiceListener` listener
* in boolean isFolder
* in boolean allowUndo

copyFolder
----------

``void copyFolder(srcFolder, isMoveFolder, msgWindow, listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in boolean isMoveFolder
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgCopyServiceListener` listener

copyFileMessage
---------------

``void copyFileMessage(file, msgToReplace, isDraft, newMsgFlags, aKeywords, msgWindow, listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` file
* in :doc:`nsIMsgDBHdr` msgToReplace
* in boolean isDraft
* in unsigned long newMsgFlags
* in ACString aKeywords
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgCopyServiceListener` listener

acquireSemaphore
----------------

``void acquireSemaphore(semHolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` semHolder

releaseSemaphore
----------------

``void releaseSemaphore(semHolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` semHolder

testSemaphore
-------------

``boolean testSemaphore(semHolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` semHolder

Return value
^^^^^^^^^^^^

* boolean

getNewMessages
--------------

``void getNewMessages(aWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow
* in :doc:`nsIUrlListener` aListener

writeToFolderCache
------------------

``void writeToFolderCache(folderCache, deep)``

Write out summary data for this folder to the given folder cache.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolderCache` folderCache
* in boolean deep

getNumNewMessages
-----------------

``long getNumNewMessages(deep)``

The number of new messages since this folder's last biff.

Parameters
^^^^^^^^^^

* in boolean deep

Return value
^^^^^^^^^^^^

* long

setNumNewMessages
-----------------

``void setNumNewMessages(numNewMessages)``

Parameters
^^^^^^^^^^

* in long numNewMessages

generateMessageURI
------------------

``AUTF8String generateMessageURI(msgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* AUTF8String

addMessageDispositionState
--------------------------

``void addMessageDispositionState(aMessage, aDispositionFlag)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMessage
* in nsMsgDispositionState aDispositionFlag

markMessagesRead
----------------

``void markMessagesRead(messages, markRead)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages
* in boolean markRead

markAllMessagesRead
-------------------

``void markAllMessagesRead(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

markMessagesFlagged
-------------------

``void markMessagesFlagged(messages, markFlagged)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages
* in boolean markFlagged

markThreadRead
--------------

``void markThreadRead(thread)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgThread` thread

setLabelForMessages
-------------------

``void setLabelForMessages(messages, label)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages
* in nsMsgLabelValue label

getBackupMsgDatabase
--------------------

``nsIMsgDatabase getBackupMsgDatabase()``

Get the backup message database, used in reparsing. This database must
be created first using closeAndBackupFolderDB()

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

  backup message database

removeBackupMsgDatabase
-----------------------

``void removeBackupMsgDatabase()``

Remove the backup message database file

openBackupMsgDatabase
---------------------

``void openBackupMsgDatabase()``

Open the backup message database file

getDBFolderInfoAndDB
--------------------

``nsIMsgDatabase getDBFolderInfoAndDB(folderInfo)``

Parameters
^^^^^^^^^^

* out :doc:`nsIDBFolderInfo` folderInfo

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

GetMessageHeader
----------------

``nsIMsgDBHdr GetMessageHeader(msgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

shouldStoreMsgOffline
---------------------

``boolean shouldStoreMsgOffline(msgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* boolean

hasMsgOffline
-------------

``boolean hasMsgOffline(msgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* boolean

getOfflineFileStream
--------------------

``nsIInputStream getOfflineFileStream(aMsgKey, aOffset, aSize)``

Get an input stream to read the offline contents of an imap or news
message.

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey
* out long long aOffset
* out unsigned long aSize

Return value
^^^^^^^^^^^^

* :doc:`nsIInputStream`

  input stream to read the message from.

getSlicedOfflineFileStream
--------------------------

``nsIInputStream getSlicedOfflineFileStream(aMsgKey)``

Similar to getOfflineFileStream, but returns a sliced stream directly.

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey

Return value
^^^^^^^^^^^^

* :doc:`nsIInputStream`

  sliced input stream to read the message from.

getOfflineStoreOutputStream
---------------------------

``nsIOutputStream getOfflineStoreOutputStream(aHdr)``

Get an offline store output stream for the passed message header.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdr

Return value
^^^^^^^^^^^^

* :doc:`nsIOutputStream`

  An output stream to write to.

getMsgInputStream
-----------------

``nsIInputStream getMsgInputStream(aHdr, aReusable)``

Get an input stream for the passed message header. The stream will
be positioned at the start of the message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdr
* out boolean aReusable

Return value
^^^^^^^^^^^^

* :doc:`nsIInputStream`

  an input stream to read the message from

downloadMessagesForOffline
--------------------------

``void downloadMessagesForOffline(messages, window)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages
* in :doc:`nsIMsgWindow` window

getChildWithURI
---------------

``nsIMsgFolder getChildWithURI(uri, deep, caseInsensitive)``

Parameters
^^^^^^^^^^

* in AUTF8String uri
* in boolean deep
* in boolean caseInsensitive

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

downloadAllForOffline
---------------------

``void downloadAllForOffline(listener, window)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` listener
* in :doc:`nsIMsgWindow` window

enableNotifications
-------------------

``void enableNotifications(notificationType, enable)``

Parameters
^^^^^^^^^^

* in long notificationType
* in boolean enable

isCommandEnabled
----------------

``boolean isCommandEnabled(command)``

Parameters
^^^^^^^^^^

* in ACString command

Return value
^^^^^^^^^^^^

* boolean

matchOrChangeFilterDestination
------------------------------

``boolean matchOrChangeFilterDestination(folder, caseInsensitive)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
* in boolean caseInsensitive

Return value
^^^^^^^^^^^^

* boolean

confirmFolderDeletionForFilter
------------------------------

``boolean confirmFolderDeletionForFilter(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* boolean

alertFilterChanged
------------------

``void alertFilterChanged(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

throwAlertMsg
-------------

``void throwAlertMsg(msgName, msgWindow)``

Parameters
^^^^^^^^^^

* in string msgName
* in :doc:`nsIMsgWindow` msgWindow

getStringWithFolderNameFromBundle
---------------------------------

``AString getStringWithFolderNameFromBundle(msgName)``

Parameters
^^^^^^^^^^

* in string msgName

Return value
^^^^^^^^^^^^

* AString

notifyCompactCompleted
----------------------

``void notifyCompactCompleted()``

compareSortKeys
---------------

``long compareSortKeys(msgFolder)``

Calculate ordering of this folder against another.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` msgFolder

Return value
^^^^^^^^^^^^

* long

callFilterPlugins
-----------------

``boolean callFilterPlugins(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* boolean

getStringProperty
-----------------

``ACString getStringProperty(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* ACString

setStringProperty
-----------------

``void setStringProperty(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in ACString propertyValue

isAncestorOf
------------

``boolean isAncestorOf(folder)``

Determines if this folder is an ancestor of the supplied folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

Return value
^^^^^^^^^^^^

* boolean

containsChildNamed
------------------

``boolean containsChildNamed(name)``

Looks in immediate children of this folder for the given name.

Parameters
^^^^^^^^^^

* in AString name

Return value
^^^^^^^^^^^^

* boolean

getChildNamed
-------------

``nsIMsgFolder getChildNamed(aName)``

Return the child folder which the specified name.

Parameters
^^^^^^^^^^

* in AString aName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  The child folder

Throws
^^^^^^

* NS_ERROR_FAILURE Thrown if the folder with aName does not exist

findSubFolder
-------------

``nsIMsgFolder findSubFolder(escapedSubFolderName)``

Finds the sub folder with the specified name.
@note                        Even if the folder doesn't currently exist,
a nsIMsgFolder may be returned.

Parameters
^^^^^^^^^^

* in ACString escapedSubFolderName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

AddFolderListener
-----------------

``void AddFolderListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` listener

RemoveFolderListener
--------------------

``void RemoveFolderListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` listener

NotifyPropertyChanged
---------------------

``void NotifyPropertyChanged(property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in ACString property
* in ACString oldValue
* in ACString newValue

NotifyIntPropertyChanged
------------------------

``void NotifyIntPropertyChanged(property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in ACString property
* in long long oldValue
* in long long newValue

NotifyBoolPropertyChanged
-------------------------

``void NotifyBoolPropertyChanged(property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in ACString property
* in boolean oldValue
* in boolean newValue

NotifyPropertyFlagChanged
-------------------------

``void NotifyPropertyFlagChanged(item, property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` item
* in ACString property
* in unsigned long oldValue
* in unsigned long newValue

NotifyUnicharPropertyChanged
----------------------------

``void NotifyUnicharPropertyChanged(property, oldValue, newValue)``

Parameters
^^^^^^^^^^

* in ACString property
* in AString oldValue
* in AString newValue

notifyMessageAdded
------------------

``void notifyMessageAdded(msg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

notifyMessageRemoved
--------------------

``void notifyMessageRemoved(msg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msg

notifyFolderAdded
-----------------

``void notifyFolderAdded(child)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` child

notifyFolderRemoved
-------------------

``void notifyFolderRemoved(child)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` child

NotifyFolderEvent
-----------------

``void NotifyFolderEvent(event)``

Parameters
^^^^^^^^^^

* in ACString event

Shutdown
--------

``void Shutdown(shutdownChildren)``

Parameters
^^^^^^^^^^

* in boolean shutdownChildren

copyDataToOutputStreamForAppend
-------------------------------

``void copyDataToOutputStreamForAppend(aIStream, aLength, outputStream)``

Parameters
^^^^^^^^^^

* in :doc:`nsIInputStream` aIStream
* in long aLength
* in :doc:`nsIOutputStream` outputStream

copyDataDone
------------

``void copyDataDone()``

setJunkScoreForMessages
-----------------------

``void setJunkScoreForMessages(aMessages, aJunkScore)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMessages
* in ACString aJunkScore

applyRetentionSettings
----------------------

``void applyRetentionSettings()``

fetchMsgPreviewText
-------------------

``boolean fetchMsgPreviewText(aKeysToFetch, aUrlListener)``

Get the beginning of the message bodies for the passed in keys and store
them in the msg hdr property "preview". This is intended for
new mail alerts, title tips on folders with new messages, and perhaps
titletips/message preview in the thread pane.

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> aKeysToFetch
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* boolean

  aAsyncResults if true, we ran a url to fetch one or more of msg bodies

addKeywordsToMessages
---------------------

``void addKeywordsToMessages(aMessages, aKeywords)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMessages
* in ACString aKeywords

removeKeywordsFromMessages
--------------------------

``void removeKeywordsFromMessages(aMessages, aKeywords)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMessages
* in ACString aKeywords

getMsgTextFromStream
--------------------

``AUTF8String getMsgTextFromStream(aStream, aCharset, aBytesToRead, aMaxOutputLen, aCompressQuotes, aStripHTMLTags, aContentType)``

Extract the message text from aStream.

Parameters
^^^^^^^^^^

* in :doc:`nsIInputStream` aStream
* in ACString aCharset
* in unsigned long aBytesToRead
* in unsigned long aMaxOutputLen
* in boolean aCompressQuotes
* in boolean aStripHTMLTags
* out ACString aContentType

Return value
^^^^^^^^^^^^

* AUTF8String

convertMsgSnippetToPlainText
----------------------------

``AString convertMsgSnippetToPlainText(aMessageText)``

Parameters
^^^^^^^^^^

* in AString aMessageText

Return value
^^^^^^^^^^^^

* AString

getProcessingFlags
------------------

``unsigned long getProcessingFlags(msgKey)``

@{
Processing flags, used to manage message processing.

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* unsigned long

  processing flags

orProcessingFlags
-----------------

``void orProcessingFlags(msgKey, mask)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey
* in unsigned long mask

andProcessingFlags
------------------

``void andProcessingFlags(msgKey, mask)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey
* in unsigned long mask

getInheritedStringProperty
--------------------------

``ACString getInheritedStringProperty(propertyName)``

@} */
Gets an inherited string property from the folder.
If the forcePropertyEmpty boolean is set (see below), return an
empty string.
If the specified folder has a non-empty value for the property,
return that value. Otherwise, return getInheritedStringProperty
for the folder's parent.
If a folder is the root folder for a server, then instead of
checking the folder property, check the property of the same name
for the server using nsIMsgIncomingServer.getCharValue(...)
Note nsIMsgIncomingServer.getCharValue for a server inherits from
the preference mail.server.default.(propertyName) as a global value
(ex: if propertyName = "IAmAGlobal" and no folder nor server properties
are set, then the inherited property will return the preference value
mail.server.default.IAmAGlobal)
If the propertyName is undefined, returns an empty, void string.

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* ACString

setForcePropertyEmpty
---------------------

``void setForcePropertyEmpty(propertyName, aForcePropertyEmpty)``

Set a boolean to force an inherited propertyName to return empty instead
of inheriting from a parent folder, server, or the global

Parameters
^^^^^^^^^^

* in string propertyName
* in boolean aForcePropertyEmpty

getForcePropertyEmpty
---------------------

``boolean getForcePropertyEmpty(propertyName)``

Get a boolean to force an inherited propertyName to return empty instead
of inheriting from a parent folder, server, or the global

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* boolean

  true if an empty inherited property should be returned
