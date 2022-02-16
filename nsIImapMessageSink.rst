==================
nsIImapMessageSink
==================

`mailnews/imap/public/nsIImapMessageSink.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapMessageSink.idl>`_

nsIImapMessageSink provides a way for the IMAP system to exchange
message-related information with the local folder representation.

The IMAP system could poke folders directly, but going through this
interface has a couple of benefits:

1. It better defines the public coupling between the two systems.
2. It's easier to wrap with a proxy class so the IMAP system can safely
call the methods across thread boundaries (see ImapMessageSinkProxy).

Methods
=======

setupMsgWriteStream
-------------------

``void setupMsgWriteStream(aFile, aAppendDummyEnvelope)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in boolean aAppendDummyEnvelope

parseAdoptedMsgLine
-------------------

``void parseAdoptedMsgLine(aAdoptedMsgLine, aUidOfMsg, aImapUrl)``

Used by the imap protocol code to notify the core backend code about
downloaded imap messages.

Parameters
^^^^^^^^^^

* in string aAdoptedMsgLine
* in nsMsgKey aUidOfMsg
* in :doc:`nsIImapUrl` aImapUrl

normalEndMsgWriteStream
-----------------------

``void normalEndMsgWriteStream(aUidOfMessage, aMarkMsgRead, aImapUrl, aUpdatedMessageSize)``

Notify the backend that the imap protocol is done downloading a message

Parameters
^^^^^^^^^^

* in nsMsgKey aUidOfMessage
* in boolean aMarkMsgRead
* in :doc:`nsIImapUrl` aImapUrl
* in long aUpdatedMessageSize

abortMsgWriteStream
-------------------

``void abortMsgWriteStream()``

beginMessageUpload
------------------

``void beginMessageUpload()``

notifyMessageFlags
------------------

``void notifyMessageFlags(aFlags, aKeywords, aMessageKey, aHighestModSeq)``

Notify the message sink that one or more flags have changed
For Condstore servers, also update the highestMod Sequence

Parameters
^^^^^^^^^^

* in unsigned long aFlags

  - The new flags for the message
* in ACString aKeywords

  keywords for the message
* in nsMsgKey aMessageKey

  - The UID of the message that changed
* in unsigned long long aHighestModSeq

  The highest mod seq the parser has seen
  for this folder
*/

notifyMessageDeleted
--------------------

``void notifyMessageDeleted(aOnlineFolderName, aDeleteAllMsgs, aMsgIdString)``

Parameters
^^^^^^^^^^

* in string aOnlineFolderName
* in boolean aDeleteAllMsgs
* in string aMsgIdString

getMessageSizeFromDB
--------------------

``void getMessageSizeFromDB(aId, aSize)``

Parameters
^^^^^^^^^^

* in string aId
* out unsigned long aSize

setContentModified
------------------

``void setContentModified(aImapUrl, aModified)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aImapUrl
* in :doc:`nsImapContentModifiedType` aModified

getCurMoveCopyMessageInfo
-------------------------

``unsigned long getCurMoveCopyMessageInfo(aRunningUrl, aDate, aKeywords)``

For a message stored in a file, get the message metadata needed to copy
that message to an imap folder

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aRunningUrl
* out PRTime aDate
* out ACString aKeywords

Return value
^^^^^^^^^^^^

* unsigned long

  message flags
