=================
nsIImportFieldMap
=================

`mailnews/import/public/nsIImportFieldMap.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/import/public/nsIImportFieldMap.idl>`_


Properties
==========

skipFirstRecord
---------------

``attribute boolean skipFirstRecord``

numMozFields
------------

``readonly attribute long numMozFields``

mapSize
-------

``readonly attribute long mapSize``

Methods
=======

GetFieldDescription
-------------------

``wstring GetFieldDescription(index)``

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* wstring

SetFieldMapSize
---------------

``void SetFieldMapSize(size)``

Parameters
^^^^^^^^^^

* in long size

DefaultFieldMap
---------------

``void DefaultFieldMap(size)``

Parameters
^^^^^^^^^^

* in long size

GetFieldMap
-----------

``long GetFieldMap(index)``

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* long

SetFieldMap
-----------

``void SetFieldMap(index, fieldNum)``

Parameters
^^^^^^^^^^

* in long index
* in long fieldNum

GetFieldActive
--------------

``boolean GetFieldActive(index)``

Parameters
^^^^^^^^^^

* in long index

Return value
^^^^^^^^^^^^

* boolean

SetFieldActive
--------------

``void SetFieldActive(index, active)``

Parameters
^^^^^^^^^^

* in long index
* in boolean active

SetFieldValue
-------------

``void SetFieldValue(database, row, fieldNum, value)``

Parameters
^^^^^^^^^^

* in :doc:`nsIAbDirectory` database
* in :doc:`nsIAbCard` row
* in long fieldNum
* in AString value
