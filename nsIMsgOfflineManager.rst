====================
nsIMsgOfflineManager
====================

`mailnews/base/public/nsIMsgOfflineManager.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgOfflineManager.idl>`_


Properties
==========

window
------

``attribute nsIMsgWindow window``

inProgress
----------

``attribute boolean inProgress``

Methods
=======

goOnline
--------

``void goOnline(sendUnsentMessages, playbackOfflineImapOperations, aMsgWindow)``

Parameters
^^^^^^^^^^

* in boolean sendUnsentMessages
* in boolean playbackOfflineImapOperations
* in :doc:`nsIMsgWindow` aMsgWindow

synchronizeForOffline
---------------------

``void synchronizeForOffline(downloadNews, downloadMail, sendUnsentMessages, goOfflineWhenDone, aMsgWindow)``

Parameters
^^^^^^^^^^

* in boolean downloadNews
* in boolean downloadMail
* in boolean sendUnsentMessages
* in boolean goOfflineWhenDone
* in :doc:`nsIMsgWindow` aMsgWindow
