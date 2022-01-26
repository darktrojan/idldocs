=========================
nsIMsgAsyncPromptListener
=========================

`mailnews/base/public/nsIMsgAsyncPrompter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgAsyncPrompter.idl>`_

This is used in combination with nsIMsgAsyncPrompter.

Methods
=======

onPromptStart
-------------

``boolean onPromptStart()``

This method has been deprecated, please use onPromptStartAsync instead.

Return value
^^^^^^^^^^^^

* boolean

onPromptStartAsync
------------------

``void onPromptStartAsync(aCallback)``

Called when the listener should do its prompt. This can happen
synchronously or asynchronously, but in any case when done the callback
method should be called.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgAsyncPromptCallback` aCallback

onPromptAuthAvailable
---------------------

``void onPromptAuthAvailable()``

Called in the case that the queued prompt was combined with another and
there is now authentication information available.

onPromptCanceled
----------------

``void onPromptCanceled()``

Called in the case that the queued prompt was combined with another but
the prompt was canceled.
