===============================
nsIMsgFolderNotificationService
===============================

`mailnews/base/public/nsIMsgFolderNotificationService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolderNotificationService.idl>`_

nsIMsgFolderNotificationService provides a central point for sending out
notifications related to folders.
nsIMsgFolderListeners are registered with the service along with flags to
indicate which kinds of notifications are of interest.

Constants
=========

msgAdded
--------

**Type**: ``msgFolderListenerFlag``

**Value**: ``1``

@name Notification flags
These flags determine which notifications will be sent.
@{

msgsDeleted
-----------

**Type**: ``msgFolderListenerFlag``

**Value**: ``2``


msgsMoveCopyCompleted
---------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``4``


msgsClassified
--------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``8``


msgsJunkStatusChanged
---------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``16``


msgUnincorporatedMoved
----------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``32``


folderAdded
-----------

**Type**: ``msgFolderListenerFlag``

**Value**: ``32768``


folderDeleted
-------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``4096``


folderMoveCopyCompleted
-----------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``8192``


folderRenamed
-------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``16384``


folderCompactStart
------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``65536``


folderCompactFinish
-------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``131072``


folderReindexTriggered
----------------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``262144``


msgKeyChanged
-------------

**Type**: ``msgFolderListenerFlag``

**Value**: ``33554432``


Properties
==========

hasListeners
------------

``readonly attribute boolean hasListeners``

@} */

Methods
=======

addListener
-----------

``void addListener(aListener, flags)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolderListener` aListener
* in msgFolderListenerFlag flags

removeListener
--------------

``void removeListener(aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolderListener` aListener

notifyMsgAdded
--------------

``void notifyMsgAdded(aMsg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsg

notifyMsgsClassified
--------------------

``void notifyMsgsClassified(aMsgs, aJunkProcessed, aTraitProcessed)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMsgs
* in boolean aJunkProcessed
* in boolean aTraitProcessed

notifyMsgsJunkStatusChanged
---------------------------

``void notifyMsgsJunkStatusChanged(messages)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages

notifyMsgsDeleted
-----------------

``void notifyMsgsDeleted(aMsgs)``

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMsgs

notifyMsgsMoveCopyCompleted
---------------------------

``void notifyMsgsMoveCopyCompleted(aMove, aSrcMsgs, aDestFolder, aDestMsgs)``

Parameters
^^^^^^^^^^

* in boolean aMove
* in Array<:doc:`nsIMsgDBHdr`> aSrcMsgs
* in :doc:`nsIMsgFolder` aDestFolder
* in Array<:doc:`nsIMsgDBHdr`> aDestMsgs

notifyMsgKeyChanged
-------------------

``void notifyMsgKeyChanged(aOldKey, aNewHdr)``

Notify listeners that the msg key for a header has changed. Currently,
this is used when we create a header for an offline imap move result,
without knowing what the ultimate UID will be. When we download the
headers for the new message, we replace the old "pseudo" header with
a new header that has the correct UID/message key, by cloning the pseudo
header, which maintains all the existing header attributes.

Parameters
^^^^^^^^^^

* in nsMsgKey aOldKey
* in :doc:`nsIMsgDBHdr` aNewHdr

notifyMsgUnincorporatedMoved
----------------------------

``void notifyMsgUnincorporatedMoved(srcFolder, msg)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in :doc:`nsIMsgDBHdr` msg

notifyFolderAdded
-----------------

``void notifyFolderAdded(aFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

notifyFolderDeleted
-------------------

``void notifyFolderDeleted(aFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

notifyFolderMoveCopyCompleted
-----------------------------

``void notifyFolderMoveCopyCompleted(aMove, aSrcFolder, aDestFolder)``

Parameters
^^^^^^^^^^

* in boolean aMove
* in :doc:`nsIMsgFolder` aSrcFolder
* in :doc:`nsIMsgFolder` aDestFolder

notifyFolderRenamed
-------------------

``void notifyFolderRenamed(aOrigFolder, aNewFolder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aOrigFolder
* in :doc:`nsIMsgFolder` aNewFolder

notifyFolderCompactStart
------------------------

``void notifyFolderCompactStart(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

notifyFolderCompactFinish
-------------------------

``void notifyFolderCompactFinish(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

notifyFolderReindexTriggered
----------------------------

``void notifyFolderReindexTriggered(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder
