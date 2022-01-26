==========================
nsILocalMailIncomingServer
==========================

`mailnews/local/public/nsILocalMailIncomingServer.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsILocalMailIncomingServer.idl>`_


Methods
=======

createDefaultMailboxes
----------------------

``void createDefaultMailboxes()``

setFlagsOnDefaultMailboxes
--------------------------

``void setFlagsOnDefaultMailboxes()``

getNewMail
----------

``nsIURI getNewMail(aMsgWindow, aUrlListener, aInbox)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgFolder` aInbox

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`
