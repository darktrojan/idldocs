===============
nsISpamSettings
===============

`mailnews/base/public/nsISpamSettings.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/base/public/nsISpamSettings.idl>`_


Constants
=========

MOVE_TARGET_MODE_ACCOUNT
------------------------

**Type**: ``long``

**Value**: ``0``


MOVE_TARGET_MODE_FOLDER
-----------------------

**Type**: ``long``

**Value**: ``1``


MANUAL_MARK_MODE_MOVE
---------------------

**Type**: ``long``

**Value**: ``0``


MANUAL_MARK_MODE_DELETE
-----------------------

**Type**: ``long``

**Value**: ``1``


TRUST_POSITIVES
---------------

**Type**: ``long``

**Value**: ``1``


TRUST_NEGATIVES
---------------

**Type**: ``long``

**Value**: ``2``


Properties
==========

level
-----

``attribute long level``

0 for nothing, 100 for highest

moveOnSpam
----------

``attribute boolean moveOnSpam``

markAsReadOnSpam
----------------

``readonly attribute boolean markAsReadOnSpam``

moveTargetMode
--------------

``attribute long moveTargetMode``

Most consumers will just use spamFolderURI rather than accessing any of
target attributes directly.

actionTargetAccount
-------------------

``attribute AUTF8String actionTargetAccount``

actionTargetFolder
------------------

``attribute AUTF8String actionTargetFolder``

spamFolderURI
-------------

``readonly attribute AUTF8String spamFolderURI``

built from moveTargetMode, actionTargetAccount, actionTargetFolder

purge
-----

``attribute boolean purge``

purgeInterval
-------------

``attribute long purgeInterval``

interval, in days

useWhiteList
------------

``attribute boolean useWhiteList``

whiteListAbURI
--------------

``attribute AUTF8String whiteListAbURI``

manualMark
----------

``readonly attribute boolean manualMark``

Should we do something when the user manually marks a message as junk?

manualMarkMode
--------------

``readonly attribute long manualMarkMode``

With manualMark true, which action (move to the Junk folder, or delete)
should we take when the user marks a message as junk.

useServerFilter
---------------

``attribute boolean useServerFilter``

integrate with server-side spam detection programs

serverFilterName
----------------

``attribute ACString serverFilterName``

serverFilterFile
----------------

``readonly attribute nsIFile serverFilterFile``

serverFilterTrustFlags
----------------------

``attribute long serverFilterTrustFlags``

loggingEnabled
--------------

``readonly attribute boolean loggingEnabled``

logStream
---------

``attribute nsIOutputStream logStream``

Methods
=======

logJunkHit
----------

``void logJunkHit(aMsgHdr, aMoveMessage)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr
* in boolean aMoveMessage

logJunkString
-------------

``void logJunkString(aLogText)``

Parameters
^^^^^^^^^^

* in string aLogText

clone
-----

``void clone(aSpamSettings)``

Parameters
^^^^^^^^^^

* in :doc:`nsISpamSettings` aSpamSettings

initialize
----------

``void initialize(aServer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgIncomingServer` aServer

checkWhiteList
--------------

``boolean checkWhiteList(aMsgHdr)``

check if junk processing for a message should be bypassed

Typically this is determined by comparing message to: address
to a whitelist of known good addresses or domains.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aMsgHdr

Return value
^^^^^^^^^^^^

* boolean

  true  if this message is whitelisted, and junk
  processing should be bypassed

  false otherwise (including in case of error)
