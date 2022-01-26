=========================
nsIMessengerOSIntegration
=========================

`mailnews/base/public/nsIMessengerOSIntegration.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMessengerOSIntegration.idl>`_

Common interfaces to integrate with different platforms, how they are
implemented depends on the specific platform.

Methods
=======

updateUnreadCount
-----------------

``void updateUnreadCount(unreadCount, unreadTooltip)``

Update the unread count.

Parameters
^^^^^^^^^^

* in unsigned long unreadCount
* in AString unreadTooltip

onExit
------

``void onExit()``

Use this to do necessary clean up on exit, e.g. reset the badge/tray icon.
