==============
nsIMsgKeyArray
==============

`mailnews/base/public/nsIMsgKeyArray.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgKeyArray.idl>`_


Properties
==========

length
------

``readonly attribute unsigned long length``

Methods
=======

getKeyAt
--------

``nsMsgKey getKeyAt(aIndex)``

Get the key at the specified 0-based array index.

Parameters
^^^^^^^^^^

* in long aIndex

Return value
^^^^^^^^^^^^

* nsMsgKey

  key at the specified index.

setCapacity
-----------

``void setCapacity(aCapacity)``

Parameters
^^^^^^^^^^

* in unsigned long aCapacity

appendElement
-------------

``void appendElement(aMsgKey)``

Adds a key to the end of the array

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey

insertElementSorted
-------------------

``void insertElementSorted(aMsgKey)``

Inserts a key into a previously sorted array

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey

sort
----

``void sort()``

Sort the array by key.

getArray
--------

``Array<nsMsgKey> getArray()``

Retrieves the entire array in such a way that xpconnect can easily
create a js array of the keys.

Return value
^^^^^^^^^^^^

* Array<nsMsgKey>

  array of the keys
