===============
nsIDBFolderInfo
===============

`mailnews/db/msgdb/public/nsIDBFolderInfo.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIDBFolderInfo.idl>`_


Properties
==========

flags
-----

``attribute long flags``

highWater
---------

``attribute nsMsgKey highWater``

expiredMark
-----------

``attribute nsMsgKey expiredMark``

folderSize
----------

``attribute long long folderSize``

folderDate
----------

``attribute unsigned long folderDate``

numUnreadMessages
-----------------

``attribute long numUnreadMessages``

numMessages
-----------

``attribute long numMessages``

expungedBytes
-------------

``attribute long long expungedBytes``

imapUidValidity
---------------

``attribute long imapUidValidity``

version
-------

``attribute unsigned long version``

imapTotalPendingMessages
------------------------

``attribute long imapTotalPendingMessages``

imapUnreadPendingMessages
-------------------------

``attribute long imapUnreadPendingMessages``

viewType
--------

``attribute nsMsgViewTypeValue viewType``

viewFlags
---------

``attribute nsMsgViewFlagsTypeValue viewFlags``

sortType
--------

``attribute nsMsgViewSortTypeValue sortType``

sortOrder
---------

``attribute nsMsgViewSortOrderValue sortOrder``

locale
------

``attribute AString locale``

mailboxName
-----------

``attribute AString mailboxName``

knownArtsSet
------------

``attribute string knownArtsSet``

folderName
----------

``attribute ACString folderName``

Methods
=======

orFlags
-------

``long orFlags(aFlags)``

Or's aFlags into flags.

Parameters
^^^^^^^^^^

* in long aFlags

Return value
^^^^^^^^^^^^

* long

  - the resulting flags.

andFlags
--------

``long andFlags(aFlags)``

And's aFlags with flags, set flags to the result

Parameters
^^^^^^^^^^

* in long aFlags

Return value
^^^^^^^^^^^^

* long

  the resulting flags.

onKeyAdded
----------

``void onKeyAdded(aNewKey)``

Allows us to keep track of the highwater mark

Parameters
^^^^^^^^^^

* in nsMsgKey aNewKey

changeNumUnreadMessages
-----------------------

``void changeNumUnreadMessages(aDelta)``

Parameters
^^^^^^^^^^

* in long aDelta

changeNumMessages
-----------------

``void changeNumMessages(aDelta)``

Parameters
^^^^^^^^^^

* in long aDelta

changeExpungedBytes
-------------------

``void changeExpungedBytes(aDelta)``

Parameters
^^^^^^^^^^

* in long aDelta

getCharProperty
---------------

``AUTF8String getCharProperty(propertyName)``

Gets a string property from the folder. Also used for URIs, hence the AUTF8String type.

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* AUTF8String

setCharProperty
---------------

``void setCharProperty(aPropertyName, aPropertyValue)``

Sets a string property from the folder. Also used for URIs, hence the AUTF8String type.

Parameters
^^^^^^^^^^

* in string aPropertyName
* in AUTF8String aPropertyValue

setUint32Property
-----------------

``void setUint32Property(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in unsigned long propertyValue

setInt64Property
----------------

``void setInt64Property(propertyName, propertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in long long propertyValue

getUint32Property
-----------------

``unsigned long getUint32Property(propertyName, defaultValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in unsigned long defaultValue

Return value
^^^^^^^^^^^^

* unsigned long

getInt64Property
----------------

``long long getInt64Property(propertyName, defaultValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in long long defaultValue

Return value
^^^^^^^^^^^^

* long long

getBooleanProperty
------------------

``boolean getBooleanProperty(propertyName, defaultValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in boolean defaultValue

Return value
^^^^^^^^^^^^

* boolean

setBooleanProperty
------------------

``void setBooleanProperty(propertyName, aPropertyValue)``

Parameters
^^^^^^^^^^

* in string propertyName
* in boolean aPropertyValue

GetTransferInfo
---------------

``nsIDBFolderInfo GetTransferInfo()``

Return value
^^^^^^^^^^^^

* :doc:`nsIDBFolderInfo`

initFromTransferInfo
--------------------

``void initFromTransferInfo(transferInfo)``

Parameters
^^^^^^^^^^

* in :doc:`nsIDBFolderInfo` transferInfo

getProperty
-----------

``AString getProperty(propertyName)``

Parameters
^^^^^^^^^^

* in string propertyName

Return value
^^^^^^^^^^^^

* AString

setProperty
-----------

``void setProperty(propertyName, propertyStr)``

Parameters
^^^^^^^^^^

* in string propertyName
* in AString propertyStr
