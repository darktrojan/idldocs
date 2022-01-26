======================
nsIImapFlagAndUidState
======================

`mailnews/imap/public/nsIImapFlagAndUidState.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapFlagAndUidState.idl>`_


Properties
==========

numberOfMessages
----------------

``readonly attribute long numberOfMessages``

numberOfRecentMessages
----------------------

``readonly attribute long numberOfRecentMessages``

numberOfDeletedMessages
-----------------------

``readonly attribute long numberOfDeletedMessages``

If a full update, the total number of deleted messages
in the folder; if a partial update, the number of deleted
messages in the partial update
*/

partialUIDFetch
---------------

``readonly attribute boolean partialUIDFetch``

If this is true, instead of fetching 1:* (FLAGS), and putting all
UIDs and flags in the array, we only fetched the uids and flags
that changed since the last time we were selected on this folder.
This means we have a sparse array, and should not assume missing
UIDs have been deleted.
*/

supportedUserFlags
------------------

``readonly attribute unsigned short supportedUserFlags``

Set of flags the server supports storing per message. See nsImapCore.h
for the set of flags.

Methods
=======

orSupportedUserFlags
--------------------

``void orSupportedUserFlags(aFlags)``

OR's the  passed in flags with the previous flags because we want to
accumulate the FLAGS and PERMANENTFLAGS response.

Parameters
^^^^^^^^^^

* in unsigned short aFlags

getUidOfMessage
---------------

``void getUidOfMessage(zeroBasedIndex, result)``

Parameters
^^^^^^^^^^

* in long zeroBasedIndex
* out unsigned long result

getMessageFlags
---------------

``void getMessageFlags(zeroBasedIndex, result)``

Parameters
^^^^^^^^^^

* in long zeroBasedIndex
* out unsigned short result

setMessageFlags
---------------

``void setMessageFlags(zeroBasedIndex, flags)``

Parameters
^^^^^^^^^^

* in long zeroBasedIndex
* in unsigned short flags

expungeByIndex
--------------

``void expungeByIndex(zeroBasedIndex)``

Parameters
^^^^^^^^^^

* in unsigned long zeroBasedIndex

addUidFlagPair
--------------

``void addUidFlagPair(uid, flags, zeroBasedIndex)``

Parameters
^^^^^^^^^^

* in unsigned long uid
* in unsigned short flags
* in unsigned long zeroBasedIndex

addUidCustomFlagPair
--------------------

``void addUidCustomFlagPair(uid, customFlag)``

Parameters
^^^^^^^^^^

* in unsigned long uid
* in string customFlag

getCustomFlags
--------------

``string getCustomFlags(uid)``

Parameters
^^^^^^^^^^

* in unsigned long uid

Return value
^^^^^^^^^^^^

* string

reset
-----

``void reset()``

clearCustomFlags
----------------

``void clearCustomFlags(uid)``

Parameters
^^^^^^^^^^

* in unsigned long uid

setCustomAttribute
------------------

``void setCustomAttribute(aUid, aCustomAttributeName, aCustomAttributeValue)``

Adds custom attributes to a hash table for the purpose of storing them
them.

Parameters
^^^^^^^^^^

* in unsigned long aUid
* in ACString aCustomAttributeName
* in ACString aCustomAttributeValue

getCustomAttribute
------------------

``ACString getCustomAttribute(aUid, aCustomAttributeName)``

Gets the custom attributes from the hash table where they were stored earlier
them.

Parameters
^^^^^^^^^^

* in unsigned long aUid
* in ACString aCustomAttributeName

Return value
^^^^^^^^^^^^

* ACString
