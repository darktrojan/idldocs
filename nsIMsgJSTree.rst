============
nsIMsgJSTree
============

`mailnews/base/public/nsIMsgDBView.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgDBView.idl>`_

A shim of XULTreeElement, with only the methods called by nsMsgDBView.

Methods
=======

beginUpdateBatch
----------------

``void beginUpdateBatch()``

endUpdateBatch
--------------

``void endUpdateBatch()``

invalidate
----------

``void invalidate()``

invalidateRange
---------------

``void invalidateRange(startIndex, endIndex)``

Parameters
^^^^^^^^^^

* in long startIndex
* in long endIndex

rowCountChanged
---------------

``void rowCountChanged(index, count)``

Parameters
^^^^^^^^^^

* in long index
* in long count
