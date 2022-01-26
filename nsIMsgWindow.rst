============
nsIMsgWindow
============

`mailnews/base/public/nsIMsgWindow.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgWindow.idl>`_


Properties
==========

statusFeedback
--------------

``attribute nsIMsgStatusFeedback statusFeedback``

windowCommands
--------------

``attribute nsIMsgWindowCommands windowCommands``

msgHeaderSink
-------------

``attribute nsIMsgHeaderSink msgHeaderSink``

transactionManager
------------------

``attribute nsITransactionManager transactionManager``

openFolder
----------

``attribute nsIMsgFolder openFolder``

rootDocShell
------------

``attribute nsIDocShell rootDocShell``

@note Setting this attribute has various side effects, including
wiring up this object as the parent nsIURIContentListener for the
passed-in docshell as well as setting the message content policy service
to listen for OnLocationChange notifications.

messageWindowDocShell
---------------------

``readonly attribute nsIDocShell messageWindowDocShell``

@note Small helper function used to optimize our use of a weak reference
on the message window docshell. Under no circumstances should you be
holding on to the docshell returned here outside the scope of your routine.

authPrompt
----------

``readonly attribute nsIAuthPrompt authPrompt``

Returns the auth prompt associated with the window. This will only return
a value if the rootDocShell has been set.

notificationCallbacks
---------------------

``attribute nsIInterfaceRequestor notificationCallbacks``

These are currently used to set notification callbacks on
protocol channels to handle things like bad cert exceptions.

promptDialog
------------

``readonly attribute nsIPrompt promptDialog``

mailCharacterSet
----------------

``attribute ACString mailCharacterSet``

charsetOverride
---------------

``attribute boolean charsetOverride``

Remember the message's charaset was overridden, so it can be inherited (e.g for quoting).

stopped
-------

``attribute boolean stopped``

Has a running url been stopped? If you care about checking
this flag, you need to clear it before you start your operation since
there's no convenient place to clear it.

domWindow
---------

``attribute mozIDOMWindowProxy domWindow``

Methods
=======

displayURIInMessagePane
-----------------------

``void displayURIInMessagePane(uri, clearMsgHdr, principal)``

Parameters
^^^^^^^^^^

* in AString uri
* in boolean clearMsgHdr
* in :doc:`nsIPrincipal` principal

displayHTMLInMessagePane
------------------------

``void displayHTMLInMessagePane(title, body, clearMsgHdr)``

Parameters
^^^^^^^^^^

* in AString title
* in AString body
* in boolean clearMsgHdr

StopUrls
--------

``void StopUrls()``

closeWindow
-----------

``void closeWindow()``

when the msg window is being unloaded from the content window,
we can use this notification to force a flush on anything the
msg window hangs on too. For some reason xpconnect is still hanging
onto the msg window even though all of our objects have let go of it
this forces a release...
