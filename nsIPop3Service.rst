==============
nsIPop3Service
==============

`mailnews/local/public/nsIPop3Service.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIPop3Service.idl>`_


Methods
=======

GetNewMail
----------

``nsIURI GetNewMail(aMsgWindow, aUrlListener, aInbox, popServer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgFolder` aInbox
* in :doc:`nsIPop3IncomingServer` popServer

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

CheckForNewMail
---------------

``nsIURI CheckForNewMail(aMsgWindow, aUrlListener, inbox, popServer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgFolder` inbox
* in :doc:`nsIPop3IncomingServer` popServer

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

verifyLogon
-----------

``nsIURI verifyLogon(aServer, aUrlListener, aMsgWindow)``

Verify that we can logon

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` aServer

  pop3 server we're logging on to.
* in :doc:`nsIUrlListener` aUrlListener

  gets called back with success or failure.
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  - the url that we run.

addListener
-----------

``void addListener(aListener)``

Add a listener for pop3 events like message download. This is
used by the activity manager.

Parameters
^^^^^^^^^^

* in :doc:`nsIPop3ServiceListener` aListener

removeListener
--------------

``void removeListener(aListener)``

Remove a listener for pop3 events like message download.

Parameters
^^^^^^^^^^

* in :doc:`nsIPop3ServiceListener` aListener

notifyDownloadStarted
---------------------

``void notifyDownloadStarted(aFolder)``

Send the notification that a pop3 download has started.
This is called from the nsIPop3Sink code.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

notifyDownloadProgress
----------------------

``void notifyDownloadProgress(aFolder, aNumDownloaded, aTotalToDownload)``

Send notification about download progress.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumDownloaded
* in unsigned long aTotalToDownload

notifyDownloadCompleted
-----------------------

``void notifyDownloadCompleted(aFolder, aNumberOfMessages)``

Send the notification that a download has completed.
This is called from the nsIPop3Sink code.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in unsigned long aNumberOfMessages
