==============
nsIImapService
==============

`mailnews/imap/public/nsIImapService.idl <https://hg.mozilla.org/comm-central/file/tip/mailnews/imap/public/nsIImapService.idl>`_

Most of the nsIImapService methods are friendly front ends for composing and
issuing "imap://" protocol operations. Usually a nsImapUrl will be returned.
This url object is stateful and tracks the issued request.

Properties
==========

cacheStorage
------------

``readonly attribute nsICacheStorage cacheStorage``

Methods
=======

selectFolder
------------

``void selectFolder(aImapMailFolder, aUrlListener, aMsgWindow, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow
* out :doc:`nsIURI` aURL

liteSelectFolder
----------------

``nsIURI liteSelectFolder(aImapMailFolder, aUrlListener, aMsgWindow)``

Select the folder on the imap server without doing a sync of flags or
headers. This is used for offline playback, where we don't want to
download hdrs we don't have, because they may have been offline deleted.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  the url created to run the lite select in.

addImapFetchToUrl
-----------------

``void addImapFetchToUrl(aURL, aImapMailFolder, aMessageIdentifierList, aAdditionalHeader)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgMailNewsUrl` aURL
* in :doc:`nsIMsgFolder` aImapMailFolder
* in ACString aMessageIdentifierList
* in ACString aAdditionalHeader

fetchMessage
------------

``void fetchMessage(aUrl, aImapAction, aImapMailFolder, aImapMessageSink, aMsgWindow, aConsumer, aMessageIdentifierList, convertDataToText, aOutURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapUrl` aUrl
* in :doc:`nsImapState` aImapAction
* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIImapMessageSink` aImapMessageSink
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsISupports` aConsumer
* in ACString aMessageIdentifierList
* in boolean convertDataToText
* out :doc:`nsIURI` aOutURL

noop
----

``void noop(aImapMailFolder, aUrlListener, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL

getHeaders
----------

``void getHeaders(aImapMailFolder, aUrlListener, aURL, aMessageIdentifierList, aMessageIdsAreUID)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in ACString aMessageIdentifierList
* in boolean aMessageIdsAreUID

getBodyStart
------------

``nsIURI getBodyStart(aImapMailFolder, aUrlListener, aMessageIdentifierList, numBytes)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in ACString aMessageIdentifierList
* in long numBytes

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

expunge
-------

``void expunge(aImapMailFolder, aUrlListener, aMsgWindow, aURL)``

Issue an EXPUNGE on the target folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow
* out :doc:`nsIURI` aURL

updateFolderStatus
------------------

``nsIURI updateFolderStatus(aImapMailFolder, aUrlListener)``

Issue a STATUS on the target folder.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  the url created to run the status.

verifyLogon
-----------

``nsIURI verifyLogon(aImapMailFolder, aUrlListener, aMsgWindow)``

Verify that we can login.

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

  - the url that we run.

biff
----

``void biff(aImapMailFolder, aUrlListener, aURL, aUidHighWater)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in unsigned long aUidHighWater

deleteMessages
--------------

``void deleteMessages(aImapMailFolder, aUrlListener, aURL, aMessageIdentifierList, aMessageIdsAreUID)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in ACString aMessageIdentifierList
* in boolean aMessageIdsAreUID

deleteAllMessages
-----------------

``void deleteAllMessages(aImapMailFolder, aUrlListener, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL

addMessageFlags
---------------

``void addMessageFlags(aImapMailFolder, aUrlListener, aURL, aMessageIdentifierList, aFlags, aMessageIdsAreUID)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in ACString aMessageIdentifierList
* in imapMessageFlagsType aFlags
* in boolean aMessageIdsAreUID

subtractMessageFlags
--------------------

``void subtractMessageFlags(aImapMailFolder, aUrlListener, aURL, aMessageIdentifierList, aFlags, aMessageIdsAreUID)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in ACString aMessageIdentifierList
* in imapMessageFlagsType aFlags
* in boolean aMessageIdsAreUID

setMessageFlags
---------------

``void setMessageFlags(aImapMailFolder, aUrlListener, aURL, aMessageIdentifierList, aFlags, aMessageIdsAreUID)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in ACString aMessageIdentifierList
* in imapMessageFlagsType aFlags
* in boolean aMessageIdsAreUID

discoverAllFolders
------------------

``void discoverAllFolders(aImapMailFolder, aUrlListener, aMsgWindow, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow
* out :doc:`nsIURI` aURL

discoverAllAndSubscribedFolders
-------------------------------

``void discoverAllAndSubscribedFolders(aImapMailFolder, aUrlListener, aMsgWindow, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow
* out :doc:`nsIURI` aURL

discoverChildren
----------------

``void discoverChildren(aImapMailFolder, aUrlListener, folderPath, aURL)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aImapMailFolder
* in :doc:`nsIUrlListener` aUrlListener
* in ACString folderPath
* out :doc:`nsIURI` aURL

onlineMessageCopy
-----------------

``void onlineMessageCopy(aSrcFolder, aMessageIds, aDstFolder, aIdsAreUids, aIsMove, aUrlListener, aURL, aCopyState, aWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aSrcFolder
* in ACString aMessageIds
* in :doc:`nsIMsgFolder` aDstFolder
* in boolean aIdsAreUids
* in boolean aIsMove
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in :doc:`nsISupports` aCopyState
* in :doc:`nsIMsgWindow` aWindow

appendMessageFromFile
---------------------

``void appendMessageFromFile(aFile, aDstFolder, aMessageId, idsAreUids, aInSelectedState, aUrlListener, aURL, aCopyState, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIFile` aFile
* in :doc:`nsIMsgFolder` aDstFolder
* in ACString aMessageId
* in boolean idsAreUids
* in boolean aInSelectedState
* in :doc:`nsIUrlListener` aUrlListener
* out :doc:`nsIURI` aURL
* in :doc:`nsISupports` aCopyState
* in :doc:`nsIMsgWindow` aMsgWindow

downloadMessagesForOffline
--------------------------

``void downloadMessagesForOffline(aMessageIds, aSrcFolder, aListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in ACString aMessageIds
* in :doc:`nsIMsgFolder` aSrcFolder
* in :doc:`nsIUrlListener` aListener
* in :doc:`nsIMsgWindow` aMsgWindow

moveFolder
----------

``nsIURI moveFolder(aSrcFolder, aDstFolder, aUrlListener, msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aSrcFolder
* in :doc:`nsIMsgFolder` aDstFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

renameLeaf
----------

``nsIURI renameLeaf(aSrcFolder, aLeafName, aUrlListener, msgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aSrcFolder
* in AString aLeafName
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` msgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

deleteFolder
------------

``nsIURI deleteFolder(aFolder, aUrlListener, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aFolder
* in :doc:`nsIUrlListener` aUrlListener
* in :doc:`nsIMsgWindow` aMsgWindow

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

createFolder
------------

``nsIURI createFolder(aParentFolder, aLeafName, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aParentFolder
* in AString aLeafName
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

listFolder
----------

``nsIURI listFolder(aMailFolder, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

subscribeFolder
---------------

``nsIURI subscribeFolder(aMailFolder, mailboxName, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in AString mailboxName
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

unsubscribeFolder
-----------------

``nsIURI unsubscribeFolder(aMailFolder, mailboxName, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in AString mailboxName
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

ensureFolderExists
------------------

``nsIURI ensureFolderExists(aParentFolder, aLeafName, aMsgWindow, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aParentFolder
* in AString aLeafName
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

getFolderAdminUrl
-----------------

``nsIURI getFolderAdminUrl(aMailFolder, aMsgWindow, aUrlListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aUrlListener

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

issueCommandOnMsgs
------------------

``nsIURI issueCommandOnMsgs(aMailFolder, aMsgWindow, aCommand, aMessageIdentifierList)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in ACString aCommand
* in ACString aMessageIdentifierList

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

fetchCustomMsgAttribute
-----------------------

``nsIURI fetchCustomMsgAttribute(aMailFolder, aMsgWindow, aAttribute, aMessageIdentifierList)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in ACString aAttribute
* in ACString aMessageIdentifierList

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

storeCustomKeywords
-------------------

``nsIURI storeCustomKeywords(aMailFolder, aMsgWindow, flagsToAdd, flagsToSubtract, aMessageIdentifierList)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgFolder` aMailFolder
* in :doc:`nsIMsgWindow` aMsgWindow
* in ACString flagsToAdd
* in ACString flagsToSubtract
* in ACString aMessageIdentifierList

Return value
^^^^^^^^^^^^

* :doc:`nsIURI`

getListOfFoldersOnServer
------------------------

``void getListOfFoldersOnServer(aServer, aMsgWindow)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapIncomingServer` aServer
* in :doc:`nsIMsgWindow` aMsgWindow

getListOfFoldersWithPath
------------------------

``void getListOfFoldersWithPath(aServer, aMsgWindow, folderPath)``

Parameters
^^^^^^^^^^

* in :doc:`nsIImapIncomingServer` aServer
* in :doc:`nsIMsgWindow` aMsgWindow
* in ACString folderPath

playbackAllOfflineOperations
----------------------------

``nsISupports playbackAllOfflineOperations(aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener

Return value
^^^^^^^^^^^^

* :doc:`nsISupports`

downloadAllOffineImapFolders
----------------------------

``void downloadAllOffineImapFolders(aMsgWindow, aListener)``

Parameters
^^^^^^^^^^

* in :doc:`nsIMsgWindow` aMsgWindow
* in :doc:`nsIUrlListener` aListener
