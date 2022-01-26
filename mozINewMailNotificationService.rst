==============================
mozINewMailNotificationService
==============================

`mailnews/base/public/mozINewMailNotificationService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/mozINewMailNotificationService.idl>`_

New mail notification service. This service watches all the relevant
folder and message change events, preferences etc. and keeps track of
the specific messages the user wants notifications for.
NOTE: THIS INTERFACE IS UNDER ACTIVE DEVELOPMENT AND SUBJECT TO CHANGE,
see https://bugzilla.mozilla.org/show_bug.cgi?id=715799
Registered mozINewMailListeners are called when the message count or
specific list of notified messages changes.
** Should also document the observer service callback that allows
plugins to override notifications by folder

Constants
=========

count
-----

**Type**: ``newMailListenerFlag``

**Value**: ``1``

@name Notification flags
These flags determine which notifications will be sent.
@{

messages
--------

**Type**: ``newMailListenerFlag``

**Value**: ``2``


Properties
==========

messageCount
------------

``readonly attribute long messageCount``

Methods
=======

addListener
-----------

``void addListener(aListener, flags)``

@} */
addListener - Register a mozINewMailListener to receive callbacks
when the count or list of notification-worthy messages
changes.

Parameters
^^^^^^^^^^

* in mozINewMailListener aListener
* in newMailListenerFlag flags

removeListener
--------------

``void removeListener(aListener)``

removeListener - remove a listener from the service

Parameters
^^^^^^^^^^

* in mozINewMailListener aListener
