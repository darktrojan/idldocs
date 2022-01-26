==========
nsIMsgSend
==========

`mailnews/compose/public/nsIMsgSend.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSend.idl>`_


Constants
=========

nsMsgDeliverNow
---------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``0``


nsMsgQueueForLater
------------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``1``

Queue the message for sending later, but then wait for the user to
request to send it.

nsMsgSave
---------

**Type**: ``nsMsgDeliverMode``

**Value**: ``2``


nsMsgSaveAs
-----------

**Type**: ``nsMsgDeliverMode``

**Value**: ``3``


nsMsgSaveAsDraft
----------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``4``


nsMsgSaveAsTemplate
-------------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``5``


nsMsgSendUnsent
---------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``6``


nsMsgDeliverBackground
----------------------

**Type**: ``nsMsgDeliverMode``

**Value**: ``8``


Properties
==========

sendReport
----------

``readonly attribute nsIMsgSendReport sendReport``

folderUri
---------

``readonly attribute AUTF8String folderUri``

messageKey
----------

``attribute nsMsgKey messageKey``

processAttachmentsSynchronously
-------------------------------

``readonly attribute boolean processAttachmentsSynchronously``

attachmentCount
---------------

``readonly attribute unsigned long attachmentCount``

pendingAttachmentCount
----------------------

``attribute unsigned long pendingAttachmentCount``

deliveryMode
------------

``readonly attribute nsMsgDeliverMode deliveryMode``

runningRequest
--------------

``attribute nsIRequest runningRequest``

status
------

``attribute nsresult status``

cryptoclosure
-------------

``attribute nsIMsgComposeSecure cryptoclosure``

sendCompFields
--------------

``readonly attribute nsIMsgCompFields sendCompFields``

sendBody
--------

``readonly attribute AString sendBody``

sendBodyType
------------

``readonly attribute ACString sendBodyType``

identity
--------

``readonly attribute nsIMsgIdentity identity``

savedToFolderName
-----------------

``attribute AString savedToFolderName``

dontDeliver
-----------

``attribute boolean dontDeliver``

Methods
=======

createAndSendMessage
--------------------

``Promise createAndSendMessage(aEditor, aUserIdentity, aAccountKey, aFields, aIsDigest, aDontDeliver, aMode, aMsgToReplace, aBodyType, aBody, aParentWindow, aProgress, aListener, aPassword, aOriginalMsgURI, aType)``

Create an rfc822 message and send it.

Parameters
^^^^^^^^^^

* in :doc:`nsIEditor` aEditor
* in :doc:`nsIMsgIdentity` aUserIdentity
* in string aAccountKey
* in :doc:`nsIMsgCompFields` aFields
* in boolean aIsDigest
* in boolean aDontDeliver
* in nsMsgDeliverMode aMode
* in :doc:`nsIMsgDBHdr` aMsgToReplace
* in string aBodyType
* in AString aBody
* in mozIDOMWindowProxy aParentWindow
* in :doc:`nsIMsgProgress` aProgress
* in :doc:`nsIMsgSendListener` aListener
* in AString aPassword
* in AUTF8String aOriginalMsgURI
* in MSG_ComposeType aType

Return value
^^^^^^^^^^^^

* Promise

createRFC822Message
-------------------

``void createRFC822Message(aUserIdentity, aFields, aBodyType, aBody, aCreateAsDraft, aAttachments, aEmbeddedObjects, aListener)``

Creates a file containing an rfc822 message, using the passed information.
aListener's OnStopSending method will get called with the file the message
was stored in. OnStopSending may be called sync or async, depending on
content, so you need to handle both cases.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aUserIdentity
* in :doc:`nsIMsgCompFields` aFields
* in string aBodyType
* in ACString aBody
* in boolean aCreateAsDraft
* in Array<:doc:`nsIMsgAttachedFile`> aAttachments
* in Array<:doc:`nsIMsgEmbeddedImageData`> aEmbeddedObjects
* in :doc:`nsIMsgSendListener` aListener

sendMessageFile
---------------

``Promise sendMessageFile(aUserIdentity, aAccountKey, aFields, aSendIFile, aDeleteSendFileOnCompletion, aDigest, aMode, aMsgToReplace, aListener, aStatusFeedback, aPassword)``

