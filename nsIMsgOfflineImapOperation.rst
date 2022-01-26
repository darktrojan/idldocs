==========================
nsIMsgOfflineImapOperation
==========================

`mailnews/db/msgdb/public/nsIMsgOfflineImapOperation.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIMsgOfflineImapOperation.idl>`_


Constants
=========

kFlagsChanged
-------------

**Type**: ``long``

**Value**: ``1``


kMsgMoved
---------

**Type**: ``long``

**Value**: ``2``


kMsgCopy
--------

**Type**: ``long``

**Value**: ``4``


kMoveResult
-----------

**Type**: ``long``

**Value**: ``8``


kAppendDraft
------------

**Type**: ``long``

**Value**: ``16``


kAddedHeader
------------

**Type**: ``long``

**Value**: ``32``


kDeletedMsg
-----------

**Type**: ``long``

**Value**: ``64``


kMsgMarkedDeleted
-----------------

**Type**: ``long``

**Value**: ``128``


kAppendTemplate
---------------

**Type**: ``long``

**Value**: ``256``


kDeleteAllMsgs
--------------

**Type**: ``long``

**Value**: ``512``


kAddKeywords
------------

**Type**: ``long``

**Value**: ``1024``


kRemoveKeywords
---------------

**Type**: ``long``

**Value**: ``2048``


Properties
==========

operation
---------

``attribute nsOfflineImapOperationType operation``

messageKey
----------

``attribute nsMsgKey messageKey``

srcMessageKey
-------------

``attribute nsMsgKey srcMessageKey``

flagOperation
-------------

``attribute imapMessageFlagsType flagOperation``

newFlags
--------

``attribute imapMessageFlagsType newFlags``

destinationFolderURI
--------------------

``attribute AUTF8String destinationFolderURI``

sourceFolderURI
---------------

``attribute AUTF8String sourceFolderURI``

keywordsToAdd
-------------

``readonly attribute string keywordsToAdd``

keywordsToRemove
----------------

``readonly attribute string keywordsToRemove``

numberOfCopies
--------------

``readonly attribute long numberOfCopies``

msgSize
-------

``attribute unsigned long msgSize``

playingBack
-----------

``attribute boolean playingBack``

Methods
=======

clearOperation
--------------

``void clearOperation(operation)``

Parameters
^^^^^^^^^^

* in nsOfflineImapOperationType operation

addKeywordToAdd
---------------

``void addKeywordToAdd(aKeyword)``

Parameters
^^^^^^^^^^

* in string aKeyword

addKeywordToRemove
------------------

``void addKeywordToRemove(aKeyword)``

Parameters
^^^^^^^^^^

* in string aKeyword

addMessageCopyOperation
-----------------------

``void addMessageCopyOperation(destinationBox)``

Parameters
^^^^^^^^^^

* in AUTF8String destinationBox

getCopyDestination
------------------

``string getCopyDestination(copyIndex)``

Parameters
^^^^^^^^^^

* in long copyIndex

Return value
^^^^^^^^^^^^

* string
