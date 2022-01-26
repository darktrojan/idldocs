==============
nsIUrlListener
==============

`mailnews/base/public/nsIUrlListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIUrlListener.idl>`_


Methods
=======

OnStartRunningUrl
-----------------

``void OnStartRunningUrl(url)``

Called to signify the beginning of an URL processing.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` url

OnStopRunningUrl
----------------

``void OnStopRunningUrl(url, aExitCode)``

Called to signify the end of an URL processing.
This call is always preceded by a call to OnStartRunningUrl.

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` url
* in nsresult aExitCode
