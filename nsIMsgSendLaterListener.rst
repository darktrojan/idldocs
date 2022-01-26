=======================
nsIMsgSendLaterListener
=======================

`mailnews/compose/public/nsIMsgSendLaterListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSendLaterListener.idl>`_

Implement this interface and add to nsIMsgSendLater to receive notifications
of send later actions.

Methods
=======

onStartSending
--------------

``void onStartSending(aTotalMessageCount)``

Notify the observer that the operation of sending messages later has
started.

Parameters
^^^^^^^^^^

* in unsigned long aTotalMessageCount

onMessageStartSending
---------------------

``void onMessageStartSending(aCurrentMessage, aTotalMessageCount, aMessageHeader, aIdentity)``

Notify the observer that the next message send/copy is starting and
provide details about the message.

Parameters
^^^^^^^^^^

* in unsigned long aCurrentMessage
* in unsigned long aTotalMessageCount
* in :doc:`nsIMsgDBHdr` aMessageHeader
* in :doc:`nsIMsgIdentity` aIdentity

onMessageSendProgress
---------------------

``void onMessageSendProgress(aCurrentMessage, aTotalMessageCount, aMessageSendPercent, aMessageCopyPercent)``

Notify the observer of the current progress of sending a message. The one
function covers sending the message over the network and copying to the
appropriate sent folder.

Parameters
^^^^^^^^^^

* in unsigned long aCurrentMessage
* in unsigned long aTotalMessageCount
* in unsigned long aMessageSendPercent
* in unsigned long aMessageCopyPercent

onMessageSendError
------------------

``void onMessageSendError(aCurrentMessage, aMessageHeader, aStatus, aMsg)``

Notify the observer of an error in the send message later function.

Parameters
^^^^^^^^^^

* in unsigned long aCurrentMessage
* in :doc:`nsIMsgDBHdr` aMessageHeader
* in nsresult aStatus
* in wstring aMsg

onStopSending
-------------

``void onStopSending(aStatus, aMsg, aTotalTried, aSuccessful)``

Notify the observer that the send unsent messages operation has finished.
This is called regardless of the success/failure of the operation.

Parameters
^^^^^^^^^^

* in nsresult aStatus
* in wstring aMsg
* in unsigned long aTotalTried
* in unsigned long aSuccessful
