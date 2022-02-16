====================
nsIMsgImapMailFolder
====================

`mailnews/imap/public/nsIMsgImapMailFolder.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIMsgImapMailFolder.idl>`_


Properties
==========

verifiedAsOnlineFolder
----------------------

``attribute boolean verifiedAsOnlineFolder``

explicitlyVerify
----------------

``attribute boolean explicitlyVerify``

hierarchyDelimiter
------------------

``attribute char hierarchyDelimiter``

boxFlags
--------

``attribute long boxFlags``

onlineName
----------

``attribute ACString onlineName``

onlineName is the IMAP name of the mailbox that this folder represents.
It's a path with components separated by hierarchyDelimiter.
For example, "INBOX/bar/wibble", "INBOX.bar.wibble", etc...

isNamespace
-----------

``attribute boolean isNamespace``

canOpenFolder
-------------

``readonly attribute boolean canOpenFolder``

adminUrl
--------

``attribute ACString adminUrl``

hasAdminUrl
-----------

``readonly attribute boolean hasAdminUrl``

performingBiff
--------------

``attribute boolean performingBiff``

hdrParser
---------

``readonly attribute nsIMsgParseMailMsgState hdrParser``

imapIncomingServer
------------------

``readonly attribute nsIImapIncomingServer imapIncomingServer``

autoSyncStateObj
----------------

``readonly attribute nsIAutoSyncState autoSyncStateObj``

shouldUseUtf8FolderName
-----------------------

``readonly attribute boolean shouldUseUtf8FolderName``

serverTotal
-----------

``readonly attribute long serverTotal``

