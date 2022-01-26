=====================
nsIMsgFolderCompactor
=====================

`mailnews/base/public/nsIMsgFolderCompactor.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolderCompactor.idl>`_

Use this for any object that wants to handle compacting folders.
Currently, the folders themselves create this object.

Methods
=======

compact
-------

``void compact(aFolder, aOfflineStore, aListener, aMsgWindow)``

Compact the given folder, or its offline store (imap/news only)

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in boolean aOfflineStore
* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

compactFolders
--------------

``void compactFolders(aArrayOfFoldersToCompact, aOfflineFolderArray, aListener, aMsgWindow)``

Compact the passed in array of folders, and the passed in offline stores.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgFolder`> aArrayOfFoldersToCompact
* in Array<:doc:`nsIMsgFolder`> aOfflineFolderArray
* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow
