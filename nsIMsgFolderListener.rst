====================
nsIMsgFolderListener
====================

`mailnews/base/public/nsIMsgFolderListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolderListener.idl>`_

nsIMsgFolderListener defines the callbacks which are invoked by
nsIMsgFolderNotificationService.

This is similar to nsIFolderListener, but with slightly different semantics,
especially w.r.t. moving messages and folders.  Some listeners want to know
about moves, instead of getting an itemAdded and itemRemoved notification.
Folder listeners also only tend to get called if a view is open on the folder,
which is not always the case. I don't want to change nsIFolderListener at this
point since there are lots of extensions that rely on it. Eventually,
these two interfaces should be combined somehow.

Methods
=======

msgAdded
--------

``void msgAdded(aMsg)``

Notified immediately after a message is added to a folder. This could be a
new incoming message to a local folder, or a new message in an IMAP folder
when it is opened.

You may want to consider using the msgsClassified notification instead of
this notification if any of the following are true:

- You only want to be notified about messages after junk classification
has occurred (if it is going to occur for a message).  This also goes for
trait classification which is a generic use of the bayesian engine at
the heart of the spam logic.

- You only want to be notified about messages after all filters have been
run.  Although some filters may be run before the msgAdded notification
is generated, filters dependent on junk/trait classification wait until
classification completes.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsg

msgsClassified
--------------

``void msgsClassified(aMsgs, aJunkProcessed, aTraitProcessed)``

Notification that (new to the client) messages have been through junk and
trait classification.  This event will occur for all messages at some point
after their existence is revealed by msgAdded.

Because junk classification does not run if no messages have ever been
marked as junk by the user, it is possible to receive this message without
any classification having actually been performed.  We still generate the
notification in this case so that code is reliably notified about the
existence of the new message headers.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMsgs
* in boolean aJunkProcessed
* in boolean aTraitProcessed

msgsJunkStatusChanged
---------------------

``void msgsJunkStatusChanged(messages)``

msgsJunkStatusChanged indicates that some messages that had already been
reported by msgsClassified have had their junk status changed.  This
event will not fire for the initial automatic classification of
messages; msgsClassified will tell you about those messages.
This is not guaranteed to be a comprehensive source of junk
notification events; right now any time an nsMsgDBView marks things as
junk/non-junk a notification is produced.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> messages

  The affected messages.

msgsDeleted
-----------

``void msgsDeleted(aMsgs)``

Notified after a command to delete a group of messages has been given, but before the
messages have actually been deleted.

@note
This notification will not take place if the messages are being deleted from the folder
as the result of a move to another folder. Instead, the msgsMoveCopyCompleted() notification
takes place.

@note
"Deleting" to a trash folder is actually a move, and is covered by msgsMoveCopyCompleted()

@note
If the user has selected the IMAP delete model (marking messages as deleted, then purging them
later) for an IMAP account, this notification will not take place on the delete. This will only
take place on the purge.

Parameters
^^^^^^^^^^

* in Array<:doc:`nsIMsgDBHdr`> aMsgs

msgsMoveCopyCompleted
---------------------

``void msgsMoveCopyCompleted(aMove, aSrcMsgs, aDestFolder, aDestMsgs)``

Notified after a command to move or copy a group of messages completes. In
case of a move, this is before the messages have been deleted from the
source folder.

@note
If messages are moved from a server which uses the IMAP delete model,
you'll get aMove = false. That's because the messages are not deleted from
the source database, but instead simply marked deleted.

Parameters
^^^^^^^^^^

* in boolean aMove
* in Array<:doc:`nsIMsgDBHdr`> aSrcMsgs
* in :doc:`nsIMsgFolder` aDestFolder
* in Array<:doc:`nsIMsgDBHdr`> aDestMsgs

msgKeyChanged
-------------

``void msgKeyChanged(aOldKey, aNewHdr)``

Notification sent when the msg key for a header may have changed.
This is used when we create a header for an offline imap move result,
without knowing what the ultimate UID will be. When we download the
headers for the new message, we replace the old "pseudo" header with
a new header that has the correct UID/message key. The uid of the new hdr
may turn out to be the same as aOldKey if we've guessed correctly but
the listener can use this notification to know that it can ignore the
msgAdded notification that's coming for aNewHdr. We do NOT send a
msgsDeleted notification for the pseudo header.

Parameters
^^^^^^^^^^

* in nsMsgKey aOldKey
* in :doc:`nsIMsgDBHdr` aNewHdr

msgUnincorporatedMoved
----------------------

``void msgUnincorporatedMoved(srcFolder, msg)``

msgUnincorporatedMoved: A message received via POP was moved by a
"before junk" rule.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder

  Folder the message was moved from.
* in :doc:`nsIMsgDBHdr` msg

  The message.

folderAdded
-----------

``void folderAdded(aFolder)``

Notified after a folder has been added.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

folderDeleted
-------------

``void folderDeleted(aFolder)``

Notified after a folder has been deleted and its corresponding file(s) deleted from disk.

@note
"Deleting" to a trash folder is actually a move, and is covered by folderMoveCopyCompleted()

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

folderMoveCopyCompleted
-----------------------

``void folderMoveCopyCompleted(aMove, aSrcFolder, aDestFolder)``

Notified after a command to move or copy a folder completes. In case of a move, at this point,
the original folder and its files have already been moved to the new location.

Parameters
^^^^^^^^^^

* in boolean aMove
* in :doc:`nsIMsgFolder` aSrcFolder
* in :doc:`nsIMsgFolder` aDestFolder

folderRenamed
-------------

``void folderRenamed(aOrigFolder, aNewFolder)``

Notified after a folder is renamed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aOrigFolder
* in :doc:`nsIMsgFolder` aNewFolder

folderCompactStart
------------------

``void folderCompactStart(folder)``

Called to indicate nsIMsgFolderCompactor is beginning compaction of the
folder.  If the summary file was missing or out-of-date and a parse
is required, this notification will come after the completion of the
parse.  The compactor will be holding the folder's semaphore when
this notification is generated.  This only happens for local folders
currently.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

  Target folder of the compaction.

folderCompactFinish
-------------------

``void folderCompactFinish(folder)``

Called when nsIMsgFolderCompactor has completed compaction of
the folder. This notification will be generated immediately prior to
the nsIFolderListener::itemEvent() notification with a
"CompactCompleted" atom.  At this point, the folder semaphore has been
released and the database has been committed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

  Target folder of the compaction.

folderReindexTriggered
----------------------

``void folderReindexTriggered(folder)``

The user has opted to rebuild the mork msf index for a folder.
Following this notification, the database will be closed, backed up
(so that header properties can be propagated), and then rebuilt from the
source. The rebuild is triggered by a call to updateFolder, so an
nsIFolderListener OnFolderEvent(folder, FolderLoaded atom) notification
will be received if you want to know when this is all completed.
Note: this event is only generated for Thunderbird because the event
currently comes from Thunderbird-specific code.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

  The folder being reindexed.
