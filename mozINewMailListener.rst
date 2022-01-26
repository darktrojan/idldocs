===================
mozINewMailListener
===================

`mailnews/base/public/mozINewMailListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/mozINewMailListener.idl>`_

Callback interface for objects interested in receiving new mail notifications
from mozINewMailNotificationService
NOTE: THIS INTERFACE IS UNDER ACTIVE DEVELOPMENT AND SUBJECT TO CHANGE,
see https://bugzilla.mozilla.org/show_bug.cgi?id=715799

Methods
=======

onCountChanged
--------------

``void onCountChanged(count)``

The new mail notification service will call this when the number of interesting
messages has changed

Parameters
^^^^^^^^^^

* in unsigned long count
