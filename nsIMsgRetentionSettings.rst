=======================
nsIMsgRetentionSettings
=======================

`mailnews/db/msgdb/public/nsIMsgDatabase.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/db/msgdb/public/nsIMsgDatabase.idl>`_


Constants
=========

nsMsgRetainAll
--------------

**Type**: ``unsigned long``

**Value**: ``1``


nsMsgRetainByAge
----------------

**Type**: ``unsigned long``

**Value**: ``2``


nsMsgRetainByNumHeaders
-----------------------

**Type**: ``unsigned long``

**Value**: ``3``


Properties
==========

useServerDefaults
-----------------

``attribute boolean useServerDefaults``

retainByPreference
------------------

``attribute nsMsgRetainByPreference retainByPreference``

daysToKeepHdrs
--------------

``attribute unsigned long daysToKeepHdrs``

numHeadersToKeep
----------------

``attribute unsigned long numHeadersToKeep``

cleanupBodiesByDays
-------------------

``attribute boolean cleanupBodiesByDays``

daysToKeepBodies
----------------

``attribute unsigned long daysToKeepBodies``

applyToFlaggedMessages
----------------------

``attribute boolean applyToFlaggedMessages``

Should retention settings be applied to flagged/starred messages?
If false, flagged messages are never automatically deleted.
