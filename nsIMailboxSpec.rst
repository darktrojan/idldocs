==============
nsIMailboxSpec
==============

`mailnews/imap/public/nsIMailboxSpec.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIMailboxSpec.idl>`_


Properties
==========

folder_UIDVALIDITY
------------------

``attribute long folder_UIDVALIDITY``

highestModSeq
-------------

``attribute unsigned long long highestModSeq``

The highest modification sequence number the parser has seen
for this mailbox. See IMAP RFC 4551
*/

numMessages
-----------

``attribute long numMessages``

numUnseenMessages
-----------------

``attribute long numUnseenMessages``

numRecentMessages
-----------------

``attribute long numRecentMessages``

nextUID
-------

``attribute long nextUID``

box_flags
---------

``attribute unsigned long box_flags``

supportedUserFlags
------------------

``attribute unsigned long supportedUserFlags``

allocatedPathName
-----------------

``attribute ACString allocatedPathName``

unicharPathName
---------------

``attribute AString unicharPathName``

hierarchyDelimiter
------------------

``attribute char hierarchyDelimiter``

hostName
--------

``attribute ACString hostName``

flagState
---------

``attribute nsIImapFlagAndUidState flagState``

folderSelected
--------------

``attribute boolean folderSelected``

discoveredFromLsub
------------------

``attribute boolean discoveredFromLsub``

onlineVerified
--------------

``attribute boolean onlineVerified``

namespaceForFolder
------------------

``attribute nsImapNamespace namespaceForFolder``
