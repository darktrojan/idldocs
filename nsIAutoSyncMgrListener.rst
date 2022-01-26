======================
nsIAutoSyncMgrListener
======================

`mailnews/imap/public/nsIAutoSyncManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIAutoSyncManager.idl>`_


Constants
=========

PriorityQueue
-------------

**Type**: ``long``

**Value**: ``1``

Queue types

UpdateQueue
-----------

**Type**: ``long``

**Value**: ``2``


DiscoveryQueue
--------------

**Type**: ``long``

**Value**: ``3``


Methods
=======

onFolderAddedIntoQ
------------------

``void onFolderAddedIntoQ(aQType, aFolder)``

It is called on the listener when a new folder is added into
the queue

Parameters
^^^^^^^^^^

* in long aQType
* in :doc:`nsIMsgFolder` aFolder

onFolderRemovedFromQ
--------------------

``void onFolderRemovedFromQ(aQType, aFolder)``

It is called on the listener when a folder is removed from
the queue

Parameters
^^^^^^^^^^

* in long aQType
* in :doc:`nsIMsgFolder` aFolder

onDownloadStarted
-----------------

``void onDownloadStarted(aFolder, aNumberOfMessages, aTotalPending)``

It is called on the listener when a message download is successfully started

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumberOfMessages
* in unsigned long aTotalPending

onDownloadCompleted
-------------------

``void onDownloadCompleted(aFolder)``

It is called on the listener when a message download on the given folder
is completed

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

onDownloadError
---------------

``void onDownloadError(aFolder)``

It is called on the listener when an error occurs during the message download

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

onStateChanged
--------------

``void onStateChanged(aRunning)``

Parameters
^^^^^^^^^^

* in boolean aRunning

onDiscoveryQProcessed
---------------------

``void onDiscoveryQProcessed(aFolder, aNumberOfHdrsProcessed, aLeftToProcess)``

It is called on the listener after the auto-sync manager starts to process
existing headers of the given folder to find missing message bodies
(mostly for debugging purposes)

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumberOfHdrsProcessed
* in unsigned long aLeftToProcess

onAutoSyncInitiated
-------------------

``void onAutoSyncInitiated(aFolder)``

It is called on the listener after the auto-sync manager updates the given folder
(mostly for debugging purposes)

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
