=================
nsIMsgMailSession
=================

`mailnews/base/public/nsIMsgMailSession.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgMailSession.idl>`_


Properties
==========

topmostMsgWindow
----------------

``readonly attribute nsIMsgWindow topmostMsgWindow``

Methods
=======

Shutdown
--------

``void Shutdown()``

AddFolderListener
-----------------

``void AddFolderListener(aListener, aNotifyFlags)``

Adds a listener to be notified when folders update.

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` aListener

  The listener to add.
* in folderListenerNotifyFlagValue aNotifyFlags

  A combination of flags detailing on which operations
  to notify the listener. See nsIFolderListener.idl for
  details.

RemoveFolderListener
--------------------

``void RemoveFolderListener(aListener)``

Removes a listener from the folder notification list.

Parameters
^^^^^^^^^^

* in :doc:`nsIFolderListener` aListener

  The listener to remove.

addUserFeedbackListener
-----------------------

``void addUserFeedbackListener(aListener)``

Adds a listener to be notified of alert or prompt style feedback that
should go to the user.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgUserFeedbackListener` aListener

  The listener to add.

removeUserFeedbackListener
--------------------------

``void removeUserFeedbackListener(aListener)``

Removes a user feedback listener.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgUserFeedbackListener` aListener

  The listener to remove.

alertUser
---------

``void alertUser(aMessage, aUrl)``

Call to alert the listeners of the message. If there are no listeners,
or the listeners do not handle the alert, then this function will present
the user with a modal dialog if aMsgWindow isn't null.

Parameters
^^^^^^^^^^

* in AString aMessage
* in :doc:`nsIMsgMailNewsUrl` aUrl

AddMsgWindow
------------

``void AddMsgWindow(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

RemoveMsgWindow
---------------

``void RemoveMsgWindow(msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow

IsFolderOpenInWindow
--------------------

``boolean IsFolderOpenInWindow(folder)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` folder

Return value
^^^^^^^^^^^^

* boolean

ConvertMsgURIToMsgURL
---------------------

``AUTF8String ConvertMsgURIToMsgURL(aURI, aMsgWindow)``

Parameters
^^^^^^^^^^

* in AUTF8String aURI
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* AUTF8String

getDataFilesDir
---------------

``nsIFile getDataFilesDir(dirName)``

Parameters
^^^^^^^^^^

* in string dirName

Return value
^^^^^^^^^^^^

* :doc:`nsIFile`
