====================
nsIMsgPluggableStore
====================

`mailnews/base/public/nsIMsgPluggableStore.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgPluggableStore.idl>`_

Pluggable message store interface. Each incoming server can have a different
message store.
All methods are synchronous unless otherwise specified.

Properties
==========

supportsCompaction
------------------

``readonly attribute boolean supportsCompaction``

Does this store require compaction? For example, maildir doesn't require
compaction at all. Berkeley mailbox does. A sqlite store probably doesn't.
This is a static property of the store. It doesn't mean that any particular
folder has space that can be reclaimed via compaction. Right now, the core
code keeps track of the size of messages deleted, which it can use in
conjunction with this store attribute.

storeType
---------

``readonly attribute ACString storeType``

Identifies a specific type of store. Please use this only for legacy
bug fixes, and not as a method to change behavior!

Typical values: "mbox", "maildir"

Methods
=======

discoverSubFolders
------------------

``void discoverSubFolders(aParentFolder, aDeep)``

Examines the store and adds subfolders for the existing folders in the
profile directory. aParentFolder->AddSubfolder is the normal way
to register the subfolders. This method is expected to be synchronous.
This shouldn't be confused with server folder discovery, which is allowed
to be asynchronous.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aParentFolder
* in boolean aDeep

createFolder
------------

``nsIMsgFolder createFolder(aParent, aFolderName)``

Creates storage for a new, empty folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aParent
* in AString aFolderName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  newly created folder.

Throws
^^^^^^

* NS_MSG_FOLDER_EXISTS If the child exists.
* NS_MSG_CANT_CREATE_FOLDER for other errors.

deleteFolder
------------

``void deleteFolder(aFolder)``

Delete storage for a folder and its subfolders, if any.
This is a real delete, not a move to the trash folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

renameFolder
------------

``nsIMsgFolder renameFolder(aFolder, aNewName)``

Rename storage for an existing folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in AString aNewName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  the renamed folder object

hasSpaceAvailable
-----------------

``boolean hasSpaceAvailable(aFolder, aSpaceRequested)``

Tells if the store has the requested amount of space available in the
specified folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in long long aSpaceRequested

Return value
^^^^^^^^^^^^

* boolean

copyFolder
----------

``void copyFolder(aSrcFolder, aDstFolder, aIsMoveFolder, aMsgWindow, aListener, aNewName)``

