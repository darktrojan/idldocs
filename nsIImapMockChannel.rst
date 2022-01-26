==================
nsIImapMockChannel
==================

`mailnews/imap/public/nsIImapMockChannel.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapMockChannel.idl>`_


Properties
==========

progressEventSink
-----------------

``attribute nsIProgressEventSink progressEventSink``

Methods
=======

GetChannelListener
------------------

``void GetChannelListener(aChannelListener)``

Parameters
^^^^^^^^^^

* out :doc:`nsIStreamListener` aChannelListener

Close
-----

``void Close()``

setImapProtocol
---------------

``void setImapProtocol(aProtocol)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapProtocol` aProtocol

setSecurityInfo
---------------

``void setSecurityInfo(securityInfo)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` securityInfo

setURI
------

``void setURI(uri)``

Parameters
^^^^^^^^^^

* in :doc:`nsIURI` uri
