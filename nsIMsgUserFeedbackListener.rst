==========================
nsIMsgUserFeedbackListener
==========================

`mailnews/base/public/nsIMsgUserFeedbackListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgUserFeedbackListener.idl>`_

Implement this interface to subscribe to errors and warnings passed out via
nsIMsgMailSession.

Methods
=======

onAlert
-------

``boolean onAlert(aMessage, aUrl)``

Called when an alert from a protocol level implementation is generated.

Parameters
^^^^^^^^^^

* in AString aMessage
* in :doc:`nsIMsgMailNewsUrl` aUrl

Return value
^^^^^^^^^^^^

* boolean

  True if you serviced the alert and it does not need
  to be prompted to the user separately.
  Note: The caller won't prompt if msgWindow in aUrl is
  null, regardless of the value returned.
