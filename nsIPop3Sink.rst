===========
nsIPop3Sink
===========

`mailnews/local/public/nsIPop3Sink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIPop3Sink.idl>`_


Properties
==========

userAuthenticated
-----------------

``attribute boolean userAuthenticated``

mailAccountURL
--------------

``attribute AUTF8String mailAccountURL``

buildMessageUri
---------------

``attribute boolean buildMessageUri``

messageUri
----------

``attribute AUTF8String messageUri``

baseMessageUri
--------------

``attribute AUTF8String baseMessageUri``

origMessageUri
--------------

``attribute AUTF8String origMessageUri``

popServer
---------

``attribute nsIPop3IncomingServer popServer``

folder
------

``attribute nsIMsgFolder folder``

Methods
=======

beginMailDelivery
-----------------

``boolean beginMailDelivery(uidlDownload, msgWindow)``

Parameters
^^^^^^^^^^

* in boolean uidlDownload
* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* boolean

endMailDelivery
---------------

``void endMailDelivery(protocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIPop3Protocol` protocol

abortMailDelivery
-----------------

``void abortMailDelivery(protocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIPop3Protocol` protocol

incorporateBegin
----------------

``void incorporateBegin(uidlString, flags)``

Parameters
^^^^^^^^^^

* in string uidlString
* in unsigned long flags

incorporateWrite
----------------

``void incorporateWrite(block, length)``

Parameters
^^^^^^^^^^

* in string block
* in long length

incorporateComplete
-------------------

``void incorporateComplete(aMsgWindow, aSize)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in int32_t aSize

incorporateAbort
----------------

``void incorporateAbort(uidlDownload)``

Parameters
^^^^^^^^^^

* in boolean uidlDownload

biffGetNewMail
--------------

``void biffGetNewMail()``

setMsgsToDownload
-----------------

``void setMsgsToDownload(aNumMessages)``

Tell the pop3sink how many messages we're going to download.

Parameters
^^^^^^^^^^

* in unsigned long aNumMessages

setBiffStateAndUpdateFE
-----------------------

``void setBiffStateAndUpdateFE(biffState, numNewMessages, notify)``

Parameters
^^^^^^^^^^

* in unsigned long biffState
* in long numNewMessages
* in boolean notify

setSenderAuthedFlag
-------------------

``void setSenderAuthedFlag(authed)``

Parameters
^^^^^^^^^^

* in boolean authed
