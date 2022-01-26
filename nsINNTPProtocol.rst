===============
nsINNTPProtocol
===============

`mailnews/news/public/nsINNTPProtocol.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/news/public/nsINNTPProtocol.idl>`_


Properties
==========

isBusy
------

``attribute boolean isBusy``

currentFolder
-------------

``readonly attribute nsIMsgFolder currentFolder``

Methods
=======

LoadNewsUrl
-----------

``void LoadNewsUrl(aUri, aConsumer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aUri
* in :doc:`nsISupports` aConsumer

Initialize
----------

``void Initialize(aURL, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` aURL
* in :doc:`nsIMsgWindow` aMsgWindow

GetLastActiveTimeStamp
----------------------

``void GetLastActiveTimeStamp(aTimeStamp)``

Parameters
^^^^^^^^^^

* out PRTime aTimeStamp

CloseConnection
---------------

``void CloseConnection()``
