=====================
nsIMsgShutdownService
=====================

`mailnews/base/public/nsIMsgShutdown.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgShutdown.idl>`_


Methods
=======

getNumTasks
-----------

``long getNumTasks()``

Get the number of tasks that will need to be processed at shutdown time.

Return value
^^^^^^^^^^^^

* long

  The number of shutdown tasks to do.

startShutdownTasks
------------------

``void startShutdownTasks()``

Start the shutdown tasks.

cancelShutdownTasks
-------------------

``void cancelShutdownTasks()``

Tell the service to stop running tasks and go ahead and shutdown the application.

setShutdownListener
-------------------

``void setShutdownListener(inListener)``

Set the shutdown listener.

Parameters
^^^^^^^^^^

* in :doc:`nsIWebProgressListener` inListener

setStatusText
-------------

``void setStatusText(inStatusString)``

Set the status text of the shutdown progress dialog.

Parameters
^^^^^^^^^^

* in AString inStatusString
