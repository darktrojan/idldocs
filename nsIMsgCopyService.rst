=================
nsIMsgCopyService
=================

`mailnews/base/public/nsIMsgCopyService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgCopyService.idl>`_

nsIMsgCopyService is a central point for kicking off message and folder
copy/move operations.
Each operation is queued up and executed in sequence. The actual work is
handled by folder code in an asynchronous fashion. The folder indicates
completion by calling notifyCompletion().

If the operation was initiated with a non-null nsIMsgCopyServiceListener,
its OnStartCopy() and OnStopCopy() methods will be called when the
operation begins/ends. Any errors are communicated via the result code
parameter passed to OnStopCopy().

Methods
=======

copyMessages
------------

``void copyMessages(srcFolder, messages, dstFolder, isMove, listener, msgWindow, allowUndo)``

Copies or moves existing messages from source folder to destination folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in Array<:doc:`nsIMsgDBHdr`> messages
* in :doc:`nsIMsgFolder` dstFolder
* in boolean isMove
* in :doc:`nsIMsgCopyServiceListener` listener
* in :doc:`nsIMsgWindow` msgWindow
* in boolean allowUndo

copyFolder
----------

``void copyFolder(srcFolder, dstFolder, isMove, listener, msgWindow)``

Copies or moves a folder into an existing destination folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` srcFolder
* in :doc:`nsIMsgFolder` dstFolder
* in boolean isMove
* in :doc:`nsIMsgCopyServiceListener` listener
* in :doc:`nsIMsgWindow` msgWindow

copyFileMessage
---------------

``void copyFileMessage(aFile, dstFolder, msgToReplace, isDraftOrTemplate, aMsgFlags, aMsgKeywords, listener, msgWindow)``

Copies message in rfc format from file to folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in :doc:`nsIMsgFolder` dstFolder
* in :doc:`nsIMsgDBHdr` msgToReplace
* in boolean isDraftOrTemplate
* in unsigned long aMsgFlags
* in ACString aMsgKeywords
* in :doc:`nsIMsgCopyServiceListener` listener
* in :doc:`nsIMsgWindow` msgWindow

notifyCompletion
----------------

``void notifyCompletion(aSupport, dstFolder, result)``

Notify the message copy service that the destination folder has finished
it's messages copying operation so that the copy service can continue
copying the rest of the messages if there are more to copy with.
aSupport and dstFolder uniquely identify a copy service request.

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` aSupport
* in :doc:`nsIMsgFolder` dstFolder
* in nsresult result
