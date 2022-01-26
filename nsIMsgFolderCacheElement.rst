========================
nsIMsgFolderCacheElement
========================

`mailnews/base/public/nsIMsgFolderCacheElement.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsIMsgFolderCacheElement.idl>`_

Interface for a folder to get/set its values in the foldercache.

Properties
==========

key
---

``readonly attribute ACString key``

Methods
=======

getCachedString
---------------

``AUTF8String getCachedString(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* AUTF8String

getCachedInt32
--------------

``long getCachedInt32(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* long

getCachedUInt32
---------------

``unsigned long getCachedUInt32(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* unsigned long

getCachedInt64
--------------

``long long getCachedInt64(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* long long

setCachedString
---------------

``void setCachedString(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in AUTF8String propertyValue

setCachedInt32
--------------

``void setCachedInt32(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in long propertyValue

setCachedUInt32
---------------

``void setCachedUInt32(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in unsigned long propertyValue

setCachedInt64
--------------

``void setCachedInt64(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in long long propertyValue