Move/Copy a folder to a new parent folder. This method is asynchronous.
The store needs to use the aListener to notify the core code of the
completion of the operation. And it must send the appropriate
nsIMsgFolderNotificationService notifications.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aSrcFolder
* in :doc:`nsIMsgFolder` aDstFolder
* in boolean aIsMoveFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgCopyServiceListener` aListener
* in AString aNewName

getNewMsgOutputStream
---------------------

``nsIOutputStream getNewMsgOutputStream(aFolder, aNewHdr, aReusable)``

Get an output stream for a message in a folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* inout :doc:`nsIMsgDBHdr` aNewHdr
* out boolean aReusable

Return value
^^^^^^^^^^^^

* :doc:`nsIOutputStream`

  The output stream to write to. The output stream will be positioned
  for writing (e.g., for berkeley mailbox, it will be at the end).

discardNewMessage
-----------------

``void discardNewMessage(aOutputStream, aNewHdr)``

Called when the current message is discarded, e.g., it is moved
to an other folder as a filter action, or is deleted because it's
a duplicate. This gives the berkeley mailbox store a chance to simply
truncate the Inbox w/o leaving a deleted message in the store.

Parameters
^^^^^^^^^^

* in :doc:`nsIOutputStream` aOutputStream
* in :doc:`nsIMsgDBHdr` aNewHdr

finishNewMessage
----------------

``void finishNewMessage(aOutputStream, aNewHdr)``

Must be called by code that calls getNewMsgOutputStream to finish
the process of storing a new message, if the new msg has not been
discarded. Could/should this be combined with discardNewMessage?

Parameters
^^^^^^^^^^

* in :doc:`nsIOutputStream` aOutputStream
* in :doc:`nsIMsgDBHdr` aNewHdr

moveNewlyDownloadedMessage
--------------------------

``boolean moveNewlyDownloadedMessage(aNewHdr, aDestFolder)``

Called by pop3 message filters when a newly downloaded message is being
moved by an incoming filter. This is called before finishNewMessage, and
it allows the store to optimize that case.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aNewHdr
* in :doc:`nsIMsgFolder` aDestFolder

Return value
^^^^^^^^^^^^

* boolean

  true if successful, false if the store doesn't want to optimize
  this.

Throws
^^^^^^

* If the moved failed. values TBD

getMsgInputStream
-----------------

``nsIInputStream getMsgInputStream(aFolder, aMsgToken, aReusable)``

Get an input stream that we can read the contents of a message from.
If the input stream is reusable, and the caller is going to ask
for input streams for other messages in the folder, then the caller
should not close the stream until it is done with its messages.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in ACString aMsgToken
* out boolean aReusable

Return value
^^^^^^^^^^^^

* :doc:`nsIInputStream`

deleteMessages
--------------

``void deleteMessages(aHdrArray)``

Delete the passed in messages. These message should all be in the
same folder.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aHdrArray

copyMessages
------------

``boolean copyMessages(isMove, aHdrArray, aDstFolder, aDstHdrs, aUndoAction)``

This allows the store to handle a msg move/copy if it wants. This lets
it optimize move/copies within the same store. E.g., for maildir, a
msg move mostly entails moving the file containing the message, and
updating the db.
If the store does the copy, it must return the appropriate undo action,
which can be store dependent. And it must send the appropriate
nsIMsgFolderNotificationService notifications.
If the store does not perform the copy, it returns false and the caller
has to handle the copy itself (by streaming messages).
This function is synchronous.

Parameters
^^^^^^^^^^

* in boolean isMove
* in Array<:doc:`nsIMsgDBHdr`> aHdrArray
* in :doc:`nsIMsgFolder` aDstFolder
* out Array<:doc:`nsIMsgDBHdr`> aDstHdrs
* out :doc:`nsITransaction` aUndoAction

Return value
^^^^^^^^^^^^

* boolean

  true if messages were copied, false if the core code should
  do the copy.

compactFolder
-------------

``void compactFolder(aFolder, aListener, aMsgWindow)``

Remove deleted messages from the store, reclaiming space. Some stores
won't need to do anything here (e.g., maildir), and those stores
should return false for needsCompaction. This operation is asynchronous,
and the passed url listener should be called when the operation is done.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

isSummaryFileValid
------------------

``boolean isSummaryFileValid(aFolder, aDB)``

Is the summary file for the passed folder valid? For Berkeley Mailboxes,
for local mail folders, this checks the timestamp and size of the local
mail folder against values stored in the db. For other stores, this may
be a noop, though other stores could certainly become invalid. For
Berkeley Mailboxes, this is to deal with the case of other apps altering
mailboxes from outside mailnews code, and this is certainly possible
with other stores.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgDatabase` aDB

Return value
^^^^^^^^^^^^

* boolean

  return true if the summary file is valid, false otherwise.

setSummaryFileValid
-------------------

``void setSummaryFileValid(aFolder, aDB, aValid)``

Marks the summary file for aFolder as valid or invalid. This method
may not be required, since it's really used by Berkeley Mailbox code
to fix the timestamp and size for a folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgDatabase` aDB
* in boolean aValid

rebuildIndex
------------

``void rebuildIndex(aFolder, aMsgDB, aMsgWindow, aListener)``

Rebuild the index from information in the store. This involves creating
a new nsIMsgDatabase for the folder, adding the information for all the
messages in the store, and then copying the new msg database over the
existing database. For Berkeley mailbox, we try to maintain meta data
stored in the existing database when possible, and other stores should do
the same. Ideally, I would figure out a way of making that easy. That
might entail reworking the rebuild index process into one where the store
would iterate over the messages, and stream each message through the
message parser, and the common code would handle maintaining the
meta data. But the berkeley mailbox code needs to do some parsing because
it doesn't know how big the message is (i.e., the stream can't simply be
a file stream).
This operation is asynchronous,
and the passed url listener should be called when the operation is done.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgDatabase` aMsgDB
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener

changeFlags
-----------

``void changeFlags(aHdrArray, aFlags, aSet)``

Sets/Clears the passed flags on the passed messages.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aHdrArray
* in unsigned long aFlags
* in boolean aSet

changeKeywords
--------------

``void changeKeywords(aHdrArray, aKeywords, aAdd)``

Sets/Clears the passed keywords on the passed messages.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aHdrArray
* in ACString aKeywords
* in boolean aAdd