@{
These are used to access the response to the STATUS or SELECT command.
The counts include deleted messages, or headers we haven't downloaded yet.

serverUnseen
------------

``readonly attribute long serverUnseen``

serverRecent
------------

``readonly attribute long serverRecent``

serverNextUID
-------------

``readonly attribute long serverNextUID``

Methods
=======

removeLocalSelf
---------------

``void removeLocalSelf()``

Remove the local version of this folder (used to clean up local folders
which don't correspond to ones on the server).

createClientSubfolderInfo
-------------------------

``void createClientSubfolderInfo(folderName, hierarchyDelimiter, flags, suppressNotification)``

Parameters
^^^^^^^^^^

* in ACString folderName
* in char hierarchyDelimiter
* in long flags
* in boolean suppressNotification

list
----

``void list()``

renameLocal
-----------

``void renameLocal(newname, parent)``

Parameters
^^^^^^^^^^

* in ACString newname
* in :doc:`nsIMsgFolder` parent

prepareToRename
---------------

``void prepareToRename()``

performExpand
-------------

``void performExpand(aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow

recursiveCloseActiveConnections
-------------------------------

``void recursiveCloseActiveConnections(aImapServer)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapIncomingServer` aImapServer

renameClient
------------

``void renameClient(msgWindow, msgFolder, oldName, newName)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` msgWindow
* in :doc:`nsIMsgFolder` msgFolder
* in ACString oldName
* in ACString newName

storeImapFlags
--------------

``void storeImapFlags(aFlags, aAddFlags, aKeysToFlag, aUrlListener)``

Parameters
^^^^^^^^^^

* in long aFlags
* in boolean aAddFlags
* in Array<nsMsgKey> aKeysToFlag
* in :doc:`nsIUrlListener` aUrlListener

setImapFlags
------------

``nsIURI setImapFlags(uids, flags)``

Parameters
^^^^^^^^^^

* in string uids
* in long flags

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

replayOfflineMoveCopy
---------------------

``void replayOfflineMoveCopy(keys, isMove, aDstFolder, aUrlListener, aWindow)``

Parameters
^^^^^^^^^^

* in Array<nsMsgKey> keys
* in boolean isMove
* in :doc:`nsIMsgFolder` aDstFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aWindow

playbackOfflineFolderCreate
---------------------------

``nsIURI playbackOfflineFolderCreate(folderName, aWindow)``

Parameters
^^^^^^^^^^

* in AString folderName
* in :doc:`nsIMsgWindow` aWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

addMoveResultPseudoKey
----------------------

``void addMoveResultPseudoKey(aMsgKey)``

This is called by the offline sync code to tell the imap folder to
remember info about the header with this key (messageId and key) because
it's an offline move result header, and we need to generate an
nsIMsgFolderListener.msgKeyChanged notification when we download the
real header from the imap server.

Parameters
^^^^^^^^^^

* in nsMsgKey aMsgKey

liteSelect
----------

``void liteSelect(aUrlListener, aWindow)``

Select this folder on the imap server without doing a sync of flags or
headers. This is used for offline playback, where we don't want to
download hdrs we don't have, because they may have been offline deleted.

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aWindow

fillInFolderProps
-----------------

``void fillInFolderProps(aFolderProps)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgImapFolderProps` aFolderProps

resetNamespaceReferences
------------------------

``void resetNamespaceReferences()``

folderPrivileges
----------------

``void folderPrivileges(aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aWindow

findOnlineSubFolder
-------------------

``nsIMsgImapMailFolder findOnlineSubFolder(onlineName)``

Parameters
^^^^^^^^^^

* in ACString onlineName

Return value
^^^^^^^^^^^^

* :doc:`nsIMsgImapMailFolder`

addFolderRights
---------------

``void addFolderRights(userName, rights)``

Parameters
^^^^^^^^^^

* in ACString userName
* in ACString rights

refreshFolderRights
-------------------

``void refreshFolderRights()``

markPendingRemoval
------------------

``void markPendingRemoval(aHdr, aMark)``

Mark/unmark the header as pending removal from the offline store. If mark,
this also increases the expungedBytes count on the folder so we know
there's more local disk space to be reclaimed.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgDBHdr` aHdr
* in boolean aMark

expunge
-------

``void expunge(aListener, aMsgWindow)``

Issue an expunge of this folder to the imap server.

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

updateStatus
------------

``void updateStatus(aListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

updateFolderWithListener
------------------------

``void updateFolderWithListener(aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener

issueCommandOnMsgs
------------------

``nsIURI issueCommandOnMsgs(command, uids, aWindow)``

Parameters
^^^^^^^^^^

* in ACString command
* in string uids
* in :doc:`nsIMsgWindow` aWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

fetchCustomMsgAttribute
-----------------------

``nsIURI fetchCustomMsgAttribute(msgAttribute, uids, aWindow)``

Parameters
^^^^^^^^^^

* in ACString msgAttribute
* in string uids
* in :doc:`nsIMsgWindow` aWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

storeCustomKeywords
-------------------

``nsIURI storeCustomKeywords(aMsgWindow, aFlagsToAdd, aFlagsToSubtract, aKeysToStore)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in ACString aFlagsToAdd
* in ACString aFlagsToSubtract
* in Array<nsMsgKey> aKeysToStore

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

notifyIfNewMail
---------------

``void notifyIfNewMail()``

initiateAutoSync
----------------

``void initiateAutoSync(aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIUrlListener` aUrlListener

getQuota
--------

``Array<nsIMsgQuota> getQuota()``

@} */
Return an array of quota items of type nsIMsgQuota defined above.
A not-empty array indicates that the server has provided one or more
sets of quota information on this folder. The array will be empty
- if the server does not supports quotas,
- if there are no resource quotas on this folder, or
- if the folder has yet to be opened (selected) by the user.

Return value
^^^^^^^^^^^^

* Array<:doc:`nsIMsgQuota`>

getOtherUsersWithAccess
-----------------------

``nsIUTF8StringEnumerator getOtherUsersWithAccess()``

List all (human) users apart from the current user who have access to
this folder.

You can find out which rights they have with getRightsForUser().

Return value
^^^^^^^^^^^^

* :doc:`nsIUTF8StringEnumerator`

getPermissionsForUser
---------------------

``ACString getPermissionsForUser(username)``

Which access rights a certain user has for this folder.

Parameters
^^^^^^^^^^

* in ACString username

Return value
^^^^^^^^^^^^

* ACString

  list of flags
  e.g. "lrswipcd" for write access and "lrs" for read only access.

  See RFC 2086 (e.g. Cyrus) and RFC 4314 (e.g. dovecot)

  l = locate = visible in folder list
  r = read = list mails, get/read mail contents
  s = set seen flag = mark read. Does not affect other users.
  d (or t) = delete mails
  w = write = change (other) flags of existing mails
  i = insert = add mails to this folder
  p = post = send mail directly to the submission address for folder
  c (or k) = create subfolders
  (e = expunge = compress)
  (x = delete folder)
  a = admin = change permissions

changePendingTotal
------------------

``void changePendingTotal(aDelta)``

Change the number of "pending" messages in a folder,
messages we know about, but don't have the headers for yet

Parameters
^^^^^^^^^^

* in long aDelta

changePendingUnread
-------------------

``void changePendingUnread(aDelta)``

Change the number of "pending" unread messages in a folder,
unread messages we know about, but don't have the headers for yet

Parameters
^^^^^^^^^^

* in long aDelta
