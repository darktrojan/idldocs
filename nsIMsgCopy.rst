==========
nsIMsgCopy
==========

`mailnews/compose/public/nsIMsgCopy.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgCopy.idl>`_

The contract ID for this component is @mozilla.org/messengercompose/msgcopy;1.

Properties
==========

dstFolder
---------

``readonly attribute nsIMsgFolder dstFolder``

Destination folder of the copy operation. Used when aborting copy operation.

Methods
=======

startCopyOperation
------------------

``void startCopyOperation(aUserIdentity, aFile, aMode, aMsgSendObj, aSavePref, aMsgToReplace)``

Start the process of copying a message file to a message folder. The
destinationfolder depends on pref and deliver mode.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aUserIdentity
* in :doc:`nsIFile` aFile
* in nsMsgDeliverMode aMode
* in :doc:`nsIMsgSend` aMsgSendObj
* in AUTF8String aSavePref
* in :doc:`nsIMsgDBHdr` aMsgToReplace
