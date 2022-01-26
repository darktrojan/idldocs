===================
nsIImapProtocolSink
===================

`mailnews/imap/public/nsIImapProtocolSink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapProtocolSink.idl>`_

Helper interface that contains operations MUST be proxied
over UI thread.

Methods
=======

closeStreams
------------

``void closeStreams()``

Does general cleanup for the imap protocol object.

getUrlWindow
------------

``nsIMsgWindow getUrlWindow(aUrl)``

Get the msg window associated with a url

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aUrl

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgWindow`

  msgWindow associated with url.

setupMainThreadProxies
----------------------

``void setupMainThreadProxies()``

Setup main thread proxies.
