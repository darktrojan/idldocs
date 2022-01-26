=============
nsIMailboxUrl
=============

`mailnews/local/public/nsIMailboxUrl.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/local/public/nsIMailboxUrl.idl>`_


Constants
=========

ActionParseMailbox
------------------

**Type**: ``long``

**Value**: ``0``


ActionFetchMessage
------------------

**Type**: ``long``

**Value**: ``1``


ActionCopyMessage
-----------------

**Type**: ``long``

**Value**: ``2``


ActionMoveMessage
-----------------

**Type**: ``long``

**Value**: ``3``


ActionSaveMessageToDisk
-----------------------

**Type**: ``long``

**Value**: ``4``


ActionAppendMessageToDisk
-------------------------

**Type**: ``long``

**Value**: ``5``


ActionFetchPart
---------------

**Type**: ``long``

**Value**: ``6``


Properties
==========

mailboxParser
-------------

``attribute nsIStreamListener mailboxParser``

mailboxCopyHandler
------------------

``attribute nsIStreamListener mailboxCopyHandler``

messageKey
----------

``readonly attribute nsMsgKey messageKey``

numMoveCopyMsgs
---------------

``readonly attribute unsigned long numMoveCopyMsgs``

curMoveCopyMsgIndex
-------------------

``attribute unsigned long curMoveCopyMsgIndex``

messageSize
-----------

``attribute unsigned long messageSize``

mailboxAction
-------------

``attribute nsMailboxAction mailboxAction``

Methods
=======

setMoveCopyMsgKeys
------------------

``void setMoveCopyMsgKeys(keysToFlag)``

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> keysToFlag

getMoveCopyMsgHdrForIndex
-------------------------

``void getMoveCopyMsgHdrForIndex(msgIndex, msgHdr)``

Parameters
^^^^^^^^^^

* in unsigned long msgIndex
* out :doc:`nsIMsgDBHdr` msgHdr
