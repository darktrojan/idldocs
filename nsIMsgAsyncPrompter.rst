===================
nsIMsgAsyncPrompter
===================

`mailnews/base/public/nsIMsgAsyncPrompter.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgAsyncPrompter.idl>`_

The nsIMsgAsyncPrompter is intended to provide a way to make asynchronous
message prompts into synchronous ones - so that the user is only prompted
with one at a time.

Methods
=======

queueAsyncAuthPrompt
--------------------

``void queueAsyncAuthPrompt(aKey, aPromptImmediately, aCaller)``

Queues an async prompt request. If there are none queued then this will be
actioned straight away, otherwise the prompt will be queued for action
once previous prompt(s) have been cleared.
Queued prompts using the same aKey may be amalgamated into one prompt to
save repeated prompts to the user.

Parameters
^^^^^^^^^^

* in ACString aKey
* in boolean aPromptImmediately
* in :doc:`nsIMsgAsyncPromptListener` aCaller
