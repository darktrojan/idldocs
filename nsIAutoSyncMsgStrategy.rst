======================
nsIAutoSyncMsgStrategy
======================

`mailnews/imap/public/nsIAutoSyncMsgStrategy.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIAutoSyncMsgStrategy.idl>`_


Methods
=======

sort
----

``nsAutoSyncStrategyDecisionType sort(aFolder, aMsgHdr1, aMsgHdr2)``

Returns a relative-priority for the second message by comparing with the first message.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgDBHdr` aMsgHdr1
* in :doc:`nsIMsgDBHdr` aMsgHdr2

Return value
^^^^^^^^^^^^

* nsAutoSyncStrategyDecisionType

isExcluded
----------

``boolean isExcluded(aFolder, aMsgHdr)``

Tests whether the given message should be excluded or not.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIMsgDBHdr` aMsgHdr

Return value
^^^^^^^^^^^^

* boolean
