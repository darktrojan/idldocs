================
nsIAutoSyncState
================

`mailnews/imap/public/nsIAutoSyncState.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIAutoSyncState.idl>`_


Constants
=========

stCompletedIdle
---------------

**Type**: ``long``

**Value**: ``0``

Auto-Sync states.

***WARNING***: If you change these, be sure to update stateStrings in
nsAutoSyncState.cpp. If you do not, out-of-bounds memory accesses may
happen.
sync'd and no pending messages */

stStatusIssued
--------------

**Type**: ``long``

**Value**: ``1``

STATUS issued. Will check to see if  any counts changed since last STATUS */

stUpdateNeeded
--------------

**Type**: ``long``

**Value**: ``2``

Status found new messages. Update should be issued next. Status most
likely was issued by non-autosync code (e.g., check other folders for
new messages).

stUpdateIssued
--------------

**Type**: ``long``

**Value**: ``3``

Update issued. Will figure out if there are any bodies to download */

stDownloadInProgress
--------------------

**Type**: ``long``

**Value**: ``4``

Message body download in progress */

stReadyToDownload
-----------------

**Type**: ``long``

**Value**: ``5``

ready to download the next group of messages */

Properties
==========

lastSyncTime
------------

``readonly attribute PRTime lastSyncTime``

Last time the existing headers are completely processed.

lastUpdateTime
--------------

``attribute PRTime lastUpdateTime``

Last time the owner folder is updated.

state
-----

``attribute long state``

Download operation state.

pendingMessageCount
-------------------

``readonly attribute long pendingMessageCount``

Number of messages waiting to be downloaded.

totalMessageCount
-----------------

``readonly attribute long totalMessageCount``

Total number of messages in the download queue.

ownerFolder
-----------

``readonly attribute nsIMsgFolder ownerFolder``

The folder this auto-sync object is related to.

Methods
=======

rollback
--------

``void rollback()``

Puts the download queue offset to its previous position.

resetDownloadQ
--------------

``void resetDownloadQ()``

Clears the download queue. Resets the offsets.

tryCurrentGroupAgain
--------------------

``void tryCurrentGroupAgain(aRetryCount)``

Rollbacks the offset to the previous position and
changes the state to ready-to-download.

Parameters
^^^^^^^^^^

* in unsigned long aRetryCount

resetRetryCounter
-----------------

``void resetRetryCounter()``

Resets the retry counter.

isSibling
---------

``boolean isSibling(aAnotherStateObj)``

Tests whether the given folder has the same imap server.

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncState` aAnotherStateObj

Return value
^^^^^^^^^^^^

* boolean

updateFolder
------------

``void updateFolder()``

Update the folder to find new message headers to download

downloadMessagesForOffline
--------------------------

``void downloadMessagesForOffline(aMessageList)``

Downloads the bodies of the given messages from the server.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMessageList

getNextGroupOfMessages
----------------------

``Array<nsIMsgDBHdr> getNextGroupOfMessages(aSuggestedGroupSizeLimit, aActualGroupSize)``

Returns an array containing the nsIMsgDBHdrs of the messages that will
be downloaded next.

Parameters
^^^^^^^^^^

* in unsigned long aSuggestedGroupSizeLimit
* out unsigned long aActualGroupSize

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgDBHdr`>

processExistingHeaders
----------------------

``unsigned long processExistingHeaders(aNumberOfHeadersToProcess)``

Iterates through the existing headers of the folder to find
the messages not downloaded yet.

Parameters
^^^^^^^^^^

* in unsigned long aNumberOfHeadersToProcess

Return value
^^^^^^^^^^^^

* unsigned long

  the number of headers left to process
