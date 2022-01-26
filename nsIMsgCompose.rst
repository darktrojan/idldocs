=============
nsIMsgCompose
=============

`mailnews/compose/public/nsIMsgCompose.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgCompose.idl>`_


Properties
==========

identity
--------

``attribute nsIMsgIdentity identity``

The identity currently selected for the message compose object. When set
this may change the signature on a message being composed. Note that
typically SendMsg will be called with the same identity as is set here, but
if it is different the SendMsg version will overwrite this identity.

messageSend
-----------

``attribute nsIMsgSend messageSend``

editor
------

``attribute nsIEditor editor``

domWindow
---------

``readonly attribute mozIDOMWindowProxy domWindow``

compFields
----------

``readonly attribute nsIMsgCompFields compFields``

composeHTML
-----------

``readonly attribute boolean composeHTML``

type
----

``attribute MSG_ComposeType type``

wrapLength
----------

``readonly attribute long wrapLength``

bodyModified
------------

``attribute boolean bodyModified``

savedFolderURI
--------------

``attribute AUTF8String savedFolderURI``

progress
--------

``readonly attribute nsIMsgProgress progress``

originalMsgURI
--------------

``readonly attribute AUTF8String originalMsgURI``

deleteDraft
-----------

``attribute boolean deleteDraft``

insertingQuotedContent
----------------------

``attribute boolean insertingQuotedContent``

deliverMode
-----------

``readonly attribute MSG_DeliverMode deliverMode``

Methods
=======

initialize
----------

``void initialize(aParams, aWindow, aDocShell)``

Initializes the msg compose object.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgComposeParams` aParams
* in mozIDOMWindowProxy aWindow
* in :doc:`nsIDocShell` aDocShell

RegisterStateListener
---------------------

``void RegisterStateListener(stateListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgComposeStateListener` stateListener

UnregisterStateListener
-----------------------

``void UnregisterStateListener(stateListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgComposeStateListener` stateListener

sendMsg
-------

``Promise sendMsg(deliverMode, identity, accountKey, aMsgWindow, progress)``

Parameters
^^^^^^^^^^

* in MSG_DeliverMode deliverMode
* in :doc:`nsIMsgIdentity` identity
* in string accountKey
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIMsgProgress` progress

Return value
^^^^^^^^^^^^

* Promise

sendMsgToServer
---------------

``Promise sendMsgToServer(deliverMode, identity, accountKey)``

After all Compose preparations are complete, send the prepared message to
the server. This exists primarily to allow an override of the sending to
use a non-SMTP method for send.

Parameters
^^^^^^^^^^

* in MSG_DeliverMode deliverMode
* in :doc:`nsIMsgIdentity` identity
* in string accountKey

Return value
^^^^^^^^^^^^

* Promise

CloseWindow
-----------

``void CloseWindow()``

abort
-----

``void abort()``

quoteMessage
------------

``void quoteMessage(msgURI)``

Parameters
^^^^^^^^^^

* in AUTF8String msgURI

AttachmentPrettyName
--------------------

``AUTF8String AttachmentPrettyName(url, charset)``

Parameters
^^^^^^^^^^

* in AUTF8String url
* in string charset

Return value
^^^^^^^^^^^^

* AUTF8String

expandMailingLists
------------------

``void expandMailingLists()``

Expand all mailing lists in the relevant compose fields to include the
members of their output. This method will additionally update the
popularity field of cards in the addressing header.

determineHTMLAction
-------------------

``long determineHTMLAction(aConvertible)``

Returns how we should send this message in terms of HTML, plaintext, or
both. Note that this method should not be called until after mailing lists
have been expanded if correct results are desired.

Parameters
^^^^^^^^^^

* in long aConvertible

Return value
^^^^^^^^^^^^

* long

  The HTML action to use (from nsIMsgCompSendFormat).

bodyConvertible
---------------

``long bodyConvertible()``

The level of "convertibility" of the message body (whole HTML document)
to plaintext.

Return value
^^^^^^^^^^^^

* long

  a value from nsIMsgCompConvertible.

checkCharsetConversion
----------------------

``boolean checkCharsetConversion(identity, fallbackCharset)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity
* out string fallbackCharset

Return value
^^^^^^^^^^^^

* boolean

clearMessageSend
----------------

``void clearMessageSend()``

initEditor
----------

``void initEditor(editor, contentWindow)``

Init the editor THIS USED TO BE [noscript]
Now, this is called after editor is created,
which is triggered by loading startup url from JS.
The completion of document loading is detected by observing
the "obs_documentCreated" command

Parameters
^^^^^^^^^^

* in :doc:`nsIEditor` editor
* in mozIDOMWindowProxy contentWindow

setCiteReference
----------------

``void setCiteReference(citeReference)``

Parameters
^^^^^^^^^^

* in nsString citeReference

processSignature
----------------

``void processSignature(identity, aQuoted, aMsgBody)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` identity
* in boolean aQuoted
* inout nsString aMsgBody

processReplyFlags
-----------------

``void processReplyFlags()``

rememberQueuedDisposition
-------------------------

``void rememberQueuedDisposition()``

convertAndLoadComposeWindow
---------------------------

``void convertAndLoadComposeWindow(aPrefix, aBuf, aSignature, aQuoted, aHTMLEditor)``

Parameters
^^^^^^^^^^

* in nsStringRef aPrefix
* in nsStringRef aBuf
* in nsStringRef aSignature
* in boolean aQuoted
* in boolean aHTMLEditor

notifyStateListeners
--------------------

``void notifyStateListeners(aNotificationType, aResult)``

Parameters
^^^^^^^^^^

* in long aNotificationType
* in nsresult aResult

buildBodyMessageAndSignature
----------------------------

``void buildBodyMessageAndSignature()``

buildQuotedMessageAndSignature
------------------------------

``void buildQuotedMessageAndSignature()``

getQuotingToFollow
------------------

``void getQuotingToFollow(quotingToFollow)``

Parameters
^^^^^^^^^^

* out boolean quotingToFollow

addMsgSendListener
------------------

``void addMsgSendListener(sendListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSendListener` sendListener

removeMsgSendListener
---------------------

``void removeMsgSendListener(sendListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSendListener` sendListener
