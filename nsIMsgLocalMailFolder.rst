=====================
nsIMsgLocalMailFolder
=====================

`mailnews/local/public/nsIMsgLocalMailFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIMsgLocalMailFolder.idl>`_


Properties
==========

checkForNewMessagesAfterParsing
-------------------------------

``attribute boolean checkForNewMessagesAfterParsing``

Methods
=======

setFlagsOnDefaultMailboxes
--------------------------

``void setFlagsOnDefaultMailboxes(flags)``

Set the default flags on the subfolders of this folder, such as
Drafts, Templates, etc.

Parameters
^^^^^^^^^^

* in unsigned long flags

getDatabaseWOReparse
--------------------

``nsIMsgDatabase getDatabaseWOReparse()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

getDatabaseWithReparse
----------------------

``nsIMsgDatabase getDatabaseWithReparse(aReparseUrlListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aReparseUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDatabase`

parseFolder
-----------

``void parseFolder(aMsgWindow, listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` listener

copyFolderLocal
---------------

``void copyFolderLocal(srcFolder, isMove, msgWindow, listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in boolean isMove
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgCopyServiceListener` listener

copyAllSubFolders
-----------------

``void copyAllSubFolders(srcFolder, msgWindow, listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgCopyServiceListener` listener

onCopyCompleted
---------------

``void onCopyCompleted(aSrcSupport, aMoveCopySucceeded)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` aSrcSupport
* in boolean aMoveCopySucceeded

markMsgsOnPop3Server
--------------------

``void markMsgsOnPop3Server(aMessages, aMark)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMessages
* in int32_t aMark

refreshSizeOnDisk
-----------------

``void refreshSizeOnDisk()``

File size on disk has possibly changed - update and notify.

createLocalSubfolder
--------------------

``nsIMsgFolder createLocalSubfolder(aFolderName)``

Creates a subfolder to the current folder with the passed in folder name.

Parameters
^^^^^^^^^^

* in AString aFolderName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

  newly created folder.

addMessage
----------

``nsIMsgDBHdr addMessage(aMessage)``

Adds a message to the end of the folder, parsing it as it goes, and
applying filters, if applicable.

Parameters
^^^^^^^^^^

* in string aMessage

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

  the nsIMsgDBHdr of the added message

addMessageBatch
---------------

``Array<nsIMsgDBHdr> addMessageBatch(aMessages)``

Add one or more messages to the end of the folder in a single batch. Each
batch requires an fsync() on the mailbox file so it is a good idea to
try and minimize the number of calls you make to this method or addMessage.

Filters are applied, if applicable.

Parameters
^^^^^^^^^^

* in Array<ACString> aMessages

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgDBHdr`>

  an array of nsIMsgDBHdr of the added messages

deleteDownloadMsg
-----------------

``void deleteDownloadMsg(aMsgHdr, aDoSelect)``

Functions for updating the UI while running downloadMessagesForOffline:
delete the old message before adding its newly downloaded body, and
select the new message after it has replaced the old one

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* out boolean aDoSelect

selectDownloadMsg
-----------------

``void selectDownloadMsg()``

notifyDelete
------------

``void notifyDelete()``

getFolderScanState
------------------

``void getFolderScanState(aState)``

Functions for grubbing through a folder to find the Uidl for a
given msgDBHdr.

Parameters
^^^^^^^^^^

* in nsLocalFolderScanState aState

getUidlFromFolder
-----------------

``void getUidlFromFolder(aState, aMsgHdr)``

Parameters
^^^^^^^^^^

* in nsLocalFolderScanState aState
* in :doc:`nsIMsgDBHdr` aMsgHdr

warnIfLocalFileTooBig
---------------------

``boolean warnIfLocalFileTooBig(aWindow, aSpaceRequested)``

Shows warning if there is not enough space in the message store
for a message of the given size.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow
* in long long aSpaceRequested

Return value
^^^^^^^^^^^^

* boolean

updateNewMsgHdr
---------------

``void updateNewMsgHdr(aOldHdr, aNewHdr)``

Update properties on a new header from an old header, for cases where
a partial message will be replaced with a full message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aOldHdr

  message header used as properties source
* in :doc:`nsIMsgDBHdr` aNewHdr

  message header used as properties destination
