==================
nsIAutoSyncManager
==================

`mailnews/imap/public/nsIAutoSyncManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIAutoSyncManager.idl>`_


Constants
=========

dmParallel
----------

**Type**: ``long``

**Value**: ``0``

Download models

dmChained
---------

**Type**: ``long``

**Value**: ``1``


Properties
==========

groupSize
---------

``attribute unsigned long groupSize``

Suggested minimum grouping size in bytes for message downloads.
Setting this attribute to 0 resets its value to the
hardcoded default.

msgStrategy
-----------

``attribute nsIAutoSyncMsgStrategy msgStrategy``

Active strategy function to prioritize
messages in the download queue

folderStrategy
--------------

``attribute nsIAutoSyncFolderStrategy folderStrategy``

Active strategy function to prioritize
folders in the download queue

discoveryQLength
----------------

``readonly attribute unsigned long discoveryQLength``

Number of elements in the discovery queue.
@see nsAutoSyncManager.h for details

updateQLength
-------------

``readonly attribute unsigned long updateQLength``

Number of elements in the update queue.
@see nsAutoSyncManager.h for details

downloadQLength
---------------

``readonly attribute unsigned long downloadQLength``

Number of elements in the download queue (a.k.a priority queue).
@see nsAutoSyncManager.h for details

downloadModel
-------------

``attribute long downloadModel``

Active download model; Chained (serial), or Parallel

Methods
=======

addListener
-----------

``void addListener(aListener)``

Adds a listener to notify about auto-sync events

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncMgrListener` aListener

removeListener
--------------

``void removeListener(aListener)``

Removes the listener from notification list

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncMgrListener` aListener

doesMsgFitDownloadCriteria
--------------------------

``boolean doesMsgFitDownloadCriteria(aMsgHdr)``

Tests the given message to make sure that whether
it fits the download criteria or not

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr

Return value
^^^^^^^^^^^^

* boolean

onDownloadQChanged
------------------

``void onDownloadQChanged(aAutoSyncStateObj)``

Called by the nsAutoSyncState object when the download
queue is changed. Given interface is already addref'd.

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncState` aAutoSyncStateObj

onDownloadStarted
-----------------

``void onDownloadStarted(aAutoSyncStateObj, aStartCode)``

Called by the nsAutoSyncState object when the download
is started. Given interface is already addref'd.

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncState` aAutoSyncStateObj
* in nsresult aStartCode

onDownloadCompleted
-------------------

``void onDownloadCompleted(aAutoSyncStateObj, aExitCode)``

Called by the nsAutoSyncState object when the download
completed. Given interface is already addref'd.

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncState` aAutoSyncStateObj
* in nsresult aExitCode

onFolderHasPendingMsgs
----------------------

``void onFolderHasPendingMsgs(aAutoSyncState)``

The imap folder corresponding to aAutoSyncState has had a message
added to it. Autosync may want to add this folder to the update q.

Parameters
^^^^^^^^^^

* in :doc:`nsIAutoSyncState` aAutoSyncState

pause
-----

``void pause()``

resume
------

``void resume()``
