==============
nsIMsgProgress
==============

`mailnews/base/public/nsIMsgProgress.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgProgress.idl>`_


Properties
==========

processCanceledByUser
---------------------

``attribute boolean processCanceledByUser``

msgWindow
---------

``attribute nsIMsgWindow msgWindow``

Methods
=======

openProgressDialog
------------------

``void openProgressDialog(parent, aMsgWindow, dialogURL, inDisplayModal, parameters)``

Open the progress dialog, you can specify parameters through an xpcom object

Parameters
^^^^^^^^^^

* in mozIDOMWindowProxy parent
* in :doc:`nsIMsgWindow` aMsgWindow
* in string dialogURL
* in boolean inDisplayModal
* in :doc:`nsISupports` parameters

closeProgressDialog
-------------------

``void closeProgressDialog(forceClose)``

Parameters
^^^^^^^^^^

* in boolean forceClose

registerListener
----------------

``void registerListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIWebProgressListener` listener

unregisterListener
------------------

``void unregisterListener(listener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIWebProgressListener` listener
