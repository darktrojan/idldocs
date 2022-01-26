==================
nsIMsgShutdownTask
==================

`mailnews/base/public/nsIMsgShutdown.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgShutdown.idl>`_


Properties
==========

needsToRunTask
--------------

``readonly attribute boolean needsToRunTask``

Inform the caller whether or not the task needs to be run. This method
gives the task the flexibility to cancel running a task on shutdown
if nothing needs to be run.

Methods
=======

doShutdownTask
--------------

``boolean doShutdownTask(inUrlListener, inMsgWindow)``

At shutdown-time, this function will be called to all registered implementors.
Shutdown will be temporarily postponed until |OnStopRequest()| has been called
on the passed in url-listener.

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` inUrlListener
* in :doc:`nsIMsgWindow` inMsgWindow

Return value
^^^^^^^^^^^^

* boolean

  If the shutdown URL was run or not. If the URL is running, the task
  will be responsible for notifying |inUrlListener| when the task is completed.

getCurrentTaskName
------------------

``AString getCurrentTaskName()``

Get the displayable name of the current task. This textual information will be
shown to the user so they know what shutdown task is being performed.

Return value
^^^^^^^^^^^^

* AString

  The name of the current task being performed.
