====================
nsIMsgComposeService
====================

`mailnews/compose/public/nsIMsgComposeService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgComposeService.idl>`_


Constants
=========

kForwardAsDefault
-----------------

**Type**: ``unsigned long``

**Value**: ``0``

@{
These constants control how to forward messages in forwardMessage.
kForwardAsDefault uses value of pref "mail.forward_message_mode".

kForwardAsAttachment
--------------------

**Type**: ``unsigned long``

**Value**: ``1``


kForwardInline
--------------

**Type**: ``unsigned long``

**Value**: ``2``


Properties
==========

defaultIdentity
---------------

``readonly attribute nsIMsgIdentity defaultIdentity``

defaultIdentity

@return the default identity, in case no identity has been setup yet, will return null

logComposePerformance
---------------------

``readonly attribute boolean logComposePerformance``

Methods
=======

OpenComposeWindow
-----------------

``void OpenComposeWindow(msgComposeWindowURL, msgHdr, originalMsgURI, type, format, identity, from, aMsgWindow, suppressReplyQuote)``

Open a compose window given a mailto url and other options.

Parameters
^^^^^^^^^^

* in AUTF8String msgComposeWindowURL
* in :doc:`nsIMsgDBHdr` msgHdr
* in AUTF8String originalMsgURI
* in MSG_ComposeType type
* in MSG_ComposeFormat format
* in :doc:`nsIMsgIdentity` identity
* in AUTF8String from
* in :doc:`nsIMsgWindow` aMsgWindow
* in boolean suppressReplyQuote

OpenComposeWindowWithURI
------------------------

``void OpenComposeWindowWithURI(msgComposeWindowURL, aURI, aIdentity)``

Open a compose window given a mailto url and (optionally) an identity.

Parameters
^^^^^^^^^^

* in string msgComposeWindowURL
* in :doc:`nsIURI` aURI
* in :doc:`nsIMsgIdentity` aIdentity

OpenComposeWindowWithParams
---------------------------

``void OpenComposeWindowWithParams(msgComposeWindowURL, params)``

Parameters
^^^^^^^^^^

* in string msgComposeWindowURL
* in :doc:`nsIMsgComposeParams` params

initCompose
-----------

``nsIMsgCompose initCompose(aParams, aWindow, aDocShell)``

Creates an nsIMsgCompose instance and initializes it.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgComposeParams` aParams
* in mozIDOMWindowProxy aWindow
* in :doc:`nsIDocShell` aDocShell

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgCompose`

TimeStamp
---------

``void TimeStamp(label, resetTime)``

Parameters
^^^^^^^^^^

* in string label
* in boolean resetTime

determineComposeHTML
--------------------

``boolean determineComposeHTML(aIdentity, aFormat)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aIdentity
* in MSG_ComposeFormat aFormat

Return value
^^^^^^^^^^^^

* boolean

getParamsForMailto
------------------

``nsIMsgComposeParams getParamsForMailto(aURI)``

given a mailto url, parse the attributes and turn them into a nsIMsgComposeParams object

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aURI

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgComposeParams`

  nsIMsgComposeParams which corresponds to the passed in mailto url

forwardMessage
--------------

``void forwardMessage(forwardTo, msgHdr, msgWindow, server, aForwardType)``

@} */
Allow filters to automatically forward a message to the given address(es).

Parameters
^^^^^^^^^^

* in AString forwardTo
* in :doc:`nsIMsgDBHdr` msgHdr
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgIncomingServer` server
* in unsigned long aForwardType

replyWithTemplate
-----------------

``void replyWithTemplate(msgHdr, templateUri, msgWindow, server)``

Allow filters to automatically reply to a message. The reply message is
based on the given template.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` msgHdr
* in AUTF8String templateUri
* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgIncomingServer` server

registerComposeDocShell
-----------------------

``void registerComposeDocShell(aDocShell, aMsgCompose)``

The docShell of each editor element used for composing should be registered
with this service. docShells passed to initCompose get registered
automatically. The registrations are typically used to get the msgCompose
window when determining what remote content to allow to be displayed.

Parameters
^^^^^^^^^^

* in :doc:`nsIDocShell` aDocShell
* in :doc:`nsIMsgCompose` aMsgCompose

unregisterComposeDocShell
-------------------------

``void unregisterComposeDocShell(aDocShell)``

When an editor docShell is being closed, you should
unregister it from this service. nsIMsgCompose normally calls this
automatically for items passed to initCompose.

Parameters
^^^^^^^^^^

* in :doc:`nsIDocShell` aDocShell

getMsgComposeForDocShell
------------------------

``nsIMsgCompose getMsgComposeForDocShell(aDocShell)``

For a given docShell, returns the nsIMsgCompose object associated with it.

Parameters
^^^^^^^^^^

* in :doc:`nsIDocShell` aDocShell

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgCompose`

  NS_ERROR_FAILURE if we could not find a nsIMsgCompose for
  the passed in docShell.