Sends a file to the specified composition fields, via the user identity
provided.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aUserIdentity
* in string aAccountKey
* in :doc:`nsIMsgCompFields` aFields
* in :doc:`nsIFile` aSendIFile
* in boolean aDeleteSendFileOnCompletion
* in boolean aDigest
* in nsMsgDeliverMode aMode
* in :doc:`nsIMsgDBHdr` aMsgToReplace
* in :doc:`nsIMsgSendListener` aListener
* in :doc:`nsIMsgStatusFeedback` aStatusFeedback
* in wstring aPassword

Return value
^^^^^^^^^^^^

* Promise

abort
-----

``void abort()``

fail
----

``nsresult fail(aFailureCode, aErrorMsg)``

Report a send failure.

Parameters
^^^^^^^^^^

* in nsresult aFailureCode
* in wstring aErrorMsg

Return value
^^^^^^^^^^^^

* nsresult

  A modified result value in the case a user action results in
  a different way to handle the failure.

setGUINotificationState
-----------------------

``void setGUINotificationState(aEnableFlag)``

Parameters
^^^^^^^^^^

* in boolean aEnableFlag

BeginCryptoEncapsulation
------------------------

``void BeginCryptoEncapsulation()``

notifyListenerOnStartSending
----------------------------

``void notifyListenerOnStartSending(aMsgID, aMsgSize)``

Parameters
^^^^^^^^^^

* in string aMsgID
* in unsigned long aMsgSize

notifyListenerOnProgress
------------------------

``void notifyListenerOnProgress(aMsgID, aProgress, aProgressMax)``

Parameters
^^^^^^^^^^

* in string aMsgID
* in unsigned long aProgress
* in unsigned long aProgressMax

notifyListenerOnStatus
----------------------

``void notifyListenerOnStatus(aMsgID, aMsg)``

Parameters
^^^^^^^^^^

* in string aMsgID
* in wstring aMsg

notifyListenerOnStopSending
---------------------------

``void notifyListenerOnStopSending(aMsgID, aStatus, aMsg, returnFile)``

Parameters
^^^^^^^^^^

* in string aMsgID
* in nsresult aStatus
* in wstring aMsg
* in :doc:`nsIFile` returnFile

notifyListenerOnTransportSecurityError
--------------------------------------

``void notifyListenerOnTransportSecurityError(msgID, status, secInfo, location)``

Parameters
^^^^^^^^^^

* in string msgID
* in nsresult status
* in :doc:`nsITransportSecurityInfo` secInfo
* in ACString location

deliverAsMailExit
-----------------

``void deliverAsMailExit(aUrl, aExitCode)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUrl
* in nsresult aExitCode

deliverAsNewsExit
-----------------

``void deliverAsNewsExit(aUrl, aExitCode)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUrl
* in nsresult aExitCode

sendDeliveryCallback
--------------------

``void sendDeliveryCallback(aUrl, inIsNewsDelivery, aExitCode)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUrl
* in boolean inIsNewsDelivery
* in nsresult aExitCode

notifyListenerOnStartCopy
-------------------------

``void notifyListenerOnStartCopy()``

notifyListenerOnProgressCopy
----------------------------

``void notifyListenerOnProgressCopy(aProgress, aProgressMax)``

Parameters
^^^^^^^^^^

* in unsigned long aProgress
* in unsigned long aProgressMax

notifyListenerOnStopCopy
------------------------

``void notifyListenerOnStopCopy(aStatus)``

Parameters
^^^^^^^^^^

* in nsresult aStatus

getMessageId
------------

``void getMessageId(messageID)``

Parameters
^^^^^^^^^^

* out ACString messageID

getPartForDomIndex
------------------

``ACString getPartForDomIndex(aDomIndex)``

After a draft is saved, use this to get the mime part number for the dom
node in the editor embedded object list with the passed in index.

Parameters
^^^^^^^^^^

* in long aDomIndex

Return value
^^^^^^^^^^^^

* ACString

  the mime part number for that object.

getDefaultPrompt
----------------

``nsIPrompt getDefaultPrompt()``

Return value
^^^^^^^^^^^^

* :doc:`nsIPrompt`

gatherMimeAttachments
---------------------

``void gatherMimeAttachments()``

getProgress
-----------

``nsIMsgProgress getProgress()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgProgress`

getOutputStream
---------------

``nsIOutputStream getOutputStream()``

Return value
^^^^^^^^^^^^

* :doc:`nsIOutputStream`
