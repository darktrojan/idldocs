===============
nsIMsgSendLater
===============

`mailnews/compose/public/nsIMsgSendLater.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/compose/public/nsIMsgSendLater.idl>`_

nsIMsgSendLater is a service used for sending messages in the background.
Messages should be saved to an identity's unsent messages folder, and then
can be sent by calling sendUnsentMessages.

Although the service supports passing identities as parameters, until bug
317803 is fixed, all identities use the same folder, and hence the option
currently doesn't work.

Properties
==========

statusFeedback
--------------

``attribute nsIMsgStatusFeedback statusFeedback``

sendingMessages
---------------

``readonly attribute boolean sendingMessages``

Methods
=======

sendUnsentMessages
------------------

``void sendUnsentMessages(aIdentity)``

Sends any unsent messages in the identity's unsent messages folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aIdentity

addListener
-----------

``void addListener(aListener)``

Adds an listener to the service to receive notifications.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSendLaterListener` aListener

removeListener
--------------

``void removeListener(aListener)``

Removes a listener from the service.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgSendLaterListener` aListener

Throws
^^^^^^

* NS_ERROR_INVALID_ARG  If the listener was not already added to
  the service.

getUnsentMessagesFolder
-----------------------

``nsIMsgFolder getUnsentMessagesFolder(userIdentity)``

Returns the unsent messages folder for the identity.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` userIdentity

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFolder`

hasUnsentMessages
-----------------

``boolean hasUnsentMessages(aIdentity)``

Returns true if there are any unsent messages to send.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIdentity` aIdentity

Return value
^^^^^^^^^^^^

* boolean
