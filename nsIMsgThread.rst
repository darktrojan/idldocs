============
nsIMsgThread
============

`mailnews/base/public/nsIMsgThread.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgThread.idl>`_


Properties
==========

threadKey
---------

``attribute nsMsgKey threadKey``

flags
-----

``attribute unsigned long flags``

subject
-------

``attribute ACString subject``

newestMsgDate
-------------

``attribute unsigned long newestMsgDate``

numChildren
-----------

``readonly attribute unsigned long numChildren``

numUnreadChildren
-----------------

``readonly attribute unsigned long numUnreadChildren``

Methods
=======

addChild
--------

``void addChild(child, inReplyTo, threadInThread, announcer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` child
* in :doc:`nsIMsgDBHdr` inReplyTo
* in boolean threadInThread
* in :doc:`nsIDBChangeAnnouncer` announcer

getChildKeyAt
-------------

``nsMsgKey getChildKeyAt(index)``

Parameters
^^^^^^^^^^

* in unsigned long index

Return value
^^^^^^^^^^^^

* nsMsgKey

getChild
--------

``nsIMsgDBHdr getChild(msgKey)``

Parameters
^^^^^^^^^^

* in nsMsgKey msgKey

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

getChildHdrAt
-------------

``nsIMsgDBHdr getChildHdrAt(index)``

Parameters
^^^^^^^^^^

* in unsigned long index

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

getRootHdr
----------

``nsIMsgDBHdr getRootHdr(index)``

Parameters
^^^^^^^^^^

* out long index

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

removeChildAt
-------------

``void removeChildAt(index)``

Parameters
^^^^^^^^^^

* in unsigned long index

removeChildHdr
--------------

``void removeChildHdr(child, announcer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` child
* in :doc:`nsIDBChangeAnnouncer` announcer

markChildRead
-------------

``void markChildRead(bRead)``

Parameters
^^^^^^^^^^

* in boolean bRead

getFirstUnreadChild
-------------------

``nsIMsgDBHdr getFirstUnreadChild()``

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgDBHdr`

enumerateMessages
-----------------

``nsIMsgEnumerator enumerateMessages(parent)``

Parameters
^^^^^^^^^^

* in nsMsgKey parent

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgEnumerator`
