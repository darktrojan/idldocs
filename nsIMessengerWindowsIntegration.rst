==============================
nsIMessengerWindowsIntegration
==============================

`mailnews/base/public/nsIMessengerWindowsIntegration.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMessengerWindowsIntegration.idl>`_


Properties
==========

suppressNotification
--------------------

``readonly attribute boolean suppressNotification``

Do not show notifications in some states, e.g. when running a fullscreen app. */

Methods
=======

hideWindow
----------

``void hideWindow(aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIBaseWindow` aWindow

showWindow
----------

``void showWindow(aWindow)``

Parameters
^^^^^^^^^^

* in mozIDOMWindowProxy aWindow
