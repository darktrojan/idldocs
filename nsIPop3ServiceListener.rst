======================
nsIPop3ServiceListener
======================

`mailnews/local/public/nsIPop3Service.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIPop3Service.idl>`_


Methods
=======

onDownloadStarted
-----------------

``void onDownloadStarted(aFolder)``

Notification that a pop3 download has started.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

onDownloadProgress
------------------

``void onDownloadProgress(aFolder, aNumDownloaded, aTotalToDownload)``

Notification about download progress.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumDownloaded
* in unsigned long aTotalToDownload

onDownloadCompleted
-------------------

``void onDownloadCompleted(aFolder, aNumberOfMessages)``

Notification that a download has completed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumberOfMessages
