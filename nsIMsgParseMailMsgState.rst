=======================
nsIMsgParseMailMsgState
=======================

`mailnews/local/public/nsIMsgParseMailMsgState.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIMsgParseMailMsgState.idl>`_


Constants
=========

ParseEnvelopeState
------------------

**Type**: ``long``

**Value**: ``0``


ParseHeadersState
-----------------

**Type**: ``long``

**Value**: ``1``


ParseBodyState
--------------

**Type**: ``long``

**Value**: ``2``


Properties
==========

newMsgHdr
---------

``attribute nsIMsgDBHdr newMsgHdr``

headers
-------

``readonly attribute string headers``

state
-----

``attribute nsMailboxParseState state``

Methods
=======

SetMailDB
---------

``void SetMailDB(aDatabase)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDatabase` aDatabase

SetBackupMailDB
---------------

``void SetBackupMailDB(aDatabase)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDatabase` aDatabase

Clear
-----

``void Clear()``

ParseAFolderLine
----------------

``void ParseAFolderLine(line, lineLength)``

Parameters
^^^^^^^^^^

* in string line
* in unsigned long lineLength

FinishHeader
------------

``void FinishHeader()``

GetAllHeaders
-------------

``long GetAllHeaders(headers)``

Parameters
^^^^^^^^^^

* out string headers

Return value
^^^^^^^^^^^^

* long

setNewKey
---------

``void setNewKey(aKey)``

Set the key to be used for the new message header.

Parameters
^^^^^^^^^^

* in nsMsgKey aKey
