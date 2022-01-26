=========================
nsIAutoSyncFolderStrategy
=========================

`mailnews/imap/public/nsIAutoSyncFolderStrategy.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIAutoSyncFolderStrategy.idl>`_


Methods
=======

sort
----

``nsAutoSyncStrategyDecisionType sort(aFolder1, aFolder2)``

Returns a relative-priority for the second folder by comparing with the first one.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder1
* in :doc:`nsIMsgFolder` aFolder2

Return value
^^^^^^^^^^^^

* nsAutoSyncStrategyDecisionType

isExcluded
----------

``boolean isExcluded(aFolder)``

Tests whether the given folder should be excluded or not.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder

Return value
^^^^^^^^^^^^

* boolean
