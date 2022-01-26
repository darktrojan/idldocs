============================
nsICopyMessageStreamListener
============================

`mailnews/base/public/nsICopyMessageStreamListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsICopyMessageStreamListener.idl>`_


Methods
=======

Init
----

``void Init(destination)``

Parameters
^^^^^^^^^^

* in :doc:`nsICopyMessageListener` destination

StartMessage
------------

``void StartMessage()``

EndMessage
----------

``void EndMessage(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

EndCopy
-------

``void EndCopy(url, aStatus)``

Parameters
^^^^^^^^^^

* in :doc:`nsISupports` url
* in nsresult aStatus
