======================
nsICopyMessageListener
======================

`mailnews/base/public/nsICopyMessageListener.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsICopyMessageListener.idl>`_


Methods
=======

beginCopy
---------

``void beginCopy()``

startMessage
------------

``void startMessage()``

copyData
--------

``void copyData(aIStream, aLength)``

Parameters
^^^^^^^^^^

* in :doc:`nsIInputStream` aIStream
* in long aLength

endMessage
----------

``void endMessage(key)``

Parameters
^^^^^^^^^^

* in nsMsgKey key

endCopy
-------

``void endCopy(copySucceeded)``

Parameters
^^^^^^^^^^

* in boolean copySucceeded

endMove
-------

``void endMove(moveSucceeded)``

Parameters
^^^^^^^^^^

* in boolean moveSucceeded
