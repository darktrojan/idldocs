=================
nsIMailboxService
=================

`mailnews/local/public/nsIMailboxService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIMailboxService.idl>`_


Methods
=======

ParseMailbox
------------

``nsIURI ParseMailbox(aMsgWindow, aMailboxPath, aMailboxParser, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIFile` aMailboxPath
* in :doc:`nsIStreamListener` aMailboxParser
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`
