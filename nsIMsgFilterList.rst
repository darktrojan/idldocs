================
nsIMsgFilterList
================

`mailnews/search/public/nsIMsgFilterList.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/search/public/nsIMsgFilterList.idl>`_


Constants
=========

attribNone
----------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``0``


attribVersion
-------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``1``


attribLogging
-------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``2``


attribName
----------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``3``


attribEnabled
-------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``4``


attribDescription
-----------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``5``


attribType
----------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``6``


attribScriptFile
----------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``7``


attribAction
------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``8``


attribActionValue
-----------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``9``


attribCondition
---------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``10``


attribCustomId
--------------

**Type**: ``nsMsgFilterFileAttribValue``

**Value**: ``11``


Properties
==========

listId
------

``readonly attribute ACString listId``

folder
------

``attribute nsIMsgFolder folder``

version
-------

``readonly attribute short version``

arbitraryHeaders
----------------

``readonly attribute ACString arbitraryHeaders``

shouldDownloadAllHeaders
------------------------

``readonly attribute boolean shouldDownloadAllHeaders``

filterCount
-----------

``readonly attribute unsigned long filterCount``

defaultFile
-----------

``attribute nsIFile defaultFile``

loggingEnabled
--------------

``attribute boolean loggingEnabled``

Turn filter logging on or off. Turning logging off will close any
currently-open open logfile.

logStream
---------

``attribute nsIOutputStream logStream``

The log will be written via logStream. This may be null if
loggingEnabled is false or if there is some problem with the logging.

logURL
------

``readonly attribute ACString logURL``

Methods
=======

getFilterAt
-----------

``nsIMsgFilter getFilterAt(filterIndex)``

Parameters
^^^^^^^^^^

* in unsigned long filterIndex

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilter`

getFilterNamed
--------------

``nsIMsgFilter getFilterNamed(filterName)``

Parameters
^^^^^^^^^^

* in AString filterName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilter`

setFilterAt
-----------

``void setFilterAt(filterIndex, filter)``

Parameters
^^^^^^^^^^

* in unsigned long filterIndex
* in :doc:`nsIMsgFilter` filter

removeFilter
------------

``void removeFilter(filter)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilter` filter

removeFilterAt
--------------

``void removeFilterAt(filterIndex)``

Parameters
^^^^^^^^^^

* in unsigned long filterIndex

moveFilterAt
------------

``void moveFilterAt(filterIndex, motion)``

Parameters
^^^^^^^^^^

* in unsigned long filterIndex
* in nsMsgFilterMotionValue motion

moveFilter
----------

``void moveFilter(filter, motion)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilter` filter
* in nsMsgFilterMotionValue motion

insertFilterAt
--------------

``void insertFilterAt(filterIndex, filter)``

Parameters
^^^^^^^^^^

* in unsigned long filterIndex
* in :doc:`nsIMsgFilter` filter

createFilter
------------

``nsIMsgFilter createFilter(name)``

Parameters
^^^^^^^^^^

* in AString name

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgFilter`

saveToFile
----------

``void saveToFile(stream)``

Parameters
^^^^^^^^^^

* in :doc:`nsIOutputStream` stream

parseCondition
--------------

``void parseCondition(aFilter, condition)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFilter` aFilter
* in string condition

saveToDefaultFile
-----------------

``void saveToDefaultFile()``

applyFiltersToHdr
-----------------

``void applyFiltersToHdr(filterType, msgHdr, folder, db, headers, listener, msgWindow)``

Parameters
^^^^^^^^^^

* in nsMsgFilterTypeType filterType
* in :doc:`nsIMsgDBHdr` msgHdr
* in :doc:`nsIMsgFolder` folder
* in :doc:`nsIMsgDatabase` db
* in ACString headers
* in :doc:`nsIMsgFilterHitNotify` listener
* in :doc:`nsIMsgWindow` msgWindow

writeIntAttr
------------

``void writeIntAttr(attrib, value, stream)``

Parameters
^^^^^^^^^^

* in nsMsgFilterFileAttribValue attrib
* in long value
* in :doc:`nsIOutputStream` stream

writeStrAttr
------------

``void writeStrAttr(attrib, value, stream)``

Parameters
^^^^^^^^^^

* in nsMsgFilterFileAttribValue attrib
* in string value
* in :doc:`nsIOutputStream` stream

writeWstrAttr
-------------

``void writeWstrAttr(attrib, value, stream)``

Parameters
^^^^^^^^^^

* in nsMsgFilterFileAttribValue attrib
* in wstring value
* in :doc:`nsIOutputStream` stream

writeBoolAttr
-------------

``void writeBoolAttr(attrib, value, stream)``

Parameters
^^^^^^^^^^

* in nsMsgFilterFileAttribValue attrib
* in boolean value
* in :doc:`nsIOutputStream` stream

matchOrChangeFilterTarget
-------------------------

``boolean matchOrChangeFilterTarget(oldUri, newUri, caseInsensitive)``

Parameters
^^^^^^^^^^

* in AUTF8String oldUri
* in AUTF8String newUri
* in boolean caseInsensitive

Return value
^^^^^^^^^^^^

* boolean

clearLog
--------

``void clearLog()``

flushLogIfNecessary
-------------------

``void flushLogIfNecessary()``

logFilterMessage
----------------

``void logFilterMessage(message, filter)``

Push a message to the filter log file, adding a timestamp.

Parameters
^^^^^^^^^^

* in AString message
* in :doc:`nsIMsgFilter` filter
